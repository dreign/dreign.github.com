---
title: 云计算平台简介（App Engine）
date: 2013-03-13 05:16:00
tags: 
categories: 
---

# 1   简介

**App Engine** **： 应用程序引擎，是** **托管网络应用程序的云计算平台。**



## 1.1  什么是云



云计算通常简称为"云"，是一种通过 Internet 按需交付计算资源（从应用到数据中心都属于计算资源）和按使用付费的基础架构。



  * 富有弹性的资源：能快速轻松地扩大或缩小规模，以满足您的需求
  * 按使用付费：计量服务的使用情况，只需为所用的服务付费
  * 自助服务：使用自助服务可访问您需要的所有 IT 资源



## 1.2  云计算部署模型

### **1.2.1** 公共云

公共云由一些公司运营和拥有，这些公司使用这种云为其他组织和个人提供对价格合理的计算资源的快速访问。使用公共云服务，用户无需购买硬件、软件或支持基础架构，这些都是由提供商拥有并管理的。

### **1.2.2** 私有云

私有云由单个公司拥有和运营，该公司控制各个业务线和授权组自定义以及使用各种虚拟化资源和自动服务方式。私有云充分利用了很多云的高效性，同时提供更多的资源控制并明确掌控多租户。



### **1.2.3** 混合云

混合云使用私有云作为基础，同时结合了公共云服务的策略使用。事实是私有云不会独立于公司其他的 IT
资源和公共云而单独存在。大多数使用私有云的公司都将发展为管理跨数据中心的工作负载、私有云和公共云--因此创建了混合云。



## 1.3  云计算服务架构



### **1.3.1** 基础设施即服务(IaaS)：

基础架构即服务以"按使用付费"为基础，为公司提供各种计算资源，包括服务器、网络、存储和数据中心空间。



### **1.3.2** 平台即服务 (PaaS)

平台即服务提供了基于云的环境，其中具有可支持您构建和交付基于
web（云）应用的完整生命周期所需的一切没有购买和管理基础软件、硬件、供应和托管的成本与复杂性。



### **1.3.3** 软件即服务 (SaaS)

基于云的应用--或软件即服务 (SaaS)--在远端"云中的"计算机上运行，这些其他人拥有和运营的云计算机可以通过 Internet 和 web
浏览器连接到用户的计算机。



参考：<http://www-31.ibm.com/ibm/cn/cloud/index.shtml>



## 1.4  常见云平台



**谷歌        GAE**（Google App Engine）

              http://zh.wikipedia.org/wiki/Google_App_Engine

              支持的编程语言：Python、Java、Go（可扩展其它语言）

**新浪        SAE**（Sina App Engine）

              http://sae.sina.com.cn

              开发语言：目前只支持PHP环境，正在组建Python，Java和Nodejs相关的团队

**百度        BAE**（Baidu Cloud Environment）

              http://developer.baidu.com/bae/

              开发语言：Java、 Python， 同时 Node.js 开放内测

**阿里        ACE**（Aliyun Cloud Engine）

              http://www.aliyun.com/product/ace/

              支持PHP,NODE.JS语言编写的应用程序

**盛大        Grand Cloud**

              http://www.grandcloud.cn/product/ae

              支持PHP，Ruby，Java，Python等语言编写的Web应用



亚马逊    Amazon AWS

微软       Microsoft Server Cloud

       http://www.microsoft.com/zh-cn/server-cloud/

IBM cloud computing  

       http://www-935.ibm.com/services/cn/zh/it-services/cloud-services.html

       http://www-31.ibm.com/ibm/cn/cloud

思科       Cisco CloudVerse

       http://www.cisco.com/web/CN/solutions/trends/cloud/index.html

Autotask

       http://www.autotask.cn

# 2   GAE（Google App Engine）

<http://zh.wikipedia.org/wiki/Google_App_Engine>



## 2.1  什么是Google App Engine

**Google App Engine**
是一个开发、托管[网络应用程序](http://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F
"网络应用程序")的平台，使用[Google](http://zh.wikipedia.org/wiki/Google
"Google")管理的数据中心。它在2008年4月发布了第一个[beta](http://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E9%80%B1%E6%9C%9F#Beta
"软件版本周期")版本。

Google App
Engine使用了[云计算](http://zh.wikipedia.org/wiki/%E4%BA%91%E8%AE%A1%E7%AE%97
"云计算")技术。它跨越多个服务器和数据中心来虚拟化应用程序。[[1]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-1)
其他基于云的平台还有[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")和[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Azure%E6%9C%8D%E5%8A%A1%E5%B9%B3%E5%8F%B0
"Azure服务平台")等。

Google App
Engine在用户使用一定的资源时是免费的。支付额外的费用可以获得应用程序所需的更多的存储空间、带宽或是CPU负载。[[2]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-2)

## 2.2  支持的编程语言和框架

当前，Google App
Engine支持的[编程语言](http://zh.wikipedia.org/wiki/%E7%BC%96%E7%A8%8B%E8%AF%AD%E8%A8%80
"编程语言")是[Python](http://zh.wikipedia.org/wiki/Python
"Python")、[Java](http://zh.wikipedia.org/wiki/Java
"Java")和[Go](http://zh.wikipedia.org/wiki/Go
"Go")（通过扩展，可以支持其他[JVM语言](http://zh.wikipedia.org/w/index.php?title=JVM%E8%AF%AD%E8%A8%80&action=edit&redlink=1
"JVM语言（页面不存在）")，诸如[Groovy](http://zh.wikipedia.org/wiki/Groovy
"Groovy")、[JRuby](http://zh.wikipedia.org/wiki/JRuby
"JRuby")、[Scala](http://zh.wikipedia.org/wiki/Scala
"Scala")和[Clojure](http://zh.wikipedia.org/wiki/Clojure
"Clojure")）。支持[Django](http://zh.wikipedia.org/wiki/Django
"Django")、[WebOb](http://zh.wikipedia.org/w/index.php?title=WebOb&action=edit&redlink=1
"WebOb（页面不存在）")、[PyYAML](http://zh.wikipedia.org/wiki/PyYAML
"PyYAML")的有限版本。Google说它准备在未来支持更多的语言，Google App
Engine也将会独立于某种语言。任何支持[WSGI](http://zh.wikipedia.org/wiki/WSGI
"WSGI")的使用CGI的Python框架可以使用。框架可以与开发出的应用程序一同上传，也可以上传使用Python编写的第三方库。[[3]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-3)[[4]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-4)

## 2.3  与其他应用程序托管的区别

与其他可扩展的托管服务（例如[Amazon EC2](http://zh.wikipedia.org/wiki/Amazon_EC2 "Amazon
EC2")）比较，App Engine提供了更多基础服务来方便编写可扩展的应用程序，但仅限于App Engine设计框架以内的应用程序。

App
Engine的基础服务省却了许多系统管理的操作，以便将规模扩大到数以百万计的访问。Google负责处理一组代码，可以监测、容错，在必要的时候还会开发一些应用实例。

有些应用程序托管服务让用户安装、配置几乎所有[*NIX](http://zh.wikipedia.org/wiki/*NIX
"*NIX")兼容的软件，而App Engine则要求开发者使用[Python](http://zh.wikipedia.org/wiki/Python
"Python")或[Java](http://zh.wikipedia.org/wiki/Java
"Java")语言来编程，而且只能使用一套限定的[API](http://zh.wikipedia.org/wiki/API
"API")。当前的API允许程序于一个[BigTable](http://zh.wikipedia.org/wiki/BigTable
"BigTable")非关系数据库上存储和检索数据、提出HTTP请求、发送E-
mail、处理图像、还有[缓存](http://zh.wikipedia.org/wiki/%E7%BC%93%E5%AD%98
"缓存")。大多数现存的Web应用程序，若未经修改，均不能直接在App
Engine上运行，因为它们需要使用[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")。

带宽和CPU的使用、送达请求的数量、并发请求的数量、以及调用各种API的次数，皆设有每天和每分钟的限额。个别的请求，如果需时超过30秒或返回超过10MB的数据，都会被终止。

## 2.4  SQL与GQL的区别

Google App
Engine的Datastore使用一个与SQL类似的语言，叫做"GQL"。在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句仅可以用于一个表。因为要跨越不只一台机器，
GQL不支持效率很低的[JOIN](http://zh.wikipedia.org/w/index.php?title=JOIN&action=edit&redlink=1
"JOIN（页面不存在）")语句[[5]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-5)。欲创建一对多和多对多的关系，可使用ReferenceProperty()[[6]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-6)。采用这种无共享的方式，即使磁盘坏了，系统也不致瘫痪[[7]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-7)。

在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句中的[WHERE](http://zh.wikipedia.org/w/index.php?title=WHERE&action=edit&redlink=1
"WHERE（页面不存在）")从句只容许对仅仅一列进行>、>=、<或<=比较。所以，仅仅可以构造简单的WHERE从句。在数据建模时，要从[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")转换到Datastore，开发者需要转变观念。

App
Engine限制每次Datastore请求最多返回1000行数据。大多数Web应用程序，都不会受此影响，因为它们通常并不会在一张页面上列出超过1000条记录（可以用分页和缓存机制），只要按顺序返回结果就可以了。若有应用程序需要在一次操作中返回更多的记录，则需自行使用客户端软件或者[Ajax](http://zh.wikipedia.org/wiki/Ajax
"Ajax")页面，按查询顺序提取更多条记录。

这个Datastore的API是不关联的，有别于一般关系数据库----比如[IBM
DB2](http://zh.wikipedia.org/wiki/IBM_DB2 "IBM DB2")、[Microsoft SQL
Server](http://zh.wikipedia.org/wiki/Microsoft_SQL_Server "Microsoft SQL
Server")、[MySQL](http://zh.wikipedia.org/wiki/MySQL
"MySQL")、[Oracle数据库](http://zh.wikipedia.org/wiki/Oracle%E6%95%B0%E6%8D%AE%E5%BA%93
"Oracle数据库")、或者[PostgreSQL](http://zh.wikipedia.org/wiki/PostgreSQL
"PostgreSQL")。

## 2.5  限制

  * 在App Engine的文件系统中，开发者只有读取的权限。
  * App Engine仅可在回应HTTP请求时执行代码（计划的后台任务、任务队列和XMPP服务则不在此限）。
  * 用户可以上传任意的Python模块，但必须是纯Python模块，不得包含[C](http://zh.wikipedia.org/wiki/C%E8%AF%AD%E8%A8%80 "C语言")扩展程序或其他需要编译的代码。
  * App Engine限制每次Datastore请求最多返回1000行数据。
  * Java应用程序只能使用JRE基本版本类库中的一个子集（[JRE类白名单](http://code.google.com/appengine/docs/java/jrewhitelist.html)）[[8]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-8)。
  * Java应用程序不能创建新的线程。

## 2.6  可移植性

开发者担心App
Engine应用程序不能移植到其他平台上，因而被困在单一种技术之内。[[9]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-9)

## 2.7  从App Engine下载数据

App
Engine自SDK1.2.2版开始，已容许以批量的方式下载数据[[10]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-10)。此外，用户也可使用开源项目gaebar[[11]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-11)、approcket[[12]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-12)
和gawsh[[13]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-13)
来下载、备份在App Engine上的数据。

## 2.8  限额

免费帐户使用App
Engine时，受配额限制。应用程序作者可以视乎需要，付钱购买更多配额。[[14]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-
Quotas-14)

### **2.8.1** 硬性限制

**项目**

|

**限制**  
  
---|---  
  
每次请求的时间

|

普通请求60秒，任务请求10分钟，后台请求无限  
  
每个应用程序的文件

|

1000个  
  
HTTP响应的大小

|

32 MB  
  
Datastore单项大小

|

1 MB  
  
应用程序代码大小

|

150 MB  
  
### **2.8.2** 免费的配额

供免费使用的配额曾于[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[5月25日](http://zh.wikipedia.org/wiki/5%E6%9C%8825%E6%97%A5
"5月25日")[[15]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-15)
、[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[6月22日](http://zh.wikipedia.org/wiki/6%E6%9C%8822%E6%97%A5
"6月22日")以及[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")[5月](http://zh.wikipedia.org/wiki/5%E6%9C%88
"5月")三度下调[[16]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-16)。

**项目**

|

**配额**  
  
---|---  
  
每天的Email数量

|

100封  
  
每天的输入数据

|

无限  
  
每天的输出数据

|

1 GB  
  
每天可使用CPU

|

28小时  
  
每天调用Datastore API次数

|

50000次*  
  
数据存储

|

1 GB  
  
每天调用URLFetch API次数

|

657000次*  
  
## 2.9  竞争对手

Google App Engine与[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")（一个应用程序服务系统，支持在Amazon的服务器上托管文件、执行代码）直接竞争。不少科技分析师早在多年前已预计过，Google会加入这场竞赛。其中，Techdirt的出版人[Mike
Masnick](http://zh.wikipedia.org/w/index.php?title=Mike_Masnick&action=edit&redlink=1
"Mike
Masnick（页面不存在）")写到，"Google终于了解到它需要霸占网络平台这个地位。我们可以期待，开发及落实易于扩展的网络应用程序会变得越来越容易，而应用程序也会越来越具创意。"[[17]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-17)

此外，[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Windows_Azure "Windows
Azure")也是Google App Engine的竞争对手。

## 2.10 中国大陆封锁

由于Google App
Engine允许用户托管网络应用程序，且服务器不在[中国大陆](http://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9B%BD%E5%A4%A7%E9%99%86
"中国大陆")境内，故有部分用户利用其搭建代理（如[GoAgent](http://zh.wikipedia.org/wiki/GoAgent
"GoAgent")）用于突破[防火长城](http://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E
"防火长城")的[审查](http://zh.wikipedia.org/wiki/%E7%A0%B4%E7%BD%91
"破网")[[18]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-18)，故Google
App Engine的域名appspot.com的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")加密连接长期遭到防火长城的封锁。

[2010年](http://zh.wikipedia.org/wiki/2010%E5%B9%B4
"2010年")[12月20日](http://zh.wikipedia.org/wiki/12%E6%9C%8820%E6%97%A5
"12月20日")，Google App Engine的域名appspot.com遭到防火长城的关键词过滤封锁。由于先前Google App
Engine的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")连接已经被封，故中国大陆境内的用户无法正常连接与使用。此次Google App
Engine被封锁适逢[2010年诺贝尔和平奖](http://zh.wikipedia.org/wiki/2010%E5%B9%B4%E8%AF%BA%E8%B4%9D%E5%B0%94%E5%92%8C%E5%B9%B3%E5%A5%96
"2010年诺贝尔和平奖")颁奖典礼。appspot.com非加密连接于2010年[12月23日](http://zh.wikipedia.org/wiki/12%E6%9C%8823%E6%97%A5
"12月23日")解封。

[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")3月[两会](http://zh.wikipedia.org/wiki/%E4%B8%A4%E4%BC%9A
"两会")召开前夕，appspot.com再次遭到防火长城的关键词过滤封锁及[域名污染](http://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%B1%A1%E6%9F%93
"域名污染")，同时部分服务器的IP地址亦遭到彻底屏蔽，甚至两会结束后至今亦没有解封。

## 2.11 参见

  * [Google产品列表](http://zh.wikipedia.org/wiki/Google%E4%BA%A7%E5%93%81%E5%88%97%E8%A1%A8 "Google产品列表")



# 3   SAE（Sina App Engine）

[http://sae.sina.com.cn](http://sae.sina.com.cn/)



## 3.1  什么是Sina App Engine  



        Sina App Engine（以下简称SAE）是新浪研发中心于2009年8月开始内部开发，并在2009年11月3日正式推出第一个Alpha版本的国内首个公有云计算平台（http://sae.sina.com.cn），  SAE是新浪云计算战略的核心组成部分。     

        SAE作为国内的公有云计算，从开发伊始借鉴吸纳Google、Amazon等国外公司的公有云计算的成功技术经验，并很快推出不同于他们的具有自身特色的云计算平台。SAE选择在国内流行最广的Web开发语言PHP作为首选的支持语言，Web开发者可以在Linux/Mac/Windows上通过SVN或者Web版在线代码编辑器进行开发、部署、调试，团队开发时还可以进行成员协作，不同的角色将对代码、项目拥有不同的权限；SAE提供了一系列分布式计算、存储服务供开发者使用，包括分布式文件存储、分布式数据库集群、分布式缓存、分布式定时服务等，这些服务将大大降低开发者的开发成本。同时又由于SAE整体架构的高可靠性和新浪的品牌保证，大大降低了开发者的运营风险。另外，作为典型的云计算，SAE采用"所付即所用，所付仅所用"的计费理念，通过日志和统计中心精确的计算每个应用的资源消耗（包括CPU、内存、磁盘等）。     

      总之，SAE就是简单高效的分布式Web服务开发、运行平台。 

         目前SAE只支持PHP环境，我们正在组建Python，Java和Nodejs相关的团队

## 3.2  SAE的核心优势

        SAE的基本目标用户有两种，一种是Web开发者，另一种是普通互联网上网人群。

        对于Web开发者，SAE带来的好处有：

         *****  硬件成本更低，无需预先购买设备，承担更大的投入风险     

         *****  开发成本更低，SAE提供许多服务供开发者使用，开发者无需重复开发，包括队列、数据库、缓存、定时、验证码、计数器，几乎覆盖了Web开发的所有领域。另外对于特定开放平台的开发者，比如新浪微博开发者，SAE已经集成了完整的OpenAPI的封装，将开发者的开发成本降到最低。值得一提的是，SAE的开发者目前已经形成了良好的交流氛围，在意见反馈中心、SAE官方群，SAE官方微群可以看到很多热情的开发者在一起共同提高

         *****  运维成本更低，在SAE上的应用无需关心硬件维护、服务监控、数据容灾等操作，SAE会通过其高可靠的架构和方便的监控页面为用户将运维成本降到最低扩展性更强，在SAE上的服务无需关心服务压力猛增时带来的扩容等操作，SAE自动支持服务扩展

         *****  更加安全可靠，SAE自动提供SQL语句性能分析、前端防攻击、代码检查等功能，在SAE上的所有应用均为多机房容灾部署，比传统的部署模式更加安全可靠，并且SAE提供服务的SLA来实现对用户服务质量的承诺

        对于普通上网人群，使用SAE可以：

        使用推荐应用一键安装Web应用，普通用户无需会编码，也可以在瞬间拥有自己的团购、博客、微博、Wiki等。 

## 3.3  SAE整体架构

        SAE从架构上采用分层设计，从上往下分别为反向代理层、路由逻辑层、Web计算服务池。而从Web计算服务层延伸出SAE附属的分布式计算型服务和分布式存储型服务，具体又分成同步计算型服务、异步计算型服务、持久化存储服务、非持久化存储服务。各种服务统一向日志和统计中心汇报，参考下图：





    

        7层反向代理层：HTTP反向代理，在最外层，负责响应用户的HTTP请求，分析请求，并转发到后端的Web服务池上，并提供负载均衡、健康检查等功能。

        服务路由层：逻辑层，负责根据请求的唯一标识，快速的映射（O(1)时间复杂度）到相应的Web服务池，并映射到相应的硬件路径。如果发现映射关系不存在或者错误，则给出相应的错误提示。该层对用户隐藏了很多具体地址信息，使开发者无需关心服务的内部实际分配情况。

        Web服务池：由一些不同特性的Web服务池组成。每个Web服务池实际是由一组Apache(PHP)组成的，这些池按照不同的SLA提供不同级别的服务。每个Web服务进程实际处理用户的HTTP请求，进程运行在HTTP服务沙盒内，同时还内嵌同样运行在SAE沙盒内的PHP解析引擎。用户的代码最终通过接口调用各种服务。

        日志和统计中心：负责对用户所使用的所有服务进行统计和资源计费，并设定的分钟配额，来判定是否有非正常的使用。分钟配额描述了资源消耗的速度，当资源消耗的速度到达一个预警阈值时，SAE通知系统会提前向用户发出一个警告，提醒用户应用在某个服务上的使用可能存在问题，需要介入关注或处理，配额系统是SAE用来保证整个平台稳定的措施之一；日志中心负责将用户所有服务的日志汇总并备份，并提供检索查询服务。

        各种分布式服务：SAE提供几乎可以覆盖Web应用开发所有方面的多种服务，用户可以通过StdLib（可以理解为SAE PHP版的STL）很方便的调用它们。 

## 3.4  SAE的线路特性



                 



    SAE平台出口IP：

     220.181.129.126  
    220.181.129.121  
    220.181.136.229  
    220.181.136.230  
    220.181.129.93  
    220.181.129.102  
    220.181.129.117  
    220.181.129.90





    http接口方需要IP授权可以进行相应的设置。 

## 3.5  SAE的功能

 开发：

         *****    代码检查，帮助检查不良函数并帮助移植

         *****    代码部署

         *****   分布式数据库

         *****    分布式文件存储

         *****    分布式缓存

         *****    各种附属分布式服务，包括图像、定时、任务队列、邮件、计数器等

         *****    对接多个开放平台，如新浪微博开发平台

         *****   代码调优，通过[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)提供

         *****    数据库优化，通过[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)提供

         *****    团队协作，可以邀请好友以不同的权限加入项目

         *****    代码版本管理（计划支持）

运营：

         *****    应用打包，通过我们的应用向导进行推广

         *****   日志，包括访问日志、错误日志等

         *****    资源报表，消耗SAE各项资源的统计

         *****    服务监控，监控各项服务状态

         *****    数据迁移，包括数据库导入、数据库导出等 

## 3.6  SAE提供的服务及两大特性



SAE提供的服务

        SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下：

服务名称

|

类型

|

说明  
  
---|---|---  
  
HTTP+PHP

|

同步计算

|

带SAE沙盒的Apache和Zend为用户提供Web计算服务  
  
[Storage](http://sae.sina.com.cn/?m=devcenter&catId=204)

|

持久化存储

|

提供分布式文件存储  
  
[Memcache](http://sae.sina.com.cn/?m=devcenter&catId=201)

|

非持久化存储

|

提供分布式缓存服务  
  
[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)

|

持久化存储

|

分布式数据库集群，提供[MySQL](http://sae.sina.com.cn/?m=devcenter&catId=192)服务  
  
[TaskQueue](http://sae.sina.com.cn/?m=devcenter&catId=205)

|

异步计算

|

异步离线轻量级任务队列，HTTP方式调用  
  
[DeferredJob](http://sae.sina.com.cn/?m=devcenter&catId=196)

|

异步计算

|

异步离线重量级任务队列，系统方式调用  
  
[Counter](http://sae.sina.com.cn/?m=devcenter&catId=194)

|

持久化存储

|

计数器服务  
  
RankDB

|

持久化存储

|

分布式排行榜服务  
  
[KVDB](http://sae.sina.com.cn/?m=devcenter&catId=199)

|

持久化存储

|

分布式key/value存储服务  
  
[Cron](http://sae.sina.com.cn/?m=devcenter&catId=195)

|

异步计算

|

分布式定时服务  
  
[FetchURL](http://sae.sina.com.cn/?m=devcenter&catId=197)

|

同步计算

|

分布式抓取服务  
  
[TmpFS](http://sae.sina.com.cn/?m=devcenter&catId=206)

|

非持久化存储

|

提供临时文件存储，文件生命周期在一个会话内，Http请求结束文件自动消失  
  
[AppConfig](http://sae.sina.com.cn/?m=devcenter&catId=193)

|



|

提供应用配置功能，取代Apache htaccess  
  
[Mail](http://sae.sina.com.cn/?m=devcenter&catId=200)

|

异步计算

|

邮件发送服务  
  
[Image](http://sae.sina.com.cn/?m=devcenter&catId=198)

|

同步计算

|

图像处理服务  
  
[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)

|

同步计算

|

Facebook提供的强大的PHP调优工具  
  
SVN

|

持久存储

|

用户代码部署的入口点:https://svn.sinaapp.com/yourapp  
  
Online CodeEditor

|

持久存储

|

在线代码编辑器，编辑的代码保存后入自动入SVN并部署到Web服务器  
  
 两大特性：扩展性与可靠性

*****    扩展性

        SAE在服务的可扩展性上基本是动态可扩展性的思路，即资源和ID没有强对应关系，用户以服务使用者的身份使用SAE服务。

*****    可靠性

        在计算可靠性方面，SAE主要是依靠多点部署来完成可靠性，多节点的计算一致性上，SAE有分布式锁服务提供比Paxos更好的容错逻辑。

        在数据可靠性方面，SAE的所有数据都通过冗余存储来达到SLA。SAE通过主动复制和被动复制来实现多点数据冗余。



## 3.7  SAE和虚拟主机的区别

         *****    传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权；而SAE面向的服务，使用者得到的是服务的使用权。 

         *****    传统服务托管不面向开发者，开发者无法在其上享受到开发的乐趣；而SAE的一个重要用户就是web developer，开发者可以在其              上通过在线调试、日志分析、协作共享等功能进行web开发。 

         *****    传统服务托管不提供分布式系统解决方案；而SAE提供的完整的分布式web服务的解决方案，其中不仅仅包括分布式数据库、分布               式文件系统，更包括分布式定时器系统、网页抓取服务、图像处理服务等。

         *****    传统服务托管不解决域名问题，用户往往烦恼于域名申请；而SAE的用户将自动得到在sinaapp下的二级域名，同时SAE还支持域                名cname。 

         *****    传统服务托管无法保证SLA（Service Level Agreement），硬件故障的成本基本由使用者承担；而SAE保证用户的SLA，用户的                   web服务自动享有高冗余的前端服务器、享有自动负载均衡系统、服务自动扩展、服务自动收缩等功能。 

         *****   传统的服务托管采用预付费的方式，费用固定且和实际使用情况无直接关系；而SAE采用预充值方式，"所付即所用，所付仅所用"，             web服务的一切损耗均提供报表查询和账单汇总，让用户一目了然。



SAE公有云计算和传统的虚拟主机的区别如下表。



类项

|

SAE

|

VPS  
  
---|---|---  
  
核心用户

|

Web开发者

|

无核心用户  
  
使用方式

|

服务使用

|

设备租用  
  
目标

|

力争覆盖Web服务所有需求，提供多种服务给开发者使用

|

仅基本需求  
  
SLA（服务承诺）

|

高可靠性及严格的服务承诺

|

依服务商变化，无严格协议  
  
计费方式

|

所付即所用，所付仅所用

|

预付费，无精确计费  
  


## 3.8  为什么我们要做SAE

        Sina App Engine项目始于2009年8月，目标为云计算时代的分布式web服务提供一整套解决方案。我们开发SAE主要是出于对内、对外两方面考虑：

        对内，新浪很早以前就开始了关于私有云的开发和实践，所以为了进一步提高公司资源的利用率，更加提高web开发的效率，降低web运营的成本，决定了我们要开发SAE。

        对外，亚马逊、Google都是国外的成功的提供公有云计算服务的公司，SAE也想借助云计算这样一个趋势，为国内广大用户提供云计算的分布式web服务的开发、运行平台。



## 3.9  SAE的目标和发展  

        云计算虽然是个新名词，但实际在国外已经有4、5年的历史。2006年，亚马逊就推出了以EC2为代表的公有云计算，并且已经实现了大规模盈利；2008年，Google则推出了以Google App Engine为代表的公有云计算。国内的云计算却一直是炒的很厉害，各大互联网公司都在宣传，但真正有技术实力做出来而又对外公开使用的少之又少。

        实际从2004年开始，新浪就开始了私有云方向的研究和实践，以此为基础的动态应用平台目前已经支撑新浪内部的绝大部分业务。从2008年起，新浪又启动了"浪云"的公有云计算计划，相继开发了分布式队列服务、P2P文件系统、分布式计算框架等一系列基础服务。实际SAE就是"浪云"战略的产物。

        SAE从架构设计和代码编写开始，就明确了自身的两个目标：

         *****  做公有云计算平台。公有云不同于私有云，更强调安全性和可靠性，这也对整体的架构设计和技术实现提出了更苛刻的要求

         *****  为分布式Web服务提供一整套的解决方案。SAE争取提供开发者开发Web应用过程中所用到的所有服务。

        经过技术团队一年的开发，SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下： 

        SAE在2009年11月3日发布了alpha1版本，2010年2月1日发布了alpha2版本，2010年9月1日发布了beta版本，2011年5月17日正式开放注册。



## 3.10 加入SAE

        SAE重视每一名Web开发者和普通用户，SAE坚信：

        "SAE的未来取决于能否帮助Web开发者实现其价值体现，取决于是否能和Web开发者实现双赢的良性循环，并最终为互联网所有用户提供高质量的有价值的应用和服务。"

        所以SAE欢迎更多的Web开发者参与，并且欢迎一切喜欢热爱SAE的有志之士能够亲身的参与到SAE整体架构和技术研发中来（简历投递请关注我们的官方微博<http://t.sina.com.cn/saet>和博客[http://blog.sae.sina.com.cn](http://blog.sae.sina.com.cn/)），让我们一起搭建SAE的未来！



# 4   BAE（Baidu Cloud Environment）

<http://developer.baidu.com/bae/>



## 4.1  百度云平台

<http://developer.baidu.com/wiki/index.php?title=docs/cplat>

百度云平台是百度开放其基础能力，为开发者提供的基于"云"的服务的统称，包括云环境，云服务，集成开发环境，移动测试以及移动建站工具等，未来还会加大对移动应用开发的支持。

  
图：百度云平台构成图

## 4.2  云环境

百度云环境，即BCE（Baidu Cloud Environment），提供多语言、弹性的服务端运行环境，能帮助开发者快速 **开发并部署**
应用。云环境内置丰富的分布式计算API，并支持全方位的百度"云"服务，更能为您的应用带来强大动力，从"本地"变"分布式"，简单可依赖。

开发语言：Java、 Python， 同时 Node.js 开放内测

## 4.3  云服务

### **4.3.1** 云数据库

百度云数据库，提供基于MySQL的关系数据库服务。（已转移到应用内管理，详情请参考：[PHP](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/php/mysql
"docs/cplat/rt/php/mysql")
[Java](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/java/mysql
"docs/cplat/rt/java/mysql")
[Python](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/python/mysql
"docs/cplat/rt/python/mysql")）

### **4.3.2** 云存储

百度云存储，即BCS（Baidu Cloud Storage），提供File-Like的开放存储服务，开发者可以在任何时间、任何地点存储任何类型的数据。

### **4.3.3** 云消息

百度云消息，即BCM（Baidu Cloud Messaging），提供消息队列，短消息、电子邮件发送等服务。

### **4.3.4** 云推送

百度云推送（简称Channel）服务为开发者提供了向浏览器、手机和PC客户端推送消息的服务。

### **4.3.5** 云触发

百度云触发（简称Trigger）服务为开发者提供了"数据变更->动作"的触发机制，开发者可以通过使用云触发服务来订阅需要关注的资源，当资源数据发生变化时，服务系统就会自动调用开发者的回调接口。

### **4.3.6** 虚拟机

百度云存储，即BVM（Baidu Virtual Machine），提供多种配置的虚拟机服务。（仅对合作开发者开放）

## 4.4  工具

### **4.4.1** SiteApp

百度SiteApp，是国内首家Web应用在线生成服务，可帮您将传统网站快速转化为移动Web应用。

### **4.4.2** 移动测试中心

百度移动测试中心（MTC），提供主流手机终端的真机的遍历测试，UI适配、安装卸载测试、手动测试等功能。

### **4.4.3** 云众测

百度云众测，输出百万级别社区测试能力，提供APP评测、用户体验反馈、问卷调查等功能。



# 5   ACE（Aliyun Cloud Engine）

<http://www.aliyun.com/product/ace/>



## 5.1  什么是Cloud Engine

ACE（Aliyun Cloud
Engine）是一个基于云计算基础架构的网络应用程序托管环境，帮助应用开发者简化网络应用程序的构建和维护，并可根据应用访问量和数据存储的增长进行扩展。ACE支持PHP,NODE.JS语言编写的应用程序；支持在线创建MYSQL远程数据库应用。

Cloud
Engine（云引擎，简称CE），是阿里云历经多年研发，于今年7月推出的一款基于弹性计算平台的web应用运行环境，能够提供应用的线性伸缩、动态扩容以及多种相关服务。

Cloud
Engine借鉴并吸纳Google、Amazon、Rackspace等国外知名公司的公有云计算的成功技术经验，结合阿里云多年的技术研发沉淀，保证了该平台的高效和稳定。目前支持PHP和NodeJS两种开发语言，后续会支持更多的开发语言。围绕这个平台，我们也提供了session、storage、memcache、cron等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。模板功能的提供，可以有效的衔接开发者和站长，让开发者的成果可以更加有效的传播，同时站长也有更加灵活丰富的应用可以运营。

Cloud App是阿里云手机开发平台，Cloud
Engine作为阿里云手机在云端的延伸，为云手机开发者提供NodeJS运行环境和伸缩性的支持，让开发者有效的衔接手机和云端的开发，简化开发流程。



## 5.2  竞争力

Cloud Engine的目标用户有两种，分别是Web开发者和站长。使用Cloud Engine，可以让您：

1、无需硬件的投资，降低投入风险；

2、内置丰富的服务，包括session，memcache，storage，cron，云数据库，应用管理和配置，覆盖了web开发的大部分领域；

3、高效稳定的运行环境，兼容大部分原生的PHP 5.3程序，弹性伸缩，不用再当心访问量过大；

4、 高效安全的云存储服务，不用当心数据会丢失；

5、经验丰富的阿里运维和安全团队，协助解决网络攻击，网站挂马，漏洞扫描，代码行为分析等，并对服务异常进行告警；

6、 开发人员可以将自己的应用做成模板，发布其应用给其他人使用，站长可以从模板库中在线创建应用，即可进行自己的网站运营。

另外，ISV厂商可以在自己的系统中集成OpenAPI，允许管理和发布用户创建的应用。



## 5.3  应用程序环境

Cloud Engine可以保证您在负载很重和数据量极大的情况下，也可以轻松构建能安全运行的应用程序。

1、自动扩容，用户可以根据自身需求，申请存储，缓存等容量。

2、动态的网络服务，提供对常用网络技术的完全支持

3、持久存储空间，存储用户需要的落地的数据

4、 负载平衡，选择当前较空闲的机器，执行任务

5、与本地开发环境兼容，方便开发者移植代码到CE运行环境

6、分布式定时计算，提供定时和定期触发事件的计划任务。

您的应用程序可在以下两个运行时环境之一中运行：NodeJS 环境和 PHP
环境。各环境均为网络应用程序开发提供标准协议和常用技术。您的应用程序使用NodeJS和PHP的标准API来访问大多数CE服务。



## 5.4  功能介绍



开发：

1、Session，分布式session，开发者无需考虑跨多台机器的session处理

2、Storage，基于开放式存储服务，支持多台机器的同时访问

3、 memcache，分布式缓存，有效解决memcache的多机共享，和实例重启引发的缓存清空

4、cron，通过函数调用方式，支持定时和定期执行任务

5、 应用管理和配置，支持应用的创建、启动、停止、更新、查看等操作

6、mysql数据库支持，双机热备，支持在线迁移和备份，单表可支持上亿记录

运营：

1、开发者可利用模板库分发应用

2、站长可以通过模板库在线快速创建应用

3、平台可监控各种服务的状态

4、 对消耗的资源有详细的统计记录

5、方便的数据导入和导出



## 5.5  云引擎、虚拟主机、VPS的区别



传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权，没有相关的服务；而Cloud
Engine面向的服务，使用者得到的是稳定可靠的全面服务，同时分布式的平台保证了数据的安全性和访问的快速。

** **

|

**云引擎**

|

**虚拟主机**

|

**VPS**  
  
---|---|---|---  
  
用户群

|

web开发者和站长

|

站长

|

没有限定  
  
使用方式

|

服务租用

|

服务租用

|

虚拟设备租用  
  
运行环境

|

支持多种开发语言

|

支持较少开发语言

|

需要自己安装  
  
目标

|

开发者和站长的整体服务

|

展示性的网站

|

仅提供最基本的设施  
  
安全保证

|

沙箱+专业的安全团队

|

根据服务商来定

|

根据用户能力来定  
  
服务承诺

|

稳定可靠安全的服务承诺

|

根据服务商来定

|

根据服务商来定

  
  


## 5.6  发展目标



互联网给PC带来了时代的变革，我们相信，云计算会给互联网带来更大的变革。以亚马逊EC2为代表的IaaS和以Google代表的PaaS，已经在国外掀起了互联网应用的高潮。反观国内，以阿里云为代表的互联网企业，率先将云计算服务落地，并对外提供公有云服务。

阿里云一直有一个目标，就是做一个互联网的数据分享平台，让广大用户可以在这个平台上协作完成数据的分享。我们一直在朝着这个方向努力，Cloud
Engine的诞生就是为了进一步的实现这个目标，帮助广大的开发者和站长实现数据分享的梦想。

因此我们也向用户承诺，我们只做公有云的计算平台，保证平台上数据的安全性和可靠性，提供一个稳定高效的分布式web
service的解决方案，为用户提供尽可能多的服务。



## 5.7  服务限制

为保证应用的安全性和稳定性，我们对各类服务设定了一些限制，请用户仔细阅读。

1、每个用户最多可以创建3个应用，包含从模板创建的应用

2、 禁止本地文件读写，读写文件可以使用我们的OSS（开放存储服务），OSS存储空间不受容量限制

3、对试图破坏或滥用配额（例如同时在多个帐户上操作应用程序）违反服务条款的用户，可能导致应用程序被禁用或帐户关闭

4、我们对PHP环境进行了一些限制，具体参考：http://ace.aliyun.com/index/help/



## 5.8  产品详情



### **5.8.1** 支持多种WEB运行环境

ACE目前支持PHP运行环境，NodeJS运行环境，后续会支持更多的开发语言。

### **5.8.2** 丰富的附加服务

我们提供了分布式session，分布式memcache，开放存储，消息队列，计划任务等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。



### **5.8.3** 弹性伸缩、按需计费

自动弹性伸缩，无需人工干预运维，根据实际使用量计费。



### **5.8.4** 通过应用模板快速部署应用

系统自带常见应用模板。开发人员可以将自己的应用做成模板，发布其应用给其他人使用；站长可以从模板库中在线创建应用，即可进行自己的网站运营。



### **5.8.5** 良好的易用性

兼容原生API， 调试信息输出，可以方便的进行应用管理和配置。



## **5.9   ****价格总览：** ** **

[http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744](http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744)



### **5.9.1** **云服务器价格总览**

**类型**

|

**CPU**

|

**内存**

|

**数据盘**

|

**带宽**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**经济** **A** **型**

|

1核Xeon 2.26GHz

|

512MB

|

40GB

|

1Mbps

|

**85** 元

|

**850** 元

|

[马上购买](http://buy.aliyun.com/?cid=452/)  
  
**经济** **B** **型**

|

1核Xeon 2.26GHz

|

1.5GB

|

80GB

|

2Mbps

|

**181** 元

|

**1810** 元

|

[马上购买](http://buy.aliyun.com/?cid=453/)  
  
**标准** **A** **型**

|

2核Xeon 2.26GHz

|

1.5GB

|

130GB

|

5Mbps

|

**376** 元

|

**3760** 元

|

[马上购买](http://buy.aliyun.com/?cid=13/)  
  
**标准** **B** **型**

|

2核Xeon 2.26GHz

|

2.5GB

|

230GB

|

5Mbps

|

**500** 元

|

**5000** 元

|

[马上购买](http://buy.aliyun.com/?cid=14/)  
  
**标准** **C** **型**

|

4核Xeon 2.26GHz

|

4GB

|

480GB

|

5Mbps

|

**810** 元

|

**8100** 元

|

[马上购买](http://buy.aliyun.com/?cid=15/)  
  
**标准** **D** **型**

|

4核Xeon 2.26GHz

|

8GB

|

730GB

|

5Mbps

|

**1205** 元

|

**12050** 元

|

[马上购买](http://buy.aliyun.com/?cid=16/)  
  
**标准** **E** **型**

|

8核Xeon 2.26GHz

|

16GB

|

730GB

|

5Mbps

|

**1916** 元

|

**19160** 元

|

[马上购买](http://buy.aliyun.com/?cid=17/)  
  








### **5.9.2** **关系型数据库** **RDS** **价格总览：**



**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**MySQL**

|

新1型

|

240

|

10

|

60

|

**70** 元

|

**700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=462)  
  
新2型

|

600

|

20

|

150

|

**200** 元

|

**2000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=463)  
  
新3型

|

1200

|

50

|

300

|

**408** 元

|

**4080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=464)  
  
新4型

|

2400

|

100

|

600

|

**808** 元

|

**8080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=465)  
  
新5型

|

6000

|

200

|

1500

|

**1888** 元

|

**18880** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=466)  
  
新6型

|

12000

|

500

|

2000

|

**3816** 元

|

**38160** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=467)  
  
新7型

|

24000

|

1000

|

2000

|

**7470** 元

|

**74700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=468)  
  


**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**SQL Server**

|

1型

|

1000

|

50

|

100

|

**530** 元

|

**5300** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=469)  
  
2型

|

2000

|

100

|

200

|

**1040** 元

|

**10400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=470)  
  
3型

|

4000

|

200

|

400

|

**2050** 元

|

**20500** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=471)  
  
4型

|

6000

|

300

|

600

|

**3060** 元

|

**30600** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=472)  
  
5型

|

8000

|

400

|

800

|

**3870** 元

|

**38700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=473)  
  
6型

|

12000

|

600

|

1200

|

**5200** 元

|

**52000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=474)  
  
7型

|

24000

|

1000

|

2000

|

**10040** 元

|

**100400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=475)  
  
用户使用RDS期间产生的公网流量费用为1元/GB。内网流量免费，例如用户在云服务器和RDS之间进行的数据传输是免费的。





### **5.9.3** **开放存储服务** **OSS** **价格总览：**

  * **   OSS** **产品收费方式**
  * 开放存储服务（OSS）采用按需付费，日结算方式。采用先充值，后按实际用量结算方式进行结算。每日结算一次，按实际消费金额对充值款进行扣费。当"账户余额"不足时，服务将会自动停止。  
OSS产品计费项包括：容量、流出流量和请求次数。  
容量计费，按用户数据占用的存储空间量收取费用；  
流出流量计费，按用户存储数据被调用或下载产生的流量收取费用；  
请求次数，按调用API各种请求的次数收取费用；  
每日计费总费用=容量占用费用+流出流量费用+请求次数费用。

[[我要充值]](http://i.aliyun.com/charge)

  *  
  * **   OSS** **价格表  **

存储空间：

**0 GB - 500 GB**

0.02 元/GB * 天 (约 0.6 元/GB * 月)

**› 500 GB - 2 TB**

0.018 元/GB * 天 (约 0.55 元/GB * 月)

**› 2 TB - 10 TB**

0.016 元/GB * 天 (约 0.5 元/GB * 月)

**› 10 TB - 50 TB**

0.015 元/GB * 天 (约 0.45 元/GB * 月)

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

流入流量

**流入流量**

免费

流出流量

**0 GB - 500 GB**

0.75 元/GB

**› 500 GB - 2 TB**

0.7 元/GB

**› 2 TB - 10 TB**

0.65 元/GB

**› 10 TB - 50 TB**

0.6 元/GB

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

注：内网流量免费：即OSS与阿里云服务器之间的网络流量，通过使用oss-internal.aliyuncs.com的方式可享受内网流量免费。

数据请求

**Get/Head Object**

每 10000 次 0.01 元

**其他所有请求**

每 1000 次 0.01 元

OSS免费体验活动：

即日起新开通OSS用户，可享受50G存储空间，每月累计10G流出流量, 免费体验服务；  
免费体验时间为自服务开通之日起180天内，均可享受免费体验服务；  
免费体验期间，使用量超出免费范围，超出部分按实际报价收费；  
免费体验期间，请求次数正常收费；  
参加活动方法，立即注册、免费开通OSS服务即可。

  *  
  * **   ** **扣费说明**
  * 流出流量最小计量单位为1GB，请求次数最小计量单位为10000次，不足最小计量单位用量当日不予扣费，累加到次日使用量中。
  *  
  * **   ** **欠费说明**
  * 当"阿里云账户"出现负数（即：欠费状态），OSS服务将自动停止。而您所占用的存储空间的这部分资源仍会继续按日扣费， 因此欠费余额会累计。您可以在出现欠费之日起15天内及时充值并补足欠费后，服务会自动开启，可以继续使用。欠费超过15天，将视为您主动放弃OSS存储 服务，存储空间将被回收，存储空间内的数据会被清理，数据不可恢复。
  *  



# 6   Grand Cloud



<http://www.grandcloud.cn/product/ae>



## 6.1  盛大云引擎功能概述

盛大云引擎是基于盛大云计算基础设施服务的Web应用托管平台，旨在降低应用的部署与运维成本，让应用开发者可以专心于业务的开发设计，不再担心后台的构建与运维。云引擎支持PHP，Ruby，Java，Python等语言编写的Web应用，后端提供丰富的数据存储服务，并根据应用访问量和业务规模进行弹性扩展。云引擎目前为Beta版本，各项功能不断上线。

## 6.2  产品特点

**零运维成本**  
只需上传代码，无需手工操作，即可完成代码部署。同时，提供访问统计与运行资源监控，应用状况尽在掌控。

**多语言支持**  
应用管理基于CloudFoundry。用户可以提交PHP、Ruby、Java、Python等语言开发的Web程序。

**弹性扩展**  
按访问量自动增加运行实例，并提供访问负载均衡。

**数据可靠**  
系统使用盛大云的云硬盘与云数据库等服务，确保数据的高可靠性。

**应用仓库**  
用户可以从应用仓库中选择并快速部署应用，简化开发任务。同时，鼓励开发人员提交应用，与所有用户分享。

## 6.3  产品功能

**云端运行**  
用户提交代码后，其应用程序运行在云主机中，数据存储在各种云端数据服务中，省去了常规的部署与运维操作。

**负载均衡**  
云引擎自动调整执行应用的虚拟机数目。HTTP请求在各个运行实例间轮转服务，实现动态的负载均衡。

**开发语言**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。基于云数据库技术，内置多副本存储，保证高可靠。

**数据库服务**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。

**文件系统服务**  
提供一致共享、多副本持久的文件系统服务，供需要文件存储的应用使用。

**分布式缓存服务**  
提供兼容Memcached协议并且动态可扩展的分布式缓存系统服务。

**统计与监控**  
在网页控制台上以图表形式来来展现应用的访问统计及资源占用信息。

## 6.4  数据中心

目前云引擎部署在盛大云的华北节点。华北节点是BGP线路，包括电信、联通、移动、教育网、铁通。

## 6.5  收费概览

云引擎Beta版本目前对用户全部免费。计费标准后续推出。基本的策略是针对Web应用的访问量以及占用系统资源综合考虑进行计费。



# 7   Amazon AWS

<http://aws.amazon.com/cn/free/>

## 7.1  亚马逊云服务平台

亚马逊是全球最大的在线图书零售商，在发展主营业务即 在线图书零售的过程中，亚马逊为支撑业务的发展，在全美 部署 IT
基础设施，其中包括存储服务器、带宽、CPU 资源。为充分支持业务的发展，IT基础设施需要有一定富裕。2002
年，亚马逊意识到闲置资源的浪费，开始把这部分富裕 的存储服务器、带宽、CPU 资源租给第三方用户。亚马逊将该云服务命名为亚马逊网络服务（Amazon
WebServices，简称 AWS）。2006年初，亚马逊成立了网络服务部门，专为各类企业
提供云计算基础架构网络服务平台，用户（包括软件开发者与企业）可以通过亚马逊网络服务获得存储、带宽、CPU资源，同时还能获得其他IT服务，如亚马逊私有云（VPC）等。
_(_ _以上介绍摘自互联网_ _)_

对于个人用户来说，使用Amazon
AWS就意味着拥有独立的主机，存储空间，带宽，ip，数据库服务器，CDN等等，说白了就是有了实现各种互联网服务的十八般兵器。小到搭建自己的SVN/VNP服务器，网络硬盘，中到搭建个人网站/博客，大到构建大型网站，实施集群计算，AWS都能轻松应对。

AWS的第二个优点就是便宜，虽然消费的是美元，但是经过仔细对比你就会发现，你只需要话费一半甚至更少的钱就能够享受到世界上最好的云计算服务。好比在国外只需要花几千美元就能开宝马一样。我会在后续的文章中详细介绍AWS的价格体系。而且一个非常好的消息就是，AWS对新用户有一个为期一年的免费使用计划(Free
Tier)，在你注册后的一年内，你可以使用AWS所有子业务的免费套餐。如果你希望在一年后继续免费使用的话，换一张信用卡注册就行了。

在我看来，AWS的好处数不胜数，缺点只有一个，那就是在中国没有数据中心，离大陆最近的数据中心是日本。这意味着第一你的用户访问会有一定延迟(100ms以内)，我的网站和博客就是放在日本数据中心，如果你觉得打开网页的速度可以接受，那就不是问题；第二就是你通过AWS建立的网站目前不可能获得工信部备案，对个人用户来说影响不大。

## 7.2  AWS Free Usage Tier (Per Month):

#### 7.2.1.1     Elastic Compute Cloud (EC2)

  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Linux`†` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Microsoft Windows Server`‡` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of an [Elastic Load Balancer](http://aws.amazon.com/elasticloadbalancing/) plus 15 GB data processing*
  * 30 GB of [Amazon Elastic Block Storage](http://aws.amazon.com/ebs "EBS"), plus 2 million I/Os and 1 GB of snapshot storage`*`
  * 5 GB of [Amazon S3](http://aws.amazon.com/s3) standard storage, 20,000 Get Requests, and 2,000 Put Requests`*`
  * 100 MB of storage, 5 units of write capacity, and 10 units of read capacity for [Amazon DynamoDB](http://aws.amazon.com/dynamodb/).**
  * 750 hours of [Amazon RDS](http://aws.amazon.com/rds) Single-AZ Micro DB Instances, for running MySQL, Oracle BYOL or SQL Server (running SQL Server Express Edition) - enough hours to run a DB Instance continuously each month`*`
  * 20 GB of database storage
  * 10 million I/Os
  * 20 GB of backup storage for your automated database backups and any user-initiated DB Snapshots
  * 1,000 [Amazon SWF](http://aws.amazon.com/swf) workflow executions can be initiated for free. A total of 10,000 activity tasks, signals, timers and markers, and 30,000 workflow-days can also be used for free`**`
  * 1,000,000 Requests of [Amazon Simple Queue Service](http://aws.amazon.com/sqs "SQS")`**`
  * 1,000,000 Requests, 100,000 HTTP notifications and 1,000 email notifications for [Amazon Simple Notification Service](http://aws.amazon.com/sns "SNS")`**`
  * 20 minutes of SD transcoding  **or**  10 minutes of HD transcoding`**`
  * 10 [Amazon Cloudwatch](http://aws.amazon.com/cloudwatch) metrics, 10 alarms, and 1,000,000 API requests`**`
  * 15 GB of bandwidth out aggregated across all AWS services`*`
  * 3 low frequency preconditions running on AWS per month*
  * 5 low frequency activities running on AWS per month*
  * 750 hours of [Amazon ElastiCache](http://aws.amazon.com/elasticache) \- enough hours to run a Cache Node continuously each month.`*`

#### 7.2.1.2     Simple Storage Service (S3)

#### 7.2.1.3     DynamoDB

#### 7.2.1.4     Relational Database Service (RDS)

#### 7.2.1.5     Simple Workflow (SWF)

#### 7.2.1.6     Simple Queue Service (SQS) and Simple Notification Service
(SNS)

#### 7.2.1.7     Amazon Elastic Transcoder

#### 7.2.1.8     CloudWatch

#### 7.2.1.9     Data Transfer

#### 7.2.1.10  Data Pipeline

#### 7.2.1.11  ElastiCache



# 8   BAE、SAE 与 GAE 对比

<http://88250.b3log.org/bae-sae-gae>

从数据库、应用配置、计费、域名绑定、平台服务对比了 BAE、SAE 以及 GAE 的优劣，最后给出云平台选型的建议。

## 8.1  数据库

SAE 不支持 InnoDB（可申请支持），BAE 默认支持。

BAE 不支持数据库连接池（c3p0、BoneCP 已测不支持），数据库连接不能长时间保持。

GAE 使用 Datasotre 存取数据，最近也提供了云 SQL（MySQL），但申请比较困难，配额/性能笔者未测试过。

另外，SAE 显式给出了主从库的访问方式，应用可以比较灵活地设计存取策略，例如读写分离。并且 SAE 是每个应用都拥有自己的数据库，而 BAE
是所有应用共用一个库。

## 8.2  应用配置

BAE 的 duapp-web.xml 基本是抄袭 GAE 的 appengine-web.xml，元素基本一致。

比较奇葩的是 BAE 静态资源配置默认所有后缀为静态文件类型（例如 .html）的请求路径都默认假设为静态资源，需要在 duapp-web.xml
中指定排除。

## 8.3  计费与配额

SAE 按应用天计费"豆豆"，服务也按流量计费、CPU 时间、调用次数计费。注册或活动送配额，否则需要购买。

BAE 目前还没有详细的计费，只限定了应用数。公测结束后应该会细化计费模型。

GAE 目前的计费模型主要是按 API 调用计数，流量分为 In/Out 配额。每天会定时刷新免费配额。

综上，GAE 的计费一目了然，主要就是 API 调用次数；SAE 的计费比较复杂，不同服务有不同的计费策略；BAE 还没有明确的计费模型。

## 8.4  域名绑定

GAE 开通企业套件后随便绑，企业套件有免费版。

SAE 需要确认通过域名备案才能绑定，并且绑定后的流量计费翻倍。

SAE 目前可以随便绑，但没备案的话绑定域名的请求走海外中转，流量计费翻倍（原二级域名请求计费不变）。

BAE 目前可以随便绑，但没备案的后果自负。

## 8.5  平台服务

SAE 提供了 SDK 包，包含了开发需要的本地服务实现。

BAE 则分别提供了服务 Jar，调用方式按不同服务而异。

GAE 提供了完整的 SDK 包，包含了开发需要的本地运行环境和配置客户端。

综上，GAE 提供了完整的平台化服务，覆盖了从开发到上线运维的一系列工具；SAE 则提供了部分工具，平台化不完整，增加了开发、运维难度；BAE
则是分别提供不同服务给开发，没有统一的 SDK 与调用方式。

另外，值得一提的是 BAE 虽然服务没有整合到一个 SDK 中，但其分散的服务也比较适合应用自己选择。 其中云消息（消息服务）以及云触发（数据变更通知）是
GAE/SAE 没有提供的服务，某些业务场景应该会非常适用。

## 8.6  结论

SAE 与 BAE 主要还是面向应用部署托管，普通应用修改后易迁移部署到 BAE 或 SAE。

新应用开发可以选择和平台绑死（依赖平台服务）或按照普通应用开发。

使用配置工具来上传、更新应用配置其实是非常好的方式，但目前 SAE/J、BAE/J 都没有提供客户端配置工具，这增加了使用者的维护工作量。

GAE 提供了比较完整的服务平台，覆盖了应用的生命周期，最近也提供了云 MySQL 服务以吸引更多开发者。

需要根据应用类型来考虑平台选型，例如 GAE 基本以 API 计数的配额就不适合做社交应用，'墙'的问题也需要考虑解决方案。

**\---- EOF ----**





# 9   附录

## 9.1  连接到云，第 1 部分: 在应用程序中使用云

_**充分利用混合模型**_

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/>

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html>

**简介**

多年来，在网络图中，我们已经习惯于使用一个云（特别是积雨云）来表示
Internet。云状图像常被用来表示无固定形状的、不清晰但又必须包含在图表中的一些内容。而网络上的线惟一的作用就是穿过云以表示数据通过
Internet。在以安全性为中心的图表上，这条穿过云的线可能还会在旁边多出一个挂锁以表示这个连接是安全的。

**_常用缩略词_**

  * Ajax: Asynchronous JavaScript + XML
  * API: 应用程序编程接口（application programming interface）
  * HTML: 超文本标记语言（Hypertext Markup Language）
  * HTTP: 超文本传输协议（Hypertext Transfer Protocol）
  * JMS: Java™ 消息服务（Java™Message Service）
  * REST: 具象状态传输（Representational State Transfer）
  * XML: 可扩展标记语言（Extensible Markup Language）

现在云已经在网络图中扮演着主要角色。应用程序可以利用云来调用所添加的值，比如存储、队列及宿主应用程序。应用程序本身也可以被托管在云上。现在的线已不再是简单地穿过云，而是连接到云并将云用作应用程序的一部分。这就使云有了更实际的意义。

在这个由三个部分组成的系列文章中，我们将探究云计算的方方面面。云计算的提供商相对较少，每个提供商着眼于不同的方向并提供不同的服务。编程语言各异，从
Python 到 C#、再到 Java 或其他的专有语言。与云的接口也各不相同，虽然轻量的 REST
接口是首选，但现在并不是每个云计算提供商都提供这种接口。

在本系列的第 1
部分，我们将着重研究一个混合示例，一个使用云计算服务和基础设施进行增强了的专用应用程序。通过研究这个混合应用程序，了解云计算的功用。为此，您需要探究它的渊源、云计算的主要提供商目前所能提供的功能。本系列的第
2 部分将会涵盖在第 1 部分中设计的这个混合应用程序的开发。第 3 部分将着重介绍此解决方案在安全性和管理方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云计算究竟是什么？**

IBM 将云计算定义为一个新兴的计算范型，在这个范型中，数据和服务位于可大规模伸缩的数据中心中，并可被 Internet
上的任何连接设备随时访问。它为应用程序提供了可观的伸缩能力（在使用 Amazon Elastic Computing Cloud 的情况下 -- 通常被称为
Amazon EC2），并能托管应用程序自身。

云计算并不适合所有的情形，但是对于一个在不同时期需要不同计算能力的组织来说，云是很有吸引力的。如果一个组织对处理和存储能力的要求是不均衡的，比如每周六的午夜进行批处理，那么此时与其采用一个大多数时间都空闲的数据中心，到不如使用云更有意义。

云计算也特别适合于那些刚刚起步的公司。这些公司的创业者对投资资本家提出的问题恐怕都不会陌生，即
"您的技术如何伸缩？"云计算是对此问题的一个很好的答案。然而，正如您在本系列后面的部分看到的，云计算也带来了所有权、安全与成本方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云的形成**

**_IBM_** ** _和 Amazon Web Services_**

IBM 与 AWS 合作提供了在虚拟的计算环境中对 IBM 中间件的访问。Amazon EC2
的体验让您能够在无需在系统中安装软件的情况下评估并使用软件。您可以即时调整容量，在一个可靠、高效的环境中构建完备的企业应用程序，而您只需要花费一些时间并购买存储容量。我们的
EC2 上的中间件包括：

  * [DB2 Express-C 9.5](http://www.ibm.com/developerworks/cn/downloads/im/udbexp/)
  * [Informix Dynamic Server Developer Edition 11.5](http://www.ibm.com/developerworks/cn/db2/downloads/idsde/)
  * [WebSphere® Portal Server 和 Lotus Web Content Management 标准版](http://www.ibm.com/developerworks/downloads/ls/wps-wcmse/ec2.html#productionami)
  * [WebSphere sMash](http://www.projectzero.org/download/)

这是产品级的代码，启用了所有特性和选项。在[developerWorks Amazon EC2
云计算页面](http://www.ibm.com/developerworks/downloads/cloud.html)
可以获得更多信息并可以下载这些产品的 Amazon Machine Images。

更多云计算的参考资料，请见 developerWorks 上的
[云计算页面](http://www.ibm.com/developerworks/spaces/cloud/)。

在云计算得到广泛应用之前，我们使用的是网格计算与效用计算。网格计算与云计算的主要区别就是网格计算环境多是由不同的机器组成的，而云计算环境则更加可控制，后端机器通常都是相同的。效用计算是指按数据流量或应用程序的使用支付费用的一种业务模型。服务的
"弹性" 增长的概念也没有现在这么盛行，而随着使用的改变而相应增加（或减少）容量的能力却是云计算的一个重要部分。

从 2000 年初到 2000 年中，Google 和 Amazon
各自独立开发了自己的云计算架构以便在其上运行各自的业务。开发了这种基础设施后，二者发现他们自已的基础设施本身成为了一个服务，可以按照每次的使用量卖给开发人员。Amazon
更是意识到了其平台中的关键价值，以至于它完全相信有一天 Amazon 将会因其计算平台而再次名扬天下，一如它的在线零售网站一样。Amazon
认识到它可以以服务的形式出售其平台（即 Platform as a Service，缩写为 PaaS -- 与 Software as a Service
即 SaaS 类似）。因此，Amazon 常被视为是云计算商业化方面的领跑者，在计费和使用模型方面尤为突出。

在基于云的计算环境的设计方面堪称专业的成功供应商为数不多，其中包括 Amazon 和 Google。认识到这一点，Google、IBM 和几所大学组建了一个
_research cloud_  来为从事云计算研究的学生提供一个云计算环境以便开发新的云计算技术与应用程序。尽管其规模不能与 Amazon 与
Google
的基础设施相提并论，但此项目还是为学生研究云服务提供了一个很好的环境。来自此项目的研究成果将会有助于对云计算进行更进一步的开发，比如有创建条件的组织可以在其基础上开发
_专用云_ 。

  
  

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**混合模型应运而生**

放弃所有本地应用程序而只使用云，或相反地，只依靠本地应用程序而忽略云，都不是明智之举，现在最流行的办法是将本地应用程序与云相结合使用。即所谓的 _混合模型_
。这就让一个公司在必要的时候使用云计算，而同时又能保持它对其关键应用程序的控制。例如，很多公司已经发现，使用 Amazon 的 Simple Storage
Service (S3) 存储图片、视频或文档等会更经济。混合模型也有助于增量方法。

即使您认为将大部分甚至全部的应用程序都转向云更有意义，但是也不建议您这么做，因为一次性完成这样的转移风险太大。借助混合模型，可以先将容易的东西（比如文件存储）转向云。然后在您适应了这种部署模型后，再将应用程序更重要的部分转向云。这也是我在本系列中所采用的方式。接下来，让我们先看一下这个通过转移部分基础设施实现混合的应用程序。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**设计一个混合应用程序**

这个示例混合应用程序是一个异步的电子邮件通知系统。它可以是一个工作流系统中的一个子系统。当一个新行为被提交并等待批准时，就会向能够做出批准或拒绝决定的主体发送电子邮件。这种系统可以用于一个履行订单的系统中。当订单货物运出时，就会发出一个电子邮件以通知相关的人订单在货运途中。不难想象，在很多种应用程序中都可以使用到这个系统。电子邮件在本质上是异步的，所以能生成电子邮件的异步机制是满足此类用例的一种有效途径。

假设有一个现成的应用程序，在此应用程序的某个位置已经具有了这种系统，可以使用很多种方法实现此类系统，但一个相对优雅的方式是使用一个 JMS。JMS 规范是
J2EE™ 技术栈的一个重要部分。目前，针对此标准已经有很多专有或开源的实现。很容易想像有这样一个系统，它向一个 JMS 队列发送通知，而另外一个系统对这个
JMS 队列进行周期性地读取并为每个消息生成电子邮件提醒。

对于一个混合模型，可以先将这个 JMS
队列转移到云。换句话说，就是用在云中运行的一个服务来替代它。这是一种什么样的服务呢？如何更改应用程序以使其与此服务进行交互呢？这取决于所使用的云平台。接下来，我们来看一下各种平台及怎样使用这些平台来实现或像本例一样重新实现一个
JMS 队列的功能性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Amazon Web Services**

作为一个商业化云计算的先躯，Amazon 提供了一系列开发人员感兴趣的成熟服务。Amazon 最知名的云服务莫过于 EC2 (Elastic
Computing Cloud) 服务。它允许构建可在 Amazon 自已的基础设施上运行的虚拟机实例（被称为 AMI -- Amazon Machine
Images）。也许有人会说，除了使用的不是真实的计算机以及基于流量使用收费而非收取机器的租赁费之外，EC2 更接近于托管提供商的一项服务。

Amazon 的 S3 服务是一个在线存储服务，对于需要扩展存储能力的新起步的那些公司来说尤其具有引吸力。它可用作其他 Amazon 云服务（比如
EC2）的一个附件。这就意味着一个 AMI ，或是一个运行着 PHP 的 Linux™ 计算机，可以使用 Amazon S3
作为它的数据存储。随着数据流量的增长，S3 服??也会弹性扩展。Amazon 的 SimpleDB
是一个基于云的快速而简单的数据库，它可以提供索引、存储及访问。很显然，它比功能完善的关系数据库要简单很多，因为它不需要模式，它可以自动地索引数据，并提供了
API 用于存储及访问。

Amazon 的 SQS (Simple Queue Service) 提供了一个队列服务，类似于 JMS，但有一个 RESTful 接口。您也可以将
SQS 与 Amazon 的其他云服务联合使用，也可以将它作为任何一个可用简单的 HTTP GET 或 POST
连接到它的应用程序的一部分使用。对于这个混合应用程序，它是 JMS 队列的一个很好的替代品。它可以通过它的 RESTful 的 XML
接口访问到，可以方便地与一个现有应用程序集成。SQS 可能是这类混合应用程序的最为直接的选择。

很多软件提供商都与 Amazon 有过合作以帮助其客户充分利用 EC2。例如，IBM 和 Amazon 合作开发了 IBM 的很多最受欢迎的企业软件，比如
EC2 上的 DB2®、Informix® 及 WebSphere®。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Google**

Google 因其快速而准确的搜索而闻名，对于很多用户来说，它都是 Arthur C Clarke 的名言 "任何足够先进的技术都与魔法没有区别"
的最好的体现。由于是技术将魔法变成了现实，因此 Google 是提供云计算平台的最佳之选。在 Google
的平台上运行应用程序的美好前景让开发人员无比兴奋，这完全可以理解。

Google 提供了一个名为 App Engine 的云计算平台，它基于的是 Google 早就建立起来的底层平台。这个平台包括 GFS（Google
File System）和 Bigtable（构建于 GFS 之上的数据库系统）。Google App Engine 内的编程采用的是
Python。程序员用 Python 编写应用程序，然后再在 App Engine 框架上运行。除 Python
外的其他语言在将来也会得到支持。出于开发的需要，可以下载 App Engine 环境的一个本地仿真程序。App Engine 可免费使用并且包括多达 500
MB 的存储及足够的 CPU 带宽来满足每天 5 百万次页面浏览。

Google App Engine 提供了一些有用的基础设施，比如源自 GFS 的数据存储和一个 memcache
实现。然而，它并不提供开箱即用的排队机制。不过，有了这样一个纯 Python 的编程环境，就可以在 App Engine 之上很容易地创建您自已的 JMS
替代。这个数据存储很适合于混合应用程序，并且只需很少的 Python 编程就可以打造出一个面向您的队列的 RESTful 式接口。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Microsoft Azure**

正如您所期望的，Windows® 和 .NET 是 Windows Azure 的主要特点。Microsoft 已经提供了一个开发环境，在这个环境中，用
Visual Studio® 编写的应用程序可以被托管于 Windows Azure 环境并在其上运行。Azure
平台提供了很多服务，比如像用于文件存储与数据访问的面向基础设施的服务，同时也提供了更为专用的服务，比如搜索和联系人管理。它还包括了 NET Service
Bus。这是典型的 Enterprise Service Bus (ESB) 设计模式的 Microsoft 实现。ESB
最简单的用法之一就是消息队列，它完全可以充当 JSM 队列的替代。NET Service Bus 还是开发者友好的。它既支持使用 XML 的轻量的
RESTful 接口，也支持较重量的、包括了 WS-* 标准全部实现的基于 SOAP 的接口。这两个接口均支持现有应用程序和 NET Service Bus
间的简便的互操作性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**SalesForce.com**

SalesForce.com 提供了一个模型，借助这个模型，开发人员可以使用其 Apex 开发语言来访问 SalesForce.com
服务。SalesForce 称 Apex 是 "世界上第一个随需应变的编程语言"。 随需应变主要表现在 Apex 代码托管于 SalesForce 的
Force.com 云服务，并在该上下文运行。在句法方面，Apex 与 Java 或 C# 语言类似。

Apex 代码被用来生成服务于 VisualForce 层的 Web 页面，该层就是实际的用户界面。它也使用了 Model-View-Controller
(MVC) 模型。这非常类似于 .NET 中借助 C# 生成 ASPX 页面。这些 VisualForce 页面可以包含
HTML、Ajax（XMLHttpRequest 对象）及 Adobe Flex。

VisualForce 允许开发人员在 SalesForce.com Web 界面上创建不同的变体。这对于喜欢 SalesForce.com
但又想向其添加功能的公司来说十分有用。与其要求 SalesForce.com 构建这种功能性，不如让 Salesforce.com 的用户通过创建
VisualForce 页面并用 Apex 代码将它们写入 SalesForce.com 后端来实现同样的目的。

Salesforce 还提供了控制器，用来连接页面表示与来自 SalesForce 数据库的底层数据，包括如 Edit 或 Save
这样的标准的例程。Force.com
云实现了巨大的成功。它不仅为开发人员提供了在云上构建应用程序的方法，借助它，还可以通过直接发行模型来向用户收取这些应用程序的使用费用。然而，它是一个非常专门化的云。它并不太适合增量方法。通常需要对
Force.com 云进行构建。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**结束语**

在本文中，我们了解了不同的云服务提供商能为我们带来的各种功能，另外还学习了如何使用这些云服务来代替 JMS
队列以及如何将一个现有的应用程序转变成一个混合的云应用程序。在接下来的两篇文章中，我们将了解绑定本地应用程序与云服务的这个混合模型是如何实现的。我们还将研究能够影响云计算的安全与管理方面的重要问题。



## 9.2  连接到云，第 2 部分: 实现混合云模型

_**将**_ _ **JMS**_ _ **队列数据推向**_ _ **Amazon SQS**_ _ **队列**_



**混合模型**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

在本文中，我将集中介绍如何向一个云提供商 Amazon 创建混合云应用程序。示例应用程序名为 HybridCloud，它将从 JMS
队列中取出数据并将数据传送到寄存在 Amazon 云中的 Amazon SQS 队列。进入 Amazon SQS
队列之后，可以使用有权访问该队列的应用程序拉取数据。

具体情况请看示例。假设一家医疗组织需要通过图片处理应用程序处理 X 射线图。该组织安全地将 X 射线图写入 Amazon SQS
队列，射线图临时存储在该位置。即使 X 射线图的文件非常大，这对于云计算提供商而言也不是什么问题。同时，图片处理应用程序占用队列，在 X
射线图进入后进行读取。图片处理应用程序需要大量处理能力，因此它最好部署在虚拟环境中（ _私有云_
），在这个环境中可以快速添加硬件功能。经过图片处理应用程序的处理之后，X 射线图将返回到另一个队列，可通过医疗应用程序接收。尽管 X
射线图是该示例的主要问题，实际上这适用于任何数据。很明显，X 射线图涉及到较高的隐私和安全问题。本文的第 3 部分将探讨云的安全性和治理。

**_云计算空间_**

您是否希望随时获取最新的云计算消息？是否想得到云计算相关的技术知识？developerWorks
云计算空间就是这样一个云计算信息资源的门户，在这里您可以了解来自 IBM 和业界其他媒体的最新信息，并且得到如何在云环境中使用 IBM 软件的入门知识。

IBM 在 Amazon EC2 云计算环境中提供了 DB2、Informix、Lotus、WebSphere 等方面的 AMI
镜像资源。您只需按使用量支付少量费用，就可以使用到云上的数据、门户、Web 内容管理、情景应用等服务。欢迎您随时访问
[云计算空间](http://www.ibm.com/developerworks/spaces/cn/cloud)，获取更多信息。

该架构的好处包括：

  * 该系统不需要队列写入程序（医疗应用程序）或队列读取程序（图片处理应用程序）同时在线。如果文件只是在两个应用程序之间通过 FTP 传输，系统会在任何一方脱机时崩溃。通过使用 Amazon SQS 队列，系统变得更加灵活。
  * 可以向解决方案的任何一方添加功能，不会影响系统的工作。例如，您可以增加图片处理应用程序端的计算能力，这可以加倍图片处理速度。这种变化对于医疗应用程序是透明的，它会继续将 X 射线图写入 Amazon SQS 队列，不会造成影响。
  * 该混合模型非常适合于考虑使用云计算的架构师。全有或全无解决方案要么将所有内容都放到云计算平台，要么完全避开云计算，更好的选择是选择云计算中有用的功能并战略性地使用该功能。在本地应用程序端，虚拟化（私有云）使得动态添加功能变得更加容易，这对于处理器密集型应用程序（如图片处理）而言是很重要的。在云端，Amazon SQS 服务提供应用程序之间的队列服务，即使它们没有连接网络。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**向** **Amazon SQS** **云服务确认身份**

**_常用缩略词_**

  * FTP：文件传输协议（File Transfer Protocol）
  * API：应用程序编程接口（application programming interface）
  * HTTP：超文本传输协议（Hypertext Transfer Protocol）
  * JMS：Java™ 消息服务（Java™ Message Service）
  * JNDI：Java 命名和目录接口（Java Naming and Directory Interface）
  * REST：具象状态传输（Representational State Transfer）
  * SQS：简单队列服务（Simple Queue Service）
  * URL：统一资源定位符（Uniform Resource Locator）
  * XML：可扩展标记语言（Extensible Markup Language）

您的 HybridCloud Java 应用程序使用 Amazon
SQS（[下载](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#download)
应用程序源代码）。HybridCloud 应用程序与 Amazon SQS 云之间的连接使用经过验证的 Web
服务。执行这种验证出于两个原因：首先，Amazon 要收取 Amazon SQS
的使用费，因此必须跟踪每个人的使用；其次，对每个队列的访问必须受到控制。在我们的 HybridCloud 应用程序中，很明显第三方不适合访问包含私有 X
射线图片的 Amazon SQS 队列。

使用 Amazon SQS 队列的第一步是成为 Amazon Web Services (AWS) 的用户，这需要登录 Amazon.com。登录
Amazon.com 没有什么不同之处 -- 任何在 Amazon.com 站点买过书的用户都已经有了一个 Amazon.com
帐户。但是，Amazon.com 登录还只是第一步。AWS 需要使用 "访问密匙 ID" 以及相关的密钥。

Amazon Web Services 模型中的 Secret Access Key 可以视为在 Amazon.com 和连接到 Amazon Web
服务的开发人员之间的一个共享密匙。相反，Access Key ID 并不私密，因为它用于识别而不是验证。在第 3
部分中，我们将讨论这两个密匙的更多细节，以及其他云计算提供商使用的其他验证模型。

开发人员登录 Amazon Web Services 并获取了他们的 Access Key ID 以及 Secret Access Key
之后，他们就可以订阅特定的服务。在本例中，我们将订阅 Amazon.com SQS 服务。开发人员必须使用 Amazon Web Services
注册信用卡才能使用 SQS 之类的服务。信用卡详情必须存储在 Amazon 中，在有未付帐单时无法进入 -- 它是现收现付模型。如果尝试未注册就访问 SQS
服务，您将看到 "The AWS Access Key Id needs a subscription for the service" 异常。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**设计混合应用程序**

正如开头所述，混合应用程序在本地处理数据并使用 Amazon SQS 云服务。因此，它有一个本地组件和一个云组件。在该应用程序设计中，通过本地从 JMS
队列接收数据（也许是从主机应用程序接收），然后使用 HTTP GET 和 POST 将数据发送到 Amazon SQS 队列。您将使用 Java
作为应用程序的语言。

应用程序有三个主要部分：

  1. 创建 Amazon SQS 队列。
  2. 读取本地数据（从 JMS 队列）并将其放入 Amazon SQS 队列。
  3. 从 Amazon SQS 队列检索响应数据。

在 [使用 Amazon
SQS](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#makeuseSQS)
应用程序代码片段中，注意处理本地 JMS 队列连接和 Amazon SQS 队列连接之间的相似之处。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **Amazon SQS**

在 HybridCloud Java 应用程序中，首先放入 Amazon SQS 类（见清单 1）。

  
**清单** **1.** **导入** **Amazon SQS** **类**

    
    
                                       
    
    
    Import com.amazonaws.queue.*;  
  
---  
  
  
  

HybridCloud 应用程序使用 Amazon SQS 将数据写入队列，然后从队列读回数据。与 Amazon SQS 的连接建立在通过验证的 Web
服务连接之上，客户端使用 Amazon Access Key ID 识别，使用 Amazon Secret Key ID 进行验证。要通过 Java
代码使用 Amazon SQS，首先将 Amazon Access Key ID 和 Amazon Secret Key ID 放入代码中（见清单 2）。

  
**清单** **2.** **设置** **Amazon** **键**

    
    
                                       
    
    
    String accessKeyId = "12345678901234567890";
    
    
    String secretAccessKey = "abcdefghijklmnopqrstuvwxyz";  
  
---  
  
  
  

接下来，实例化 Amazon SQS 的 HTTP Client 实现，传入 Access Key ID 和 Secret Access key
作为变量（见清单 3）。

  
**清单** **3.** **实例化** **Amazon SQS http** **客户端**

    
    
                                       
    
    
    AmazonSQS service = new AmazonSQSClient(accessKeyId, secretAccessKey);  
  
---  
  
  
  

现在，您已经实例化了 Amazon SQS 客户端对象，但是还没有通过 Internet 连接到 Amazon SQS 服务。这是下一步要做的工作，您将在
Amazon SQS 云服务上创建队列。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**创建** **Amazon SQS** **队列**

该应用程序使用队列存储 X 射线图文件。在使用 Amazon SQS 队列之前，必须先创建一个队列。该队列必须有一个名称，在本例中为
"imageQueue"。这是 HybridCloud 应用程序放置 X 射线图文件的地方（见清单 4）。

  
**清单** **4.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueRequest request = new CreateQueueRequest();
    
    
    request.setQueueName("imageQueue");  
  
---  
  
  
  

现在运行名为 `createQueue` 的 Amazon SQS 服务对象方法，该方法创建对 Amazon Web Services 的 HTTP GET
(REST-style) 请求以创建队列（见清单 5）。

  
**清单** **5.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueResponse response = service.createQueue(request);  
  
---  
  
  
  

这将在 Amazon SQS 上创建一个 REST 风格的 Web 服务。当您运行代码创建 Amazon SQS 队列时，检测发送给 Amazon SQS
的 REST 风格的 URL 会很有趣。在此 URL 中，您可以清楚地看到 Access Key ID、签名（使用 Secret Key ID）和实际的
SQS 队列，创建的队列名为 `imageQueue`。当然，实际的 Secret Key ID 是不会发送的。消息的签名组件（见清单 6）提供拥有
Secret Key ID 的证明。只有密钥持有者才能创建签名组件。

  
**清单** **6.** **将** **REST** **风格的** **Web** **服务请求发送到** **Amazon Web** **服务**

    
    
                                       
    
    
    queue.amazonaws.com?Action=CreateQueue&SignatureMethod=HmacSHA256&AWSAccessKeyId
    
    
    =12345678901234567890&QueueName=imageQueue&SignatureVersion=2&Version
    
    
    =2008-01-01&Signature=U859J2Hoi5qBqlQx1R18dKPgSgrgjlOiJIDD8ug9FPI%3D&Timestamp
    
    
    =2009-04-01T03%3A25%3A13.575Z  
  
---  
  
  
  

创建签名不仅要使用 QueueName，还使用时间戳。这确保了对 Amazon SQS 的请求无法被攻击者捕获并回放以模拟有效用户。如果攻击者重新向
Amazon SQS 服务发送请求，则重复的签名表示该请求属于捕获重放攻击，Amazon Web 服务将会阻塞它。

现在，您已经创建了 imageQueue 队列，您可以将图像数据加载到其中。现在可以从本地 JMS
队列中获取该数据。本地队列本身可以来自虚拟环境（本地云）。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**从本地** **JMS** **队列检索数据**

现在已经创建了 Amazon SQS 队列，接下来将注意力转移到该混合应用程序的本地端。在将数据提供给 Amazon SQS
队列之前，您必须从本地队列中读取数据。比较本地队列使用的步骤与连接 Amazon 的 SQS 队列所需的步骤将会很有用。

需要导入 Java 库，首先是所有的 JMS jar，然后是 JNDI jar。这些文件允许 Java 应用程序使用 JMS（见清单 7）。

  
**清单** **7.** **导入** **JMS** **类**

    
    
                                       
    
    
    import javax.jms.ConnectionFactory;
    
    
    import javax.jms.Connection;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.MessageProducer;
    
    
    import javax.jms.MessageConsumer;
    
    
    import javax.jms.Queue;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.Message;
    
    
    import javax.jms.TextMessage;
    
    
    //Required for JNDI.
    
    
    import javax.naming.*;  
  
---  
  
  
  

您使用 JNDI 设置 JMS 连接的上下文。例如，如果从文件系统读取数据，您可以使用清单 8 中的代码。

  
**清单** **8.** **从本地队列读取文件**

    
    
                                       
    
    
    ConnectionFactory myConnFactory;
    
    
    Queue myQueue;
    
    
    Hashtable env;
    
    
    Context ctx = null; 
    
    
    env = new Hashtable();
    
    
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.fscontext.RefFSContextFactory");
    
    
    env.put(Context.PROVIDER_URL, "file:///C:/Images"); 
    
    
    ctx = new InitialContext(env);  
  
---  
  
  
  

现在创建队列和连接工厂（见清单 9）：

  
**清单** **9.** **创建队列和连接工厂**

    
    
                                       
    
    
    String MYCONNECTIONFACTORY = "MyConnectionFactory";
    
    
    String MYQUEUE = "MyQueue";
    
    
    myConnFactory = (javax.jms.ConnectionFactory) ctx.lookup(MYCONNECTIONFACTORY);
    
    
    myQueue = (javax.jms.Queue)ctx.lookup(MYQUEUE);  
  
---  
  
  
  

接下来，创建一个连接，然后创建连接中的会话（见清单 10）。

  
**清单** **10.** **创建一个本地** **JMS** **队列的连接**

    
    
                                       
    
    
    Connection myConn = myConnFactory.createConnection();
    
    
    Session mySess = myConn.createSession(false, Session.AUTO_ACKNOWLEDGE);  
  
---  
  
  
  

要从队列中读取消息（在本例中最终涉及到从文件系统中读取数据，因为我们使用文件系统的 JNDI 标识符），使用清单 11 中的代码。

  
**清单** **11.** **从本地** **JMS** **队列中读取**

    
    
                                       
    
    
    MessageConsumer myMsgConsumer = mySess.createConsumer(myQueue);
    
    
    myConn.start();
    
    
    Message msg = myMsgConsumer.receive();  
  
---  
  
  
  

现在检查从本地检索的消息中的内容（见清单 12）。

  
**清单** **12.** **检查本地检索消息的内容**

    
    
                                       
    
    
    if (msg instanceof TextMessage) {
    
    
                    TextMessage txtMsg = (TextMessage) msg;
    
    
                    String inputText = txtMsg.getText());
    
    
    }  
  
---  
  
  
  

最后，关闭 JMS 队列的连接（见清单 13）。

  
**清单** **13.** **关闭本地** **JMS** **队列的连接**

    
    
                                       
    
    
    mySess.close();
    
    
    myConn.close();  
  
---  
  
  
  

现在，您已经将希望写入 Amazon SQS 队列的数据放到了名为 inputText 的字符串中。这是接下来要写入 Amazon SQS 队列的内容。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**写入到** **Amazon SQS** **队列**

传入到 Amazon SQS 队列的数据以字符串形式发送。尽管数据是图片，但它仍然以字符串形式发送到 Amazon SQS。可以看到，它在
`SendMessageRequest` 对象中设置，以将消息发送到 Amazon SQS 队列（见清单 14）。

  
**清单** **14.** **向** **Amazon SQS** **队列发送消息**

    
    
                                       
    
    
    SendMessageRequest sendRequest = new SendMessageRequest();
    
    
    sendRequest.setMessageBody(inputText);  
  
---  
  
  
  

您必须设置相应的队列名称，这与您之前创建的队列名称相同（见清单 15）。

  
**清单** **15.** **设置** **Amazon SQS** **上的队列名称**

    
    
                                       
    
    
    sendRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在通过使用 Amazon SQS 对象的 `sendMessage` 方法将消息发送到 Amazon SQS 队列（见清单 16）。

  
**清单** **16.** **将我们的数据发送到** **Amazon SQS** **队列**

    
    
                                       
    
    
    SendMessageResponse response = service.sendMessage(sendRequest);  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**读取** **Amazon SQS** **响应**

接下来从 Amazon SQS 队列读取响应。首先创建 `ReceiveMessageRequest` 对象（见清单 17）。

  
**清单** **17.** **创建** ** **` **ReceiveMessageObject**` ** ** **从** **Amazon
SQS** **队列中检索数据**

    
    
                                       
    
    
    receiveRequest = new ReceiveMessageRequest();  
  
---  
  
  
  

接下来，设置队列名称（见清单 18）。

  
**清单** **18.** **设置队列名称**

    
    
                                       
    
    
    receiveRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在使用 `receiveMessage` 方法尝试从 Amazon SQS 队列中检索消息（见清单 19）。

  
**清单** **19.** **从** **Amazon SQS** **队列中检索响应**

    
    
                                       
    
    
    ReceiveMessageResponse response = service.receiveMessage(receiveRequest);  
  
---  
  
  
  

要检测结果，包括从云中检索到的消息 ID 和消息正文（见清单 20），请将其传递到标准输出。

  
**清单** **20.** **检查** **Amazon SQS** **队列中的响应**

    
    
                                       
    
    
    if (response.isSetReceiveMessageResult()) {
    
    
    ReceiveMessageResult  receiveMessageResult = response.getReceiveMessageResult();
    
    
    java.util.List<Message> messageList = receiveMessageResult.getMessage();
    
    
    for (Message message : messageList) {
    
    
    if (message.isSetMessageId()) {
    
    
                            System.out.print("            MessageId");
    
    
                            System.out.print("                " + message.getMessageId());
    
    
                            System.out.println();
    
    
                        }
    
    
                        if (message.isSetBody()) {
    
    
                            System.out.print("            Body");
    
    
                            System.out.println();
    
    
                            System.out.print("                " + message.getBody());
    
    
                            System.out.println();
    
    
                        }
    
    
    }  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **XML** **网关连接本地应用程序和云**

在本文中，使用 Java 代码连接本地应用程序和云计算环境。这是开发人员的理想解决方案，但作为应用程序的一部分，到 Amazon
云计算服务的连接不在网络运营团队的控制之下，网络运营团队监控使用、通信和可用性。此外，任何到云计算连接的更改都涉及到代码更改。尽管这超出了本文的范围，但可以使用网络基础结构在本地
JMS 队列和 Amazon SQS 云服务之间实现相同的连接，从而将连接置于网络运营团队的控制之下。

要将一个本地应用程序组件（比如 JMS 队列）连接到云，需要一个包含云计算连接器的 XML 网关（见参考资料中此类网关的示例）。将 JMS 队列连接到
Amazon SQS 队列的任务涉及到拖放连接筛选器，从而将数据从 JMS 队列中拉出然后传递到 Amazon 云服务。

这与我们熟悉的有线电视机顶盒很类似。电视机顶盒连接本地基础设施（电视机）和云（有线电视操作员）。XML
网关提供本地有线电视机顶盒的功能。除了提供到云服务的连接之外，它还提供对该连接的监控和安全性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**结束语**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

您了解了 Java 应用程序如何将本地 JMS 队列和 Amazon SQS 云连接起来。您的 HybridCloud 应用程序使用本地资源（JMS
队列）和基于云的资源（Amazon SQS）执行示例图片共享任务。使用比较类似的方法连接本地队列和 Amazon SQS 队列，但是在网络级别上，到
Amazon SQS 的连接通过 HTTP GET 和 PUT（包含 URL 中传递的参数）发送。

在第 3
部分，即本系列的最后一部分，您将了解云计算中的治理和安全问题。您将看到各种云提供商使用的验证模型，并将讨论在隐私性、法规遵从性方面出现的问题和针对拒绝服务威胁提供的保护。

  
  

**参考资料**

**学习**

  * developerWorks 上的 [云计算空间](http://www.ibm.com/developerworks/spaces/cloud/)：了解为何云计算如此重要、如何起步以及在何处可以了解到更多的相关信息。
  * IBM 的 [云计算项目](http://www.ibm.com/ibm/cloud/)：随时随地获得对您的应用程序的访问。
  * [Amazon Web Services](http://aws.amazon.com/)：查阅 Amazon Web Services 和云计算的相关内容。了解 IBM 和 Amazon Web Services 如何能够帮助您构建和运行一系列的 IBM 平台技术。
  * [用 Amazon Web Services 进行云计算，第 1 部分：简介](http://www.ibm.com/developerworks/cn/web/ar-cloudaws1/)（Prabhakar Chaganti，developerWorks，2008 年 7 月）：阅读这个有关使用 Amazon Web Services 的逐步指南。
  * [Microsoft Windows Azure](http://www.microsoft.com/azure/windowsazure.mspx)：访问这个针对云服务操作系统的 Web 站点，该系统充当了面向 Azure Services Platform 的开发、服务托管和服务管理环境。
  * [Google App Engine Blog](http://googleappengine.blogspot.com/)：一个了解其发展的优秀资源。
  * [developerWorks Cloud Computing Resource Center](http://www.ibm.com/developerworks/downloads/cloud.html)：用现在可用于 Amazon EC2 平台的 IBM 产品在虚拟环境中开发应用程序。让云计算负责解决容量计算、带宽、安全性和可靠性方面的问题。
  * [将 Google 的云计算功能连接到 Apple 的 iPhone 中](http://www.ibm.com/developerworks/cn/web/wa-aj-iphone/)（Noah Gift 和 Jonathan Saggau，developerWorks，2009 年 1 月）：了解如何在移动设备上访问云。
  * [使用 IBM InfoSphere Information Server 与 Salesforce CRM 进行数据集成](http://www.ibm.com/developerworks/cn/data/library/techarticles/dm-0807deng/)（Jon Deng 和 Jeff J. Li，developerWorks，2008 年 7 月）：探究如何从您的应用程序访问 Salesforce 中的数据。
  * [Navigate the cloud computing labyrinth](http://www.ibm.com/developerworks/library/wa-cloudflavor/)（Brett McLaughlin，developerWorks，2009 年 3 月）：选用这个最佳云计算平台是一个明智之举，它能满足您的特殊应用程序需求。 
  * [IBM XML 认证](https://www.ibm.com/developerworks/cn/offers/lp/x/xmlcert/)：了解如何成为 IBM 认证的 XML 和相关技术开发人员。
  * [XML 技术库](http://www.ibm.com/developerworks/cn/views/xml/libraryview.jsp)：developerWorks XML 专区提供了大量技术文章和技巧、教程、标准以及 IBM 红皮书。
  * [developerWorks Web 开发专区](http://www.ibm.com/developerworks/cn/web/)：访问 developerWorks Web 开发专区获得大量的技术文章和技巧、教程和标准。
  * [developerWorks 技术活动和网络广播](http://www.ibm.com/developerworks/cn/offers/techbriefings/)：随时关注这些领域内的技术进展。
  * [developerWorks podcasts](http://www.ibm.com/developerworks/podcast/)：收听面向软件开发人员的有趣访谈和讨论。

**获得产品和技术**

  * [Aptana Studio](http://www.aptana.com/)：下载并尝试在 Web 开发环境中使用 Aptana Studio。
  * [IBM 产品评估试用软件](http://www.ibm.com/developerworks/cn/downloads/)：下载或 [在 IBM SOA Sandbox 进行在线测试](http://www.ibm.com/developerworks/downloads/soasandbox/) 并尝试使用这些来自 DB2®、Lotus®、Rational®、Tivoli® 和 WebSphere® 的应用程序开发工具和中间件产品。

**讨论**

  * [XML 专区讨论论坛](http://www.ibm.com/developerworks/forums/dw_xforums.jsp)：参与任何与 XML 相关的讨论。
  * [developerWorks blogs](http://www.ibm.com/developerworks/blogs/)：查阅这些 blogs 并加入 [developerWorks 社区](http://www.ibm.com/developerworks/community)。

**关于作者**

Mark O'Neill 是 Vordel 的 CTO，这是一家 XML 网络公司。他还是 "Web Services Security"
一书的作者，另外也参与了 "Hardening Network Security" 一书的写作，两本书均由 McGraw-Hill/Osborne
Media 出版。Mark 负责监督 Vordel 的产品开发路线图，并建议 Global 2000 公司和各国政府战略性地采用 XML、Web 服务和
SOA 技术。他具有 Trinity College Dublin 的数学与心理学的学位，并从牛津大学获得了神经网络编程的硕士学位。Mark
现生活在马萨诸塞州的波士顿。



---
title: 云计算平台简介（App Engine）
date: 2013-03-13 05:16:00
tags: 
categories: 
---


# 1   简介

**App Engine** **： 应用程序引擎，是** **托管网络应用程序的云计算平台。**



## 1.1  什么是云



云计算通常简称为"云"，是一种通过 Internet 按需交付计算资源（从应用到数据中心都属于计算资源）和按使用付费的基础架构。



  * 富有弹性的资源：能快速轻松地扩大或缩小规模，以满足您的需求
  * 按使用付费：计量服务的使用情况，只需为所用的服务付费
  * 自助服务：使用自助服务可访问您需要的所有 IT 资源



## 1.2  云计算部署模型

### **1.2.1** 公共云

公共云由一些公司运营和拥有，这些公司使用这种云为其他组织和个人提供对价格合理的计算资源的快速访问。使用公共云服务，用户无需购买硬件、软件或支持基础架构，这些都是由提供商拥有并管理的。

### **1.2.2** 私有云

私有云由单个公司拥有和运营，该公司控制各个业务线和授权组自定义以及使用各种虚拟化资源和自动服务方式。私有云充分利用了很多云的高效性，同时提供更多的资源控制并明确掌控多租户。



### **1.2.3** 混合云

混合云使用私有云作为基础，同时结合了公共云服务的策略使用。事实是私有云不会独立于公司其他的 IT
资源和公共云而单独存在。大多数使用私有云的公司都将发展为管理跨数据中心的工作负载、私有云和公共云--因此创建了混合云。



## 1.3  云计算服务架构



### **1.3.1** 基础设施即服务(IaaS)：

基础架构即服务以"按使用付费"为基础，为公司提供各种计算资源，包括服务器、网络、存储和数据中心空间。



### **1.3.2** 平台即服务 (PaaS)

平台即服务提供了基于云的环境，其中具有可支持您构建和交付基于
web（云）应用的完整生命周期所需的一切没有购买和管理基础软件、硬件、供应和托管的成本与复杂性。



### **1.3.3** 软件即服务 (SaaS)

基于云的应用--或软件即服务 (SaaS)--在远端"云中的"计算机上运行，这些其他人拥有和运营的云计算机可以通过 Internet 和 web
浏览器连接到用户的计算机。



参考：<http://www-31.ibm.com/ibm/cn/cloud/index.shtml>



## 1.4  常见云平台



**谷歌        GAE**（Google App Engine）

              http://zh.wikipedia.org/wiki/Google_App_Engine

              支持的编程语言：Python、Java、Go（可扩展其它语言）

**新浪        SAE**（Sina App Engine）

              http://sae.sina.com.cn

              开发语言：目前只支持PHP环境，正在组建Python，Java和Nodejs相关的团队

**百度        BAE**（Baidu Cloud Environment）

              http://developer.baidu.com/bae/

              开发语言：Java、 Python， 同时 Node.js 开放内测

**阿里        ACE**（Aliyun Cloud Engine）

              http://www.aliyun.com/product/ace/

              支持PHP,NODE.JS语言编写的应用程序

**盛大        Grand Cloud**

              http://www.grandcloud.cn/product/ae

              支持PHP，Ruby，Java，Python等语言编写的Web应用



亚马逊    Amazon AWS

微软       Microsoft Server Cloud

       http://www.microsoft.com/zh-cn/server-cloud/

IBM cloud computing  

       http://www-935.ibm.com/services/cn/zh/it-services/cloud-services.html

       http://www-31.ibm.com/ibm/cn/cloud

思科       Cisco CloudVerse

       http://www.cisco.com/web/CN/solutions/trends/cloud/index.html

Autotask

       http://www.autotask.cn

# 2   GAE（Google App Engine）

<http://zh.wikipedia.org/wiki/Google_App_Engine>



## 2.1  什么是Google App Engine

**Google App Engine**
是一个开发、托管[网络应用程序](http://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F
"网络应用程序")的平台，使用[Google](http://zh.wikipedia.org/wiki/Google
"Google")管理的数据中心。它在2008年4月发布了第一个[beta](http://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E9%80%B1%E6%9C%9F#Beta
"软件版本周期")版本。

Google App
Engine使用了[云计算](http://zh.wikipedia.org/wiki/%E4%BA%91%E8%AE%A1%E7%AE%97
"云计算")技术。它跨越多个服务器和数据中心来虚拟化应用程序。[[1]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-1)
其他基于云的平台还有[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")和[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Azure%E6%9C%8D%E5%8A%A1%E5%B9%B3%E5%8F%B0
"Azure服务平台")等。

Google App
Engine在用户使用一定的资源时是免费的。支付额外的费用可以获得应用程序所需的更多的存储空间、带宽或是CPU负载。[[2]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-2)

## 2.2  支持的编程语言和框架

当前，Google App
Engine支持的[编程语言](http://zh.wikipedia.org/wiki/%E7%BC%96%E7%A8%8B%E8%AF%AD%E8%A8%80
"编程语言")是[Python](http://zh.wikipedia.org/wiki/Python
"Python")、[Java](http://zh.wikipedia.org/wiki/Java
"Java")和[Go](http://zh.wikipedia.org/wiki/Go
"Go")（通过扩展，可以支持其他[JVM语言](http://zh.wikipedia.org/w/index.php?title=JVM%E8%AF%AD%E8%A8%80&action=edit&redlink=1
"JVM语言（页面不存在）")，诸如[Groovy](http://zh.wikipedia.org/wiki/Groovy
"Groovy")、[JRuby](http://zh.wikipedia.org/wiki/JRuby
"JRuby")、[Scala](http://zh.wikipedia.org/wiki/Scala
"Scala")和[Clojure](http://zh.wikipedia.org/wiki/Clojure
"Clojure")）。支持[Django](http://zh.wikipedia.org/wiki/Django
"Django")、[WebOb](http://zh.wikipedia.org/w/index.php?title=WebOb&action=edit&redlink=1
"WebOb（页面不存在）")、[PyYAML](http://zh.wikipedia.org/wiki/PyYAML
"PyYAML")的有限版本。Google说它准备在未来支持更多的语言，Google App
Engine也将会独立于某种语言。任何支持[WSGI](http://zh.wikipedia.org/wiki/WSGI
"WSGI")的使用CGI的Python框架可以使用。框架可以与开发出的应用程序一同上传，也可以上传使用Python编写的第三方库。[[3]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-3)[[4]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-4)

## 2.3  与其他应用程序托管的区别

与其他可扩展的托管服务（例如[Amazon EC2](http://zh.wikipedia.org/wiki/Amazon_EC2 "Amazon
EC2")）比较，App Engine提供了更多基础服务来方便编写可扩展的应用程序，但仅限于App Engine设计框架以内的应用程序。

App
Engine的基础服务省却了许多系统管理的操作，以便将规模扩大到数以百万计的访问。Google负责处理一组代码，可以监测、容错，在必要的时候还会开发一些应用实例。

有些应用程序托管服务让用户安装、配置几乎所有[*NIX](http://zh.wikipedia.org/wiki/*NIX
"*NIX")兼容的软件，而App Engine则要求开发者使用[Python](http://zh.wikipedia.org/wiki/Python
"Python")或[Java](http://zh.wikipedia.org/wiki/Java
"Java")语言来编程，而且只能使用一套限定的[API](http://zh.wikipedia.org/wiki/API
"API")。当前的API允许程序于一个[BigTable](http://zh.wikipedia.org/wiki/BigTable
"BigTable")非关系数据库上存储和检索数据、提出HTTP请求、发送E-
mail、处理图像、还有[缓存](http://zh.wikipedia.org/wiki/%E7%BC%93%E5%AD%98
"缓存")。大多数现存的Web应用程序，若未经修改，均不能直接在App
Engine上运行，因为它们需要使用[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")。

带宽和CPU的使用、送达请求的数量、并发请求的数量、以及调用各种API的次数，皆设有每天和每分钟的限额。个别的请求，如果需时超过30秒或返回超过10MB的数据，都会被终止。

## 2.4  SQL与GQL的区别

Google App
Engine的Datastore使用一个与SQL类似的语言，叫做"GQL"。在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句仅可以用于一个表。因为要跨越不只一台机器，
GQL不支持效率很低的[JOIN](http://zh.wikipedia.org/w/index.php?title=JOIN&action=edit&redlink=1
"JOIN（页面不存在）")语句[[5]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-5)。欲创建一对多和多对多的关系，可使用ReferenceProperty()[[6]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-6)。采用这种无共享的方式，即使磁盘坏了，系统也不致瘫痪[[7]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-7)。

在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句中的[WHERE](http://zh.wikipedia.org/w/index.php?title=WHERE&action=edit&redlink=1
"WHERE（页面不存在）")从句只容许对仅仅一列进行>、>=、<或<=比较。所以，仅仅可以构造简单的WHERE从句。在数据建模时，要从[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")转换到Datastore，开发者需要转变观念。

App
Engine限制每次Datastore请求最多返回1000行数据。大多数Web应用程序，都不会受此影响，因为它们通常并不会在一张页面上列出超过1000条记录（可以用分页和缓存机制），只要按顺序返回结果就可以了。若有应用程序需要在一次操作中返回更多的记录，则需自行使用客户端软件或者[Ajax](http://zh.wikipedia.org/wiki/Ajax
"Ajax")页面，按查询顺序提取更多条记录。

这个Datastore的API是不关联的，有别于一般关系数据库----比如[IBM
DB2](http://zh.wikipedia.org/wiki/IBM_DB2 "IBM DB2")、[Microsoft SQL
Server](http://zh.wikipedia.org/wiki/Microsoft_SQL_Server "Microsoft SQL
Server")、[MySQL](http://zh.wikipedia.org/wiki/MySQL
"MySQL")、[Oracle数据库](http://zh.wikipedia.org/wiki/Oracle%E6%95%B0%E6%8D%AE%E5%BA%93
"Oracle数据库")、或者[PostgreSQL](http://zh.wikipedia.org/wiki/PostgreSQL
"PostgreSQL")。

## 2.5  限制

  * 在App Engine的文件系统中，开发者只有读取的权限。
  * App Engine仅可在回应HTTP请求时执行代码（计划的后台任务、任务队列和XMPP服务则不在此限）。
  * 用户可以上传任意的Python模块，但必须是纯Python模块，不得包含[C](http://zh.wikipedia.org/wiki/C%E8%AF%AD%E8%A8%80 "C语言")扩展程序或其他需要编译的代码。
  * App Engine限制每次Datastore请求最多返回1000行数据。
  * Java应用程序只能使用JRE基本版本类库中的一个子集（[JRE类白名单](http://code.google.com/appengine/docs/java/jrewhitelist.html)）[[8]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-8)。
  * Java应用程序不能创建新的线程。

## 2.6  可移植性

开发者担心App
Engine应用程序不能移植到其他平台上，因而被困在单一种技术之内。[[9]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-9)

## 2.7  从App Engine下载数据

App
Engine自SDK1.2.2版开始，已容许以批量的方式下载数据[[10]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-10)。此外，用户也可使用开源项目gaebar[[11]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-11)、approcket[[12]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-12)
和gawsh[[13]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-13)
来下载、备份在App Engine上的数据。

## 2.8  限额

免费帐户使用App
Engine时，受配额限制。应用程序作者可以视乎需要，付钱购买更多配额。[[14]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-
Quotas-14)

### **2.8.1** 硬性限制

**项目**

|

**限制**  
  
---|---  
  
每次请求的时间

|

普通请求60秒，任务请求10分钟，后台请求无限  
  
每个应用程序的文件

|

1000个  
  
HTTP响应的大小

|

32 MB  
  
Datastore单项大小

|

1 MB  
  
应用程序代码大小

|

150 MB  
  
### **2.8.2** 免费的配额

供免费使用的配额曾于[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[5月25日](http://zh.wikipedia.org/wiki/5%E6%9C%8825%E6%97%A5
"5月25日")[[15]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-15)
、[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[6月22日](http://zh.wikipedia.org/wiki/6%E6%9C%8822%E6%97%A5
"6月22日")以及[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")[5月](http://zh.wikipedia.org/wiki/5%E6%9C%88
"5月")三度下调[[16]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-16)。

**项目**

|

**配额**  
  
---|---  
  
每天的Email数量

|

100封  
  
每天的输入数据

|

无限  
  
每天的输出数据

|

1 GB  
  
每天可使用CPU

|

28小时  
  
每天调用Datastore API次数

|

50000次*  
  
数据存储

|

1 GB  
  
每天调用URLFetch API次数

|

657000次*  
  
## 2.9  竞争对手

Google App Engine与[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")（一个应用程序服务系统，支持在Amazon的服务器上托管文件、执行代码）直接竞争。不少科技分析师早在多年前已预计过，Google会加入这场竞赛。其中，Techdirt的出版人[Mike
Masnick](http://zh.wikipedia.org/w/index.php?title=Mike_Masnick&action=edit&redlink=1
"Mike
Masnick（页面不存在）")写到，"Google终于了解到它需要霸占网络平台这个地位。我们可以期待，开发及落实易于扩展的网络应用程序会变得越来越容易，而应用程序也会越来越具创意。"[[17]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-17)

此外，[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Windows_Azure "Windows
Azure")也是Google App Engine的竞争对手。

## 2.10 中国大陆封锁

由于Google App
Engine允许用户托管网络应用程序，且服务器不在[中国大陆](http://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9B%BD%E5%A4%A7%E9%99%86
"中国大陆")境内，故有部分用户利用其搭建代理（如[GoAgent](http://zh.wikipedia.org/wiki/GoAgent
"GoAgent")）用于突破[防火长城](http://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E
"防火长城")的[审查](http://zh.wikipedia.org/wiki/%E7%A0%B4%E7%BD%91
"破网")[[18]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-18)，故Google
App Engine的域名appspot.com的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")加密连接长期遭到防火长城的封锁。

[2010年](http://zh.wikipedia.org/wiki/2010%E5%B9%B4
"2010年")[12月20日](http://zh.wikipedia.org/wiki/12%E6%9C%8820%E6%97%A5
"12月20日")，Google App Engine的域名appspot.com遭到防火长城的关键词过滤封锁。由于先前Google App
Engine的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")连接已经被封，故中国大陆境内的用户无法正常连接与使用。此次Google App
Engine被封锁适逢[2010年诺贝尔和平奖](http://zh.wikipedia.org/wiki/2010%E5%B9%B4%E8%AF%BA%E8%B4%9D%E5%B0%94%E5%92%8C%E5%B9%B3%E5%A5%96
"2010年诺贝尔和平奖")颁奖典礼。appspot.com非加密连接于2010年[12月23日](http://zh.wikipedia.org/wiki/12%E6%9C%8823%E6%97%A5
"12月23日")解封。

[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")3月[两会](http://zh.wikipedia.org/wiki/%E4%B8%A4%E4%BC%9A
"两会")召开前夕，appspot.com再次遭到防火长城的关键词过滤封锁及[域名污染](http://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%B1%A1%E6%9F%93
"域名污染")，同时部分服务器的IP地址亦遭到彻底屏蔽，甚至两会结束后至今亦没有解封。

## 2.11 参见

  * [Google产品列表](http://zh.wikipedia.org/wiki/Google%E4%BA%A7%E5%93%81%E5%88%97%E8%A1%A8 "Google产品列表")



# 3   SAE（Sina App Engine）

[http://sae.sina.com.cn](http://sae.sina.com.cn/)



## 3.1  什么是Sina App Engine  



        Sina App Engine（以下简称SAE）是新浪研发中心于2009年8月开始内部开发，并在2009年11月3日正式推出第一个Alpha版本的国内首个公有云计算平台（http://sae.sina.com.cn），  SAE是新浪云计算战略的核心组成部分。     

        SAE作为国内的公有云计算，从开发伊始借鉴吸纳Google、Amazon等国外公司的公有云计算的成功技术经验，并很快推出不同于他们的具有自身特色的云计算平台。SAE选择在国内流行最广的Web开发语言PHP作为首选的支持语言，Web开发者可以在Linux/Mac/Windows上通过SVN或者Web版在线代码编辑器进行开发、部署、调试，团队开发时还可以进行成员协作，不同的角色将对代码、项目拥有不同的权限；SAE提供了一系列分布式计算、存储服务供开发者使用，包括分布式文件存储、分布式数据库集群、分布式缓存、分布式定时服务等，这些服务将大大降低开发者的开发成本。同时又由于SAE整体架构的高可靠性和新浪的品牌保证，大大降低了开发者的运营风险。另外，作为典型的云计算，SAE采用"所付即所用，所付仅所用"的计费理念，通过日志和统计中心精确的计算每个应用的资源消耗（包括CPU、内存、磁盘等）。     

      总之，SAE就是简单高效的分布式Web服务开发、运行平台。 

         目前SAE只支持PHP环境，我们正在组建Python，Java和Nodejs相关的团队

## 3.2  SAE的核心优势

        SAE的基本目标用户有两种，一种是Web开发者，另一种是普通互联网上网人群。

        对于Web开发者，SAE带来的好处有：

         *****  硬件成本更低，无需预先购买设备，承担更大的投入风险     

         *****  开发成本更低，SAE提供许多服务供开发者使用，开发者无需重复开发，包括队列、数据库、缓存、定时、验证码、计数器，几乎覆盖了Web开发的所有领域。另外对于特定开放平台的开发者，比如新浪微博开发者，SAE已经集成了完整的OpenAPI的封装，将开发者的开发成本降到最低。值得一提的是，SAE的开发者目前已经形成了良好的交流氛围，在意见反馈中心、SAE官方群，SAE官方微群可以看到很多热情的开发者在一起共同提高

         *****  运维成本更低，在SAE上的应用无需关心硬件维护、服务监控、数据容灾等操作，SAE会通过其高可靠的架构和方便的监控页面为用户将运维成本降到最低扩展性更强，在SAE上的服务无需关心服务压力猛增时带来的扩容等操作，SAE自动支持服务扩展

         *****  更加安全可靠，SAE自动提供SQL语句性能分析、前端防攻击、代码检查等功能，在SAE上的所有应用均为多机房容灾部署，比传统的部署模式更加安全可靠，并且SAE提供服务的SLA来实现对用户服务质量的承诺

        对于普通上网人群，使用SAE可以：

        使用推荐应用一键安装Web应用，普通用户无需会编码，也可以在瞬间拥有自己的团购、博客、微博、Wiki等。 

## 3.3  SAE整体架构

        SAE从架构上采用分层设计，从上往下分别为反向代理层、路由逻辑层、Web计算服务池。而从Web计算服务层延伸出SAE附属的分布式计算型服务和分布式存储型服务，具体又分成同步计算型服务、异步计算型服务、持久化存储服务、非持久化存储服务。各种服务统一向日志和统计中心汇报，参考下图：





    

        7层反向代理层：HTTP反向代理，在最外层，负责响应用户的HTTP请求，分析请求，并转发到后端的Web服务池上，并提供负载均衡、健康检查等功能。

        服务路由层：逻辑层，负责根据请求的唯一标识，快速的映射（O(1)时间复杂度）到相应的Web服务池，并映射到相应的硬件路径。如果发现映射关系不存在或者错误，则给出相应的错误提示。该层对用户隐藏了很多具体地址信息，使开发者无需关心服务的内部实际分配情况。

        Web服务池：由一些不同特性的Web服务池组成。每个Web服务池实际是由一组Apache(PHP)组成的，这些池按照不同的SLA提供不同级别的服务。每个Web服务进程实际处理用户的HTTP请求，进程运行在HTTP服务沙盒内，同时还内嵌同样运行在SAE沙盒内的PHP解析引擎。用户的代码最终通过接口调用各种服务。

        日志和统计中心：负责对用户所使用的所有服务进行统计和资源计费，并设定的分钟配额，来判定是否有非正常的使用。分钟配额描述了资源消耗的速度，当资源消耗的速度到达一个预警阈值时，SAE通知系统会提前向用户发出一个警告，提醒用户应用在某个服务上的使用可能存在问题，需要介入关注或处理，配额系统是SAE用来保证整个平台稳定的措施之一；日志中心负责将用户所有服务的日志汇总并备份，并提供检索查询服务。

        各种分布式服务：SAE提供几乎可以覆盖Web应用开发所有方面的多种服务，用户可以通过StdLib（可以理解为SAE PHP版的STL）很方便的调用它们。 

## 3.4  SAE的线路特性



                 



    SAE平台出口IP：

     220.181.129.126  
    220.181.129.121  
    220.181.136.229  
    220.181.136.230  
    220.181.129.93  
    220.181.129.102  
    220.181.129.117  
    220.181.129.90





    http接口方需要IP授权可以进行相应的设置。 

## 3.5  SAE的功能

 开发：

         *****    代码检查，帮助检查不良函数并帮助移植

         *****    代码部署

         *****   分布式数据库

         *****    分布式文件存储

         *****    分布式缓存

         *****    各种附属分布式服务，包括图像、定时、任务队列、邮件、计数器等

         *****    对接多个开放平台，如新浪微博开发平台

         *****   代码调优，通过[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)提供

         *****    数据库优化，通过[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)提供

         *****    团队协作，可以邀请好友以不同的权限加入项目

         *****    代码版本管理（计划支持）

运营：

         *****    应用打包，通过我们的应用向导进行推广

         *****   日志，包括访问日志、错误日志等

         *****    资源报表，消耗SAE各项资源的统计

         *****    服务监控，监控各项服务状态

         *****    数据迁移，包括数据库导入、数据库导出等 

## 3.6  SAE提供的服务及两大特性



SAE提供的服务

        SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下：

服务名称

|

类型

|

说明  
  
---|---|---  
  
HTTP+PHP

|

同步计算

|

带SAE沙盒的Apache和Zend为用户提供Web计算服务  
  
[Storage](http://sae.sina.com.cn/?m=devcenter&catId=204)

|

持久化存储

|

提供分布式文件存储  
  
[Memcache](http://sae.sina.com.cn/?m=devcenter&catId=201)

|

非持久化存储

|

提供分布式缓存服务  
  
[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)

|

持久化存储

|

分布式数据库集群，提供[MySQL](http://sae.sina.com.cn/?m=devcenter&catId=192)服务  
  
[TaskQueue](http://sae.sina.com.cn/?m=devcenter&catId=205)

|

异步计算

|

异步离线轻量级任务队列，HTTP方式调用  
  
[DeferredJob](http://sae.sina.com.cn/?m=devcenter&catId=196)

|

异步计算

|

异步离线重量级任务队列，系统方式调用  
  
[Counter](http://sae.sina.com.cn/?m=devcenter&catId=194)

|

持久化存储

|

计数器服务  
  
RankDB

|

持久化存储

|

分布式排行榜服务  
  
[KVDB](http://sae.sina.com.cn/?m=devcenter&catId=199)

|

持久化存储

|

分布式key/value存储服务  
  
[Cron](http://sae.sina.com.cn/?m=devcenter&catId=195)

|

异步计算

|

分布式定时服务  
  
[FetchURL](http://sae.sina.com.cn/?m=devcenter&catId=197)

|

同步计算

|

分布式抓取服务  
  
[TmpFS](http://sae.sina.com.cn/?m=devcenter&catId=206)

|

非持久化存储

|

提供临时文件存储，文件生命周期在一个会话内，Http请求结束文件自动消失  
  
[AppConfig](http://sae.sina.com.cn/?m=devcenter&catId=193)

|



|

提供应用配置功能，取代Apache htaccess  
  
[Mail](http://sae.sina.com.cn/?m=devcenter&catId=200)

|

异步计算

|

邮件发送服务  
  
[Image](http://sae.sina.com.cn/?m=devcenter&catId=198)

|

同步计算

|

图像处理服务  
  
[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)

|

同步计算

|

Facebook提供的强大的PHP调优工具  
  
SVN

|

持久存储

|

用户代码部署的入口点:https://svn.sinaapp.com/yourapp  
  
Online CodeEditor

|

持久存储

|

在线代码编辑器，编辑的代码保存后入自动入SVN并部署到Web服务器  
  
 两大特性：扩展性与可靠性

*****    扩展性

        SAE在服务的可扩展性上基本是动态可扩展性的思路，即资源和ID没有强对应关系，用户以服务使用者的身份使用SAE服务。

*****    可靠性

        在计算可靠性方面，SAE主要是依靠多点部署来完成可靠性，多节点的计算一致性上，SAE有分布式锁服务提供比Paxos更好的容错逻辑。

        在数据可靠性方面，SAE的所有数据都通过冗余存储来达到SLA。SAE通过主动复制和被动复制来实现多点数据冗余。



## 3.7  SAE和虚拟主机的区别

         *****    传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权；而SAE面向的服务，使用者得到的是服务的使用权。 

         *****    传统服务托管不面向开发者，开发者无法在其上享受到开发的乐趣；而SAE的一个重要用户就是web developer，开发者可以在其              上通过在线调试、日志分析、协作共享等功能进行web开发。 

         *****    传统服务托管不提供分布式系统解决方案；而SAE提供的完整的分布式web服务的解决方案，其中不仅仅包括分布式数据库、分布               式文件系统，更包括分布式定时器系统、网页抓取服务、图像处理服务等。

         *****    传统服务托管不解决域名问题，用户往往烦恼于域名申请；而SAE的用户将自动得到在sinaapp下的二级域名，同时SAE还支持域                名cname。 

         *****    传统服务托管无法保证SLA（Service Level Agreement），硬件故障的成本基本由使用者承担；而SAE保证用户的SLA，用户的                   web服务自动享有高冗余的前端服务器、享有自动负载均衡系统、服务自动扩展、服务自动收缩等功能。 

         *****   传统的服务托管采用预付费的方式，费用固定且和实际使用情况无直接关系；而SAE采用预充值方式，"所付即所用，所付仅所用"，             web服务的一切损耗均提供报表查询和账单汇总，让用户一目了然。



SAE公有云计算和传统的虚拟主机的区别如下表。



类项

|

SAE

|

VPS  
  
---|---|---  
  
核心用户

|

Web开发者

|

无核心用户  
  
使用方式

|

服务使用

|

设备租用  
  
目标

|

力争覆盖Web服务所有需求，提供多种服务给开发者使用

|

仅基本需求  
  
SLA（服务承诺）

|

高可靠性及严格的服务承诺

|

依服务商变化，无严格协议  
  
计费方式

|

所付即所用，所付仅所用

|

预付费，无精确计费  
  


## 3.8  为什么我们要做SAE

        Sina App Engine项目始于2009年8月，目标为云计算时代的分布式web服务提供一整套解决方案。我们开发SAE主要是出于对内、对外两方面考虑：

        对内，新浪很早以前就开始了关于私有云的开发和实践，所以为了进一步提高公司资源的利用率，更加提高web开发的效率，降低web运营的成本，决定了我们要开发SAE。

        对外，亚马逊、Google都是国外的成功的提供公有云计算服务的公司，SAE也想借助云计算这样一个趋势，为国内广大用户提供云计算的分布式web服务的开发、运行平台。



## 3.9  SAE的目标和发展  

        云计算虽然是个新名词，但实际在国外已经有4、5年的历史。2006年，亚马逊就推出了以EC2为代表的公有云计算，并且已经实现了大规模盈利；2008年，Google则推出了以Google App Engine为代表的公有云计算。国内的云计算却一直是炒的很厉害，各大互联网公司都在宣传，但真正有技术实力做出来而又对外公开使用的少之又少。

        实际从2004年开始，新浪就开始了私有云方向的研究和实践，以此为基础的动态应用平台目前已经支撑新浪内部的绝大部分业务。从2008年起，新浪又启动了"浪云"的公有云计算计划，相继开发了分布式队列服务、P2P文件系统、分布式计算框架等一系列基础服务。实际SAE就是"浪云"战略的产物。

        SAE从架构设计和代码编写开始，就明确了自身的两个目标：

         *****  做公有云计算平台。公有云不同于私有云，更强调安全性和可靠性，这也对整体的架构设计和技术实现提出了更苛刻的要求

         *****  为分布式Web服务提供一整套的解决方案。SAE争取提供开发者开发Web应用过程中所用到的所有服务。

        经过技术团队一年的开发，SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下： 

        SAE在2009年11月3日发布了alpha1版本，2010年2月1日发布了alpha2版本，2010年9月1日发布了beta版本，2011年5月17日正式开放注册。



## 3.10 加入SAE

        SAE重视每一名Web开发者和普通用户，SAE坚信：

        "SAE的未来取决于能否帮助Web开发者实现其价值体现，取决于是否能和Web开发者实现双赢的良性循环，并最终为互联网所有用户提供高质量的有价值的应用和服务。"

        所以SAE欢迎更多的Web开发者参与，并且欢迎一切喜欢热爱SAE的有志之士能够亲身的参与到SAE整体架构和技术研发中来（简历投递请关注我们的官方微博<http://t.sina.com.cn/saet>和博客[http://blog.sae.sina.com.cn](http://blog.sae.sina.com.cn/)），让我们一起搭建SAE的未来！



# 4   BAE（Baidu Cloud Environment）

<http://developer.baidu.com/bae/>



## 4.1  百度云平台

<http://developer.baidu.com/wiki/index.php?title=docs/cplat>

百度云平台是百度开放其基础能力，为开发者提供的基于"云"的服务的统称，包括云环境，云服务，集成开发环境，移动测试以及移动建站工具等，未来还会加大对移动应用开发的支持。

  
图：百度云平台构成图

## 4.2  云环境

百度云环境，即BCE（Baidu Cloud Environment），提供多语言、弹性的服务端运行环境，能帮助开发者快速 **开发并部署**
应用。云环境内置丰富的分布式计算API，并支持全方位的百度"云"服务，更能为您的应用带来强大动力，从"本地"变"分布式"，简单可依赖。

开发语言：Java、 Python， 同时 Node.js 开放内测

## 4.3  云服务

### **4.3.1** 云数据库

百度云数据库，提供基于MySQL的关系数据库服务。（已转移到应用内管理，详情请参考：[PHP](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/php/mysql
"docs/cplat/rt/php/mysql")
[Java](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/java/mysql
"docs/cplat/rt/java/mysql")
[Python](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/python/mysql
"docs/cplat/rt/python/mysql")）

### **4.3.2** 云存储

百度云存储，即BCS（Baidu Cloud Storage），提供File-Like的开放存储服务，开发者可以在任何时间、任何地点存储任何类型的数据。

### **4.3.3** 云消息

百度云消息，即BCM（Baidu Cloud Messaging），提供消息队列，短消息、电子邮件发送等服务。

### **4.3.4** 云推送

百度云推送（简称Channel）服务为开发者提供了向浏览器、手机和PC客户端推送消息的服务。

### **4.3.5** 云触发

百度云触发（简称Trigger）服务为开发者提供了"数据变更->动作"的触发机制，开发者可以通过使用云触发服务来订阅需要关注的资源，当资源数据发生变化时，服务系统就会自动调用开发者的回调接口。

### **4.3.6** 虚拟机

百度云存储，即BVM（Baidu Virtual Machine），提供多种配置的虚拟机服务。（仅对合作开发者开放）

## 4.4  工具

### **4.4.1** SiteApp

百度SiteApp，是国内首家Web应用在线生成服务，可帮您将传统网站快速转化为移动Web应用。

### **4.4.2** 移动测试中心

百度移动测试中心（MTC），提供主流手机终端的真机的遍历测试，UI适配、安装卸载测试、手动测试等功能。

### **4.4.3** 云众测

百度云众测，输出百万级别社区测试能力，提供APP评测、用户体验反馈、问卷调查等功能。



# 5   ACE（Aliyun Cloud Engine）

<http://www.aliyun.com/product/ace/>



## 5.1  什么是Cloud Engine

ACE（Aliyun Cloud
Engine）是一个基于云计算基础架构的网络应用程序托管环境，帮助应用开发者简化网络应用程序的构建和维护，并可根据应用访问量和数据存储的增长进行扩展。ACE支持PHP,NODE.JS语言编写的应用程序；支持在线创建MYSQL远程数据库应用。

Cloud
Engine（云引擎，简称CE），是阿里云历经多年研发，于今年7月推出的一款基于弹性计算平台的web应用运行环境，能够提供应用的线性伸缩、动态扩容以及多种相关服务。

Cloud
Engine借鉴并吸纳Google、Amazon、Rackspace等国外知名公司的公有云计算的成功技术经验，结合阿里云多年的技术研发沉淀，保证了该平台的高效和稳定。目前支持PHP和NodeJS两种开发语言，后续会支持更多的开发语言。围绕这个平台，我们也提供了session、storage、memcache、cron等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。模板功能的提供，可以有效的衔接开发者和站长，让开发者的成果可以更加有效的传播，同时站长也有更加灵活丰富的应用可以运营。

Cloud App是阿里云手机开发平台，Cloud
Engine作为阿里云手机在云端的延伸，为云手机开发者提供NodeJS运行环境和伸缩性的支持，让开发者有效的衔接手机和云端的开发，简化开发流程。



## 5.2  竞争力

Cloud Engine的目标用户有两种，分别是Web开发者和站长。使用Cloud Engine，可以让您：

1、无需硬件的投资，降低投入风险；

2、内置丰富的服务，包括session，memcache，storage，cron，云数据库，应用管理和配置，覆盖了web开发的大部分领域；

3、高效稳定的运行环境，兼容大部分原生的PHP 5.3程序，弹性伸缩，不用再当心访问量过大；

4、 高效安全的云存储服务，不用当心数据会丢失；

5、经验丰富的阿里运维和安全团队，协助解决网络攻击，网站挂马，漏洞扫描，代码行为分析等，并对服务异常进行告警；

6、 开发人员可以将自己的应用做成模板，发布其应用给其他人使用，站长可以从模板库中在线创建应用，即可进行自己的网站运营。

另外，ISV厂商可以在自己的系统中集成OpenAPI，允许管理和发布用户创建的应用。



## 5.3  应用程序环境

Cloud Engine可以保证您在负载很重和数据量极大的情况下，也可以轻松构建能安全运行的应用程序。

1、自动扩容，用户可以根据自身需求，申请存储，缓存等容量。

2、动态的网络服务，提供对常用网络技术的完全支持

3、持久存储空间，存储用户需要的落地的数据

4、 负载平衡，选择当前较空闲的机器，执行任务

5、与本地开发环境兼容，方便开发者移植代码到CE运行环境

6、分布式定时计算，提供定时和定期触发事件的计划任务。

您的应用程序可在以下两个运行时环境之一中运行：NodeJS 环境和 PHP
环境。各环境均为网络应用程序开发提供标准协议和常用技术。您的应用程序使用NodeJS和PHP的标准API来访问大多数CE服务。



## 5.4  功能介绍



开发：

1、Session，分布式session，开发者无需考虑跨多台机器的session处理

2、Storage，基于开放式存储服务，支持多台机器的同时访问

3、 memcache，分布式缓存，有效解决memcache的多机共享，和实例重启引发的缓存清空

4、cron，通过函数调用方式，支持定时和定期执行任务

5、 应用管理和配置，支持应用的创建、启动、停止、更新、查看等操作

6、mysql数据库支持，双机热备，支持在线迁移和备份，单表可支持上亿记录

运营：

1、开发者可利用模板库分发应用

2、站长可以通过模板库在线快速创建应用

3、平台可监控各种服务的状态

4、 对消耗的资源有详细的统计记录

5、方便的数据导入和导出



## 5.5  云引擎、虚拟主机、VPS的区别



传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权，没有相关的服务；而Cloud
Engine面向的服务，使用者得到的是稳定可靠的全面服务，同时分布式的平台保证了数据的安全性和访问的快速。

** **

|

**云引擎**

|

**虚拟主机**

|

**VPS**  
  
---|---|---|---  
  
用户群

|

web开发者和站长

|

站长

|

没有限定  
  
使用方式

|

服务租用

|

服务租用

|

虚拟设备租用  
  
运行环境

|

支持多种开发语言

|

支持较少开发语言

|

需要自己安装  
  
目标

|

开发者和站长的整体服务

|

展示性的网站

|

仅提供最基本的设施  
  
安全保证

|

沙箱+专业的安全团队

|

根据服务商来定

|

根据用户能力来定  
  
服务承诺

|

稳定可靠安全的服务承诺

|

根据服务商来定

|

根据服务商来定

  
  


## 5.6  发展目标



互联网给PC带来了时代的变革，我们相信，云计算会给互联网带来更大的变革。以亚马逊EC2为代表的IaaS和以Google代表的PaaS，已经在国外掀起了互联网应用的高潮。反观国内，以阿里云为代表的互联网企业，率先将云计算服务落地，并对外提供公有云服务。

阿里云一直有一个目标，就是做一个互联网的数据分享平台，让广大用户可以在这个平台上协作完成数据的分享。我们一直在朝着这个方向努力，Cloud
Engine的诞生就是为了进一步的实现这个目标，帮助广大的开发者和站长实现数据分享的梦想。

因此我们也向用户承诺，我们只做公有云的计算平台，保证平台上数据的安全性和可靠性，提供一个稳定高效的分布式web
service的解决方案，为用户提供尽可能多的服务。



## 5.7  服务限制

为保证应用的安全性和稳定性，我们对各类服务设定了一些限制，请用户仔细阅读。

1、每个用户最多可以创建3个应用，包含从模板创建的应用

2、 禁止本地文件读写，读写文件可以使用我们的OSS（开放存储服务），OSS存储空间不受容量限制

3、对试图破坏或滥用配额（例如同时在多个帐户上操作应用程序）违反服务条款的用户，可能导致应用程序被禁用或帐户关闭

4、我们对PHP环境进行了一些限制，具体参考：http://ace.aliyun.com/index/help/



## 5.8  产品详情



### **5.8.1** 支持多种WEB运行环境

ACE目前支持PHP运行环境，NodeJS运行环境，后续会支持更多的开发语言。

### **5.8.2** 丰富的附加服务

我们提供了分布式session，分布式memcache，开放存储，消息队列，计划任务等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。



### **5.8.3** 弹性伸缩、按需计费

自动弹性伸缩，无需人工干预运维，根据实际使用量计费。



### **5.8.4** 通过应用模板快速部署应用

系统自带常见应用模板。开发人员可以将自己的应用做成模板，发布其应用给其他人使用；站长可以从模板库中在线创建应用，即可进行自己的网站运营。



### **5.8.5** 良好的易用性

兼容原生API， 调试信息输出，可以方便的进行应用管理和配置。



## **5.9   ****价格总览：** ** **

[http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744](http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744)



### **5.9.1** **云服务器价格总览**

**类型**

|

**CPU**

|

**内存**

|

**数据盘**

|

**带宽**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**经济** **A** **型**

|

1核Xeon 2.26GHz

|

512MB

|

40GB

|

1Mbps

|

**85** 元

|

**850** 元

|

[马上购买](http://buy.aliyun.com/?cid=452/)  
  
**经济** **B** **型**

|

1核Xeon 2.26GHz

|

1.5GB

|

80GB

|

2Mbps

|

**181** 元

|

**1810** 元

|

[马上购买](http://buy.aliyun.com/?cid=453/)  
  
**标准** **A** **型**

|

2核Xeon 2.26GHz

|

1.5GB

|

130GB

|

5Mbps

|

**376** 元

|

**3760** 元

|

[马上购买](http://buy.aliyun.com/?cid=13/)  
  
**标准** **B** **型**

|

2核Xeon 2.26GHz

|

2.5GB

|

230GB

|

5Mbps

|

**500** 元

|

**5000** 元

|

[马上购买](http://buy.aliyun.com/?cid=14/)  
  
**标准** **C** **型**

|

4核Xeon 2.26GHz

|

4GB

|

480GB

|

5Mbps

|

**810** 元

|

**8100** 元

|

[马上购买](http://buy.aliyun.com/?cid=15/)  
  
**标准** **D** **型**

|

4核Xeon 2.26GHz

|

8GB

|

730GB

|

5Mbps

|

**1205** 元

|

**12050** 元

|

[马上购买](http://buy.aliyun.com/?cid=16/)  
  
**标准** **E** **型**

|

8核Xeon 2.26GHz

|

16GB

|

730GB

|

5Mbps

|

**1916** 元

|

**19160** 元

|

[马上购买](http://buy.aliyun.com/?cid=17/)  
  








### **5.9.2** **关系型数据库** **RDS** **价格总览：**



**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**MySQL**

|

新1型

|

240

|

10

|

60

|

**70** 元

|

**700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=462)  
  
新2型

|

600

|

20

|

150

|

**200** 元

|

**2000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=463)  
  
新3型

|

1200

|

50

|

300

|

**408** 元

|

**4080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=464)  
  
新4型

|

2400

|

100

|

600

|

**808** 元

|

**8080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=465)  
  
新5型

|

6000

|

200

|

1500

|

**1888** 元

|

**18880** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=466)  
  
新6型

|

12000

|

500

|

2000

|

**3816** 元

|

**38160** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=467)  
  
新7型

|

24000

|

1000

|

2000

|

**7470** 元

|

**74700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=468)  
  


**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**SQL Server**

|

1型

|

1000

|

50

|

100

|

**530** 元

|

**5300** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=469)  
  
2型

|

2000

|

100

|

200

|

**1040** 元

|

**10400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=470)  
  
3型

|

4000

|

200

|

400

|

**2050** 元

|

**20500** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=471)  
  
4型

|

6000

|

300

|

600

|

**3060** 元

|

**30600** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=472)  
  
5型

|

8000

|

400

|

800

|

**3870** 元

|

**38700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=473)  
  
6型

|

12000

|

600

|

1200

|

**5200** 元

|

**52000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=474)  
  
7型

|

24000

|

1000

|

2000

|

**10040** 元

|

**100400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=475)  
  
用户使用RDS期间产生的公网流量费用为1元/GB。内网流量免费，例如用户在云服务器和RDS之间进行的数据传输是免费的。





### **5.9.3** **开放存储服务** **OSS** **价格总览：**

  * **   OSS** **产品收费方式**
  * 开放存储服务（OSS）采用按需付费，日结算方式。采用先充值，后按实际用量结算方式进行结算。每日结算一次，按实际消费金额对充值款进行扣费。当"账户余额"不足时，服务将会自动停止。  
OSS产品计费项包括：容量、流出流量和请求次数。  
容量计费，按用户数据占用的存储空间量收取费用；  
流出流量计费，按用户存储数据被调用或下载产生的流量收取费用；  
请求次数，按调用API各种请求的次数收取费用；  
每日计费总费用=容量占用费用+流出流量费用+请求次数费用。

[[我要充值]](http://i.aliyun.com/charge)

  *  
  * **   OSS** **价格表  **

存储空间：

**0 GB - 500 GB**

0.02 元/GB * 天 (约 0.6 元/GB * 月)

**› 500 GB - 2 TB**

0.018 元/GB * 天 (约 0.55 元/GB * 月)

**› 2 TB - 10 TB**

0.016 元/GB * 天 (约 0.5 元/GB * 月)

**› 10 TB - 50 TB**

0.015 元/GB * 天 (约 0.45 元/GB * 月)

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

流入流量

**流入流量**

免费

流出流量

**0 GB - 500 GB**

0.75 元/GB

**› 500 GB - 2 TB**

0.7 元/GB

**› 2 TB - 10 TB**

0.65 元/GB

**› 10 TB - 50 TB**

0.6 元/GB

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

注：内网流量免费：即OSS与阿里云服务器之间的网络流量，通过使用oss-internal.aliyuncs.com的方式可享受内网流量免费。

数据请求

**Get/Head Object**

每 10000 次 0.01 元

**其他所有请求**

每 1000 次 0.01 元

OSS免费体验活动：

即日起新开通OSS用户，可享受50G存储空间，每月累计10G流出流量, 免费体验服务；  
免费体验时间为自服务开通之日起180天内，均可享受免费体验服务；  
免费体验期间，使用量超出免费范围，超出部分按实际报价收费；  
免费体验期间，请求次数正常收费；  
参加活动方法，立即注册、免费开通OSS服务即可。

  *  
  * **   ** **扣费说明**
  * 流出流量最小计量单位为1GB，请求次数最小计量单位为10000次，不足最小计量单位用量当日不予扣费，累加到次日使用量中。
  *  
  * **   ** **欠费说明**
  * 当"阿里云账户"出现负数（即：欠费状态），OSS服务将自动停止。而您所占用的存储空间的这部分资源仍会继续按日扣费， 因此欠费余额会累计。您可以在出现欠费之日起15天内及时充值并补足欠费后，服务会自动开启，可以继续使用。欠费超过15天，将视为您主动放弃OSS存储 服务，存储空间将被回收，存储空间内的数据会被清理，数据不可恢复。
  *  



# 6   Grand Cloud



<http://www.grandcloud.cn/product/ae>



## 6.1  盛大云引擎功能概述

盛大云引擎是基于盛大云计算基础设施服务的Web应用托管平台，旨在降低应用的部署与运维成本，让应用开发者可以专心于业务的开发设计，不再担心后台的构建与运维。云引擎支持PHP，Ruby，Java，Python等语言编写的Web应用，后端提供丰富的数据存储服务，并根据应用访问量和业务规模进行弹性扩展。云引擎目前为Beta版本，各项功能不断上线。

## 6.2  产品特点

**零运维成本**  
只需上传代码，无需手工操作，即可完成代码部署。同时，提供访问统计与运行资源监控，应用状况尽在掌控。

**多语言支持**  
应用管理基于CloudFoundry。用户可以提交PHP、Ruby、Java、Python等语言开发的Web程序。

**弹性扩展**  
按访问量自动增加运行实例，并提供访问负载均衡。

**数据可靠**  
系统使用盛大云的云硬盘与云数据库等服务，确保数据的高可靠性。

**应用仓库**  
用户可以从应用仓库中选择并快速部署应用，简化开发任务。同时，鼓励开发人员提交应用，与所有用户分享。

## 6.3  产品功能

**云端运行**  
用户提交代码后，其应用程序运行在云主机中，数据存储在各种云端数据服务中，省去了常规的部署与运维操作。

**负载均衡**  
云引擎自动调整执行应用的虚拟机数目。HTTP请求在各个运行实例间轮转服务，实现动态的负载均衡。

**开发语言**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。基于云数据库技术，内置多副本存储，保证高可靠。

**数据库服务**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。

**文件系统服务**  
提供一致共享、多副本持久的文件系统服务，供需要文件存储的应用使用。

**分布式缓存服务**  
提供兼容Memcached协议并且动态可扩展的分布式缓存系统服务。

**统计与监控**  
在网页控制台上以图表形式来来展现应用的访问统计及资源占用信息。

## 6.4  数据中心

目前云引擎部署在盛大云的华北节点。华北节点是BGP线路，包括电信、联通、移动、教育网、铁通。

## 6.5  收费概览

云引擎Beta版本目前对用户全部免费。计费标准后续推出。基本的策略是针对Web应用的访问量以及占用系统资源综合考虑进行计费。



# 7   Amazon AWS

<http://aws.amazon.com/cn/free/>

## 7.1  亚马逊云服务平台

亚马逊是全球最大的在线图书零售商，在发展主营业务即 在线图书零售的过程中，亚马逊为支撑业务的发展，在全美 部署 IT
基础设施，其中包括存储服务器、带宽、CPU 资源。为充分支持业务的发展，IT基础设施需要有一定富裕。2002
年，亚马逊意识到闲置资源的浪费，开始把这部分富裕 的存储服务器、带宽、CPU 资源租给第三方用户。亚马逊将该云服务命名为亚马逊网络服务（Amazon
WebServices，简称 AWS）。2006年初，亚马逊成立了网络服务部门，专为各类企业
提供云计算基础架构网络服务平台，用户（包括软件开发者与企业）可以通过亚马逊网络服务获得存储、带宽、CPU资源，同时还能获得其他IT服务，如亚马逊私有云（VPC）等。
_(_ _以上介绍摘自互联网_ _)_

对于个人用户来说，使用Amazon
AWS就意味着拥有独立的主机，存储空间，带宽，ip，数据库服务器，CDN等等，说白了就是有了实现各种互联网服务的十八般兵器。小到搭建自己的SVN/VNP服务器，网络硬盘，中到搭建个人网站/博客，大到构建大型网站，实施集群计算，AWS都能轻松应对。

AWS的第二个优点就是便宜，虽然消费的是美元，但是经过仔细对比你就会发现，你只需要话费一半甚至更少的钱就能够享受到世界上最好的云计算服务。好比在国外只需要花几千美元就能开宝马一样。我会在后续的文章中详细介绍AWS的价格体系。而且一个非常好的消息就是，AWS对新用户有一个为期一年的免费使用计划(Free
Tier)，在你注册后的一年内，你可以使用AWS所有子业务的免费套餐。如果你希望在一年后继续免费使用的话，换一张信用卡注册就行了。

在我看来，AWS的好处数不胜数，缺点只有一个，那就是在中国没有数据中心，离大陆最近的数据中心是日本。这意味着第一你的用户访问会有一定延迟(100ms以内)，我的网站和博客就是放在日本数据中心，如果你觉得打开网页的速度可以接受，那就不是问题；第二就是你通过AWS建立的网站目前不可能获得工信部备案，对个人用户来说影响不大。

## 7.2  AWS Free Usage Tier (Per Month):

#### 7.2.1.1     Elastic Compute Cloud (EC2)

  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Linux`†` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Microsoft Windows Server`‡` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of an [Elastic Load Balancer](http://aws.amazon.com/elasticloadbalancing/) plus 15 GB data processing*
  * 30 GB of [Amazon Elastic Block Storage](http://aws.amazon.com/ebs "EBS"), plus 2 million I/Os and 1 GB of snapshot storage`*`
  * 5 GB of [Amazon S3](http://aws.amazon.com/s3) standard storage, 20,000 Get Requests, and 2,000 Put Requests`*`
  * 100 MB of storage, 5 units of write capacity, and 10 units of read capacity for [Amazon DynamoDB](http://aws.amazon.com/dynamodb/).**
  * 750 hours of [Amazon RDS](http://aws.amazon.com/rds) Single-AZ Micro DB Instances, for running MySQL, Oracle BYOL or SQL Server (running SQL Server Express Edition) - enough hours to run a DB Instance continuously each month`*`
  * 20 GB of database storage
  * 10 million I/Os
  * 20 GB of backup storage for your automated database backups and any user-initiated DB Snapshots
  * 1,000 [Amazon SWF](http://aws.amazon.com/swf) workflow executions can be initiated for free. A total of 10,000 activity tasks, signals, timers and markers, and 30,000 workflow-days can also be used for free`**`
  * 1,000,000 Requests of [Amazon Simple Queue Service](http://aws.amazon.com/sqs "SQS")`**`
  * 1,000,000 Requests, 100,000 HTTP notifications and 1,000 email notifications for [Amazon Simple Notification Service](http://aws.amazon.com/sns "SNS")`**`
  * 20 minutes of SD transcoding  **or**  10 minutes of HD transcoding`**`
  * 10 [Amazon Cloudwatch](http://aws.amazon.com/cloudwatch) metrics, 10 alarms, and 1,000,000 API requests`**`
  * 15 GB of bandwidth out aggregated across all AWS services`*`
  * 3 low frequency preconditions running on AWS per month*
  * 5 low frequency activities running on AWS per month*
  * 750 hours of [Amazon ElastiCache](http://aws.amazon.com/elasticache) \- enough hours to run a Cache Node continuously each month.`*`

#### 7.2.1.2     Simple Storage Service (S3)

#### 7.2.1.3     DynamoDB

#### 7.2.1.4     Relational Database Service (RDS)

#### 7.2.1.5     Simple Workflow (SWF)

#### 7.2.1.6     Simple Queue Service (SQS) and Simple Notification Service
(SNS)

#### 7.2.1.7     Amazon Elastic Transcoder

#### 7.2.1.8     CloudWatch

#### 7.2.1.9     Data Transfer

#### 7.2.1.10  Data Pipeline

#### 7.2.1.11  ElastiCache



# 8   BAE、SAE 与 GAE 对比

<http://88250.b3log.org/bae-sae-gae>

从数据库、应用配置、计费、域名绑定、平台服务对比了 BAE、SAE 以及 GAE 的优劣，最后给出云平台选型的建议。

## 8.1  数据库

SAE 不支持 InnoDB（可申请支持），BAE 默认支持。

BAE 不支持数据库连接池（c3p0、BoneCP 已测不支持），数据库连接不能长时间保持。

GAE 使用 Datasotre 存取数据，最近也提供了云 SQL（MySQL），但申请比较困难，配额/性能笔者未测试过。

另外，SAE 显式给出了主从库的访问方式，应用可以比较灵活地设计存取策略，例如读写分离。并且 SAE 是每个应用都拥有自己的数据库，而 BAE
是所有应用共用一个库。

## 8.2  应用配置

BAE 的 duapp-web.xml 基本是抄袭 GAE 的 appengine-web.xml，元素基本一致。

比较奇葩的是 BAE 静态资源配置默认所有后缀为静态文件类型（例如 .html）的请求路径都默认假设为静态资源，需要在 duapp-web.xml
中指定排除。

## 8.3  计费与配额

SAE 按应用天计费"豆豆"，服务也按流量计费、CPU 时间、调用次数计费。注册或活动送配额，否则需要购买。

BAE 目前还没有详细的计费，只限定了应用数。公测结束后应该会细化计费模型。

GAE 目前的计费模型主要是按 API 调用计数，流量分为 In/Out 配额。每天会定时刷新免费配额。

综上，GAE 的计费一目了然，主要就是 API 调用次数；SAE 的计费比较复杂，不同服务有不同的计费策略；BAE 还没有明确的计费模型。

## 8.4  域名绑定

GAE 开通企业套件后随便绑，企业套件有免费版。

SAE 需要确认通过域名备案才能绑定，并且绑定后的流量计费翻倍。

SAE 目前可以随便绑，但没备案的话绑定域名的请求走海外中转，流量计费翻倍（原二级域名请求计费不变）。

BAE 目前可以随便绑，但没备案的后果自负。

## 8.5  平台服务

SAE 提供了 SDK 包，包含了开发需要的本地服务实现。

BAE 则分别提供了服务 Jar，调用方式按不同服务而异。

GAE 提供了完整的 SDK 包，包含了开发需要的本地运行环境和配置客户端。

综上，GAE 提供了完整的平台化服务，覆盖了从开发到上线运维的一系列工具；SAE 则提供了部分工具，平台化不完整，增加了开发、运维难度；BAE
则是分别提供不同服务给开发，没有统一的 SDK 与调用方式。

另外，值得一提的是 BAE 虽然服务没有整合到一个 SDK 中，但其分散的服务也比较适合应用自己选择。 其中云消息（消息服务）以及云触发（数据变更通知）是
GAE/SAE 没有提供的服务，某些业务场景应该会非常适用。

## 8.6  结论

SAE 与 BAE 主要还是面向应用部署托管，普通应用修改后易迁移部署到 BAE 或 SAE。

新应用开发可以选择和平台绑死（依赖平台服务）或按照普通应用开发。

使用配置工具来上传、更新应用配置其实是非常好的方式，但目前 SAE/J、BAE/J 都没有提供客户端配置工具，这增加了使用者的维护工作量。

GAE 提供了比较完整的服务平台，覆盖了应用的生命周期，最近也提供了云 MySQL 服务以吸引更多开发者。

需要根据应用类型来考虑平台选型，例如 GAE 基本以 API 计数的配额就不适合做社交应用，'墙'的问题也需要考虑解决方案。

**\---- EOF ----**





# 9   附录

## 9.1  连接到云，第 1 部分: 在应用程序中使用云

_**充分利用混合模型**_

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/>

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html>

**简介**

多年来，在网络图中，我们已经习惯于使用一个云（特别是积雨云）来表示
Internet。云状图像常被用来表示无固定形状的、不清晰但又必须包含在图表中的一些内容。而网络上的线惟一的作用就是穿过云以表示数据通过
Internet。在以安全性为中心的图表上，这条穿过云的线可能还会在旁边多出一个挂锁以表示这个连接是安全的。

**_常用缩略词_**

  * Ajax: Asynchronous JavaScript + XML
  * API: 应用程序编程接口（application programming interface）
  * HTML: 超文本标记语言（Hypertext Markup Language）
  * HTTP: 超文本传输协议（Hypertext Transfer Protocol）
  * JMS: Java™ 消息服务（Java™Message Service）
  * REST: 具象状态传输（Representational State Transfer）
  * XML: 可扩展标记语言（Extensible Markup Language）

现在云已经在网络图中扮演着主要角色。应用程序可以利用云来调用所添加的值，比如存储、队列及宿主应用程序。应用程序本身也可以被托管在云上。现在的线已不再是简单地穿过云，而是连接到云并将云用作应用程序的一部分。这就使云有了更实际的意义。

在这个由三个部分组成的系列文章中，我们将探究云计算的方方面面。云计算的提供商相对较少，每个提供商着眼于不同的方向并提供不同的服务。编程语言各异，从
Python 到 C#、再到 Java 或其他的专有语言。与云的接口也各不相同，虽然轻量的 REST
接口是首选，但现在并不是每个云计算提供商都提供这种接口。

在本系列的第 1
部分，我们将着重研究一个混合示例，一个使用云计算服务和基础设施进行增强了的专用应用程序。通过研究这个混合应用程序，了解云计算的功用。为此，您需要探究它的渊源、云计算的主要提供商目前所能提供的功能。本系列的第
2 部分将会涵盖在第 1 部分中设计的这个混合应用程序的开发。第 3 部分将着重介绍此解决方案在安全性和管理方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云计算究竟是什么？**

IBM 将云计算定义为一个新兴的计算范型，在这个范型中，数据和服务位于可大规模伸缩的数据中心中，并可被 Internet
上的任何连接设备随时访问。它为应用程序提供了可观的伸缩能力（在使用 Amazon Elastic Computing Cloud 的情况下 -- 通常被称为
Amazon EC2），并能托管应用程序自身。

云计算并不适合所有的情形，但是对于一个在不同时期需要不同计算能力的组织来说，云是很有吸引力的。如果一个组织对处理和存储能力的要求是不均衡的，比如每周六的午夜进行批处理，那么此时与其采用一个大多数时间都空闲的数据中心，到不如使用云更有意义。

云计算也特别适合于那些刚刚起步的公司。这些公司的创业者对投资资本家提出的问题恐怕都不会陌生，即
"您的技术如何伸缩？"云计算是对此问题的一个很好的答案。然而，正如您在本系列后面的部分看到的，云计算也带来了所有权、安全与成本方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云的形成**

**_IBM_** ** _和 Amazon Web Services_**

IBM 与 AWS 合作提供了在虚拟的计算环境中对 IBM 中间件的访问。Amazon EC2
的体验让您能够在无需在系统中安装软件的情况下评估并使用软件。您可以即时调整容量，在一个可靠、高效的环境中构建完备的企业应用程序，而您只需要花费一些时间并购买存储容量。我们的
EC2 上的中间件包括：

  * [DB2 Express-C 9.5](http://www.ibm.com/developerworks/cn/downloads/im/udbexp/)
  * [Informix Dynamic Server Developer Edition 11.5](http://www.ibm.com/developerworks/cn/db2/downloads/idsde/)
  * [WebSphere® Portal Server 和 Lotus Web Content Management 标准版](http://www.ibm.com/developerworks/downloads/ls/wps-wcmse/ec2.html#productionami)
  * [WebSphere sMash](http://www.projectzero.org/download/)

这是产品级的代码，启用了所有特性和选项。在[developerWorks Amazon EC2
云计算页面](http://www.ibm.com/developerworks/downloads/cloud.html)
可以获得更多信息并可以下载这些产品的 Amazon Machine Images。

更多云计算的参考资料，请见 developerWorks 上的
[云计算页面](http://www.ibm.com/developerworks/spaces/cloud/)。

在云计算得到广泛应用之前，我们使用的是网格计算与效用计算。网格计算与云计算的主要区别就是网格计算环境多是由不同的机器组成的，而云计算环境则更加可控制，后端机器通常都是相同的。效用计算是指按数据流量或应用程序的使用支付费用的一种业务模型。服务的
"弹性" 增长的概念也没有现在这么盛行，而随着使用的改变而相应增加（或减少）容量的能力却是云计算的一个重要部分。

从 2000 年初到 2000 年中，Google 和 Amazon
各自独立开发了自己的云计算架构以便在其上运行各自的业务。开发了这种基础设施后，二者发现他们自已的基础设施本身成为了一个服务，可以按照每次的使用量卖给开发人员。Amazon
更是意识到了其平台中的关键价值，以至于它完全相信有一天 Amazon 将会因其计算平台而再次名扬天下，一如它的在线零售网站一样。Amazon
认识到它可以以服务的形式出售其平台（即 Platform as a Service，缩写为 PaaS -- 与 Software as a Service
即 SaaS 类似）。因此，Amazon 常被视为是云计算商业化方面的领跑者，在计费和使用模型方面尤为突出。

在基于云的计算环境的设计方面堪称专业的成功供应商为数不多，其中包括 Amazon 和 Google。认识到这一点，Google、IBM 和几所大学组建了一个
_research cloud_  来为从事云计算研究的学生提供一个云计算环境以便开发新的云计算技术与应用程序。尽管其规模不能与 Amazon 与
Google
的基础设施相提并论，但此项目还是为学生研究云服务提供了一个很好的环境。来自此项目的研究成果将会有助于对云计算进行更进一步的开发，比如有创建条件的组织可以在其基础上开发
_专用云_ 。

  
  

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**混合模型应运而生**

放弃所有本地应用程序而只使用云，或相反地，只依靠本地应用程序而忽略云，都不是明智之举，现在最流行的办法是将本地应用程序与云相结合使用。即所谓的 _混合模型_
。这就让一个公司在必要的时候使用云计算，而同时又能保持它对其关键应用程序的控制。例如，很多公司已经发现，使用 Amazon 的 Simple Storage
Service (S3) 存储图片、视频或文档等会更经济。混合模型也有助于增量方法。

即使您认为将大部分甚至全部的应用程序都转向云更有意义，但是也不建议您这么做，因为一次性完成这样的转移风险太大。借助混合模型，可以先将容易的东西（比如文件存储）转向云。然后在您适应了这种部署模型后，再将应用程序更重要的部分转向云。这也是我在本系列中所采用的方式。接下来，让我们先看一下这个通过转移部分基础设施实现混合的应用程序。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**设计一个混合应用程序**

这个示例混合应用程序是一个异步的电子邮件通知系统。它可以是一个工作流系统中的一个子系统。当一个新行为被提交并等待批准时，就会向能够做出批准或拒绝决定的主体发送电子邮件。这种系统可以用于一个履行订单的系统中。当订单货物运出时，就会发出一个电子邮件以通知相关的人订单在货运途中。不难想象，在很多种应用程序中都可以使用到这个系统。电子邮件在本质上是异步的，所以能生成电子邮件的异步机制是满足此类用例的一种有效途径。

假设有一个现成的应用程序，在此应用程序的某个位置已经具有了这种系统，可以使用很多种方法实现此类系统，但一个相对优雅的方式是使用一个 JMS。JMS 规范是
J2EE™ 技术栈的一个重要部分。目前，针对此标准已经有很多专有或开源的实现。很容易想像有这样一个系统，它向一个 JMS 队列发送通知，而另外一个系统对这个
JMS 队列进行周期性地读取并为每个消息生成电子邮件提醒。

对于一个混合模型，可以先将这个 JMS
队列转移到云。换句话说，就是用在云中运行的一个服务来替代它。这是一种什么样的服务呢？如何更改应用程序以使其与此服务进行交互呢？这取决于所使用的云平台。接下来，我们来看一下各种平台及怎样使用这些平台来实现或像本例一样重新实现一个
JMS 队列的功能性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Amazon Web Services**

作为一个商业化云计算的先躯，Amazon 提供了一系列开发人员感兴趣的成熟服务。Amazon 最知名的云服务莫过于 EC2 (Elastic
Computing Cloud) 服务。它允许构建可在 Amazon 自已的基础设施上运行的虚拟机实例（被称为 AMI -- Amazon Machine
Images）。也许有人会说，除了使用的不是真实的计算机以及基于流量使用收费而非收取机器的租赁费之外，EC2 更接近于托管提供商的一项服务。

Amazon 的 S3 服务是一个在线存储服务，对于需要扩展存储能力的新起步的那些公司来说尤其具有引吸力。它可用作其他 Amazon 云服务（比如
EC2）的一个附件。这就意味着一个 AMI ，或是一个运行着 PHP 的 Linux™ 计算机，可以使用 Amazon S3
作为它的数据存储。随着数据流量的增长，S3 服??也会弹性扩展。Amazon 的 SimpleDB
是一个基于云的快速而简单的数据库，它可以提供索引、存储及访问。很显然，它比功能完善的关系数据库要简单很多，因为它不需要模式，它可以自动地索引数据，并提供了
API 用于存储及访问。

Amazon 的 SQS (Simple Queue Service) 提供了一个队列服务，类似于 JMS，但有一个 RESTful 接口。您也可以将
SQS 与 Amazon 的其他云服务联合使用，也可以将它作为任何一个可用简单的 HTTP GET 或 POST
连接到它的应用程序的一部分使用。对于这个混合应用程序，它是 JMS 队列的一个很好的替代品。它可以通过它的 RESTful 的 XML
接口访问到，可以方便地与一个现有应用程序集成。SQS 可能是这类混合应用程序的最为直接的选择。

很多软件提供商都与 Amazon 有过合作以帮助其客户充分利用 EC2。例如，IBM 和 Amazon 合作开发了 IBM 的很多最受欢迎的企业软件，比如
EC2 上的 DB2®、Informix® 及 WebSphere®。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Google**

Google 因其快速而准确的搜索而闻名，对于很多用户来说，它都是 Arthur C Clarke 的名言 "任何足够先进的技术都与魔法没有区别"
的最好的体现。由于是技术将魔法变成了现实，因此 Google 是提供云计算平台的最佳之选。在 Google
的平台上运行应用程序的美好前景让开发人员无比兴奋，这完全可以理解。

Google 提供了一个名为 App Engine 的云计算平台，它基于的是 Google 早就建立起来的底层平台。这个平台包括 GFS（Google
File System）和 Bigtable（构建于 GFS 之上的数据库系统）。Google App Engine 内的编程采用的是
Python。程序员用 Python 编写应用程序，然后再在 App Engine 框架上运行。除 Python
外的其他语言在将来也会得到支持。出于开发的需要，可以下载 App Engine 环境的一个本地仿真程序。App Engine 可免费使用并且包括多达 500
MB 的存储及足够的 CPU 带宽来满足每天 5 百万次页面浏览。

Google App Engine 提供了一些有用的基础设施，比如源自 GFS 的数据存储和一个 memcache
实现。然而，它并不提供开箱即用的排队机制。不过，有了这样一个纯 Python 的编程环境，就可以在 App Engine 之上很容易地创建您自已的 JMS
替代。这个数据存储很适合于混合应用程序，并且只需很少的 Python 编程就可以打造出一个面向您的队列的 RESTful 式接口。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Microsoft Azure**

正如您所期望的，Windows® 和 .NET 是 Windows Azure 的主要特点。Microsoft 已经提供了一个开发环境，在这个环境中，用
Visual Studio® 编写的应用程序可以被托管于 Windows Azure 环境并在其上运行。Azure
平台提供了很多服务，比如像用于文件存储与数据访问的面向基础设施的服务，同时也提供了更为专用的服务，比如搜索和联系人管理。它还包括了 NET Service
Bus。这是典型的 Enterprise Service Bus (ESB) 设计模式的 Microsoft 实现。ESB
最简单的用法之一就是消息队列，它完全可以充当 JSM 队列的替代。NET Service Bus 还是开发者友好的。它既支持使用 XML 的轻量的
RESTful 接口，也支持较重量的、包括了 WS-* 标准全部实现的基于 SOAP 的接口。这两个接口均支持现有应用程序和 NET Service Bus
间的简便的互操作性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**SalesForce.com**

SalesForce.com 提供了一个模型，借助这个模型，开发人员可以使用其 Apex 开发语言来访问 SalesForce.com
服务。SalesForce 称 Apex 是 "世界上第一个随需应变的编程语言"。 随需应变主要表现在 Apex 代码托管于 SalesForce 的
Force.com 云服务，并在该上下文运行。在句法方面，Apex 与 Java 或 C# 语言类似。

Apex 代码被用来生成服务于 VisualForce 层的 Web 页面，该层就是实际的用户界面。它也使用了 Model-View-Controller
(MVC) 模型。这非常类似于 .NET 中借助 C# 生成 ASPX 页面。这些 VisualForce 页面可以包含
HTML、Ajax（XMLHttpRequest 对象）及 Adobe Flex。

VisualForce 允许开发人员在 SalesForce.com Web 界面上创建不同的变体。这对于喜欢 SalesForce.com
但又想向其添加功能的公司来说十分有用。与其要求 SalesForce.com 构建这种功能性，不如让 Salesforce.com 的用户通过创建
VisualForce 页面并用 Apex 代码将它们写入 SalesForce.com 后端来实现同样的目的。

Salesforce 还提供了控制器，用来连接页面表示与来自 SalesForce 数据库的底层数据，包括如 Edit 或 Save
这样的标准的例程。Force.com
云实现了巨大的成功。它不仅为开发人员提供了在云上构建应用程序的方法，借助它，还可以通过直接发行模型来向用户收取这些应用程序的使用费用。然而，它是一个非常专门化的云。它并不太适合增量方法。通常需要对
Force.com 云进行构建。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**结束语**

在本文中，我们了解了不同的云服务提供商能为我们带来的各种功能，另外还学习了如何使用这些云服务来代替 JMS
队列以及如何将一个现有的应用程序转变成一个混合的云应用程序。在接下来的两篇文章中，我们将了解绑定本地应用程序与云服务的这个混合模型是如何实现的。我们还将研究能够影响云计算的安全与管理方面的重要问题。



## 9.2  连接到云，第 2 部分: 实现混合云模型

_**将**_ _ **JMS**_ _ **队列数据推向**_ _ **Amazon SQS**_ _ **队列**_



**混合模型**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

在本文中，我将集中介绍如何向一个云提供商 Amazon 创建混合云应用程序。示例应用程序名为 HybridCloud，它将从 JMS
队列中取出数据并将数据传送到寄存在 Amazon 云中的 Amazon SQS 队列。进入 Amazon SQS
队列之后，可以使用有权访问该队列的应用程序拉取数据。

具体情况请看示例。假设一家医疗组织需要通过图片处理应用程序处理 X 射线图。该组织安全地将 X 射线图写入 Amazon SQS
队列，射线图临时存储在该位置。即使 X 射线图的文件非常大，这对于云计算提供商而言也不是什么问题。同时，图片处理应用程序占用队列，在 X
射线图进入后进行读取。图片处理应用程序需要大量处理能力，因此它最好部署在虚拟环境中（ _私有云_
），在这个环境中可以快速添加硬件功能。经过图片处理应用程序的处理之后，X 射线图将返回到另一个队列，可通过医疗应用程序接收。尽管 X
射线图是该示例的主要问题，实际上这适用于任何数据。很明显，X 射线图涉及到较高的隐私和安全问题。本文的第 3 部分将探讨云的安全性和治理。

**_云计算空间_**

您是否希望随时获取最新的云计算消息？是否想得到云计算相关的技术知识？developerWorks
云计算空间就是这样一个云计算信息资源的门户，在这里您可以了解来自 IBM 和业界其他媒体的最新信息，并且得到如何在云环境中使用 IBM 软件的入门知识。

IBM 在 Amazon EC2 云计算环境中提供了 DB2、Informix、Lotus、WebSphere 等方面的 AMI
镜像资源。您只需按使用量支付少量费用，就可以使用到云上的数据、门户、Web 内容管理、情景应用等服务。欢迎您随时访问
[云计算空间](http://www.ibm.com/developerworks/spaces/cn/cloud)，获取更多信息。

该架构的好处包括：

  * 该系统不需要队列写入程序（医疗应用程序）或队列读取程序（图片处理应用程序）同时在线。如果文件只是在两个应用程序之间通过 FTP 传输，系统会在任何一方脱机时崩溃。通过使用 Amazon SQS 队列，系统变得更加灵活。
  * 可以向解决方案的任何一方添加功能，不会影响系统的工作。例如，您可以增加图片处理应用程序端的计算能力，这可以加倍图片处理速度。这种变化对于医疗应用程序是透明的，它会继续将 X 射线图写入 Amazon SQS 队列，不会造成影响。
  * 该混合模型非常适合于考虑使用云计算的架构师。全有或全无解决方案要么将所有内容都放到云计算平台，要么完全避开云计算，更好的选择是选择云计算中有用的功能并战略性地使用该功能。在本地应用程序端，虚拟化（私有云）使得动态添加功能变得更加容易，这对于处理器密集型应用程序（如图片处理）而言是很重要的。在云端，Amazon SQS 服务提供应用程序之间的队列服务，即使它们没有连接网络。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**向** **Amazon SQS** **云服务确认身份**

**_常用缩略词_**

  * FTP：文件传输协议（File Transfer Protocol）
  * API：应用程序编程接口（application programming interface）
  * HTTP：超文本传输协议（Hypertext Transfer Protocol）
  * JMS：Java™ 消息服务（Java™ Message Service）
  * JNDI：Java 命名和目录接口（Java Naming and Directory Interface）
  * REST：具象状态传输（Representational State Transfer）
  * SQS：简单队列服务（Simple Queue Service）
  * URL：统一资源定位符（Uniform Resource Locator）
  * XML：可扩展标记语言（Extensible Markup Language）

您的 HybridCloud Java 应用程序使用 Amazon
SQS（[下载](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#download)
应用程序源代码）。HybridCloud 应用程序与 Amazon SQS 云之间的连接使用经过验证的 Web
服务。执行这种验证出于两个原因：首先，Amazon 要收取 Amazon SQS
的使用费，因此必须跟踪每个人的使用；其次，对每个队列的访问必须受到控制。在我们的 HybridCloud 应用程序中，很明显第三方不适合访问包含私有 X
射线图片的 Amazon SQS 队列。

使用 Amazon SQS 队列的第一步是成为 Amazon Web Services (AWS) 的用户，这需要登录 Amazon.com。登录
Amazon.com 没有什么不同之处 -- 任何在 Amazon.com 站点买过书的用户都已经有了一个 Amazon.com
帐户。但是，Amazon.com 登录还只是第一步。AWS 需要使用 "访问密匙 ID" 以及相关的密钥。

Amazon Web Services 模型中的 Secret Access Key 可以视为在 Amazon.com 和连接到 Amazon Web
服务的开发人员之间的一个共享密匙。相反，Access Key ID 并不私密，因为它用于识别而不是验证。在第 3
部分中，我们将讨论这两个密匙的更多细节，以及其他云计算提供商使用的其他验证模型。

开发人员登录 Amazon Web Services 并获取了他们的 Access Key ID 以及 Secret Access Key
之后，他们就可以订阅特定的服务。在本例中，我们将订阅 Amazon.com SQS 服务。开发人员必须使用 Amazon Web Services
注册信用卡才能使用 SQS 之类的服务。信用卡详情必须存储在 Amazon 中，在有未付帐单时无法进入 -- 它是现收现付模型。如果尝试未注册就访问 SQS
服务，您将看到 "The AWS Access Key Id needs a subscription for the service" 异常。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**设计混合应用程序**

正如开头所述，混合应用程序在本地处理数据并使用 Amazon SQS 云服务。因此，它有一个本地组件和一个云组件。在该应用程序设计中，通过本地从 JMS
队列接收数据（也许是从主机应用程序接收），然后使用 HTTP GET 和 POST 将数据发送到 Amazon SQS 队列。您将使用 Java
作为应用程序的语言。

应用程序有三个主要部分：

  1. 创建 Amazon SQS 队列。
  2. 读取本地数据（从 JMS 队列）并将其放入 Amazon SQS 队列。
  3. 从 Amazon SQS 队列检索响应数据。

在 [使用 Amazon
SQS](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#makeuseSQS)
应用程序代码片段中，注意处理本地 JMS 队列连接和 Amazon SQS 队列连接之间的相似之处。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **Amazon SQS**

在 HybridCloud Java 应用程序中，首先放入 Amazon SQS 类（见清单 1）。

  
**清单** **1.** **导入** **Amazon SQS** **类**

    
    
                                       
    
    
    Import com.amazonaws.queue.*;  
  
---  
  
  
  

HybridCloud 应用程序使用 Amazon SQS 将数据写入队列，然后从队列读回数据。与 Amazon SQS 的连接建立在通过验证的 Web
服务连接之上，客户端使用 Amazon Access Key ID 识别，使用 Amazon Secret Key ID 进行验证。要通过 Java
代码使用 Amazon SQS，首先将 Amazon Access Key ID 和 Amazon Secret Key ID 放入代码中（见清单 2）。

  
**清单** **2.** **设置** **Amazon** **键**

    
    
                                       
    
    
    String accessKeyId = "12345678901234567890";
    
    
    String secretAccessKey = "abcdefghijklmnopqrstuvwxyz";  
  
---  
  
  
  

接下来，实例化 Amazon SQS 的 HTTP Client 实现，传入 Access Key ID 和 Secret Access key
作为变量（见清单 3）。

  
**清单** **3.** **实例化** **Amazon SQS http** **客户端**

    
    
                                       
    
    
    AmazonSQS service = new AmazonSQSClient(accessKeyId, secretAccessKey);  
  
---  
  
  
  

现在，您已经实例化了 Amazon SQS 客户端对象，但是还没有通过 Internet 连接到 Amazon SQS 服务。这是下一步要做的工作，您将在
Amazon SQS 云服务上创建队列。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**创建** **Amazon SQS** **队列**

该应用程序使用队列存储 X 射线图文件。在使用 Amazon SQS 队列之前，必须先创建一个队列。该队列必须有一个名称，在本例中为
"imageQueue"。这是 HybridCloud 应用程序放置 X 射线图文件的地方（见清单 4）。

  
**清单** **4.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueRequest request = new CreateQueueRequest();
    
    
    request.setQueueName("imageQueue");  
  
---  
  
  
  

现在运行名为 `createQueue` 的 Amazon SQS 服务对象方法，该方法创建对 Amazon Web Services 的 HTTP GET
(REST-style) 请求以创建队列（见清单 5）。

  
**清单** **5.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueResponse response = service.createQueue(request);  
  
---  
  
  
  

这将在 Amazon SQS 上创建一个 REST 风格的 Web 服务。当您运行代码创建 Amazon SQS 队列时，检测发送给 Amazon SQS
的 REST 风格的 URL 会很有趣。在此 URL 中，您可以清楚地看到 Access Key ID、签名（使用 Secret Key ID）和实际的
SQS 队列，创建的队列名为 `imageQueue`。当然，实际的 Secret Key ID 是不会发送的。消息的签名组件（见清单 6）提供拥有
Secret Key ID 的证明。只有密钥持有者才能创建签名组件。

  
**清单** **6.** **将** **REST** **风格的** **Web** **服务请求发送到** **Amazon Web** **服务**

    
    
                                       
    
    
    queue.amazonaws.com?Action=CreateQueue&SignatureMethod=HmacSHA256&AWSAccessKeyId
    
    
    =12345678901234567890&QueueName=imageQueue&SignatureVersion=2&Version
    
    
    =2008-01-01&Signature=U859J2Hoi5qBqlQx1R18dKPgSgrgjlOiJIDD8ug9FPI%3D&Timestamp
    
    
    =2009-04-01T03%3A25%3A13.575Z  
  
---  
  
  
  

创建签名不仅要使用 QueueName，还使用时间戳。这确保了对 Amazon SQS 的请求无法被攻击者捕获并回放以模拟有效用户。如果攻击者重新向
Amazon SQS 服务发送请求，则重复的签名表示该请求属于捕获重放攻击，Amazon Web 服务将会阻塞它。

现在，您已经创建了 imageQueue 队列，您可以将图像数据加载到其中。现在可以从本地 JMS
队列中获取该数据。本地队列本身可以来自虚拟环境（本地云）。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**从本地** **JMS** **队列检索数据**

现在已经创建了 Amazon SQS 队列，接下来将注意力转移到该混合应用程序的本地端。在将数据提供给 Amazon SQS
队列之前，您必须从本地队列中读取数据。比较本地队列使用的步骤与连接 Amazon 的 SQS 队列所需的步骤将会很有用。

需要导入 Java 库，首先是所有的 JMS jar，然后是 JNDI jar。这些文件允许 Java 应用程序使用 JMS（见清单 7）。

  
**清单** **7.** **导入** **JMS** **类**

    
    
                                       
    
    
    import javax.jms.ConnectionFactory;
    
    
    import javax.jms.Connection;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.MessageProducer;
    
    
    import javax.jms.MessageConsumer;
    
    
    import javax.jms.Queue;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.Message;
    
    
    import javax.jms.TextMessage;
    
    
    //Required for JNDI.
    
    
    import javax.naming.*;  
  
---  
  
  
  

您使用 JNDI 设置 JMS 连接的上下文。例如，如果从文件系统读取数据，您可以使用清单 8 中的代码。

  
**清单** **8.** **从本地队列读取文件**

    
    
                                       
    
    
    ConnectionFactory myConnFactory;
    
    
    Queue myQueue;
    
    
    Hashtable env;
    
    
    Context ctx = null; 
    
    
    env = new Hashtable();
    
    
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.fscontext.RefFSContextFactory");
    
    
    env.put(Context.PROVIDER_URL, "file:///C:/Images"); 
    
    
    ctx = new InitialContext(env);  
  
---  
  
  
  

现在创建队列和连接工厂（见清单 9）：

  
**清单** **9.** **创建队列和连接工厂**

    
    
                                       
    
    
    String MYCONNECTIONFACTORY = "MyConnectionFactory";
    
    
    String MYQUEUE = "MyQueue";
    
    
    myConnFactory = (javax.jms.ConnectionFactory) ctx.lookup(MYCONNECTIONFACTORY);
    
    
    myQueue = (javax.jms.Queue)ctx.lookup(MYQUEUE);  
  
---  
  
  
  

接下来，创建一个连接，然后创建连接中的会话（见清单 10）。

  
**清单** **10.** **创建一个本地** **JMS** **队列的连接**

    
    
                                       
    
    
    Connection myConn = myConnFactory.createConnection();
    
    
    Session mySess = myConn.createSession(false, Session.AUTO_ACKNOWLEDGE);  
  
---  
  
  
  

要从队列中读取消息（在本例中最终涉及到从文件系统中读取数据，因为我们使用文件系统的 JNDI 标识符），使用清单 11 中的代码。

  
**清单** **11.** **从本地** **JMS** **队列中读取**

    
    
                                       
    
    
    MessageConsumer myMsgConsumer = mySess.createConsumer(myQueue);
    
    
    myConn.start();
    
    
    Message msg = myMsgConsumer.receive();  
  
---  
  
  
  

现在检查从本地检索的消息中的内容（见清单 12）。

  
**清单** **12.** **检查本地检索消息的内容**

    
    
                                       
    
    
    if (msg instanceof TextMessage) {
    
    
                    TextMessage txtMsg = (TextMessage) msg;
    
    
                    String inputText = txtMsg.getText());
    
    
    }  
  
---  
  
  
  

最后，关闭 JMS 队列的连接（见清单 13）。

  
**清单** **13.** **关闭本地** **JMS** **队列的连接**

    
    
                                       
    
    
    mySess.close();
    
    
    myConn.close();  
  
---  
  
  
  

现在，您已经将希望写入 Amazon SQS 队列的数据放到了名为 inputText 的字符串中。这是接下来要写入 Amazon SQS 队列的内容。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**写入到** **Amazon SQS** **队列**

传入到 Amazon SQS 队列的数据以字符串形式发送。尽管数据是图片，但它仍然以字符串形式发送到 Amazon SQS。可以看到，它在
`SendMessageRequest` 对象中设置，以将消息发送到 Amazon SQS 队列（见清单 14）。

  
**清单** **14.** **向** **Amazon SQS** **队列发送消息**

    
    
                                       
    
    
    SendMessageRequest sendRequest = new SendMessageRequest();
    
    
    sendRequest.setMessageBody(inputText);  
  
---  
  
  
  

您必须设置相应的队列名称，这与您之前创建的队列名称相同（见清单 15）。

  
**清单** **15.** **设置** **Amazon SQS** **上的队列名称**

    
    
                                       
    
    
    sendRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在通过使用 Amazon SQS 对象的 `sendMessage` 方法将消息发送到 Amazon SQS 队列（见清单 16）。

  
**清单** **16.** **将我们的数据发送到** **Amazon SQS** **队列**

    
    
                                       
    
    
    SendMessageResponse response = service.sendMessage(sendRequest);  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**读取** **Amazon SQS** **响应**

接下来从 Amazon SQS 队列读取响应。首先创建 `ReceiveMessageRequest` 对象（见清单 17）。

  
**清单** **17.** **创建** ** **` **ReceiveMessageObject**` ** ** **从** **Amazon
SQS** **队列中检索数据**

    
    
                                       
    
    
    receiveRequest = new ReceiveMessageRequest();  
  
---  
  
  
  

接下来，设置队列名称（见清单 18）。

  
**清单** **18.** **设置队列名称**

    
    
                                       
    
    
    receiveRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在使用 `receiveMessage` 方法尝试从 Amazon SQS 队列中检索消息（见清单 19）。

  
**清单** **19.** **从** **Amazon SQS** **队列中检索响应**

    
    
                                       
    
    
    ReceiveMessageResponse response = service.receiveMessage(receiveRequest);  
  
---  
  
  
  

要检测结果，包括从云中检索到的消息 ID 和消息正文（见清单 20），请将其传递到标准输出。

  
**清单** **20.** **检查** **Amazon SQS** **队列中的响应**

    
    
                                       
    
    
    if (response.isSetReceiveMessageResult()) {
    
    
    ReceiveMessageResult  receiveMessageResult = response.getReceiveMessageResult();
    
    
    java.util.List<Message> messageList = receiveMessageResult.getMessage();
    
    
    for (Message message : messageList) {
    
    
    if (message.isSetMessageId()) {
    
    
                            System.out.print("            MessageId");
    
    
                            System.out.print("                " + message.getMessageId());
    
    
                            System.out.println();
    
    
                        }
    
    
                        if (message.isSetBody()) {
    
    
                            System.out.print("            Body");
    
    
                            System.out.println();
    
    
                            System.out.print("                " + message.getBody());
    
    
                            System.out.println();
    
    
                        }
    
    
    }  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **XML** **网关连接本地应用程序和云**

在本文中，使用 Java 代码连接本地应用程序和云计算环境。这是开发人员的理想解决方案，但作为应用程序的一部分，到 Amazon
云计算服务的连接不在网络运营团队的控制之下，网络运营团队监控使用、通信和可用性。此外，任何到云计算连接的更改都涉及到代码更改。尽管这超出了本文的范围，但可以使用网络基础结构在本地
JMS 队列和 Amazon SQS 云服务之间实现相同的连接，从而将连接置于网络运营团队的控制之下。

要将一个本地应用程序组件（比如 JMS 队列）连接到云，需要一个包含云计算连接器的 XML 网关（见参考资料中此类网关的示例）。将 JMS 队列连接到
Amazon SQS 队列的任务涉及到拖放连接筛选器，从而将数据从 JMS 队列中拉出然后传递到 Amazon 云服务。

这与我们熟悉的有线电视机顶盒很类似。电视机顶盒连接本地基础设施（电视机）和云（有线电视操作员）。XML
网关提供本地有线电视机顶盒的功能。除了提供到云服务的连接之外，它还提供对该连接的监控和安全性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**结束语**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

您了解了 Java 应用程序如何将本地 JMS 队列和 Amazon SQS 云连接起来。您的 HybridCloud 应用程序使用本地资源（JMS
队列）和基于云的资源（Amazon SQS）执行示例图片共享任务。使用比较类似的方法连接本地队列和 Amazon SQS 队列，但是在网络级别上，到
Amazon SQS 的连接通过 HTTP GET 和 PUT（包含 URL 中传递的参数）发送。

在第 3
部分，即本系列的最后一部分，您将了解云计算中的治理和安全问题。您将看到各种云提供商使用的验证模型，并将讨论在隐私性、法规遵从性方面出现的问题和针对拒绝服务威胁提供的保护。

  
  

**参考资料**

**学习**

  * developerWorks 上的 [云计算空间](http://www.ibm.com/developerworks/spaces/cloud/)：了解为何云计算如此重要、如何起步以及在何处可以了解到更多的相关信息。
  * IBM 的 [云计算项目](http://www.ibm.com/ibm/cloud/)：随时随地获得对您的应用程序的访问。
  * [Amazon Web Services](http://aws.amazon.com/)：查阅 Amazon Web Services 和云计算的相关内容。了解 IBM 和 Amazon Web Services 如何能够帮助您构建和运行一系列的 IBM 平台技术。
  * [用 Amazon Web Services 进行云计算，第 1 部分：简介](http://www.ibm.com/developerworks/cn/web/ar-cloudaws1/)（Prabhakar Chaganti，developerWorks，2008 年 7 月）：阅读这个有关使用 Amazon Web Services 的逐步指南。
  * [Microsoft Windows Azure](http://www.microsoft.com/azure/windowsazure.mspx)：访问这个针对云服务操作系统的 Web 站点，该系统充当了面向 Azure Services Platform 的开发、服务托管和服务管理环境。
  * [Google App Engine Blog](http://googleappengine.blogspot.com/)：一个了解其发展的优秀资源。
  * [developerWorks Cloud Computing Resource Center](http://www.ibm.com/developerworks/downloads/cloud.html)：用现在可用于 Amazon EC2 平台的 IBM 产品在虚拟环境中开发应用程序。让云计算负责解决容量计算、带宽、安全性和可靠性方面的问题。
  * [将 Google 的云计算功能连接到 Apple 的 iPhone 中](http://www.ibm.com/developerworks/cn/web/wa-aj-iphone/)（Noah Gift 和 Jonathan Saggau，developerWorks，2009 年 1 月）：了解如何在移动设备上访问云。
  * [使用 IBM InfoSphere Information Server 与 Salesforce CRM 进行数据集成](http://www.ibm.com/developerworks/cn/data/library/techarticles/dm-0807deng/)（Jon Deng 和 Jeff J. Li，developerWorks，2008 年 7 月）：探究如何从您的应用程序访问 Salesforce 中的数据。
  * [Navigate the cloud computing labyrinth](http://www.ibm.com/developerworks/library/wa-cloudflavor/)（Brett McLaughlin，developerWorks，2009 年 3 月）：选用这个最佳云计算平台是一个明智之举，它能满足您的特殊应用程序需求。 
  * [IBM XML 认证](https://www.ibm.com/developerworks/cn/offers/lp/x/xmlcert/)：了解如何成为 IBM 认证的 XML 和相关技术开发人员。
  * [XML 技术库](http://www.ibm.com/developerworks/cn/views/xml/libraryview.jsp)：developerWorks XML 专区提供了大量技术文章和技巧、教程、标准以及 IBM 红皮书。
  * [developerWorks Web 开发专区](http://www.ibm.com/developerworks/cn/web/)：访问 developerWorks Web 开发专区获得大量的技术文章和技巧、教程和标准。
  * [developerWorks 技术活动和网络广播](http://www.ibm.com/developerworks/cn/offers/techbriefings/)：随时关注这些领域内的技术进展。
  * [developerWorks podcasts](http://www.ibm.com/developerworks/podcast/)：收听面向软件开发人员的有趣访谈和讨论。

**获得产品和技术**

  * [Aptana Studio](http://www.aptana.com/)：下载并尝试在 Web 开发环境中使用 Aptana Studio。
  * [IBM 产品评估试用软件](http://www.ibm.com/developerworks/cn/downloads/)：下载或 [在 IBM SOA Sandbox 进行在线测试](http://www.ibm.com/developerworks/downloads/soasandbox/) 并尝试使用这些来自 DB2®、Lotus®、Rational®、Tivoli® 和 WebSphere® 的应用程序开发工具和中间件产品。

**讨论**

  * [XML 专区讨论论坛](http://www.ibm.com/developerworks/forums/dw_xforums.jsp)：参与任何与 XML 相关的讨论。
  * [developerWorks blogs](http://www.ibm.com/developerworks/blogs/)：查阅这些 blogs 并加入 [developerWorks 社区](http://www.ibm.com/developerworks/community)。

**关于作者**

Mark O'Neill 是 Vordel 的 CTO，这是一家 XML 网络公司。他还是 "Web Services Security"
一书的作者，另外也参与了 "Hardening Network Security" 一书的写作，两本书均由 McGraw-Hill/Osborne
Media 出版。Mark 负责监督 Vordel 的产品开发路线图，并建议 Global 2000 公司和各国政府战略性地采用 XML、Web 服务和
SOA 技术。他具有 Trinity College Dublin 的数学与心理学的学位，并从牛津大学获得了神经网络编程的硕士学位。Mark
现生活在马萨诸塞州的波士顿。



---
title: 云计算平台简介（App Engine）
date: 2013-03-13 05:16:00
tags: 
categories: 
---


# 1   简介

**App Engine** **： 应用程序引擎，是** **托管网络应用程序的云计算平台。**



## 1.1  什么是云



云计算通常简称为"云"，是一种通过 Internet 按需交付计算资源（从应用到数据中心都属于计算资源）和按使用付费的基础架构。



  * 富有弹性的资源：能快速轻松地扩大或缩小规模，以满足您的需求
  * 按使用付费：计量服务的使用情况，只需为所用的服务付费
  * 自助服务：使用自助服务可访问您需要的所有 IT 资源



## 1.2  云计算部署模型

### **1.2.1** 公共云

公共云由一些公司运营和拥有，这些公司使用这种云为其他组织和个人提供对价格合理的计算资源的快速访问。使用公共云服务，用户无需购买硬件、软件或支持基础架构，这些都是由提供商拥有并管理的。

### **1.2.2** 私有云

私有云由单个公司拥有和运营，该公司控制各个业务线和授权组自定义以及使用各种虚拟化资源和自动服务方式。私有云充分利用了很多云的高效性，同时提供更多的资源控制并明确掌控多租户。



### **1.2.3** 混合云

混合云使用私有云作为基础，同时结合了公共云服务的策略使用。事实是私有云不会独立于公司其他的 IT
资源和公共云而单独存在。大多数使用私有云的公司都将发展为管理跨数据中心的工作负载、私有云和公共云--因此创建了混合云。



## 1.3  云计算服务架构



### **1.3.1** 基础设施即服务(IaaS)：

基础架构即服务以"按使用付费"为基础，为公司提供各种计算资源，包括服务器、网络、存储和数据中心空间。



### **1.3.2** 平台即服务 (PaaS)

平台即服务提供了基于云的环境，其中具有可支持您构建和交付基于
web（云）应用的完整生命周期所需的一切没有购买和管理基础软件、硬件、供应和托管的成本与复杂性。



### **1.3.3** 软件即服务 (SaaS)

基于云的应用--或软件即服务 (SaaS)--在远端"云中的"计算机上运行，这些其他人拥有和运营的云计算机可以通过 Internet 和 web
浏览器连接到用户的计算机。



参考：<http://www-31.ibm.com/ibm/cn/cloud/index.shtml>



## 1.4  常见云平台



**谷歌        GAE**（Google App Engine）

              http://zh.wikipedia.org/wiki/Google_App_Engine

              支持的编程语言：Python、Java、Go（可扩展其它语言）

**新浪        SAE**（Sina App Engine）

              http://sae.sina.com.cn

              开发语言：目前只支持PHP环境，正在组建Python，Java和Nodejs相关的团队

**百度        BAE**（Baidu Cloud Environment）

              http://developer.baidu.com/bae/

              开发语言：Java、 Python， 同时 Node.js 开放内测

**阿里        ACE**（Aliyun Cloud Engine）

              http://www.aliyun.com/product/ace/

              支持PHP,NODE.JS语言编写的应用程序

**盛大        Grand Cloud**

              http://www.grandcloud.cn/product/ae

              支持PHP，Ruby，Java，Python等语言编写的Web应用



亚马逊    Amazon AWS

微软       Microsoft Server Cloud

       http://www.microsoft.com/zh-cn/server-cloud/

IBM cloud computing  

       http://www-935.ibm.com/services/cn/zh/it-services/cloud-services.html

       http://www-31.ibm.com/ibm/cn/cloud

思科       Cisco CloudVerse

       http://www.cisco.com/web/CN/solutions/trends/cloud/index.html

Autotask

       http://www.autotask.cn

# 2   GAE（Google App Engine）

<http://zh.wikipedia.org/wiki/Google_App_Engine>



## 2.1  什么是Google App Engine

**Google App Engine**
是一个开发、托管[网络应用程序](http://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F
"网络应用程序")的平台，使用[Google](http://zh.wikipedia.org/wiki/Google
"Google")管理的数据中心。它在2008年4月发布了第一个[beta](http://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E9%80%B1%E6%9C%9F#Beta
"软件版本周期")版本。

Google App
Engine使用了[云计算](http://zh.wikipedia.org/wiki/%E4%BA%91%E8%AE%A1%E7%AE%97
"云计算")技术。它跨越多个服务器和数据中心来虚拟化应用程序。[[1]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-1)
其他基于云的平台还有[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")和[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Azure%E6%9C%8D%E5%8A%A1%E5%B9%B3%E5%8F%B0
"Azure服务平台")等。

Google App
Engine在用户使用一定的资源时是免费的。支付额外的费用可以获得应用程序所需的更多的存储空间、带宽或是CPU负载。[[2]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-2)

## 2.2  支持的编程语言和框架

当前，Google App
Engine支持的[编程语言](http://zh.wikipedia.org/wiki/%E7%BC%96%E7%A8%8B%E8%AF%AD%E8%A8%80
"编程语言")是[Python](http://zh.wikipedia.org/wiki/Python
"Python")、[Java](http://zh.wikipedia.org/wiki/Java
"Java")和[Go](http://zh.wikipedia.org/wiki/Go
"Go")（通过扩展，可以支持其他[JVM语言](http://zh.wikipedia.org/w/index.php?title=JVM%E8%AF%AD%E8%A8%80&action=edit&redlink=1
"JVM语言（页面不存在）")，诸如[Groovy](http://zh.wikipedia.org/wiki/Groovy
"Groovy")、[JRuby](http://zh.wikipedia.org/wiki/JRuby
"JRuby")、[Scala](http://zh.wikipedia.org/wiki/Scala
"Scala")和[Clojure](http://zh.wikipedia.org/wiki/Clojure
"Clojure")）。支持[Django](http://zh.wikipedia.org/wiki/Django
"Django")、[WebOb](http://zh.wikipedia.org/w/index.php?title=WebOb&action=edit&redlink=1
"WebOb（页面不存在）")、[PyYAML](http://zh.wikipedia.org/wiki/PyYAML
"PyYAML")的有限版本。Google说它准备在未来支持更多的语言，Google App
Engine也将会独立于某种语言。任何支持[WSGI](http://zh.wikipedia.org/wiki/WSGI
"WSGI")的使用CGI的Python框架可以使用。框架可以与开发出的应用程序一同上传，也可以上传使用Python编写的第三方库。[[3]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-3)[[4]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-4)

## 2.3  与其他应用程序托管的区别

与其他可扩展的托管服务（例如[Amazon EC2](http://zh.wikipedia.org/wiki/Amazon_EC2 "Amazon
EC2")）比较，App Engine提供了更多基础服务来方便编写可扩展的应用程序，但仅限于App Engine设计框架以内的应用程序。

App
Engine的基础服务省却了许多系统管理的操作，以便将规模扩大到数以百万计的访问。Google负责处理一组代码，可以监测、容错，在必要的时候还会开发一些应用实例。

有些应用程序托管服务让用户安装、配置几乎所有[*NIX](http://zh.wikipedia.org/wiki/*NIX
"*NIX")兼容的软件，而App Engine则要求开发者使用[Python](http://zh.wikipedia.org/wiki/Python
"Python")或[Java](http://zh.wikipedia.org/wiki/Java
"Java")语言来编程，而且只能使用一套限定的[API](http://zh.wikipedia.org/wiki/API
"API")。当前的API允许程序于一个[BigTable](http://zh.wikipedia.org/wiki/BigTable
"BigTable")非关系数据库上存储和检索数据、提出HTTP请求、发送E-
mail、处理图像、还有[缓存](http://zh.wikipedia.org/wiki/%E7%BC%93%E5%AD%98
"缓存")。大多数现存的Web应用程序，若未经修改，均不能直接在App
Engine上运行，因为它们需要使用[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")。

带宽和CPU的使用、送达请求的数量、并发请求的数量、以及调用各种API的次数，皆设有每天和每分钟的限额。个别的请求，如果需时超过30秒或返回超过10MB的数据，都会被终止。

## 2.4  SQL与GQL的区别

Google App
Engine的Datastore使用一个与SQL类似的语言，叫做"GQL"。在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句仅可以用于一个表。因为要跨越不只一台机器，
GQL不支持效率很低的[JOIN](http://zh.wikipedia.org/w/index.php?title=JOIN&action=edit&redlink=1
"JOIN（页面不存在）")语句[[5]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-5)。欲创建一对多和多对多的关系，可使用ReferenceProperty()[[6]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-6)。采用这种无共享的方式，即使磁盘坏了，系统也不致瘫痪[[7]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-7)。

在GQL中，[SELECT](http://zh.wikipedia.org/wiki/SELECT
"SELECT")语句中的[WHERE](http://zh.wikipedia.org/w/index.php?title=WHERE&action=edit&redlink=1
"WHERE（页面不存在）")从句只容许对仅仅一列进行>、>=、<或<=比较。所以，仅仅可以构造简单的WHERE从句。在数据建模时，要从[关系数据库](http://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
"关系数据库")转换到Datastore，开发者需要转变观念。

App
Engine限制每次Datastore请求最多返回1000行数据。大多数Web应用程序，都不会受此影响，因为它们通常并不会在一张页面上列出超过1000条记录（可以用分页和缓存机制），只要按顺序返回结果就可以了。若有应用程序需要在一次操作中返回更多的记录，则需自行使用客户端软件或者[Ajax](http://zh.wikipedia.org/wiki/Ajax
"Ajax")页面，按查询顺序提取更多条记录。

这个Datastore的API是不关联的，有别于一般关系数据库----比如[IBM
DB2](http://zh.wikipedia.org/wiki/IBM_DB2 "IBM DB2")、[Microsoft SQL
Server](http://zh.wikipedia.org/wiki/Microsoft_SQL_Server "Microsoft SQL
Server")、[MySQL](http://zh.wikipedia.org/wiki/MySQL
"MySQL")、[Oracle数据库](http://zh.wikipedia.org/wiki/Oracle%E6%95%B0%E6%8D%AE%E5%BA%93
"Oracle数据库")、或者[PostgreSQL](http://zh.wikipedia.org/wiki/PostgreSQL
"PostgreSQL")。

## 2.5  限制

  * 在App Engine的文件系统中，开发者只有读取的权限。
  * App Engine仅可在回应HTTP请求时执行代码（计划的后台任务、任务队列和XMPP服务则不在此限）。
  * 用户可以上传任意的Python模块，但必须是纯Python模块，不得包含[C](http://zh.wikipedia.org/wiki/C%E8%AF%AD%E8%A8%80 "C语言")扩展程序或其他需要编译的代码。
  * App Engine限制每次Datastore请求最多返回1000行数据。
  * Java应用程序只能使用JRE基本版本类库中的一个子集（[JRE类白名单](http://code.google.com/appengine/docs/java/jrewhitelist.html)）[[8]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-8)。
  * Java应用程序不能创建新的线程。

## 2.6  可移植性

开发者担心App
Engine应用程序不能移植到其他平台上，因而被困在单一种技术之内。[[9]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-9)

## 2.7  从App Engine下载数据

App
Engine自SDK1.2.2版开始，已容许以批量的方式下载数据[[10]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-10)。此外，用户也可使用开源项目gaebar[[11]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-11)、approcket[[12]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-12)
和gawsh[[13]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-13)
来下载、备份在App Engine上的数据。

## 2.8  限额

免费帐户使用App
Engine时，受配额限制。应用程序作者可以视乎需要，付钱购买更多配额。[[14]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-
Quotas-14)

### **2.8.1** 硬性限制

**项目**

|

**限制**  
  
---|---  
  
每次请求的时间

|

普通请求60秒，任务请求10分钟，后台请求无限  
  
每个应用程序的文件

|

1000个  
  
HTTP响应的大小

|

32 MB  
  
Datastore单项大小

|

1 MB  
  
应用程序代码大小

|

150 MB  
  
### **2.8.2** 免费的配额

供免费使用的配额曾于[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[5月25日](http://zh.wikipedia.org/wiki/5%E6%9C%8825%E6%97%A5
"5月25日")[[15]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-15)
、[2009年](http://zh.wikipedia.org/wiki/2009%E5%B9%B4
"2009年")[6月22日](http://zh.wikipedia.org/wiki/6%E6%9C%8822%E6%97%A5
"6月22日")以及[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")[5月](http://zh.wikipedia.org/wiki/5%E6%9C%88
"5月")三度下调[[16]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-16)。

**项目**

|

**配额**  
  
---|---  
  
每天的Email数量

|

100封  
  
每天的输入数据

|

无限  
  
每天的输出数据

|

1 GB  
  
每天可使用CPU

|

28小时  
  
每天调用Datastore API次数

|

50000次*  
  
数据存储

|

1 GB  
  
每天调用URLFetch API次数

|

657000次*  
  
## 2.9  竞争对手

Google App Engine与[Amazon Web
Services](http://zh.wikipedia.org/wiki/Amazon_Web_Services "Amazon Web
Services")（一个应用程序服务系统，支持在Amazon的服务器上托管文件、执行代码）直接竞争。不少科技分析师早在多年前已预计过，Google会加入这场竞赛。其中，Techdirt的出版人[Mike
Masnick](http://zh.wikipedia.org/w/index.php?title=Mike_Masnick&action=edit&redlink=1
"Mike
Masnick（页面不存在）")写到，"Google终于了解到它需要霸占网络平台这个地位。我们可以期待，开发及落实易于扩展的网络应用程序会变得越来越容易，而应用程序也会越来越具创意。"[[17]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-17)

此外，[微软](http://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF
"微软")的[Azure服务平台](http://zh.wikipedia.org/wiki/Windows_Azure "Windows
Azure")也是Google App Engine的竞争对手。

## 2.10 中国大陆封锁

由于Google App
Engine允许用户托管网络应用程序，且服务器不在[中国大陆](http://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9B%BD%E5%A4%A7%E9%99%86
"中国大陆")境内，故有部分用户利用其搭建代理（如[GoAgent](http://zh.wikipedia.org/wiki/GoAgent
"GoAgent")）用于突破[防火长城](http://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E
"防火长城")的[审查](http://zh.wikipedia.org/wiki/%E7%A0%B4%E7%BD%91
"破网")[[18]](http://zh.wikipedia.org/wiki/Google_App_Engine#cite_note-18)，故Google
App Engine的域名appspot.com的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")加密连接长期遭到防火长城的封锁。

[2010年](http://zh.wikipedia.org/wiki/2010%E5%B9%B4
"2010年")[12月20日](http://zh.wikipedia.org/wiki/12%E6%9C%8820%E6%97%A5
"12月20日")，Google App Engine的域名appspot.com遭到防火长城的关键词过滤封锁。由于先前Google App
Engine的[SSL](http://zh.wikipedia.org/wiki/SSL
"SSL")连接已经被封，故中国大陆境内的用户无法正常连接与使用。此次Google App
Engine被封锁适逢[2010年诺贝尔和平奖](http://zh.wikipedia.org/wiki/2010%E5%B9%B4%E8%AF%BA%E8%B4%9D%E5%B0%94%E5%92%8C%E5%B9%B3%E5%A5%96
"2010年诺贝尔和平奖")颁奖典礼。appspot.com非加密连接于2010年[12月23日](http://zh.wikipedia.org/wiki/12%E6%9C%8823%E6%97%A5
"12月23日")解封。

[2011年](http://zh.wikipedia.org/wiki/2011%E5%B9%B4
"2011年")3月[两会](http://zh.wikipedia.org/wiki/%E4%B8%A4%E4%BC%9A
"两会")召开前夕，appspot.com再次遭到防火长城的关键词过滤封锁及[域名污染](http://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%B1%A1%E6%9F%93
"域名污染")，同时部分服务器的IP地址亦遭到彻底屏蔽，甚至两会结束后至今亦没有解封。

## 2.11 参见

  * [Google产品列表](http://zh.wikipedia.org/wiki/Google%E4%BA%A7%E5%93%81%E5%88%97%E8%A1%A8 "Google产品列表")



# 3   SAE（Sina App Engine）

[http://sae.sina.com.cn](http://sae.sina.com.cn/)



## 3.1  什么是Sina App Engine  



        Sina App Engine（以下简称SAE）是新浪研发中心于2009年8月开始内部开发，并在2009年11月3日正式推出第一个Alpha版本的国内首个公有云计算平台（http://sae.sina.com.cn），  SAE是新浪云计算战略的核心组成部分。     

        SAE作为国内的公有云计算，从开发伊始借鉴吸纳Google、Amazon等国外公司的公有云计算的成功技术经验，并很快推出不同于他们的具有自身特色的云计算平台。SAE选择在国内流行最广的Web开发语言PHP作为首选的支持语言，Web开发者可以在Linux/Mac/Windows上通过SVN或者Web版在线代码编辑器进行开发、部署、调试，团队开发时还可以进行成员协作，不同的角色将对代码、项目拥有不同的权限；SAE提供了一系列分布式计算、存储服务供开发者使用，包括分布式文件存储、分布式数据库集群、分布式缓存、分布式定时服务等，这些服务将大大降低开发者的开发成本。同时又由于SAE整体架构的高可靠性和新浪的品牌保证，大大降低了开发者的运营风险。另外，作为典型的云计算，SAE采用"所付即所用，所付仅所用"的计费理念，通过日志和统计中心精确的计算每个应用的资源消耗（包括CPU、内存、磁盘等）。     

      总之，SAE就是简单高效的分布式Web服务开发、运行平台。 

         目前SAE只支持PHP环境，我们正在组建Python，Java和Nodejs相关的团队

## 3.2  SAE的核心优势

        SAE的基本目标用户有两种，一种是Web开发者，另一种是普通互联网上网人群。

        对于Web开发者，SAE带来的好处有：

         *****  硬件成本更低，无需预先购买设备，承担更大的投入风险     

         *****  开发成本更低，SAE提供许多服务供开发者使用，开发者无需重复开发，包括队列、数据库、缓存、定时、验证码、计数器，几乎覆盖了Web开发的所有领域。另外对于特定开放平台的开发者，比如新浪微博开发者，SAE已经集成了完整的OpenAPI的封装，将开发者的开发成本降到最低。值得一提的是，SAE的开发者目前已经形成了良好的交流氛围，在意见反馈中心、SAE官方群，SAE官方微群可以看到很多热情的开发者在一起共同提高

         *****  运维成本更低，在SAE上的应用无需关心硬件维护、服务监控、数据容灾等操作，SAE会通过其高可靠的架构和方便的监控页面为用户将运维成本降到最低扩展性更强，在SAE上的服务无需关心服务压力猛增时带来的扩容等操作，SAE自动支持服务扩展

         *****  更加安全可靠，SAE自动提供SQL语句性能分析、前端防攻击、代码检查等功能，在SAE上的所有应用均为多机房容灾部署，比传统的部署模式更加安全可靠，并且SAE提供服务的SLA来实现对用户服务质量的承诺

        对于普通上网人群，使用SAE可以：

        使用推荐应用一键安装Web应用，普通用户无需会编码，也可以在瞬间拥有自己的团购、博客、微博、Wiki等。 

## 3.3  SAE整体架构

        SAE从架构上采用分层设计，从上往下分别为反向代理层、路由逻辑层、Web计算服务池。而从Web计算服务层延伸出SAE附属的分布式计算型服务和分布式存储型服务，具体又分成同步计算型服务、异步计算型服务、持久化存储服务、非持久化存储服务。各种服务统一向日志和统计中心汇报，参考下图：





    

        7层反向代理层：HTTP反向代理，在最外层，负责响应用户的HTTP请求，分析请求，并转发到后端的Web服务池上，并提供负载均衡、健康检查等功能。

        服务路由层：逻辑层，负责根据请求的唯一标识，快速的映射（O(1)时间复杂度）到相应的Web服务池，并映射到相应的硬件路径。如果发现映射关系不存在或者错误，则给出相应的错误提示。该层对用户隐藏了很多具体地址信息，使开发者无需关心服务的内部实际分配情况。

        Web服务池：由一些不同特性的Web服务池组成。每个Web服务池实际是由一组Apache(PHP)组成的，这些池按照不同的SLA提供不同级别的服务。每个Web服务进程实际处理用户的HTTP请求，进程运行在HTTP服务沙盒内，同时还内嵌同样运行在SAE沙盒内的PHP解析引擎。用户的代码最终通过接口调用各种服务。

        日志和统计中心：负责对用户所使用的所有服务进行统计和资源计费，并设定的分钟配额，来判定是否有非正常的使用。分钟配额描述了资源消耗的速度，当资源消耗的速度到达一个预警阈值时，SAE通知系统会提前向用户发出一个警告，提醒用户应用在某个服务上的使用可能存在问题，需要介入关注或处理，配额系统是SAE用来保证整个平台稳定的措施之一；日志中心负责将用户所有服务的日志汇总并备份，并提供检索查询服务。

        各种分布式服务：SAE提供几乎可以覆盖Web应用开发所有方面的多种服务，用户可以通过StdLib（可以理解为SAE PHP版的STL）很方便的调用它们。 

## 3.4  SAE的线路特性



                 



    SAE平台出口IP：

     220.181.129.126  
    220.181.129.121  
    220.181.136.229  
    220.181.136.230  
    220.181.129.93  
    220.181.129.102  
    220.181.129.117  
    220.181.129.90





    http接口方需要IP授权可以进行相应的设置。 

## 3.5  SAE的功能

 开发：

         *****    代码检查，帮助检查不良函数并帮助移植

         *****    代码部署

         *****   分布式数据库

         *****    分布式文件存储

         *****    分布式缓存

         *****    各种附属分布式服务，包括图像、定时、任务队列、邮件、计数器等

         *****    对接多个开放平台，如新浪微博开发平台

         *****   代码调优，通过[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)提供

         *****    数据库优化，通过[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)提供

         *****    团队协作，可以邀请好友以不同的权限加入项目

         *****    代码版本管理（计划支持）

运营：

         *****    应用打包，通过我们的应用向导进行推广

         *****   日志，包括访问日志、错误日志等

         *****    资源报表，消耗SAE各项资源的统计

         *****    服务监控，监控各项服务状态

         *****    数据迁移，包括数据库导入、数据库导出等 

## 3.6  SAE提供的服务及两大特性



SAE提供的服务

        SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下：

服务名称

|

类型

|

说明  
  
---|---|---  
  
HTTP+PHP

|

同步计算

|

带SAE沙盒的Apache和Zend为用户提供Web计算服务  
  
[Storage](http://sae.sina.com.cn/?m=devcenter&catId=204)

|

持久化存储

|

提供分布式文件存储  
  
[Memcache](http://sae.sina.com.cn/?m=devcenter&catId=201)

|

非持久化存储

|

提供分布式缓存服务  
  
[RDC](http://sae.sina.com.cn/?m=devcenter&catId=203)

|

持久化存储

|

分布式数据库集群，提供[MySQL](http://sae.sina.com.cn/?m=devcenter&catId=192)服务  
  
[TaskQueue](http://sae.sina.com.cn/?m=devcenter&catId=205)

|

异步计算

|

异步离线轻量级任务队列，HTTP方式调用  
  
[DeferredJob](http://sae.sina.com.cn/?m=devcenter&catId=196)

|

异步计算

|

异步离线重量级任务队列，系统方式调用  
  
[Counter](http://sae.sina.com.cn/?m=devcenter&catId=194)

|

持久化存储

|

计数器服务  
  
RankDB

|

持久化存储

|

分布式排行榜服务  
  
[KVDB](http://sae.sina.com.cn/?m=devcenter&catId=199)

|

持久化存储

|

分布式key/value存储服务  
  
[Cron](http://sae.sina.com.cn/?m=devcenter&catId=195)

|

异步计算

|

分布式定时服务  
  
[FetchURL](http://sae.sina.com.cn/?m=devcenter&catId=197)

|

同步计算

|

分布式抓取服务  
  
[TmpFS](http://sae.sina.com.cn/?m=devcenter&catId=206)

|

非持久化存储

|

提供临时文件存储，文件生命周期在一个会话内，Http请求结束文件自动消失  
  
[AppConfig](http://sae.sina.com.cn/?m=devcenter&catId=193)

|



|

提供应用配置功能，取代Apache htaccess  
  
[Mail](http://sae.sina.com.cn/?m=devcenter&catId=200)

|

异步计算

|

邮件发送服务  
  
[Image](http://sae.sina.com.cn/?m=devcenter&catId=198)

|

同步计算

|

图像处理服务  
  
[XHProf](http://sae.sina.com.cn/?m=devcenter&catId=210)

|

同步计算

|

Facebook提供的强大的PHP调优工具  
  
SVN

|

持久存储

|

用户代码部署的入口点:https://svn.sinaapp.com/yourapp  
  
Online CodeEditor

|

持久存储

|

在线代码编辑器，编辑的代码保存后入自动入SVN并部署到Web服务器  
  
 两大特性：扩展性与可靠性

*****    扩展性

        SAE在服务的可扩展性上基本是动态可扩展性的思路，即资源和ID没有强对应关系，用户以服务使用者的身份使用SAE服务。

*****    可靠性

        在计算可靠性方面，SAE主要是依靠多点部署来完成可靠性，多节点的计算一致性上，SAE有分布式锁服务提供比Paxos更好的容错逻辑。

        在数据可靠性方面，SAE的所有数据都通过冗余存储来达到SLA。SAE通过主动复制和被动复制来实现多点数据冗余。



## 3.7  SAE和虚拟主机的区别

         *****    传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权；而SAE面向的服务，使用者得到的是服务的使用权。 

         *****    传统服务托管不面向开发者，开发者无法在其上享受到开发的乐趣；而SAE的一个重要用户就是web developer，开发者可以在其              上通过在线调试、日志分析、协作共享等功能进行web开发。 

         *****    传统服务托管不提供分布式系统解决方案；而SAE提供的完整的分布式web服务的解决方案，其中不仅仅包括分布式数据库、分布               式文件系统，更包括分布式定时器系统、网页抓取服务、图像处理服务等。

         *****    传统服务托管不解决域名问题，用户往往烦恼于域名申请；而SAE的用户将自动得到在sinaapp下的二级域名，同时SAE还支持域                名cname。 

         *****    传统服务托管无法保证SLA（Service Level Agreement），硬件故障的成本基本由使用者承担；而SAE保证用户的SLA，用户的                   web服务自动享有高冗余的前端服务器、享有自动负载均衡系统、服务自动扩展、服务自动收缩等功能。 

         *****   传统的服务托管采用预付费的方式，费用固定且和实际使用情况无直接关系；而SAE采用预充值方式，"所付即所用，所付仅所用"，             web服务的一切损耗均提供报表查询和账单汇总，让用户一目了然。



SAE公有云计算和传统的虚拟主机的区别如下表。



类项

|

SAE

|

VPS  
  
---|---|---  
  
核心用户

|

Web开发者

|

无核心用户  
  
使用方式

|

服务使用

|

设备租用  
  
目标

|

力争覆盖Web服务所有需求，提供多种服务给开发者使用

|

仅基本需求  
  
SLA（服务承诺）

|

高可靠性及严格的服务承诺

|

依服务商变化，无严格协议  
  
计费方式

|

所付即所用，所付仅所用

|

预付费，无精确计费  
  


## 3.8  为什么我们要做SAE

        Sina App Engine项目始于2009年8月，目标为云计算时代的分布式web服务提供一整套解决方案。我们开发SAE主要是出于对内、对外两方面考虑：

        对内，新浪很早以前就开始了关于私有云的开发和实践，所以为了进一步提高公司资源的利用率，更加提高web开发的效率，降低web运营的成本，决定了我们要开发SAE。

        对外，亚马逊、Google都是国外的成功的提供公有云计算服务的公司，SAE也想借助云计算这样一个趋势，为国内广大用户提供云计算的分布式web服务的开发、运行平台。



## 3.9  SAE的目标和发展  

        云计算虽然是个新名词，但实际在国外已经有4、5年的历史。2006年，亚马逊就推出了以EC2为代表的公有云计算，并且已经实现了大规模盈利；2008年，Google则推出了以Google App Engine为代表的公有云计算。国内的云计算却一直是炒的很厉害，各大互联网公司都在宣传，但真正有技术实力做出来而又对外公开使用的少之又少。

        实际从2004年开始，新浪就开始了私有云方向的研究和实践，以此为基础的动态应用平台目前已经支撑新浪内部的绝大部分业务。从2008年起，新浪又启动了"浪云"的公有云计算计划，相继开发了分布式队列服务、P2P文件系统、分布式计算框架等一系列基础服务。实际SAE就是"浪云"战略的产物。

        SAE从架构设计和代码编写开始，就明确了自身的两个目标：

         *****  做公有云计算平台。公有云不同于私有云，更强调安全性和可靠性，这也对整体的架构设计和技术实现提出了更苛刻的要求

         *****  为分布式Web服务提供一整套的解决方案。SAE争取提供开发者开发Web应用过程中所用到的所有服务。

        经过技术团队一年的开发，SAE目前已经提供了十多种服务，整体上分为计算型和存储型，计算型又包括同步计算和异步计算，而存储型则分为持久化存储和非持久化存储。具体列表如下： 

        SAE在2009年11月3日发布了alpha1版本，2010年2月1日发布了alpha2版本，2010年9月1日发布了beta版本，2011年5月17日正式开放注册。



## 3.10 加入SAE

        SAE重视每一名Web开发者和普通用户，SAE坚信：

        "SAE的未来取决于能否帮助Web开发者实现其价值体现，取决于是否能和Web开发者实现双赢的良性循环，并最终为互联网所有用户提供高质量的有价值的应用和服务。"

        所以SAE欢迎更多的Web开发者参与，并且欢迎一切喜欢热爱SAE的有志之士能够亲身的参与到SAE整体架构和技术研发中来（简历投递请关注我们的官方微博<http://t.sina.com.cn/saet>和博客[http://blog.sae.sina.com.cn](http://blog.sae.sina.com.cn/)），让我们一起搭建SAE的未来！



# 4   BAE（Baidu Cloud Environment）

<http://developer.baidu.com/bae/>



## 4.1  百度云平台

<http://developer.baidu.com/wiki/index.php?title=docs/cplat>

百度云平台是百度开放其基础能力，为开发者提供的基于"云"的服务的统称，包括云环境，云服务，集成开发环境，移动测试以及移动建站工具等，未来还会加大对移动应用开发的支持。

  
图：百度云平台构成图

## 4.2  云环境

百度云环境，即BCE（Baidu Cloud Environment），提供多语言、弹性的服务端运行环境，能帮助开发者快速 **开发并部署**
应用。云环境内置丰富的分布式计算API，并支持全方位的百度"云"服务，更能为您的应用带来强大动力，从"本地"变"分布式"，简单可依赖。

开发语言：Java、 Python， 同时 Node.js 开放内测

## 4.3  云服务

### **4.3.1** 云数据库

百度云数据库，提供基于MySQL的关系数据库服务。（已转移到应用内管理，详情请参考：[PHP](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/php/mysql
"docs/cplat/rt/php/mysql")
[Java](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/java/mysql
"docs/cplat/rt/java/mysql")
[Python](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/python/mysql
"docs/cplat/rt/python/mysql")）

### **4.3.2** 云存储

百度云存储，即BCS（Baidu Cloud Storage），提供File-Like的开放存储服务，开发者可以在任何时间、任何地点存储任何类型的数据。

### **4.3.3** 云消息

百度云消息，即BCM（Baidu Cloud Messaging），提供消息队列，短消息、电子邮件发送等服务。

### **4.3.4** 云推送

百度云推送（简称Channel）服务为开发者提供了向浏览器、手机和PC客户端推送消息的服务。

### **4.3.5** 云触发

百度云触发（简称Trigger）服务为开发者提供了"数据变更->动作"的触发机制，开发者可以通过使用云触发服务来订阅需要关注的资源，当资源数据发生变化时，服务系统就会自动调用开发者的回调接口。

### **4.3.6** 虚拟机

百度云存储，即BVM（Baidu Virtual Machine），提供多种配置的虚拟机服务。（仅对合作开发者开放）

## 4.4  工具

### **4.4.1** SiteApp

百度SiteApp，是国内首家Web应用在线生成服务，可帮您将传统网站快速转化为移动Web应用。

### **4.4.2** 移动测试中心

百度移动测试中心（MTC），提供主流手机终端的真机的遍历测试，UI适配、安装卸载测试、手动测试等功能。

### **4.4.3** 云众测

百度云众测，输出百万级别社区测试能力，提供APP评测、用户体验反馈、问卷调查等功能。



# 5   ACE（Aliyun Cloud Engine）

<http://www.aliyun.com/product/ace/>



## 5.1  什么是Cloud Engine

ACE（Aliyun Cloud
Engine）是一个基于云计算基础架构的网络应用程序托管环境，帮助应用开发者简化网络应用程序的构建和维护，并可根据应用访问量和数据存储的增长进行扩展。ACE支持PHP,NODE.JS语言编写的应用程序；支持在线创建MYSQL远程数据库应用。

Cloud
Engine（云引擎，简称CE），是阿里云历经多年研发，于今年7月推出的一款基于弹性计算平台的web应用运行环境，能够提供应用的线性伸缩、动态扩容以及多种相关服务。

Cloud
Engine借鉴并吸纳Google、Amazon、Rackspace等国外知名公司的公有云计算的成功技术经验，结合阿里云多年的技术研发沉淀，保证了该平台的高效和稳定。目前支持PHP和NodeJS两种开发语言，后续会支持更多的开发语言。围绕这个平台，我们也提供了session、storage、memcache、cron等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。模板功能的提供，可以有效的衔接开发者和站长，让开发者的成果可以更加有效的传播，同时站长也有更加灵活丰富的应用可以运营。

Cloud App是阿里云手机开发平台，Cloud
Engine作为阿里云手机在云端的延伸，为云手机开发者提供NodeJS运行环境和伸缩性的支持，让开发者有效的衔接手机和云端的开发，简化开发流程。



## 5.2  竞争力

Cloud Engine的目标用户有两种，分别是Web开发者和站长。使用Cloud Engine，可以让您：

1、无需硬件的投资，降低投入风险；

2、内置丰富的服务，包括session，memcache，storage，cron，云数据库，应用管理和配置，覆盖了web开发的大部分领域；

3、高效稳定的运行环境，兼容大部分原生的PHP 5.3程序，弹性伸缩，不用再当心访问量过大；

4、 高效安全的云存储服务，不用当心数据会丢失；

5、经验丰富的阿里运维和安全团队，协助解决网络攻击，网站挂马，漏洞扫描，代码行为分析等，并对服务异常进行告警；

6、 开发人员可以将自己的应用做成模板，发布其应用给其他人使用，站长可以从模板库中在线创建应用，即可进行自己的网站运营。

另外，ISV厂商可以在自己的系统中集成OpenAPI，允许管理和发布用户创建的应用。



## 5.3  应用程序环境

Cloud Engine可以保证您在负载很重和数据量极大的情况下，也可以轻松构建能安全运行的应用程序。

1、自动扩容，用户可以根据自身需求，申请存储，缓存等容量。

2、动态的网络服务，提供对常用网络技术的完全支持

3、持久存储空间，存储用户需要的落地的数据

4、 负载平衡，选择当前较空闲的机器，执行任务

5、与本地开发环境兼容，方便开发者移植代码到CE运行环境

6、分布式定时计算，提供定时和定期触发事件的计划任务。

您的应用程序可在以下两个运行时环境之一中运行：NodeJS 环境和 PHP
环境。各环境均为网络应用程序开发提供标准协议和常用技术。您的应用程序使用NodeJS和PHP的标准API来访问大多数CE服务。



## 5.4  功能介绍



开发：

1、Session，分布式session，开发者无需考虑跨多台机器的session处理

2、Storage，基于开放式存储服务，支持多台机器的同时访问

3、 memcache，分布式缓存，有效解决memcache的多机共享，和实例重启引发的缓存清空

4、cron，通过函数调用方式，支持定时和定期执行任务

5、 应用管理和配置，支持应用的创建、启动、停止、更新、查看等操作

6、mysql数据库支持，双机热备，支持在线迁移和备份，单表可支持上亿记录

运营：

1、开发者可利用模板库分发应用

2、站长可以通过模板库在线快速创建应用

3、平台可监控各种服务的状态

4、 对消耗的资源有详细的统计记录

5、方便的数据导入和导出



## 5.5  云引擎、虚拟主机、VPS的区别



传统服务托管面向的是硬件软件设备，使用者得到的也是设备的使用权，没有相关的服务；而Cloud
Engine面向的服务，使用者得到的是稳定可靠的全面服务，同时分布式的平台保证了数据的安全性和访问的快速。

** **

|

**云引擎**

|

**虚拟主机**

|

**VPS**  
  
---|---|---|---  
  
用户群

|

web开发者和站长

|

站长

|

没有限定  
  
使用方式

|

服务租用

|

服务租用

|

虚拟设备租用  
  
运行环境

|

支持多种开发语言

|

支持较少开发语言

|

需要自己安装  
  
目标

|

开发者和站长的整体服务

|

展示性的网站

|

仅提供最基本的设施  
  
安全保证

|

沙箱+专业的安全团队

|

根据服务商来定

|

根据用户能力来定  
  
服务承诺

|

稳定可靠安全的服务承诺

|

根据服务商来定

|

根据服务商来定

  
  


## 5.6  发展目标



互联网给PC带来了时代的变革，我们相信，云计算会给互联网带来更大的变革。以亚马逊EC2为代表的IaaS和以Google代表的PaaS，已经在国外掀起了互联网应用的高潮。反观国内，以阿里云为代表的互联网企业，率先将云计算服务落地，并对外提供公有云服务。

阿里云一直有一个目标，就是做一个互联网的数据分享平台，让广大用户可以在这个平台上协作完成数据的分享。我们一直在朝着这个方向努力，Cloud
Engine的诞生就是为了进一步的实现这个目标，帮助广大的开发者和站长实现数据分享的梦想。

因此我们也向用户承诺，我们只做公有云的计算平台，保证平台上数据的安全性和可靠性，提供一个稳定高效的分布式web
service的解决方案，为用户提供尽可能多的服务。



## 5.7  服务限制

为保证应用的安全性和稳定性，我们对各类服务设定了一些限制，请用户仔细阅读。

1、每个用户最多可以创建3个应用，包含从模板创建的应用

2、 禁止本地文件读写，读写文件可以使用我们的OSS（开放存储服务），OSS存储空间不受容量限制

3、对试图破坏或滥用配额（例如同时在多个帐户上操作应用程序）违反服务条款的用户，可能导致应用程序被禁用或帐户关闭

4、我们对PHP环境进行了一些限制，具体参考：http://ace.aliyun.com/index/help/



## 5.8  产品详情



### **5.8.1** 支持多种WEB运行环境

ACE目前支持PHP运行环境，NodeJS运行环境，后续会支持更多的开发语言。

### **5.8.2** 丰富的附加服务

我们提供了分布式session，分布式memcache，开放存储，消息队列，计划任务等多种服务，让开发者可以更多的关注在业务开发上，降低开发者的开发成本，其整体架构的高可靠性。



### **5.8.3** 弹性伸缩、按需计费

自动弹性伸缩，无需人工干预运维，根据实际使用量计费。



### **5.8.4** 通过应用模板快速部署应用

系统自带常见应用模板。开发人员可以将自己的应用做成模板，发布其应用给其他人使用；站长可以从模板库中在线创建应用，即可进行自己的网站运营。



### **5.8.5** 良好的易用性

兼容原生API， 调试信息输出，可以方便的进行应用管理和配置。



## **5.9   ****价格总览：** ** **

[http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744](http://help.aliyun.com/manual?spm=0.0.0.99.qy448D&helpId=744)



### **5.9.1** **云服务器价格总览**

**类型**

|

**CPU**

|

**内存**

|

**数据盘**

|

**带宽**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**经济** **A** **型**

|

1核Xeon 2.26GHz

|

512MB

|

40GB

|

1Mbps

|

**85** 元

|

**850** 元

|

[马上购买](http://buy.aliyun.com/?cid=452/)  
  
**经济** **B** **型**

|

1核Xeon 2.26GHz

|

1.5GB

|

80GB

|

2Mbps

|

**181** 元

|

**1810** 元

|

[马上购买](http://buy.aliyun.com/?cid=453/)  
  
**标准** **A** **型**

|

2核Xeon 2.26GHz

|

1.5GB

|

130GB

|

5Mbps

|

**376** 元

|

**3760** 元

|

[马上购买](http://buy.aliyun.com/?cid=13/)  
  
**标准** **B** **型**

|

2核Xeon 2.26GHz

|

2.5GB

|

230GB

|

5Mbps

|

**500** 元

|

**5000** 元

|

[马上购买](http://buy.aliyun.com/?cid=14/)  
  
**标准** **C** **型**

|

4核Xeon 2.26GHz

|

4GB

|

480GB

|

5Mbps

|

**810** 元

|

**8100** 元

|

[马上购买](http://buy.aliyun.com/?cid=15/)  
  
**标准** **D** **型**

|

4核Xeon 2.26GHz

|

8GB

|

730GB

|

5Mbps

|

**1205** 元

|

**12050** 元

|

[马上购买](http://buy.aliyun.com/?cid=16/)  
  
**标准** **E** **型**

|

8核Xeon 2.26GHz

|

16GB

|

730GB

|

5Mbps

|

**1916** 元

|

**19160** 元

|

[马上购买](http://buy.aliyun.com/?cid=17/)  
  








### **5.9.2** **关系型数据库** **RDS** **价格总览：**



**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**MySQL**

|

新1型

|

240

|

10

|

60

|

**70** 元

|

**700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=462)  
  
新2型

|

600

|

20

|

150

|

**200** 元

|

**2000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=463)  
  
新3型

|

1200

|

50

|

300

|

**408** 元

|

**4080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=464)  
  
新4型

|

2400

|

100

|

600

|

**808** 元

|

**8080** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=465)  
  
新5型

|

6000

|

200

|

1500

|

**1888** 元

|

**18880** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=466)  
  
新6型

|

12000

|

500

|

2000

|

**3816** 元

|

**38160** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=467)  
  
新7型

|

24000

|

1000

|

2000

|

**7470** 元

|

**74700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=468)  
  


**类型**

|

**型号**

|

**内存** **(M)**

|

**存储** **(G)**

|

**最大连接数** **(** **个** **)**

|

**价格（月）**

|

**价格（年）**

|

** **  
  
---|---|---|---|---|---|---|---  
  
**SQL Server**

|

1型

|

1000

|

50

|

100

|

**530** 元

|

**5300** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=469)  
  
2型

|

2000

|

100

|

200

|

**1040** 元

|

**10400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=470)  
  
3型

|

4000

|

200

|

400

|

**2050** 元

|

**20500** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=471)  
  
4型

|

6000

|

300

|

600

|

**3060** 元

|

**30600** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=472)  
  
5型

|

8000

|

400

|

800

|

**3870** 元

|

**38700** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=473)  
  
6型

|

12000

|

600

|

1200

|

**5200** 元

|

**52000** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=474)  
  
7型

|

24000

|

1000

|

2000

|

**10040** 元

|

**100400** 元

|

[马上购买](http://buy.aliyun.com/?app=rds&cid=475)  
  
用户使用RDS期间产生的公网流量费用为1元/GB。内网流量免费，例如用户在云服务器和RDS之间进行的数据传输是免费的。





### **5.9.3** **开放存储服务** **OSS** **价格总览：**

  * **   OSS** **产品收费方式**
  * 开放存储服务（OSS）采用按需付费，日结算方式。采用先充值，后按实际用量结算方式进行结算。每日结算一次，按实际消费金额对充值款进行扣费。当"账户余额"不足时，服务将会自动停止。  
OSS产品计费项包括：容量、流出流量和请求次数。  
容量计费，按用户数据占用的存储空间量收取费用；  
流出流量计费，按用户存储数据被调用或下载产生的流量收取费用；  
请求次数，按调用API各种请求的次数收取费用；  
每日计费总费用=容量占用费用+流出流量费用+请求次数费用。

[[我要充值]](http://i.aliyun.com/charge)

  *  
  * **   OSS** **价格表  **

存储空间：

**0 GB - 500 GB**

0.02 元/GB * 天 (约 0.6 元/GB * 月)

**› 500 GB - 2 TB**

0.018 元/GB * 天 (约 0.55 元/GB * 月)

**› 2 TB - 10 TB**

0.016 元/GB * 天 (约 0.5 元/GB * 月)

**› 10 TB - 50 TB**

0.015 元/GB * 天 (约 0.45 元/GB * 月)

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

流入流量

**流入流量**

免费

流出流量

**0 GB - 500 GB**

0.75 元/GB

**› 500 GB - 2 TB**

0.7 元/GB

**› 2 TB - 10 TB**

0.65 元/GB

**› 10 TB - 50 TB**

0.6 元/GB

**› 50 TB**

联系我们: 邮箱 bd@aliyun-inc.com

注：内网流量免费：即OSS与阿里云服务器之间的网络流量，通过使用oss-internal.aliyuncs.com的方式可享受内网流量免费。

数据请求

**Get/Head Object**

每 10000 次 0.01 元

**其他所有请求**

每 1000 次 0.01 元

OSS免费体验活动：

即日起新开通OSS用户，可享受50G存储空间，每月累计10G流出流量, 免费体验服务；  
免费体验时间为自服务开通之日起180天内，均可享受免费体验服务；  
免费体验期间，使用量超出免费范围，超出部分按实际报价收费；  
免费体验期间，请求次数正常收费；  
参加活动方法，立即注册、免费开通OSS服务即可。

  *  
  * **   ** **扣费说明**
  * 流出流量最小计量单位为1GB，请求次数最小计量单位为10000次，不足最小计量单位用量当日不予扣费，累加到次日使用量中。
  *  
  * **   ** **欠费说明**
  * 当"阿里云账户"出现负数（即：欠费状态），OSS服务将自动停止。而您所占用的存储空间的这部分资源仍会继续按日扣费， 因此欠费余额会累计。您可以在出现欠费之日起15天内及时充值并补足欠费后，服务会自动开启，可以继续使用。欠费超过15天，将视为您主动放弃OSS存储 服务，存储空间将被回收，存储空间内的数据会被清理，数据不可恢复。
  *  



# 6   Grand Cloud



<http://www.grandcloud.cn/product/ae>



## 6.1  盛大云引擎功能概述

盛大云引擎是基于盛大云计算基础设施服务的Web应用托管平台，旨在降低应用的部署与运维成本，让应用开发者可以专心于业务的开发设计，不再担心后台的构建与运维。云引擎支持PHP，Ruby，Java，Python等语言编写的Web应用，后端提供丰富的数据存储服务，并根据应用访问量和业务规模进行弹性扩展。云引擎目前为Beta版本，各项功能不断上线。

## 6.2  产品特点

**零运维成本**  
只需上传代码，无需手工操作，即可完成代码部署。同时，提供访问统计与运行资源监控，应用状况尽在掌控。

**多语言支持**  
应用管理基于CloudFoundry。用户可以提交PHP、Ruby、Java、Python等语言开发的Web程序。

**弹性扩展**  
按访问量自动增加运行实例，并提供访问负载均衡。

**数据可靠**  
系统使用盛大云的云硬盘与云数据库等服务，确保数据的高可靠性。

**应用仓库**  
用户可以从应用仓库中选择并快速部署应用，简化开发任务。同时，鼓励开发人员提交应用，与所有用户分享。

## 6.3  产品功能

**云端运行**  
用户提交代码后，其应用程序运行在云主机中，数据存储在各种云端数据服务中，省去了常规的部署与运维操作。

**负载均衡**  
云引擎自动调整执行应用的虚拟机数目。HTTP请求在各个运行实例间轮转服务，实现动态的负载均衡。

**开发语言**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。基于云数据库技术，内置多副本存储，保证高可靠。

**数据库服务**  
提供MySQL, PostgreSQL, MongoDB等多种数据库服务。

**文件系统服务**  
提供一致共享、多副本持久的文件系统服务，供需要文件存储的应用使用。

**分布式缓存服务**  
提供兼容Memcached协议并且动态可扩展的分布式缓存系统服务。

**统计与监控**  
在网页控制台上以图表形式来来展现应用的访问统计及资源占用信息。

## 6.4  数据中心

目前云引擎部署在盛大云的华北节点。华北节点是BGP线路，包括电信、联通、移动、教育网、铁通。

## 6.5  收费概览

云引擎Beta版本目前对用户全部免费。计费标准后续推出。基本的策略是针对Web应用的访问量以及占用系统资源综合考虑进行计费。



# 7   Amazon AWS

<http://aws.amazon.com/cn/free/>

## 7.1  亚马逊云服务平台

亚马逊是全球最大的在线图书零售商，在发展主营业务即 在线图书零售的过程中，亚马逊为支撑业务的发展，在全美 部署 IT
基础设施，其中包括存储服务器、带宽、CPU 资源。为充分支持业务的发展，IT基础设施需要有一定富裕。2002
年，亚马逊意识到闲置资源的浪费，开始把这部分富裕 的存储服务器、带宽、CPU 资源租给第三方用户。亚马逊将该云服务命名为亚马逊网络服务（Amazon
WebServices，简称 AWS）。2006年初，亚马逊成立了网络服务部门，专为各类企业
提供云计算基础架构网络服务平台，用户（包括软件开发者与企业）可以通过亚马逊网络服务获得存储、带宽、CPU资源，同时还能获得其他IT服务，如亚马逊私有云（VPC）等。
_(_ _以上介绍摘自互联网_ _)_

对于个人用户来说，使用Amazon
AWS就意味着拥有独立的主机，存储空间，带宽，ip，数据库服务器，CDN等等，说白了就是有了实现各种互联网服务的十八般兵器。小到搭建自己的SVN/VNP服务器，网络硬盘，中到搭建个人网站/博客，大到构建大型网站，实施集群计算，AWS都能轻松应对。

AWS的第二个优点就是便宜，虽然消费的是美元，但是经过仔细对比你就会发现，你只需要话费一半甚至更少的钱就能够享受到世界上最好的云计算服务。好比在国外只需要花几千美元就能开宝马一样。我会在后续的文章中详细介绍AWS的价格体系。而且一个非常好的消息就是，AWS对新用户有一个为期一年的免费使用计划(Free
Tier)，在你注册后的一年内，你可以使用AWS所有子业务的免费套餐。如果你希望在一年后继续免费使用的话，换一张信用卡注册就行了。

在我看来，AWS的好处数不胜数，缺点只有一个，那就是在中国没有数据中心，离大陆最近的数据中心是日本。这意味着第一你的用户访问会有一定延迟(100ms以内)，我的网站和博客就是放在日本数据中心，如果你觉得打开网页的速度可以接受，那就不是问题；第二就是你通过AWS建立的网站目前不可能获得工信部备案，对个人用户来说影响不大。

## 7.2  AWS Free Usage Tier (Per Month):

#### 7.2.1.1     Elastic Compute Cloud (EC2)

  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Linux`†` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of [Amazon EC2](http://aws.amazon.com/ec2) Microsoft Windows Server`‡` Micro Instance usage (613 MB of memory and 32-bit and 64-bit platform support) - enough hours to run continuously each month`*`
  * 750 hours of an [Elastic Load Balancer](http://aws.amazon.com/elasticloadbalancing/) plus 15 GB data processing*
  * 30 GB of [Amazon Elastic Block Storage](http://aws.amazon.com/ebs "EBS"), plus 2 million I/Os and 1 GB of snapshot storage`*`
  * 5 GB of [Amazon S3](http://aws.amazon.com/s3) standard storage, 20,000 Get Requests, and 2,000 Put Requests`*`
  * 100 MB of storage, 5 units of write capacity, and 10 units of read capacity for [Amazon DynamoDB](http://aws.amazon.com/dynamodb/).**
  * 750 hours of [Amazon RDS](http://aws.amazon.com/rds) Single-AZ Micro DB Instances, for running MySQL, Oracle BYOL or SQL Server (running SQL Server Express Edition) - enough hours to run a DB Instance continuously each month`*`
  * 20 GB of database storage
  * 10 million I/Os
  * 20 GB of backup storage for your automated database backups and any user-initiated DB Snapshots
  * 1,000 [Amazon SWF](http://aws.amazon.com/swf) workflow executions can be initiated for free. A total of 10,000 activity tasks, signals, timers and markers, and 30,000 workflow-days can also be used for free`**`
  * 1,000,000 Requests of [Amazon Simple Queue Service](http://aws.amazon.com/sqs "SQS")`**`
  * 1,000,000 Requests, 100,000 HTTP notifications and 1,000 email notifications for [Amazon Simple Notification Service](http://aws.amazon.com/sns "SNS")`**`
  * 20 minutes of SD transcoding  **or**  10 minutes of HD transcoding`**`
  * 10 [Amazon Cloudwatch](http://aws.amazon.com/cloudwatch) metrics, 10 alarms, and 1,000,000 API requests`**`
  * 15 GB of bandwidth out aggregated across all AWS services`*`
  * 3 low frequency preconditions running on AWS per month*
  * 5 low frequency activities running on AWS per month*
  * 750 hours of [Amazon ElastiCache](http://aws.amazon.com/elasticache) \- enough hours to run a Cache Node continuously each month.`*`

#### 7.2.1.2     Simple Storage Service (S3)

#### 7.2.1.3     DynamoDB

#### 7.2.1.4     Relational Database Service (RDS)

#### 7.2.1.5     Simple Workflow (SWF)

#### 7.2.1.6     Simple Queue Service (SQS) and Simple Notification Service
(SNS)

#### 7.2.1.7     Amazon Elastic Transcoder

#### 7.2.1.8     CloudWatch

#### 7.2.1.9     Data Transfer

#### 7.2.1.10  Data Pipeline

#### 7.2.1.11  ElastiCache



# 8   BAE、SAE 与 GAE 对比

<http://88250.b3log.org/bae-sae-gae>

从数据库、应用配置、计费、域名绑定、平台服务对比了 BAE、SAE 以及 GAE 的优劣，最后给出云平台选型的建议。

## 8.1  数据库

SAE 不支持 InnoDB（可申请支持），BAE 默认支持。

BAE 不支持数据库连接池（c3p0、BoneCP 已测不支持），数据库连接不能长时间保持。

GAE 使用 Datasotre 存取数据，最近也提供了云 SQL（MySQL），但申请比较困难，配额/性能笔者未测试过。

另外，SAE 显式给出了主从库的访问方式，应用可以比较灵活地设计存取策略，例如读写分离。并且 SAE 是每个应用都拥有自己的数据库，而 BAE
是所有应用共用一个库。

## 8.2  应用配置

BAE 的 duapp-web.xml 基本是抄袭 GAE 的 appengine-web.xml，元素基本一致。

比较奇葩的是 BAE 静态资源配置默认所有后缀为静态文件类型（例如 .html）的请求路径都默认假设为静态资源，需要在 duapp-web.xml
中指定排除。

## 8.3  计费与配额

SAE 按应用天计费"豆豆"，服务也按流量计费、CPU 时间、调用次数计费。注册或活动送配额，否则需要购买。

BAE 目前还没有详细的计费，只限定了应用数。公测结束后应该会细化计费模型。

GAE 目前的计费模型主要是按 API 调用计数，流量分为 In/Out 配额。每天会定时刷新免费配额。

综上，GAE 的计费一目了然，主要就是 API 调用次数；SAE 的计费比较复杂，不同服务有不同的计费策略；BAE 还没有明确的计费模型。

## 8.4  域名绑定

GAE 开通企业套件后随便绑，企业套件有免费版。

SAE 需要确认通过域名备案才能绑定，并且绑定后的流量计费翻倍。

SAE 目前可以随便绑，但没备案的话绑定域名的请求走海外中转，流量计费翻倍（原二级域名请求计费不变）。

BAE 目前可以随便绑，但没备案的后果自负。

## 8.5  平台服务

SAE 提供了 SDK 包，包含了开发需要的本地服务实现。

BAE 则分别提供了服务 Jar，调用方式按不同服务而异。

GAE 提供了完整的 SDK 包，包含了开发需要的本地运行环境和配置客户端。

综上，GAE 提供了完整的平台化服务，覆盖了从开发到上线运维的一系列工具；SAE 则提供了部分工具，平台化不完整，增加了开发、运维难度；BAE
则是分别提供不同服务给开发，没有统一的 SDK 与调用方式。

另外，值得一提的是 BAE 虽然服务没有整合到一个 SDK 中，但其分散的服务也比较适合应用自己选择。 其中云消息（消息服务）以及云触发（数据变更通知）是
GAE/SAE 没有提供的服务，某些业务场景应该会非常适用。

## 8.6  结论

SAE 与 BAE 主要还是面向应用部署托管，普通应用修改后易迁移部署到 BAE 或 SAE。

新应用开发可以选择和平台绑死（依赖平台服务）或按照普通应用开发。

使用配置工具来上传、更新应用配置其实是非常好的方式，但目前 SAE/J、BAE/J 都没有提供客户端配置工具，这增加了使用者的维护工作量。

GAE 提供了比较完整的服务平台，覆盖了应用的生命周期，最近也提供了云 MySQL 服务以吸引更多开发者。

需要根据应用类型来考虑平台选型，例如 GAE 基本以 API 计数的配额就不适合做社交应用，'墙'的问题也需要考虑解决方案。

**\---- EOF ----**





# 9   附录

## 9.1  连接到云，第 1 部分: 在应用程序中使用云

_**充分利用混合模型**_

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/>

<http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html>

**简介**

多年来，在网络图中，我们已经习惯于使用一个云（特别是积雨云）来表示
Internet。云状图像常被用来表示无固定形状的、不清晰但又必须包含在图表中的一些内容。而网络上的线惟一的作用就是穿过云以表示数据通过
Internet。在以安全性为中心的图表上，这条穿过云的线可能还会在旁边多出一个挂锁以表示这个连接是安全的。

**_常用缩略词_**

  * Ajax: Asynchronous JavaScript + XML
  * API: 应用程序编程接口（application programming interface）
  * HTML: 超文本标记语言（Hypertext Markup Language）
  * HTTP: 超文本传输协议（Hypertext Transfer Protocol）
  * JMS: Java™ 消息服务（Java™Message Service）
  * REST: 具象状态传输（Representational State Transfer）
  * XML: 可扩展标记语言（Extensible Markup Language）

现在云已经在网络图中扮演着主要角色。应用程序可以利用云来调用所添加的值，比如存储、队列及宿主应用程序。应用程序本身也可以被托管在云上。现在的线已不再是简单地穿过云，而是连接到云并将云用作应用程序的一部分。这就使云有了更实际的意义。

在这个由三个部分组成的系列文章中，我们将探究云计算的方方面面。云计算的提供商相对较少，每个提供商着眼于不同的方向并提供不同的服务。编程语言各异，从
Python 到 C#、再到 Java 或其他的专有语言。与云的接口也各不相同，虽然轻量的 REST
接口是首选，但现在并不是每个云计算提供商都提供这种接口。

在本系列的第 1
部分，我们将着重研究一个混合示例，一个使用云计算服务和基础设施进行增强了的专用应用程序。通过研究这个混合应用程序，了解云计算的功用。为此，您需要探究它的渊源、云计算的主要提供商目前所能提供的功能。本系列的第
2 部分将会涵盖在第 1 部分中设计的这个混合应用程序的开发。第 3 部分将着重介绍此解决方案在安全性和管理方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云计算究竟是什么？**

IBM 将云计算定义为一个新兴的计算范型，在这个范型中，数据和服务位于可大规模伸缩的数据中心中，并可被 Internet
上的任何连接设备随时访问。它为应用程序提供了可观的伸缩能力（在使用 Amazon Elastic Computing Cloud 的情况下 -- 通常被称为
Amazon EC2），并能托管应用程序自身。

云计算并不适合所有的情形，但是对于一个在不同时期需要不同计算能力的组织来说，云是很有吸引力的。如果一个组织对处理和存储能力的要求是不均衡的，比如每周六的午夜进行批处理，那么此时与其采用一个大多数时间都空闲的数据中心，到不如使用云更有意义。

云计算也特别适合于那些刚刚起步的公司。这些公司的创业者对投资资本家提出的问题恐怕都不会陌生，即
"您的技术如何伸缩？"云计算是对此问题的一个很好的答案。然而，正如您在本系列后面的部分看到的，云计算也带来了所有权、安全与成本方面的问题。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**云的形成**

**_IBM_** ** _和 Amazon Web Services_**

IBM 与 AWS 合作提供了在虚拟的计算环境中对 IBM 中间件的访问。Amazon EC2
的体验让您能够在无需在系统中安装软件的情况下评估并使用软件。您可以即时调整容量，在一个可靠、高效的环境中构建完备的企业应用程序，而您只需要花费一些时间并购买存储容量。我们的
EC2 上的中间件包括：

  * [DB2 Express-C 9.5](http://www.ibm.com/developerworks/cn/downloads/im/udbexp/)
  * [Informix Dynamic Server Developer Edition 11.5](http://www.ibm.com/developerworks/cn/db2/downloads/idsde/)
  * [WebSphere® Portal Server 和 Lotus Web Content Management 标准版](http://www.ibm.com/developerworks/downloads/ls/wps-wcmse/ec2.html#productionami)
  * [WebSphere sMash](http://www.projectzero.org/download/)

这是产品级的代码，启用了所有特性和选项。在[developerWorks Amazon EC2
云计算页面](http://www.ibm.com/developerworks/downloads/cloud.html)
可以获得更多信息并可以下载这些产品的 Amazon Machine Images。

更多云计算的参考资料，请见 developerWorks 上的
[云计算页面](http://www.ibm.com/developerworks/spaces/cloud/)。

在云计算得到广泛应用之前，我们使用的是网格计算与效用计算。网格计算与云计算的主要区别就是网格计算环境多是由不同的机器组成的，而云计算环境则更加可控制，后端机器通常都是相同的。效用计算是指按数据流量或应用程序的使用支付费用的一种业务模型。服务的
"弹性" 增长的概念也没有现在这么盛行，而随着使用的改变而相应增加（或减少）容量的能力却是云计算的一个重要部分。

从 2000 年初到 2000 年中，Google 和 Amazon
各自独立开发了自己的云计算架构以便在其上运行各自的业务。开发了这种基础设施后，二者发现他们自已的基础设施本身成为了一个服务，可以按照每次的使用量卖给开发人员。Amazon
更是意识到了其平台中的关键价值，以至于它完全相信有一天 Amazon 将会因其计算平台而再次名扬天下，一如它的在线零售网站一样。Amazon
认识到它可以以服务的形式出售其平台（即 Platform as a Service，缩写为 PaaS -- 与 Software as a Service
即 SaaS 类似）。因此，Amazon 常被视为是云计算商业化方面的领跑者，在计费和使用模型方面尤为突出。

在基于云的计算环境的设计方面堪称专业的成功供应商为数不多，其中包括 Amazon 和 Google。认识到这一点，Google、IBM 和几所大学组建了一个
_research cloud_  来为从事云计算研究的学生提供一个云计算环境以便开发新的云计算技术与应用程序。尽管其规模不能与 Amazon 与
Google
的基础设施相提并论，但此项目还是为学生研究云服务提供了一个很好的环境。来自此项目的研究成果将会有助于对云计算进行更进一步的开发，比如有创建条件的组织可以在其基础上开发
_专用云_ 。

  
  

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**混合模型应运而生**

放弃所有本地应用程序而只使用云，或相反地，只依靠本地应用程序而忽略云，都不是明智之举，现在最流行的办法是将本地应用程序与云相结合使用。即所谓的 _混合模型_
。这就让一个公司在必要的时候使用云计算，而同时又能保持它对其关键应用程序的控制。例如，很多公司已经发现，使用 Amazon 的 Simple Storage
Service (S3) 存储图片、视频或文档等会更经济。混合模型也有助于增量方法。

即使您认为将大部分甚至全部的应用程序都转向云更有意义，但是也不建议您这么做，因为一次性完成这样的转移风险太大。借助混合模型，可以先将容易的东西（比如文件存储）转向云。然后在您适应了这种部署模型后，再将应用程序更重要的部分转向云。这也是我在本系列中所采用的方式。接下来，让我们先看一下这个通过转移部分基础设施实现混合的应用程序。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**设计一个混合应用程序**

这个示例混合应用程序是一个异步的电子邮件通知系统。它可以是一个工作流系统中的一个子系统。当一个新行为被提交并等待批准时，就会向能够做出批准或拒绝决定的主体发送电子邮件。这种系统可以用于一个履行订单的系统中。当订单货物运出时，就会发出一个电子邮件以通知相关的人订单在货运途中。不难想象，在很多种应用程序中都可以使用到这个系统。电子邮件在本质上是异步的，所以能生成电子邮件的异步机制是满足此类用例的一种有效途径。

假设有一个现成的应用程序，在此应用程序的某个位置已经具有了这种系统，可以使用很多种方法实现此类系统，但一个相对优雅的方式是使用一个 JMS。JMS 规范是
J2EE™ 技术栈的一个重要部分。目前，针对此标准已经有很多专有或开源的实现。很容易想像有这样一个系统，它向一个 JMS 队列发送通知，而另外一个系统对这个
JMS 队列进行周期性地读取并为每个消息生成电子邮件提醒。

对于一个混合模型，可以先将这个 JMS
队列转移到云。换句话说，就是用在云中运行的一个服务来替代它。这是一种什么样的服务呢？如何更改应用程序以使其与此服务进行交互呢？这取决于所使用的云平台。接下来，我们来看一下各种平台及怎样使用这些平台来实现或像本例一样重新实现一个
JMS 队列的功能性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Amazon Web Services**

作为一个商业化云计算的先躯，Amazon 提供了一系列开发人员感兴趣的成熟服务。Amazon 最知名的云服务莫过于 EC2 (Elastic
Computing Cloud) 服务。它允许构建可在 Amazon 自已的基础设施上运行的虚拟机实例（被称为 AMI -- Amazon Machine
Images）。也许有人会说，除了使用的不是真实的计算机以及基于流量使用收费而非收取机器的租赁费之外，EC2 更接近于托管提供商的一项服务。

Amazon 的 S3 服务是一个在线存储服务，对于需要扩展存储能力的新起步的那些公司来说尤其具有引吸力。它可用作其他 Amazon 云服务（比如
EC2）的一个附件。这就意味着一个 AMI ，或是一个运行着 PHP 的 Linux™ 计算机，可以使用 Amazon S3
作为它的数据存储。随着数据流量的增长，S3 服??也会弹性扩展。Amazon 的 SimpleDB
是一个基于云的快速而简单的数据库，它可以提供索引、存储及访问。很显然，它比功能完善的关系数据库要简单很多，因为它不需要模式，它可以自动地索引数据，并提供了
API 用于存储及访问。

Amazon 的 SQS (Simple Queue Service) 提供了一个队列服务，类似于 JMS，但有一个 RESTful 接口。您也可以将
SQS 与 Amazon 的其他云服务联合使用，也可以将它作为任何一个可用简单的 HTTP GET 或 POST
连接到它的应用程序的一部分使用。对于这个混合应用程序，它是 JMS 队列的一个很好的替代品。它可以通过它的 RESTful 的 XML
接口访问到，可以方便地与一个现有应用程序集成。SQS 可能是这类混合应用程序的最为直接的选择。

很多软件提供商都与 Amazon 有过合作以帮助其客户充分利用 EC2。例如，IBM 和 Amazon 合作开发了 IBM 的很多最受欢迎的企业软件，比如
EC2 上的 DB2®、Informix® 及 WebSphere®。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Google**

Google 因其快速而准确的搜索而闻名，对于很多用户来说，它都是 Arthur C Clarke 的名言 "任何足够先进的技术都与魔法没有区别"
的最好的体现。由于是技术将魔法变成了现实，因此 Google 是提供云计算平台的最佳之选。在 Google
的平台上运行应用程序的美好前景让开发人员无比兴奋，这完全可以理解。

Google 提供了一个名为 App Engine 的云计算平台，它基于的是 Google 早就建立起来的底层平台。这个平台包括 GFS（Google
File System）和 Bigtable（构建于 GFS 之上的数据库系统）。Google App Engine 内的编程采用的是
Python。程序员用 Python 编写应用程序，然后再在 App Engine 框架上运行。除 Python
外的其他语言在将来也会得到支持。出于开发的需要，可以下载 App Engine 环境的一个本地仿真程序。App Engine 可免费使用并且包括多达 500
MB 的存储及足够的 CPU 带宽来满足每天 5 百万次页面浏览。

Google App Engine 提供了一些有用的基础设施，比如源自 GFS 的数据存储和一个 memcache
实现。然而，它并不提供开箱即用的排队机制。不过，有了这样一个纯 Python 的编程环境，就可以在 App Engine 之上很容易地创建您自已的 JMS
替代。这个数据存储很适合于混合应用程序，并且只需很少的 Python 编程就可以打造出一个面向您的队列的 RESTful 式接口。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**Microsoft Azure**

正如您所期望的，Windows® 和 .NET 是 Windows Azure 的主要特点。Microsoft 已经提供了一个开发环境，在这个环境中，用
Visual Studio® 编写的应用程序可以被托管于 Windows Azure 环境并在其上运行。Azure
平台提供了很多服务，比如像用于文件存储与数据访问的面向基础设施的服务，同时也提供了更为专用的服务，比如搜索和联系人管理。它还包括了 NET Service
Bus。这是典型的 Enterprise Service Bus (ESB) 设计模式的 Microsoft 实现。ESB
最简单的用法之一就是消息队列，它完全可以充当 JSM 队列的替代。NET Service Bus 还是开发者友好的。它既支持使用 XML 的轻量的
RESTful 接口，也支持较重量的、包括了 WS-* 标准全部实现的基于 SOAP 的接口。这两个接口均支持现有应用程序和 NET Service Bus
间的简便的互操作性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**SalesForce.com**

SalesForce.com 提供了一个模型，借助这个模型，开发人员可以使用其 Apex 开发语言来访问 SalesForce.com
服务。SalesForce 称 Apex 是 "世界上第一个随需应变的编程语言"。 随需应变主要表现在 Apex 代码托管于 SalesForce 的
Force.com 云服务，并在该上下文运行。在句法方面，Apex 与 Java 或 C# 语言类似。

Apex 代码被用来生成服务于 VisualForce 层的 Web 页面，该层就是实际的用户界面。它也使用了 Model-View-Controller
(MVC) 模型。这非常类似于 .NET 中借助 C# 生成 ASPX 页面。这些 VisualForce 页面可以包含
HTML、Ajax（XMLHttpRequest 对象）及 Adobe Flex。

VisualForce 允许开发人员在 SalesForce.com Web 界面上创建不同的变体。这对于喜欢 SalesForce.com
但又想向其添加功能的公司来说十分有用。与其要求 SalesForce.com 构建这种功能性，不如让 Salesforce.com 的用户通过创建
VisualForce 页面并用 Apex 代码将它们写入 SalesForce.com 后端来实现同样的目的。

Salesforce 还提供了控制器，用来连接页面表示与来自 SalesForce 数据库的底层数据，包括如 Edit 或 Save
这样的标准的例程。Force.com
云实现了巨大的成功。它不仅为开发人员提供了在云上构建应用程序的方法，借助它，还可以通过直接发行模型来向用户收取这些应用程序的使用费用。然而，它是一个非常专门化的云。它并不太适合增量方法。通常需要对
Force.com 云进行构建。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/#ibm-pcon)

**结束语**

在本文中，我们了解了不同的云服务提供商能为我们带来的各种功能，另外还学习了如何使用这些云服务来代替 JMS
队列以及如何将一个现有的应用程序转变成一个混合的云应用程序。在接下来的两篇文章中，我们将了解绑定本地应用程序与云服务的这个混合模型是如何实现的。我们还将研究能够影响云计算的安全与管理方面的重要问题。



## 9.2  连接到云，第 2 部分: 实现混合云模型

_**将**_ _ **JMS**_ _ **队列数据推向**_ _ **Amazon SQS**_ _ **队列**_



**混合模型**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

在本文中，我将集中介绍如何向一个云提供商 Amazon 创建混合云应用程序。示例应用程序名为 HybridCloud，它将从 JMS
队列中取出数据并将数据传送到寄存在 Amazon 云中的 Amazon SQS 队列。进入 Amazon SQS
队列之后，可以使用有权访问该队列的应用程序拉取数据。

具体情况请看示例。假设一家医疗组织需要通过图片处理应用程序处理 X 射线图。该组织安全地将 X 射线图写入 Amazon SQS
队列，射线图临时存储在该位置。即使 X 射线图的文件非常大，这对于云计算提供商而言也不是什么问题。同时，图片处理应用程序占用队列，在 X
射线图进入后进行读取。图片处理应用程序需要大量处理能力，因此它最好部署在虚拟环境中（ _私有云_
），在这个环境中可以快速添加硬件功能。经过图片处理应用程序的处理之后，X 射线图将返回到另一个队列，可通过医疗应用程序接收。尽管 X
射线图是该示例的主要问题，实际上这适用于任何数据。很明显，X 射线图涉及到较高的隐私和安全问题。本文的第 3 部分将探讨云的安全性和治理。

**_云计算空间_**

您是否希望随时获取最新的云计算消息？是否想得到云计算相关的技术知识？developerWorks
云计算空间就是这样一个云计算信息资源的门户，在这里您可以了解来自 IBM 和业界其他媒体的最新信息，并且得到如何在云环境中使用 IBM 软件的入门知识。

IBM 在 Amazon EC2 云计算环境中提供了 DB2、Informix、Lotus、WebSphere 等方面的 AMI
镜像资源。您只需按使用量支付少量费用，就可以使用到云上的数据、门户、Web 内容管理、情景应用等服务。欢迎您随时访问
[云计算空间](http://www.ibm.com/developerworks/spaces/cn/cloud)，获取更多信息。

该架构的好处包括：

  * 该系统不需要队列写入程序（医疗应用程序）或队列读取程序（图片处理应用程序）同时在线。如果文件只是在两个应用程序之间通过 FTP 传输，系统会在任何一方脱机时崩溃。通过使用 Amazon SQS 队列，系统变得更加灵活。
  * 可以向解决方案的任何一方添加功能，不会影响系统的工作。例如，您可以增加图片处理应用程序端的计算能力，这可以加倍图片处理速度。这种变化对于医疗应用程序是透明的，它会继续将 X 射线图写入 Amazon SQS 队列，不会造成影响。
  * 该混合模型非常适合于考虑使用云计算的架构师。全有或全无解决方案要么将所有内容都放到云计算平台，要么完全避开云计算，更好的选择是选择云计算中有用的功能并战略性地使用该功能。在本地应用程序端，虚拟化（私有云）使得动态添加功能变得更加容易，这对于处理器密集型应用程序（如图片处理）而言是很重要的。在云端，Amazon SQS 服务提供应用程序之间的队列服务，即使它们没有连接网络。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**向** **Amazon SQS** **云服务确认身份**

**_常用缩略词_**

  * FTP：文件传输协议（File Transfer Protocol）
  * API：应用程序编程接口（application programming interface）
  * HTTP：超文本传输协议（Hypertext Transfer Protocol）
  * JMS：Java™ 消息服务（Java™ Message Service）
  * JNDI：Java 命名和目录接口（Java Naming and Directory Interface）
  * REST：具象状态传输（Representational State Transfer）
  * SQS：简单队列服务（Simple Queue Service）
  * URL：统一资源定位符（Uniform Resource Locator）
  * XML：可扩展标记语言（Extensible Markup Language）

您的 HybridCloud Java 应用程序使用 Amazon
SQS（[下载](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#download)
应用程序源代码）。HybridCloud 应用程序与 Amazon SQS 云之间的连接使用经过验证的 Web
服务。执行这种验证出于两个原因：首先，Amazon 要收取 Amazon SQS
的使用费，因此必须跟踪每个人的使用；其次，对每个队列的访问必须受到控制。在我们的 HybridCloud 应用程序中，很明显第三方不适合访问包含私有 X
射线图片的 Amazon SQS 队列。

使用 Amazon SQS 队列的第一步是成为 Amazon Web Services (AWS) 的用户，这需要登录 Amazon.com。登录
Amazon.com 没有什么不同之处 -- 任何在 Amazon.com 站点买过书的用户都已经有了一个 Amazon.com
帐户。但是，Amazon.com 登录还只是第一步。AWS 需要使用 "访问密匙 ID" 以及相关的密钥。

Amazon Web Services 模型中的 Secret Access Key 可以视为在 Amazon.com 和连接到 Amazon Web
服务的开发人员之间的一个共享密匙。相反，Access Key ID 并不私密，因为它用于识别而不是验证。在第 3
部分中，我们将讨论这两个密匙的更多细节，以及其他云计算提供商使用的其他验证模型。

开发人员登录 Amazon Web Services 并获取了他们的 Access Key ID 以及 Secret Access Key
之后，他们就可以订阅特定的服务。在本例中，我们将订阅 Amazon.com SQS 服务。开发人员必须使用 Amazon Web Services
注册信用卡才能使用 SQS 之类的服务。信用卡详情必须存储在 Amazon 中，在有未付帐单时无法进入 -- 它是现收现付模型。如果尝试未注册就访问 SQS
服务，您将看到 "The AWS Access Key Id needs a subscription for the service" 异常。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**设计混合应用程序**

正如开头所述，混合应用程序在本地处理数据并使用 Amazon SQS 云服务。因此，它有一个本地组件和一个云组件。在该应用程序设计中，通过本地从 JMS
队列接收数据（也许是从主机应用程序接收），然后使用 HTTP GET 和 POST 将数据发送到 Amazon SQS 队列。您将使用 Java
作为应用程序的语言。

应用程序有三个主要部分：

  1. 创建 Amazon SQS 队列。
  2. 读取本地数据（从 JMS 队列）并将其放入 Amazon SQS 队列。
  3. 从 Amazon SQS 队列检索响应数据。

在 [使用 Amazon
SQS](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#makeuseSQS)
应用程序代码片段中，注意处理本地 JMS 队列连接和 Amazon SQS 队列连接之间的相似之处。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **Amazon SQS**

在 HybridCloud Java 应用程序中，首先放入 Amazon SQS 类（见清单 1）。

  
**清单** **1.** **导入** **Amazon SQS** **类**

    
    
                                       
    
    
    Import com.amazonaws.queue.*;  
  
---  
  
  
  

HybridCloud 应用程序使用 Amazon SQS 将数据写入队列，然后从队列读回数据。与 Amazon SQS 的连接建立在通过验证的 Web
服务连接之上，客户端使用 Amazon Access Key ID 识别，使用 Amazon Secret Key ID 进行验证。要通过 Java
代码使用 Amazon SQS，首先将 Amazon Access Key ID 和 Amazon Secret Key ID 放入代码中（见清单 2）。

  
**清单** **2.** **设置** **Amazon** **键**

    
    
                                       
    
    
    String accessKeyId = "12345678901234567890";
    
    
    String secretAccessKey = "abcdefghijklmnopqrstuvwxyz";  
  
---  
  
  
  

接下来，实例化 Amazon SQS 的 HTTP Client 实现，传入 Access Key ID 和 Secret Access key
作为变量（见清单 3）。

  
**清单** **3.** **实例化** **Amazon SQS http** **客户端**

    
    
                                       
    
    
    AmazonSQS service = new AmazonSQSClient(accessKeyId, secretAccessKey);  
  
---  
  
  
  

现在，您已经实例化了 Amazon SQS 客户端对象，但是还没有通过 Internet 连接到 Amazon SQS 服务。这是下一步要做的工作，您将在
Amazon SQS 云服务上创建队列。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**创建** **Amazon SQS** **队列**

该应用程序使用队列存储 X 射线图文件。在使用 Amazon SQS 队列之前，必须先创建一个队列。该队列必须有一个名称，在本例中为
"imageQueue"。这是 HybridCloud 应用程序放置 X 射线图文件的地方（见清单 4）。

  
**清单** **4.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueRequest request = new CreateQueueRequest();
    
    
    request.setQueueName("imageQueue");  
  
---  
  
  
  

现在运行名为 `createQueue` 的 Amazon SQS 服务对象方法，该方法创建对 Amazon Web Services 的 HTTP GET
(REST-style) 请求以创建队列（见清单 5）。

  
**清单** **5.** **创建** **Amazon** **队列**

    
    
                                       
    
    
    CreateQueueResponse response = service.createQueue(request);  
  
---  
  
  
  

这将在 Amazon SQS 上创建一个 REST 风格的 Web 服务。当您运行代码创建 Amazon SQS 队列时，检测发送给 Amazon SQS
的 REST 风格的 URL 会很有趣。在此 URL 中，您可以清楚地看到 Access Key ID、签名（使用 Secret Key ID）和实际的
SQS 队列，创建的队列名为 `imageQueue`。当然，实际的 Secret Key ID 是不会发送的。消息的签名组件（见清单 6）提供拥有
Secret Key ID 的证明。只有密钥持有者才能创建签名组件。

  
**清单** **6.** **将** **REST** **风格的** **Web** **服务请求发送到** **Amazon Web** **服务**

    
    
                                       
    
    
    queue.amazonaws.com?Action=CreateQueue&SignatureMethod=HmacSHA256&AWSAccessKeyId
    
    
    =12345678901234567890&QueueName=imageQueue&SignatureVersion=2&Version
    
    
    =2008-01-01&Signature=U859J2Hoi5qBqlQx1R18dKPgSgrgjlOiJIDD8ug9FPI%3D&Timestamp
    
    
    =2009-04-01T03%3A25%3A13.575Z  
  
---  
  
  
  

创建签名不仅要使用 QueueName，还使用时间戳。这确保了对 Amazon SQS 的请求无法被攻击者捕获并回放以模拟有效用户。如果攻击者重新向
Amazon SQS 服务发送请求，则重复的签名表示该请求属于捕获重放攻击，Amazon Web 服务将会阻塞它。

现在，您已经创建了 imageQueue 队列，您可以将图像数据加载到其中。现在可以从本地 JMS
队列中获取该数据。本地队列本身可以来自虚拟环境（本地云）。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**从本地** **JMS** **队列检索数据**

现在已经创建了 Amazon SQS 队列，接下来将注意力转移到该混合应用程序的本地端。在将数据提供给 Amazon SQS
队列之前，您必须从本地队列中读取数据。比较本地队列使用的步骤与连接 Amazon 的 SQS 队列所需的步骤将会很有用。

需要导入 Java 库，首先是所有的 JMS jar，然后是 JNDI jar。这些文件允许 Java 应用程序使用 JMS（见清单 7）。

  
**清单** **7.** **导入** **JMS** **类**

    
    
                                       
    
    
    import javax.jms.ConnectionFactory;
    
    
    import javax.jms.Connection;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.MessageProducer;
    
    
    import javax.jms.MessageConsumer;
    
    
    import javax.jms.Queue;
    
    
    import javax.jms.Session;
    
    
    import javax.jms.Message;
    
    
    import javax.jms.TextMessage;
    
    
    //Required for JNDI.
    
    
    import javax.naming.*;  
  
---  
  
  
  

您使用 JNDI 设置 JMS 连接的上下文。例如，如果从文件系统读取数据，您可以使用清单 8 中的代码。

  
**清单** **8.** **从本地队列读取文件**

    
    
                                       
    
    
    ConnectionFactory myConnFactory;
    
    
    Queue myQueue;
    
    
    Hashtable env;
    
    
    Context ctx = null; 
    
    
    env = new Hashtable();
    
    
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.fscontext.RefFSContextFactory");
    
    
    env.put(Context.PROVIDER_URL, "file:///C:/Images"); 
    
    
    ctx = new InitialContext(env);  
  
---  
  
  
  

现在创建队列和连接工厂（见清单 9）：

  
**清单** **9.** **创建队列和连接工厂**

    
    
                                       
    
    
    String MYCONNECTIONFACTORY = "MyConnectionFactory";
    
    
    String MYQUEUE = "MyQueue";
    
    
    myConnFactory = (javax.jms.ConnectionFactory) ctx.lookup(MYCONNECTIONFACTORY);
    
    
    myQueue = (javax.jms.Queue)ctx.lookup(MYQUEUE);  
  
---  
  
  
  

接下来，创建一个连接，然后创建连接中的会话（见清单 10）。

  
**清单** **10.** **创建一个本地** **JMS** **队列的连接**

    
    
                                       
    
    
    Connection myConn = myConnFactory.createConnection();
    
    
    Session mySess = myConn.createSession(false, Session.AUTO_ACKNOWLEDGE);  
  
---  
  
  
  

要从队列中读取消息（在本例中最终涉及到从文件系统中读取数据，因为我们使用文件系统的 JNDI 标识符），使用清单 11 中的代码。

  
**清单** **11.** **从本地** **JMS** **队列中读取**

    
    
                                       
    
    
    MessageConsumer myMsgConsumer = mySess.createConsumer(myQueue);
    
    
    myConn.start();
    
    
    Message msg = myMsgConsumer.receive();  
  
---  
  
  
  

现在检查从本地检索的消息中的内容（见清单 12）。

  
**清单** **12.** **检查本地检索消息的内容**

    
    
                                       
    
    
    if (msg instanceof TextMessage) {
    
    
                    TextMessage txtMsg = (TextMessage) msg;
    
    
                    String inputText = txtMsg.getText());
    
    
    }  
  
---  
  
  
  

最后，关闭 JMS 队列的连接（见清单 13）。

  
**清单** **13.** **关闭本地** **JMS** **队列的连接**

    
    
                                       
    
    
    mySess.close();
    
    
    myConn.close();  
  
---  
  
  
  

现在，您已经将希望写入 Amazon SQS 队列的数据放到了名为 inputText 的字符串中。这是接下来要写入 Amazon SQS 队列的内容。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**写入到** **Amazon SQS** **队列**

传入到 Amazon SQS 队列的数据以字符串形式发送。尽管数据是图片，但它仍然以字符串形式发送到 Amazon SQS。可以看到，它在
`SendMessageRequest` 对象中设置，以将消息发送到 Amazon SQS 队列（见清单 14）。

  
**清单** **14.** **向** **Amazon SQS** **队列发送消息**

    
    
                                       
    
    
    SendMessageRequest sendRequest = new SendMessageRequest();
    
    
    sendRequest.setMessageBody(inputText);  
  
---  
  
  
  

您必须设置相应的队列名称，这与您之前创建的队列名称相同（见清单 15）。

  
**清单** **15.** **设置** **Amazon SQS** **上的队列名称**

    
    
                                       
    
    
    sendRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在通过使用 Amazon SQS 对象的 `sendMessage` 方法将消息发送到 Amazon SQS 队列（见清单 16）。

  
**清单** **16.** **将我们的数据发送到** **Amazon SQS** **队列**

    
    
                                       
    
    
    SendMessageResponse response = service.sendMessage(sendRequest);  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**读取** **Amazon SQS** **响应**

接下来从 Amazon SQS 队列读取响应。首先创建 `ReceiveMessageRequest` 对象（见清单 17）。

  
**清单** **17.** **创建** ** **` **ReceiveMessageObject**` ** ** **从** **Amazon
SQS** **队列中检索数据**

    
    
                                       
    
    
    receiveRequest = new ReceiveMessageRequest();  
  
---  
  
  
  

接下来，设置队列名称（见清单 18）。

  
**清单** **18.** **设置队列名称**

    
    
                                       
    
    
    receiveRequest.setQueueName("imageQueue");  
  
---  
  
  
  

现在使用 `receiveMessage` 方法尝试从 Amazon SQS 队列中检索消息（见清单 19）。

  
**清单** **19.** **从** **Amazon SQS** **队列中检索响应**

    
    
                                       
    
    
    ReceiveMessageResponse response = service.receiveMessage(receiveRequest);  
  
---  
  
  
  

要检测结果，包括从云中检索到的消息 ID 和消息正文（见清单 20），请将其传递到标准输出。

  
**清单** **20.** **检查** **Amazon SQS** **队列中的响应**

    
    
                                       
    
    
    if (response.isSetReceiveMessageResult()) {
    
    
    ReceiveMessageResult  receiveMessageResult = response.getReceiveMessageResult();
    
    
    java.util.List<Message> messageList = receiveMessageResult.getMessage();
    
    
    for (Message message : messageList) {
    
    
    if (message.isSetMessageId()) {
    
    
                            System.out.print("            MessageId");
    
    
                            System.out.print("                " + message.getMessageId());
    
    
                            System.out.println();
    
    
                        }
    
    
                        if (message.isSetBody()) {
    
    
                            System.out.print("            Body");
    
    
                            System.out.println();
    
    
                            System.out.print("                " + message.getBody());
    
    
                            System.out.println();
    
    
                        }
    
    
    }  
  
---  
  


[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**使用** **XML** **网关连接本地应用程序和云**

在本文中，使用 Java 代码连接本地应用程序和云计算环境。这是开发人员的理想解决方案，但作为应用程序的一部分，到 Amazon
云计算服务的连接不在网络运营团队的控制之下，网络运营团队监控使用、通信和可用性。此外，任何到云计算连接的更改都涉及到代码更改。尽管这超出了本文的范围，但可以使用网络基础结构在本地
JMS 队列和 Amazon SQS 云服务之间实现相同的连接，从而将连接置于网络运营团队的控制之下。

要将一个本地应用程序组件（比如 JMS 队列）连接到云，需要一个包含云计算连接器的 XML 网关（见参考资料中此类网关的示例）。将 JMS 队列连接到
Amazon SQS 队列的任务涉及到拖放连接筛选器，从而将数据从 JMS 队列中拉出然后传递到 Amazon 云服务。

这与我们熟悉的有线电视机顶盒很类似。电视机顶盒连接本地基础设施（电视机）和云（有线电视操作员）。XML
网关提供本地有线电视机顶盒的功能。除了提供到云服务的连接之外，它还提供对该连接的监控和安全性。

[** **](http://www.ibm.com/developerworks/cn/xml/x-cloudpt2/index.html#ibm-
pcon)

**结束语**

**_本系列的其他文章_**

  * [连接到云，第 1 部分：在应用程序中使用云](http://www.ibm.com/developerworks/cn/xml/x-cloudpt1/)

您了解了 Java 应用程序如何将本地 JMS 队列和 Amazon SQS 云连接起来。您的 HybridCloud 应用程序使用本地资源（JMS
队列）和基于云的资源（Amazon SQS）执行示例图片共享任务。使用比较类似的方法连接本地队列和 Amazon SQS 队列，但是在网络级别上，到
Amazon SQS 的连接通过 HTTP GET 和 PUT（包含 URL 中传递的参数）发送。

在第 3
部分，即本系列的最后一部分，您将了解云计算中的治理和安全问题。您将看到各种云提供商使用的验证模型，并将讨论在隐私性、法规遵从性方面出现的问题和针对拒绝服务威胁提供的保护。

  
  

**参考资料**

**学习**

  * developerWorks 上的 [云计算空间](http://www.ibm.com/developerworks/spaces/cloud/)：了解为何云计算如此重要、如何起步以及在何处可以了解到更多的相关信息。
  * IBM 的 [云计算项目](http://www.ibm.com/ibm/cloud/)：随时随地获得对您的应用程序的访问。
  * [Amazon Web Services](http://aws.amazon.com/)：查阅 Amazon Web Services 和云计算的相关内容。了解 IBM 和 Amazon Web Services 如何能够帮助您构建和运行一系列的 IBM 平台技术。
  * [用 Amazon Web Services 进行云计算，第 1 部分：简介](http://www.ibm.com/developerworks/cn/web/ar-cloudaws1/)（Prabhakar Chaganti，developerWorks，2008 年 7 月）：阅读这个有关使用 Amazon Web Services 的逐步指南。
  * [Microsoft Windows Azure](http://www.microsoft.com/azure/windowsazure.mspx)：访问这个针对云服务操作系统的 Web 站点，该系统充当了面向 Azure Services Platform 的开发、服务托管和服务管理环境。
  * [Google App Engine Blog](http://googleappengine.blogspot.com/)：一个了解其发展的优秀资源。
  * [developerWorks Cloud Computing Resource Center](http://www.ibm.com/developerworks/downloads/cloud.html)：用现在可用于 Amazon EC2 平台的 IBM 产品在虚拟环境中开发应用程序。让云计算负责解决容量计算、带宽、安全性和可靠性方面的问题。
  * [将 Google 的云计算功能连接到 Apple 的 iPhone 中](http://www.ibm.com/developerworks/cn/web/wa-aj-iphone/)（Noah Gift 和 Jonathan Saggau，developerWorks，2009 年 1 月）：了解如何在移动设备上访问云。
  * [使用 IBM InfoSphere Information Server 与 Salesforce CRM 进行数据集成](http://www.ibm.com/developerworks/cn/data/library/techarticles/dm-0807deng/)（Jon Deng 和 Jeff J. Li，developerWorks，2008 年 7 月）：探究如何从您的应用程序访问 Salesforce 中的数据。
  * [Navigate the cloud computing labyrinth](http://www.ibm.com/developerworks/library/wa-cloudflavor/)（Brett McLaughlin，developerWorks，2009 年 3 月）：选用这个最佳云计算平台是一个明智之举，它能满足您的特殊应用程序需求。 
  * [IBM XML 认证](https://www.ibm.com/developerworks/cn/offers/lp/x/xmlcert/)：了解如何成为 IBM 认证的 XML 和相关技术开发人员。
  * [XML 技术库](http://www.ibm.com/developerworks/cn/views/xml/libraryview.jsp)：developerWorks XML 专区提供了大量技术文章和技巧、教程、标准以及 IBM 红皮书。
  * [developerWorks Web 开发专区](http://www.ibm.com/developerworks/cn/web/)：访问 developerWorks Web 开发专区获得大量的技术文章和技巧、教程和标准。
  * [developerWorks 技术活动和网络广播](http://www.ibm.com/developerworks/cn/offers/techbriefings/)：随时关注这些领域内的技术进展。
  * [developerWorks podcasts](http://www.ibm.com/developerworks/podcast/)：收听面向软件开发人员的有趣访谈和讨论。

**获得产品和技术**

  * [Aptana Studio](http://www.aptana.com/)：下载并尝试在 Web 开发环境中使用 Aptana Studio。
  * [IBM 产品评估试用软件](http://www.ibm.com/developerworks/cn/downloads/)：下载或 [在 IBM SOA Sandbox 进行在线测试](http://www.ibm.com/developerworks/downloads/soasandbox/) 并尝试使用这些来自 DB2®、Lotus®、Rational®、Tivoli® 和 WebSphere® 的应用程序开发工具和中间件产品。

**讨论**

  * [XML 专区讨论论坛](http://www.ibm.com/developerworks/forums/dw_xforums.jsp)：参与任何与 XML 相关的讨论。
  * [developerWorks blogs](http://www.ibm.com/developerworks/blogs/)：查阅这些 blogs 并加入 [developerWorks 社区](http://www.ibm.com/developerworks/community)。

**关于作者**

Mark O'Neill 是 Vordel 的 CTO，这是一家 XML 网络公司。他还是 "Web Services Security"
一书的作者，另外也参与了 "Hardening Network Security" 一书的写作，两本书均由 McGraw-Hill/Osborne
Media 出版。Mark 负责监督 Vordel 的产品开发路线图，并建议 Global 2000 公司和各国政府战略性地采用 XML、Web 服务和
SOA 技术。他具有 Trinity College Dublin 的数学与心理学的学位，并从牛津大学获得了神经网络编程的硕士学位。Mark
现生活在马萨诸塞州的波士顿。



