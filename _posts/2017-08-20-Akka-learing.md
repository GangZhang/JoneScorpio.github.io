
## What is Akka? ##

> Akka is an open-source toolkit and runtime simplifying the
> construction of concurrent and distributed applications on the JVM.
> Akka supports multiple programming models for concurrency, but it
> emphasizes actor-based concurrency, with inspiration drawn from
> Erlang.
> 
> Language bindings exist for both Java and Scala. Akka is written in
> Scala and, as of Scala 2.10, Akka's actor implementation is included
> as part of the Scala standard library.

[From wiki](https://en.wikipedia.org/wiki/Akka_(toolkit))

> Akka is a toolkit and runtime for building highly concurrent, distributed, and fault tolerant event-driven applications on the JVM.
Build powerful concurrent & distributed applications more easily.

[From Akka.io](http://akka.io/)

简单来说：
> akka是一个用scala编写的库，用于简化编写可容错的，可扩展的，高并发应用。akka使用actor模型来提升抽象能力，提供更好的平台来构建可扩展的，弹性的应用。对于比较难处理的错误，akka采用“let it crash”模型来处理，这种模式可以使得一个任务的处理失败不会导致整个应用的crash，使你的系统拥有强大的自愈能力，也不需要重启来恢复系统。同时akka的分布式部署更加简单透明。

----------
## Why Akka？##

> akka是一个可扩展性非常强的软件，这不仅不仅体现在性能上，而且还体现在它可适用的系统规模上。akka的核心包akka-actor非常小，对于已有的需要异步和无锁并发的系统而言，很容易就可以把akka融入进去。akka适用的前景非常广泛，可使用于金融系统，游戏，医疗，交通，仿真，数据分析等等场景，只要需要高吞吐量、低延迟的系统，akka就是一个可供选择的对象。

[From Akka docs](http://doc.akka.io/docs/akka/snapshot/intro/why-akka.html)

---
## 基本概念 ##


## 关于集群 ##

[akka clustering](https://tersesystems.com/2014/06/25/akka-clustering/)
---
## 关于脑裂 ##
[new features about aplit brain resolver in Akka 2.4](http://www.slideshare.net/Typesafe_Inc/akka-24-plus-commercial-features-in-typesafe-reactive-platform)
---
## Using in AC ##

----------
## 参考 ##
[Akka框架基本要点介绍](http://shiyanjun.cn/archives/1168.html)

