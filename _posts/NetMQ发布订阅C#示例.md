---
title: NetMQ发布订阅C#示例
date: 2015-01-29 08:44:00
tags: 
categories: 
---
      NetMQ （ZeroMQ to .Net），ØMQ号称史上最快中间件。它对socket通信进行了封装，使得我们不需要写socket函数调用就能完成复杂的网络通信。和一般意义上的消息队列产品不同的是，它没有消息队列服务器，而更像是一个网络通信库。从网络通信的角度看，它处于会话层之上，应用层之下。【ZeroMQ 官网】：[http://zeromq.org](http://zeromq.org/)

      ØMQ有4个基本通信模型：分别是一对一结对模型（Exclusive-Pair）、请求回应模型（Request-Reply）、发布订阅模型（Publish-Subscribe）、推拉模型（Push-Pull）。

**Request-reply pattern 请求-回复模型**  

  * 这种模型主要用于从客户端向一个或多个服务实例发送请求，然后等待紧接着对于每个请求的回复
  * 里面又具体分了ZMQ_REQ ZMQ_REP ZMQ_DEALER ZMQ_ROUTER 
  * REQ 发送完消息后，必须接收一个回应消息后，才能发送新的消息
  * REP当接收消息时，都会返回一个消息 

**Publish-subscribe pattern 发布-订阅模式**

  * 这种模式主要用于1对多的数据发布（一个发布者，多个订阅者）
  * 里面又具体分了ZMQ_PUB ZMQ_SUB 
  * PUB发送消息给所有的SUB。如果此时SUB没有启动，下次启动时会漏掉该消息 

**Pipeline pattern 管道模式**

  * 这种模式主要用于发布数据到由管道排列的节点上面，数据总是沿着管道流动。每个管道阶段连接了至少一个节点
  * 里面又具体分了ZMQ_PUSH ZMQ_PULL
  * 一个1对N队列的实现，PUSH将数据放入队列，PULL从队列中不取出数据。数据会负载均衡的发送给每一个PULL 

**Exclusive pair pattern 独立对模式**

  * peer to peer 模式。主要用于进程内部线程间通信
  * 里面又具体分了ZMQ_PAIR
  * 线程间1-to-1队列的实现，采用了lock free实现，所以速度很快

下面是订阅发布的示例代码：

发布服务端：

    
    
      public static class NetMQPub
        {
            readonly static ManualResetEvent _terminateEvent = new ManualResetEvent(false);
            /// <summary>
            /// NetMQ 发布模式
            /// </summary>
            public static void Start()
            {
                string[] wethers = new string[5] {"晴朗","多云","阴天","小雨","暴雪" };
    
                //CTRL+C 退出程序
                Console.CancelKeyPress += Console_CancelKeyPress;
                Console.WriteLine("发布多个地区天气预报：");
    
                using (var context = NetMQContext.Create())
                {
                    using (var publisher = context.CreatePublisherSocket())
                    {
                        publisher.Bind("tcp://127.0.0.1:5556");
    
                        var rng = new Random();
                        string msg;
                        int sleeptime = 10;
    
                        while (_terminateEvent.WaitOne(0) == false)
                        {
                            //随机生成天气数据
                            int zipcode = rng.Next(0, 99);
                            int temperature = rng.Next(-50, 50);
                            int wetherId = rng.Next(0, 4);
    
                            msg = string.Format("{0} {1} {2}", zipcode, temperature, wethers[wetherId]);
                            publisher.Send(msg,Encoding.UTF8, zmq.SendReceiveOptions.DontWait);
    
                            Console.WriteLine(msg);
                            Thread.Sleep(sleeptime);
                        }
                    }
                }
            }
    
            static void Console_CancelKeyPress(object sender, ConsoleCancelEventArgs e)
            {
                Console.WriteLine("exit...");
                _terminateEvent.Set();
            }
        }
    

订阅客户端，可启动多个实例来模拟接收天气信息：

    
    
      public static class NetMQSub
        {
            public delegate void GetDataHandler(string message);
            public static event GetDataHandler OnGetData;
    
            /// <summary>
            /// NetMQ 订阅模式
            /// </summary>
            public static void Start()
            {            
                var rng = new Random();
                int zipcode = rng.Next(0, 99);
                Console.WriteLine("接收本地天气预报 {0}...", zipcode);
    
                OnGetData += new GetDataHandler(ProcessData);
        
                using (var context = NetMQContext.Create())
                using (var subscriber = context.CreateSubscriberSocket())
                {
                    subscriber.Connect("tcp://127.0.0.1:5556");
                    subscriber.Subscribe(zipcode.ToString(CultureInfo.InvariantCulture));
    
                    while(true)
                    {
                        string results = subscriber.ReceiveString(Encoding.UTF8);
                        Console.Write(".");
    
                        string[] split = results.Split(new[] { ' ' }, StringSplitOptions.RemoveEmptyEntries);
    
                        int zip = int.Parse(split[0]);
                        if (zip == zipcode)
                        {
                            OnGetData(results);
                        }                  
                    }
                }
            }
    
            public static void ProcessData(string msg)
            {
                Console.WriteLine("天气情况：" + msg);
            }
        }
    



