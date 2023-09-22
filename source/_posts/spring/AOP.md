---
title: AOP入门
cover: https://cdn0.iconfinder.com/data/icons/badges-26/54/markdown-format-mark-down-arrow-sign-badge-1024.png
tags: spring

---

## 简介

AOP（Aspect Oriental Programming）是一个spring框架的核心概念(不限于spring)，含义是面向切面编程，可以在不修改源程序的基础上实现功能的扩展，spring的AOP是用**代理模式**实现的



## 核心概念

- **连接点**(JoinPoint)：原始方法
- **切入点**(PointCut)：选择要追加功能的方法，切入点可定义多个
- **通知**(Advice)：共性功能
  - 通知类：java中方法不能独立存在，要写一个通知类

- **切面**(Aspect)：通知和切入点的关系(要如何扩展)



## AOP实现方法

1. 先引入AOP坐标，groupid为org.aspectj
2. 找到程序的共性功能，写一个通知类，定义通知方法
3. 找到要添加功能的方法(切入点)
4. 确定通知和切入点的关系，进行绑定



## 通知类

```java
@Component //写了这个才能变成受spring管理的bean
@Aspect  //写了这个才知道是面向切面
public class MyAdvice {
    //这句是定义切入点(也就是要对哪个方法进行扩展)
    @Pointcut("execution(void service.sqlService.delete())")
    
    //定义一个无参无返回值的空方法
    private void pt(){}

    //定义切面，也就是在切入点的什么位置进行扩展
    @Before("pt()")
    public void showRunTime(){
        System.out.println(System.currentTimeMillis());
    }
}

```

- 注意在配置类里面要添加这一句注解：@EnableAspectJAutoProxy



## 出现的注解

- @Component
- @Aspect
- @PointCut
- @Before
- @EnableAspectJAutoProxy

