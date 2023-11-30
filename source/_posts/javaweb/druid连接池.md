---
title: druid连接池
cover: 
tags: javaweb
---

### 1.在`pom.xml`中添加`druid`依赖

```java
<dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>druid</artifactId>
      <version>1.0.18</version>
</dependency>
```



### 2.在`resources`文件夹下创建`properties`文件

```java
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://127.0.0.1:3306/mysales?useSSLuseSSL=false&serverTimezone=GMT&characterEncoding=utf-8&allowPublicKeyRetrieval=true
username=root
password=sql2008
```

- 以上四个属性是必要的，还有以下其他属性可以设置
  - `name`：用来区分不同数据源
  - `maxActive`：最大连接数量



### 3.在工具类`DBUtil`中写一个静态方法用以获取连接

```java
public static Connection getDruidConn() throws Exception {
        Properties prop = new Properties();
        InputStream is = JdbcUtils.class.getResourceAsStream("/druid.properties");
        prop.load(is);
        DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
        return dataSource.getConnection();
}
```