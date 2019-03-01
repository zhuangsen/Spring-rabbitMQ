# Spring-rabbitMQ
  - 在业务逻辑的异步处理，系统解耦，分布式通信以及控制高并发的场景下，消息队列有着广泛的应用。本项目基于Spring的AMQP模块，整合流行的开源消息队列中间件rabbitMQ,实现一个向rabbitMQ添加和读取消息的功能。并比较了两种模式：生产者-消费者模式和发布-订阅模式的区别。AMQP作为比JMS更加高级的消息协议，支持更多的消息路由和消息模式。
  
- 包含的特性如下：

  ![输入图片说明](http://git.oschina.net/uploads/images/2017/0223/081751_c96aa8d6_1110335.png "在这里输入图片标题")
  
1. 如上图，生产者消费者模型：添加了一个队列，并创建了两个消费者用于监听队列消息，我们发现，当有消息到达时，两个消费者会交替收到消息。这一过程虽然不用创建交换机，但会使用默认的交换机，并用默认的直连（default-direct）策略连接队列；

![输入图片说明](http://git.oschina.net/uploads/images/2017/0223/081802_088eb810_1110335.png "在这里输入图片标题")

2. 如下图，发布订阅模型，添加两个队列，分别各用一个消费者监听，设置一个交换机，类型为广播（fanout），交换机会将收到的消息广播给所有相连的队列：

![输入图片说明](http://git.oschina.net/uploads/images/2017/0223/081828_bb1c0dad_1110335.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0223/081836_cf8c1eca_1110335.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0223/081845_581684b4_1110335.png "在这里输入图片标题")

3. direct直连交换机通信模型，包括一个direct交换机，三个binding，两个队列，两个消费者监听器，消息只会被投入到routingkey一致的队列中

 ![输入图片说明](https://git.oschina.net/uploads/images/2017/0902/111518_ec24f2cf_1110335.png "3.png")
 ![输入图片说明](https://git.oschina.net/uploads/images/2017/0902/111713_388a2cb4_1110335.png "5.png")

4.topic主题交换机通信，包括一个topic交换机，三个binding，两个队列，两个消费者监听器，消息只会被投入到routingkey能够匹配的队列中，#表示0个或若干个关键字，*表示一个关键字

![输入图片说明](https://git.oschina.net/uploads/images/2017/0902/122830_278b8f19_1110335.png "4.png")
![输入图片说明](https://git.oschina.net/uploads/images/2017/0902/122904_a0229951_1110335.png "6.png")

5. 进入http://localhost:8080/Spring-rabbitMQ/demo 可向rabbitMQ发送消息，如下图：
 ![输入图片说明](https://git.oschina.net/uploads/images/2017/0902/122918_5adae2c4_1110335.png "QQ截图20170902122553.png")


### 附录：个人作品索引目录（持续更新）

#### 基本篇

1. [SpringMVC,Mybatis,Spring三大框架的整合实现增删改查](https://gitee.com/shenzhanwang/SSM)
2. [Struts2,Hibernate,Spring三大框架的整合实现增删改查](https://gitee.com/shenzhanwang/S2SH)
3. [Spring,SpringMVC和Hibernate的整合实现增删改查](https://gitee.com/shenzhanwang/SSH)
4. [Spring平台整合activiti工作流引擎实现OA开发](https://gitee.com/shenzhanwang/Spring-activiti)
5. [Spring发布与调用REST风格的WebService](https://gitee.com/shenzhanwang/Spring-REST)
6. [Spring整合Apache Shiro框架，实现用户管理和权限控制](https://gitee.com/shenzhanwang/Spring-shiro)
7. [使用Spring security做权限控制](https://gitee.com/shenzhanwang/spring-security-demo)

#### 中级篇

8. [Spring连接mongoDB数据库实现增删改查](https://gitee.com/shenzhanwang/Spring-mongoDB)
9. [Spring连接Redis实现缓存](https://gitee.com/shenzhanwang/Spring-redis)
10. [Spring连接图存数据库Neo4j实现增删改查](https://gitee.com/shenzhanwang/Spring-neo4j)
11. [Spring平台整合消息队列ActiveMQ实现发布订阅、生产者消费者模型（JMS）](https://gitee.com/shenzhanwang/Spring-activeMQ)
12. [Spring整合消息队列RabbitMQ实现四种消息模式（AMQP）](https://gitee.com/shenzhanwang/Spring-rabbitMQ)
13. Spring整合Jasig CAS框架实现单点登录（未开源）
14. Spring框架的session模块实现集中式session管理（未开源）
15. [Spring整合websocket实现即时通讯](https://gitee.com/shenzhanwang/Spring-websocket)
16. 使用Spring boot整合mybatis,rabbitmq,redis,mongodb实现增删改查（未开源）
17. [Spring MVC整合FastDFS客户端实现文件上传](https://gitee.com/shenzhanwang/Spring-fastdfs)

#### 高级篇

18. 搭建zookeeper集群提供目录服务（未开源）
19. 使用ubuntu+apache+SVN+SVNadmin+maven+Nexus+Hudson搭建持续集成环境（未开源）
20. Spring框架整合dubbo框架实现分布式服务治理（SOA架构）（未开源）
21. Spring框架整合dubbox实现微服务架构（MSA架构）（未开源）
22. 使用Spring Cloud实现微服务架构（MSA架构）（未开源）
23. 使用FastDFS搭建分布式文件系统（高可用、负载均衡）（未开源）
24. 搭建高可用nginx集群和Tomcat负载均衡（未开源）
25. 搭建可扩展的ActiveMQ高可用集群（未开源）
26. 实现Mysql数据库的主从复制、读写分离、分表分库、负载均衡和高可用（未开源）
27. 搭建高可用redis集群实现分布式缓存（未开源）
28. [Spring整合SolrJ实现全文检索](https://gitee.com/shenzhanwang/Spring-solr)

