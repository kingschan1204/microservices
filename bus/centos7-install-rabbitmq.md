> RabbitMQ是实现AMQP（高级消息队列协议）的消息中间件的一种，最初起源于金融系统，用于在分布式系统中存储转发消息，在易用性、扩展性、高可用性等方面表现不俗。消息中间件主要用于组件之间的解耦，消息的发送者无需知道消息使用者的存在，反之亦然。
MQ 全称为 Message Queue, 消息队列（MQ）是一种应用程序对应用程序的通信方法。应用程序通过读写出入队列的消息（针对应用程序的数据）来通信，而无需专用连接来链接它们。
RabbitMQ 是一个在 AMQP 基础上完整的，可复用的企业消息系统。他遵循 Mozilla Public License 开源协议。

- RabbitMQ 官网：[http://www.rabbitmq.com/](http://www.rabbitmq.com/)
- RabbitMQ 官网下载：[http://www.rabbitmq.com/download.html](http://www.rabbitmq.com/download.html)
- RabbitMQ 官网安装文档：[http://www.rabbitmq.com/install-rpm.html](http://www.rabbitmq.com/install-rpm.html)

# 安装Erlang 

> 由于RabbitMQ是用`Erlang`开发的，所以我们需要先安装Erlang ,在RabbitMQ官网提供了Erlang的安装包。

![centos7](https://kingschan1204.github.io/microservices/bus/res/show-centos-version.png)

![elang版本](https://kingschan1204.github.io/microservices/bus/res/erlang-release.png)

于上图所示我的系统是centos7 所以我安装的倒数第二个。
```
 rpm -ivh rabbitmq-server-3.6.10-1.el7.noarch.rpm
```

# 安装RabbitMQ
```
 rpm --import https://www.rabbitmq.com/rabbitmq-signing-key-public.asc
```
去官网下载安装包 http://www.rabbitmq.com/download.html

![ribbitMQ下载地址](https://kingschan1204.github.io/microservices/bus/res/rabbitmq-download.png)
在浏览器右键复制链接然后在linux 下执行
```
 wget http://www.rabbitmq.com/releases/rabbitmq-server/v3.6.10/rabbitmq-server-3.6.10-1.el7.noarch.rpm
```

## 安装

```
sudo yum install -y rabbitmq-server-3.6.1-1.noarch.rpm
```
# 启动服务

先看下自己的主机名：hostname，我的主机名是：`micro2`
先修改一下 host 文件：vim /etc/hosts，添加一行：127.0.0.1 micro2
- 启动：service rabbitmq-server start
- 停止：service rabbitmq-server stop
- 重启：service rabbitmq-server restart
- 设置开机启动：chkconfig rabbitmq-server on

# 配置
查找默认配置位置：find / -name "rabbitmq.config.example"，我这边搜索结果是：/usr/share/doc/rabbitmq-server-3.6.10/rabbitmq.config.example

![rabbitmq config](https://kingschan1204.github.io/microservices/bus/res/command-find-rabbit-config.png)

- 复制默认配置：cp /usr/share/doc/rabbitmq-server-3.6.10/rabbitmq.config.example /etc/rabbitmq/
- 修改配置文件名：cd /etc/rabbitmq ; mv rabbitmq.config.example rabbitmq.config
- 编辑配置文件，开启用户远程访问：vim rabbitmq.config
- 在 64 行，默认有这样一句话：%% {loopback_users, []},，注意，该语句最后有一个逗号，等下是要去掉的
- 我们需要改为：{loopback_users, []}，
- 开启 Web 界面管理：rabbitmq-plugins enable rabbitmq_management
- 重启 RabbitMQ 服务：service rabbitmq-server restart
- 浏览器访问：http://192.168.x.xxx:15672 默认管理员账号：guest 默认管理员密码：guest

> 翻看官方的release文档后，得知由于账号guest具有所有的操作权限，并且又是默认账号，出于安全因素的考虑，guest用户只能通过localhost登陆使用，并建议修改guest用户的密码以及新建其他账号管理使用rabbitmq(该功能是在3.3.0版本引入的)。`{loopback_users, []}， 这一句就是让所有地方都可以用guest登录`

## 登录成功后的控制面板
![ribbitMQ dashboard](https://kingschan1204.github.io/microservices/bus/res/rabbitmq-dashboard.png)