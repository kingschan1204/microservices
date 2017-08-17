# microservices

> 我的微服务架构探索之路,接下来所有内容围绕 `Spring Cloud ` Dalston.SR2 总结 ,工作繁忙我会每天更新一点点~ 你的Start 是对我最大的鼓励,谢谢。

* github地址: [https://github.com/kingschan1204/microservices](https://github.com/kingschan1204/microservices)

# 什么是微服务？

>`微服务`一词来源于 Martin Fowler的名为Microservices的博文，文章地址：[http://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html) 通俗的讲`微服务`就是系统架构上的一种设计风格，它的思想是将一个独立的系统拆分成多个小型服务，这些服务在各自独立的进程中运行，服务之间基本http restful api 或者消息中间件通信协作，被拆分成的小服务都围绕着系统中的某一项或者一些耦合度较高的业务功能进行构建（每个服务是独立部署的）由于有了轻量级的通信协议作为基础，所以这些微服务可以使用不同的语言来编写。


# 与单体系统的区别

> 在以往传统的企业系统架构中，我们针对一个复杂的业务需求通常使用对象或业务类 型来构建一个单体项目。在项目中我们通常将葙求分为三个主要部分：数据库、服务端处理、前端展现。在业务发展初期，由于所有的业务逻辑在一个应用中，开发、测试、部署 都还比较容結且方便。但是，随着企业的发展，系统为了应对不同的业务需求会不断为该 单体项目增加不间的业务模块：问时随着移动端设备的进步，前端展现揆块己经不仅仅局限于Web的形式，这对于系统后端向前端的支持需要更多的接口模块。单体应用由于面对的业务需求更为宽泛，不断扩大的需求会使得单体应用变得越来越臃肿。单体应用的问题就逐渐凸显出来，由于单体系统部署在一个进程内，往往我们修改了一个很小的功能，为 /部署上线会影响其他功能的运行•并且，单体应用中的这些功能模块的使用场景、并发量、消耗的资源类型都各有不同，对于资源的利用又互相影响，这样使得我们对各个业务 模块的系统容量很难给出较为准确的评估.所以，单体系统在初期虽然可以非常方便地进行开发和使用，但是随着系统的发展，维护成本会变得越来越大，且难以控制.为了解决单体系统变得庞人臃肿之后产生的难以维护的问题.微服务架构诞生了并被 大家所关注。我们将系统中的不同功能模块拆分成多个不同的服务，这些服务都能够独立 部署和扩展，由于每个服务都运行在自己的进程内，在部署上有稳固的边界，这样毎个服务的更新都不会影响其他服务的运行，同时，由于是独立部署的，我们可以更准确地为每 个服务评估性能容量,通过配合服务间的协作流程也可以更容易地发现系统的瓶颈位置，以及给出较为准确的系统级性能容最评估。



# Spring Cloud 简介

> `Spring Cloud `是一个基于`Spring boot `实现的微服务架构开发工具。`Spring Cloud`为开发人员提供了快速构建分布式系统中一些常见模式的工具（例如配置管理，服务发现，断路器，智能路由，微代理，控制总线）。分布式系统的协调导致了样板模式, 使用`Spring Cloud`开发人员可以快速地支持实现这些模式的服务和应用程序。他们将在任何分布式环境中运行良好，包括开发人员自己的笔记本电脑，裸机数据中心，以及`Cloud Foundry`等托管平台。

- 官网 ： [http://projects.spring.io/spring-cloud/](http://projects.spring.io/spring-cloud/)
- 我用的版本: `Dalston SR2`
- 官方帮助手册: [http://cloud.spring.io/spring-cloud-static/Dalston.SR2/](http://cloud.spring.io/spring-cloud-static/Dalston.SR2/)

# Spring Cloud 特性

> Spring Cloud专注于提供良好的开箱即用经验的典型用例和可扩展性机制覆盖。

* 分布式/版本化配置
* 服务注册和发现
* 路由
* service - to - service调用
* 负载均衡
* 断路器
* 分布式消息传递

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
|Bus|微服务消息总线|[RabbitMQ安装](https://github.com/kingschan1204/microservices/blob/master/bus/centos7-install-rabbitmq.md)
|Stream|微服务消息驱动|
|Sleuth|微服务分布式跟踪|