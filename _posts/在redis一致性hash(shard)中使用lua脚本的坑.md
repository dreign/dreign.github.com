---
title: 在redis一致性hash(shard)中使用lua脚本的坑
date: 2015-12-11 10:15:00
tags: 
categories: 
---
     redis 2.8之前的版本，为了实现支持巨量数据缓存或者持久化，一般需要通过redis sharding模式来实现redis集群，普遍大家使用的是twitter开源的Twemproxy。

> twemproxy不会增加redis的性能指标数据，据业界测算，使用twemproxy相比直接使用redis会带来~10%的性能下降。
但是单个redis进程的内存管理能力有限。据测算，单个redis进程内存超过20G之后，效率会急剧下降。目前，我们给出的建议值是单个redis最好配置在8G以内。8G以上的redis缓存需求，通过twemproxy来提供支持。

twemproxy

不会增加

redis

的性能指标数据，

据业界测算，

使用

twemproxy

相比直接使用

redis

会带来

~10%

的性能下降。





但是单个

redis

进程的内存管理能力有限。

据测算，

单个

redis

进程内存超过

20G

之后，

效率

会急剧下降。目前，我们给出的建议值是单个

redis

最好配置在

8G

以内。

8G

以上的

redis

缓存需求，通过

twemproxy

来提供支持。

     twemproxy的配置信息填写在nutcracker.yml之中，默认的查找位置是在conf目录下，也可以通过-c参数指定。举个栗子：

> twem1:

>

>   listen:"127.0.0.1:22121"

>

>   hash:fnv1a_64

>

>   distribution:ketama

>

>   auto_eject_hosts:false

>

>   server_failure_limit:1

>

>   server_retry_timeout:60000

>

>   redis:true

>

>   servers:

>

>    -"IP1:6379:1 shard1-master"

     你编译或者下载个老版本的ServiceStack.Redis组件（新版本收费了，有貌似1小时6000次的上限，https://servicestack.net/）。然后呢，你可以安心的读写redis了，看起来一切都很美好，某一天发现为了更新一个值，需要频繁的读写redis，这不科学，于是你继续发掘，发现redis支持lua脚本，很多事务性的操作可以直接交给lua脚本一次完成，分分钟改改代码，发个新版本，一些看起来又安逸了。

     突然，客服投诉来啦，说某个数据值不对，查数据库，数据正确的。查redis，哎~果然不对，redis没更新（假设redis是用来做缓存的，mysql做持久化），难道删除redis key更新缓存的方法有问题？你划拉代码看看没啥问题，传递一批key让lua脚本循环删掉这些key，从而达到过期缓存的目的，代码简单，流程清晰。RedisDesktopManager直连redis删除key，ok的，调试代码，的确大概有一半的redis key删除不掉，此时你就掉到redis sharding模型下执行lua脚本的坑里了。

> 坑：redis sharding模型下执行lua脚本时，假设key1在shard1，lua+key1可不一定在shard1。

>

> 即，在proxy上对key1
get/set时，Twemproxy对key1哈希计算后会保证分配到固定的shard上，但通过代理调用lua脚本批量处理redis
key时，哈希散列可能落在不同的shard上。

    

