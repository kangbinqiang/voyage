## MyBatis-Plus :100:
[官网](https://baomidou.com/) 
上对MyBatis-Plus的用法和特性做了详细的描述，这里只做一个简单的引入，具体用法参考
[官网](https://baomidou.com/) 
### 官网特性

> **无侵入**：只做增强不做改变，引入它不会对现有工程产生影响，如丝般顺滑
>
> **损耗小**：启动即会自动注入基本 CURD，性能基本无损耗，直接面向对象操作
>
> **强大的 CRUD 操作**：内置通用 Mapper、通用 Service，仅仅通过少量配置即可实现单表大部分 CRUD 操作，更有强大的条件构造器，满足各类使用需求
>
> **支持 Lambda 形式调用**：通过 Lambda 表达式，方便的编写各类查询条件，无需再担心字段写错
>
> **支持主键自动生成**：支持多达 4 种主键策略（内含分布式唯一 ID 生成器 - Sequence），可自由配置，完美解决主键问题
> 
> **支持 ActiveRecord 模式**：支持 ActiveRecord 形式调用，实体类只需继承 Model 类即可进行强大的 CRUD 操作
>
> **支持自定义全局通用操作**：支持全局通用方法注入（ Write once, use anywhere ）
>
> **内置代码生成器**：采用代码或者 Maven 插件可快速生成 Mapper 、 Model 、 Service 、 Controller 层代码，支持模板引擎，更有超多自定义配置等您来使用
>
> **内置分页插件**：基于 MyBatis 物理分页，开发者无需关心具体操作，配置好插件之后，写分页等同于普通 List 查询
>
> **分页插件支持多种数据库**：支持 MySQL、MariaDB、Oracle、DB2、H2、HSQL、SQLite、Postgre、SQLServer 等多种数据库
>
> **内置性能分析插件**：可输出 SQL 语句以及其执行时间，建议开发测试时启用该功能，能快速揪出慢查询
>
> **内置全局拦截插件**：提供全表 delete 、 update 操作智能分析阻断，也可自定义拦截规则，预防误操作

### 支持的数据库
> mysql，oracle，db2，h2，hsql，sqlite，postgresql，sqlserver，Phoenix，Gauss ，clickhouse，Sybase，OceanBase，Firebird，cubrid，goldilocks，csiidb
>
> 达梦数据库，虚谷数据库，人大金仓数据库，南大通用(华库)数据库，南大通用数据库，神通数据库，瀚高数据库

### 框架结构
![框架结构](images/Snipaste_2021-10-06_13-40-13.png)

### 添加依赖
在`pom.xml`文件中添加依赖
```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>Latest Version</version>
</dependency>
```
### 配置
在`application.yml`文件中添加
```yaml
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql:///database_name
    username: database_username
    password: database_password
```
在`SpringBoot`的启动类上添加`@MapperScan`注解，扫描`Mapper`文件夹
```java
@MapperScan("com.voyage.mapper")
```
### 生成主键

> 配置雪花算法

实体类配置：
```java
@TableId(type = IdType.ID_WORKER)
private String id;
```
可供选择的：
```java
public enum IdType {
    AUTO(0),
    NONE(1),
    INPUT(2),
    ID_WORKER(3),
    UUID(4),
    ID_WORKER_STR(5);
}
```
### 分页
添加配置如下
```java
@Bean
public PaginationInterceptor paginationInterceptor() {
    return new PaginationInterceptor();
}
```
使用
```java
@Override
public Page<CodeConfig> list() {
    Page<CodeConfig> page = new Page<>(0, 5);
    return genConfigRepository.selectPage(page,null);
}
```
测试
```text
Creating a new SqlSession
SqlSession [org.apache.ibatis.session.defaults.DefaultSqlSession@45eb9e11] was not registered for synchronization because synchronization is not active
JDBC Connection [com.alibaba.druid.proxy.jdbc.ConnectionProxyImpl@40914c5e] will not be managed by Spring
==>  Preparing: SELECT id,table_name,api_alias,pack,module_name,path,api_path,author,prefix,cover,created_time,updated_time,is_delete AS isDeleted FROM v_code_config
==> Parameters: 
<==      Total: 0
Closing non transactional SqlSession [org.apache.ibatis.session.defaults.DefaultSqlSession@45eb9e11]
```
### 自动填充
!> 在业务系统的开发过程中，有些字段和业务的耦合性不大，但是必须存在，这时候可以考虑解耦设计的自动填充

实体类配置：
```java
@TableField(value = "created_time",fill = FieldFill.INSERT)
private Date createdTime;

@TableField(value = "updated_time",fill = FieldFill.INSERT_UPDATE)
private Date updatedTime;
```
添加配置如下：
```java
@Slf4j
@Component
public class VoyageMetaObjectHandler implements MetaObjectHandler {

    @Override
    public void insertFill(MetaObject metaObject) {
        log.info("start insert fill...");
        this.setFieldValByName("createdTime", LocalDateTime.now(), metaObject);
        this.setFieldValByName("updatedTime", LocalDateTime.now(), metaObject);
    }

    @Override
    public void updateFill(MetaObject metaObject) {
        log.info("start update fill...");
        this.setFieldValByName("updatedTime", LocalDateTime.now(), metaObject);
    }
}
```
### 执行自定义SQL
!> 有时业务需要执行一些特定的`SQL`，但是`Mybatis-Plus`提供的API不能完全胜任，需要写一些自定义的`SQL`
在mapper中添加方法：
```java
@Select("select table_name ,create_time , engine, table_collation, table_comment from information_schema.tables where table_schema = (select database()) order by create_time desc")
List<TableInfo> getAllTableInfo();

@Select("select column_name, is_nullable, data_type, column_comment, column_key, extra from information_schema.columns where table_name = #{tableName} and table_schema = (select database()) order by ordinal_position")
List<ColumnInfo> getColumnsByTableName(@Param("tableName") String tableName);
```

