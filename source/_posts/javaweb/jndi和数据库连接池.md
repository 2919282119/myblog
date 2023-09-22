---
title: JNDI和数据库连接池
cover: https://cdn0.iconfinder.com/data/icons/education-364/24/school-programming-laptop-learning-coding-education-512.png
tags: javaweb

---

# JNDI

(java naming directory interface)将某个资源（对象），以配置文件(tomcat/conf/context.xml)的形式写入

## 实现步骤

tomcat/conf/context.xml配置

```xml
<Environment name="jndiname" value="jndivalue" type="java.lang.String"/>
<!--
type要写完整的包名
-->
```

## jsp中

```jsp
<%
Context ctx=new InitialContext();
String jndi=(String)ctx.lookup("java:comp/env/jndiname");
%>
```

# 连接池

由于数据库频繁地开关连接很耗费性能，所以有了连接池，里面放了一些“常年”开启的连接，这样可直接去连接池里面拿连接而不用直接连接数据库

## 常见连接池

Tomcat-dbcp,c3p0,druid

## 例Tomcat-dbcp

<img src="../../AppData/Roaming/Typora/typora-user-images/image-20230904105848127.png" alt="image-20230904105848127" style="zoom:50%;" />

<img src="../../AppData/Roaming/Typora/typora-user-images/image-20230904105924893.png" alt="image-20230904105924893" style="zoom:60%;" />

<img src="../../AppData/Roaming/Typora/typora-user-images/image-20230904110012935.png" alt="image-20230904110012935" style="zoom:50%;" />

