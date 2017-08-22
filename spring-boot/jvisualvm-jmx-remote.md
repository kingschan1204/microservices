# 使用java VisualVM 监控远程服务器jvm

# 背景

> 在部署微服务节点的时候发现在Docker容器中占用内存比较多平均一个节点要去到1.5G~2G ，因此项目组需要分析为什么会造成这种现象。此时我马上联想到用`JVisualVM `来监控应用，那么问题来了如何监控远程容器中的应用呢？

![Eureka docker内存占用情况](https://kingschan1204.github.io/microservices/spring-boot/res/eureka_docker_memory_usage.jpg)

# 解决方案
> 使用JvisualVM 通过JMX远程监控服务器上的JVM

# 命令

```
#启动JMX可以通过jvritualVM 进行监控
nohup java -Djava.rmi.server.hostname=192.168.10.232 -Dcom.sun.management.jmxremote.port=22222 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -jar eureka-0.0.1-SNAPSHOT.jar --spring.profiles.active=peer1 &
```

# 效果

 打开jvisualVM > 文件 > 添加JMX链接 > ip地址:端口

![](https://kingschan1204.github.io/microservices/spring-boot/res/jvisualvm-remote.png)
![](https://kingschan1204.github.io/microservices/spring-boot/res/jvisualvm-remote-thead.png)
 
 