---
title: AOP通知类型和获取通知数据
cover: https://cdn0.iconfinder.com/data/icons/badges-26/54/markdown-format-mark-down-arrow-sign-badge-1024.png
tags: spring

---

## AOP通知类型

- 前置通知
- 后置通知
- **环绕通知**（最重要）



### 前置通知

```java
@Before("pt()")
public void addfunc(){
   System.out.println("hello miki");
}
```



### 后置通知

```java
@After("pt()")
public void addfunc(){
}
```



### 环绕通知

```java
@Around("pt()")
public Object addfunc(ProceedingJoinPoint pjp) throws Throwable {
    //前面添加的操作
    
	Object rs=pjp.proceed()//执行原操作,得到原操作的返回值（这里可以对原始操作进行隔离，权限校验）
        
    //后面添加的操作
    return xxx;
}
```



## AOP通知获取数据

### 获取原方法参数

```java
@Before("pt()")
public void addfunc(JoinPoint jp){//通过JoinPoint接口获取
   Object[] args = jp.getArgs();//拿到参数值，为Object数组
}
```

#### 对于环绕通知

```java
@Around("pt()")
public Object addfunc(ProceedingJoinPoint pjp) throws Throwable {
    //前面添加的操作
    Object[] args = pjp.getArgs();
    
	Object rs=pjp.proceed(args);
    //可以指定原操作实际执行的参数
    //用处：可以在执行之前对参数进行处理（比如格式有问题,或者传过来的参数不能使用可以指定默认值）
        
    //后面添加的操作
    return rs;//指定实际的返回值
}
```



