# microservices

> 我的微服务架构探索之路,接下来所有内容围绕spring cloud 总结

# 什么是微服务？

>`微服务`一词来源于 Martin Fowler的名为Microservices的博文，文章地址：[http://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html) 通俗的讲`微服务`就是系统架构上的一种设计风格，它的思想是将一个独立的系统拆分成多个小型服务，这些服务在各自独立的进程中运行，服务之间基本http restful api 或者消息中间件通信协作，被拆分成的小服务都围绕着系统中的某一项或者一些耦合度较高的业务功能进行构建（每个服务是独立部署的）由于有了轻量级的通信协议作为基础，所以这些微服务可以使用不同的语言来编写。

# 微服务组件

![](https://kingschan1204.github.io/microservices/res/microservices.png )

# 组件简述

|组件|简述|备注|
|-|-|-|
|Eureka|微服务注册中心|
|Ribbon|微服务负载均衡|
|Hystrix|微服务容错保护|
|Feign|微服务声明式服务调用|
|Zuul|微服务API网关|
|Config|微服务分布式配置中心|
|Bus|微服务消息总线|
|Stream|微服务消息驱动|
|Sleuth|微服务分布式跟踪|
