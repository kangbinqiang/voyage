# Voyage交易平台  :100:

---

## 友情提示
!> 该项目只可用于学习，若商业使用需进行二次开发

## 序言

> - 极致的项目架构，优雅的代码设计
> - 分布式解耦与容灾设计
> - 高并发与高吞吐设计

## 项目介绍

?> 该项目最终的目的是打造一款集借贷、投资与一体的平台，采用分布式解耦设计，使得用户以不同的身份在平台上完成交易，同时无缝对接第三方平台，使交易如丝般顺滑

## 项目架构
![项目架构](images/voyage-architect.png)


## 项目结构

``` xml
voyage
├── common -- 工具类及通用代码
├── generator -- 代码生成平台
├── oauth -- 认证授权模块
├── system -- 后端管理模块
├── loan -- 借款模块
├── invest -- 投资模块
├── third-party -- 第三方平台
└── pay -- 支付平台
```

## 项目文档

## 项目演示

> 前端地址
>
> 后端管理

### 后端技术
| Project    | Description    |  Verion  |
| ----------- | --------- | ------------ |
| [Spring Boot](https://spring.io/projects/spring-boot)       |  微服务框架  |    |
| [Spring Cloud](https://spring.io/projects/spring-cloud)       | 分布式架构 |    |
| [Nacos](https://nacos.io/zh-cn/docs/quick-start.html)       | 微服务管理、配置中心 |    |
| [Seata](https://seata.io/en-us/)       | 分布式事物框架 |    |
| [Sentinel](https://gitee.com/rmlb/Sentinel/)       | 流量守卫 |    |
| [Spring Cloud Alibaba](https://spring.io/projects/spring-cloud-alibaba)       | 由Alibaba开发的分布式架构 |    |
| [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway)       | 网关 |    |
| [Spring Cloud OpenFeign](https://spring.io/projects/spring-cloud-openfeign)       | 微服务调用 |    |
| [MYSQL](https://www.mysql.com/)       | 关系型数据库 |    |
| [Redis](https://redis.io/)       | 非关系型数据库 |    |
| [Mybatis-Plus](https://baomidou.com/)       | ORM |    |
| [Spring Security](https://spring.io/projects/spring-security)       | 认证授权框架 |    |
| [ElasticSearch](https://www.elastic.co/cn/elasticsearch/)       | 搜索引擎 |    |
| [Logstash](https://www.mysql.com/)       | 数据库 |    |
| [Kibana](https://www.mysql.com/)       | 数据库 |    |
| [RabbitMQ](https://www.rabbitmq.com/)       | 消息队列 |    |
| [OSS](https://account.aliyun.com/)       | 对象存储 |    |
| [Lombok](https://projectlombok.org/)       | 对象封装插件 |    |
| [Swagger](https://swagger.io/)       | 接口文档框架 |    |
| [Druid](https://druid.apache.org/)       | 数据库连接池 |    |
| [Docker](https://www.docker.com/)       | 容器 |    |
| [Kubernetes](https://kubernetes.io/docs/home/)       | 容器编排 |    |
| [GitHub](https://www.github.com/)       | 代码托管 |    |
| [Oauth](https://oauth.net/2/)       | 认证授权框架 |    |


### 前端技术
| Project    | Description    |  Verion  |
| ----------- | --------- | ------------ |
| [Vue](https://cn.vuejs.org/)       |  前端框架  |    |
| [Element-UI](https://element.eleme.cn/)       |  前端管理框架  |    |
| [Vrouter](https://router.vuejs.org/zh/)       |  前端路由框架  |    |

## 参考文档
> [mall-learning](http://www.macrozheng.com/#/)
> 

## 开发环境

> JDK 1.8
>
> IDEA 2019.3
>
> MYSQL 5.7
>
> Redis 6.0
>
> Windows 10   

## 开发者

> Voyage 工作闲暇时间
>
## 开发进度
- [x] 2021-10-06 
    - 设计项目架构
    - SpringBoot自动装配原理
- [x] 2021-10-07 
    - 创建后端工程
    - Netty
- [x] 2021-10-08 
    - 创建前端工程


    



