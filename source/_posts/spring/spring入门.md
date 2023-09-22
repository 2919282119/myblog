---
title: 纯注解开发
cover: https://cdn0.iconfinder.com/data/icons/badges-26/54/markdown-format-mark-down-arrow-sign-badge-1024.png
tags: spring

---

## 引言

传统的spring是通过xml配置文件的方式进行IOC的，最新的方式是通过注解的方式来开发，即“@”,比如常见的注解有：

1. @Configration
1. @Component
1. @ComponentScan    数组
1. @Autowired
1. @Qualifier



## 各部分写法

### Dao

```java
@Repository
public class sqlDao {
    public void delete(){
        System.out.println("deleteDao...");
    }
}
```



### Service

```java
@Service
public class sqlService {
    @Autowired 
    //自动装配(按类型)
    //@Qualifier("sqlDao") 通过这种方式来注入某个特定名称的dao
    private sqlDao sqldao;
    
    public void delete(){
        System.out.println("deleteService...");
        sqldao.delete();
    }
}
```





### APP

```java
ApplicationContext ctx=new AnnotationConfigApplicationContext(springConfig.class);
sqlService sqlservice = (sqlService) ctx.getBean(sqlService.class);
sqlservice.delete();
```

