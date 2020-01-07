---
title: CentOS7搭建以太坊私有链
date: 2018-05-07 06:03:00
tags: 
categories: 
---
 1、 环境准备：Win10 64位安装 VM VirtualBox，操作系统版本：

CentOS-7-x86_64-Everything-1611.iso（7.71G）。

切换root账号，方便安装程序

2、 安装Golang 1.9以上版本，yum安装的可以是1.8.3，所以要手动下载安装

国内镜像：<https://studygolang.com/dl>

    
    
    #cd /usr
    #wget https://studygolang.com/dl/golang/go1.10.1.linux-amd64.tar.gz
    # tar -C /root -xzf go1.10.1.linux-amd64.tar.gz
    # cd /root; vi ~/.bashrc
    export GOPATH=/root/Go
    export GOROOT=/root/go
    export PATH=$PATH:$GOROOT/bin
    # source ~/.bashrc
    # go version
    go version go1.10.1 linux/amd64

3、 安装go版本的以太坊源码

    
    
    #cd /usr
    #git clone https://github.com/ethereum/go-ethereum
    #cd go-ethereum
    #make geth

4、 初始化一个创世区块

初始化创世区块时，要先创建一个genesis.json文件，utf-8编码，内容如下：

    
    
    {
      "config": {
            "chainId": 15,
            "homesteadBlock": 0,
            "eip155Block": 0,
            "eip158Block": 0
        },
        "coinbase" : "0x0000000000000000000000000000000000000000",
        "difficulty" : "0x40000",
        "extraData" : "",
        "gasLimit" : "0xffffffff",
        "nonce" : "0x0000000000000042",
        "mixhash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
        "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
        "timestamp" : "0x00",
        "alloc": { }
    }
    

**参数名称**

|

**参数描述**  
  
---|---  
  
mixhash

|

与nonce配合用于挖矿，由上一个区块的一部分生成的hash。注意他和nonce的设置需要满足以太坊的Yellow paper, 4.3.4. Block
Header Validity, (44)章节所描述的条件。  
  
nonce

|

nonce就是一个64位随机数，用于挖矿，注意他和mixhash的设置需要满足以太坊的Yellow paper, 4.3.4. Block Header
Validity, (44)章节所描述的条件。  
  
difficulty

|

设置当前区块的难度，如果难度过大，cpu挖矿就很难，这里设置较小难度  
  
alloc

|

用来预置账号以及账号的以太币数量，因为私有链挖矿比较容易，所以我们不需要预置有币的账号，需要的时候自己创建即可以。  
  
coinbase

|

矿工的账号，随便填  
  
timestamp

|

设置创世块的时间戳  
  
parentHash

|

上一个区块的hash值，因为是创世块，所以这个值是0  
  
extraData

|

附加信息，随便填，可以填你的个性信息  
  
gasLimit

|

该值设置对GAS的消耗总量限制，用来限制区块能包含的交易信息总和，因为我们是私有链，所以填最大。  
  
接下来，我们使用geth init ./inti.json --datadir
"./chain"命令，来进行创世区块的初始化，当前区块链网络数据存放的位置会保存在chain目录中：

    
    
    #cd /usr/go-ethereum/bulid/bin
    # ./geth  --datadir "./chain" init genesis.json



5、 启用私有链



**参数名称**

|

**参数描述**  
  
---|---  
  
datadir

|

设置当前区块链网络数据存放的位置  
  
console

|

启动命令行模式，可以在Geth中执行命令  
  
nodiscover

|

私有链地址，不会被网上看到  
  
使用以下命令，启用私有链：

    
    
    ./geth --datadir "./chain" --nodiscover console 2>>eth_output.log
    
    ./geth \
      --datadir "./chain" \
      --nodiscover \
      console 2>>eth_output.log　　　　

在当前目录执行`tail -f eth_output.log`，可以看到输出日志。

后面章节中的命令，都是在启动私有链后的`Geth javascript console`中操作

6、 帐户的添加和查看

查看帐户，可以看到当前帐户是空的

    
    
    > web3.eth.accounts
    []　
    
    
    　创建帐户的方式有两种，第一种创建帐户时直接初始化密码
    
    
    > web3.personal.newAccount("123456")
    "0x741d379e702f95ea8fdf96df9d8aa34e31b011e9"
    "0xe0b0bf3b64e238814dede73eca9f16e51f386819" 

其中返回的0x741d379e702f95ea8fdf96df9d8aa34e31b011e9是帐户，`123456`是帐户的密码

  
第二种方法是先创建账户，然后输入密码

    
    
    > web3.personal.newAccount()
    Passphrase:
    Repeat passphrase:
    "0x3b0ec02b4193d14abdc9cc5b264b5e3f39624d70"

这时我们再查看帐户，能够看到刚才创建的两个帐户已经存在了

    
    
    > web3.eth.accounts
    ["0xbe323cc4fde114269a9513a27d3e985f82b9e25d", "0x3b0ec02b4193d14abdc9cc5b264b5e3f39624d70"] 

7、 用到的命令汇总：

    
    
    ./geth --datadir "./chain" --nodiscover console 2>>eth_output.log
    web3.eth.accounts
    web3.personal.newAccount("123456")   
    
    miner.start(1) //办公电脑挖矿较慢
    // miner.start(1)  返回 null时，执行以下2语句：
    eth.coinbase
    miner.setEtherbase(eth.coinbase) 
    
    miner.stop()
    web3.eth.getBalance("0x741d379e702f95ea8fdf96df9d8aa34e31b011e9")
    acc0 = web3.eth.accounts[0]
    acc1 = web3.eth.accounts[1]
    acc2 = web3.eth.accounts[2]
    web3.eth.getBalance(acc0)
    web3.fromWei(web3.eth.getBalance(acc0)) 

8、 Linux命令

查看当前端口：netstat -ntlp

杀死指定进程：kill -9 pid

查看日志：tail -f eth_output.log



9、 参考教程：<http://www.cnblogs.com/lion.net/p/7809862.html>



