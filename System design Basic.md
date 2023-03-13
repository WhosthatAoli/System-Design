### Networking

1.TCP and UDP

+ *TCP*： reliable; missing resend; 3-way handshake;  expansive 
  + 三次握手保证了可靠性，丢失重发，但是占用的网络资源多
+ *UDP*： faster; useful for streaming, live
  + 网络中的零散包，速度快，不可靠。适用于注重实时传输的直播

2. *DNS*: Domain Name System

Transfer Domain Name to real IP address: google.com --> 192.168.35.46

usually provided by ISP(Internet service provider), ICANN(a organize own domains)



### APIs

#### HTTPs

1.*RPC*: Remote procedure call

Call function remotely like client call functions on code on server



2. Http 

    Request and response

   codes![HTTP status codes](https://github.com/WhosthatAoli/System-Design/blob/main/image/HTTP%20Status%20Codes.png)

#### Websocket

A websocket connection server send message, client don't need to pull

#### RestAPI

Get Post Put Delete 

send information in json



#### GraphQL

designed by http post request

要什么取什么，通过GraphQL API可以只取一些自己需要的内容，比如user有很多fields，只取其中要用的fields，省网络资源

#### gRPC

build on http2   usually used on server to server communication 

Faster and effcient than restApi

send information in protocol buffer  which provide schemas 

can use for streaming 



### Cache

Read from cache is way faster than read from disk(database), ie. Read popular tweet from memory

cache ratio = hit / hit + miss

browser cache

server cache --- memory redis

#### Cache method:

+ write-around cache: create data, put into disk, get data from cache but miss, cache the data

+ write-through cache: create data ,cache the data, put into disk

+ Write-back cache: create data, cache the data, periodically to disk

Eviction policy: FIFO, Random, LRU(least recently used), LFU(least frequently used)

#### CDN(content delivery network)

a way we cache data closer to end users. User all around the world, we put CDN all around world.

only static content(JavaScript, image, vedios), cannot run application code

Push and pull can use method like cache(write-around, write-through)

new thing called: edge server can run code, dynamic

地理上于用户近

### Proxy

forward proxy(usually): a middle server on behalf of the true client. Hide the user and protect their identity. You are allow to the end server but you are allow to the proxy server, proxy does is for you by pass the restriction. 

backward(reverse) proxy: hides the destination server, CDN, load balance

### Load Balancing

round robin

flexbile method

#### route method

+ Layer4 TCP fast; use ip

+ Layer7 flexible; expensive

### Consistent Hashing

some users go to their specific server

math circle

### Storage

#### Replication and Sharding

Sharding：range based  shard key male/female

hash based

### CAP Theorem

![CAP](https://github.com/WhosthatAoli/System-Design/blob/main/image/CAP%20Theorem.png)

### Object Storage

Stored in a flat way, no hierarchy in file systems. AWS S3

### BIG DATA

#### Message queues

So many requests at the same time and our server can't handle them all at once.

Put them in a queue and deal with them in later time

server can pull from the queue, queue can push to server

Queue should be durable in disk

Publishers/subscribers  Kafka use topic RabbitMQ

#### Map Reduce

Each worker do some portion of work-----> then aggregate

master/leader coordinate every worker's work

Spark

ie. Count words in a 500 pages book, every work counts 100 pages





### How to approach

#### 越来越多的公司开始考察系统设计。记得当我第一次听到面试官问我，你可以讲讲你的系统设计吗？我天真的以为，只要说一说数据库中的表关系是如何设计，业务逻辑是如何设计就可以了。直到我说完后发现面试官一脸的沉重，我就知道我答非所问了。
#### 那么应该如何做系统设计？这个问题很复杂。这里我想先分享我对系统设计面试问题的理解。
#### 回答系统设计问题，要将实际问题分解，满足问题/业务的要求。可以分为两大部分：
#### 第一部分：询问与分类
#### 我们要去问面试官，我要设计的系统的整体功能是什么，越详细越好。比如，面试官的问题是设计小🍠，那么我们就问，我们是要设计整体的小🍠呢（首页，购物，发现等），还是要设计核心部分，比如用户发布笔记，互相关注点赞。不同的部分，有不同的设计方向，这时候要让面试官去引导你，你才能设计出面试官想要听到的内容。千万不能是我们自己沉浸在自己的设计中，而面试官却毫不感兴趣。
#### 第二部分：如何实现我们的设计
#### 我们拿到了具体的问题之后，开始考虑两个方面，功能上的设计（Functional）与非功能上（Non-Functional）的设计。
#### 功能的设计，比如，用户互相关注，点赞，发文的功能用什么类型的数据存储？数据库应该选取关系型还是非关系型？表结构如何设计？直播（Steaming）使用什么网络协议，UDP还是HTTP2等。
#### 非功能上的设计，比如，系统要同时承载多少并发和流量（Throughput）？（这里可以做一些简单的计算，比如同时在线人数的估算）。如何增加可用性（Availability），降低延迟（Latency）？如何扩展系统（Scalability），提高系统表现（Performance）？存储方面，如何增加数据库的存储容量（Storage capacity）等。
#### 回答第二部分的问题，需要我们有足够的知识与经验。系统设计是有共同之处的，你往往需要有服务器（Server）、路由（Router），负载均衡（Load Balance），数据库（Database）。而更深入的内容，如何选择数据库类型，如何通过路由提高可用性，这些要求我们对System Design的基础知识有充分的理解。有时间的大家可以去啃一啃图二的这本书，帮助很大。我之后也会更新我的笔记，分享一些系统设计的基础知识和实际使用。

分解实际问题，满足问题要求

共同之处：服务器，路由，负载均衡，数据库

深入：数据库类型，数据关系类型，

可能我们只是在处理一个单独的问题，比如like，问面试官是整体还是一小部分，让面试官去引导你

Functional 功能

Non-Functional 扩展性 throughput storage capacity 

进行一些基础的系统理解，数学计算

trade off

performance

latency

Scalability

Throughput

Storage capacity



1,000 = kilobytes

1,000,000 = megabytes

1,000,000,000 = gigabytes

1,000,000,000,000 = terabytes

1,000,000,000,000,000 = petabytes
