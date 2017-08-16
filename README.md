# microservices

> 我的微服务架构探索之路,接下来所有内容围绕 `Spring Cloud ` Dalston.SR2 总结 ,工作繁忙我会每天更新一点点~ 你的Start 是对我最大的鼓励,谢谢。

* github地址: [https://github.com/kingschan1204/microservices](https://github.com/kingschan1204/microservices)

# 什么是微服务？

>`微服务`一词来源于 Martin Fowler的名为Microservices的博文，文章地址：[http://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html) 通俗的讲`微服务`就是系统架构上的一种设计风格，它的思想是将一个独立的系统拆分成多个小型服务，这些服务在各自独立的进程中运行，服务之间基本http restful api 或者消息中间件通信协作，被拆分成的小服务都围绕着系统中的某一项或者一些耦合度较高的业务功能进行构建（每个服务是独立部署的）由于有了轻量级的通信协议作为基础，所以这些微服务可以使用不同的语言来编写。

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