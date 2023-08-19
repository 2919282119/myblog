---
title: spring,springMVC和springboot
cover: https://afly0321.oss-cn-hangzhou.aliyuncs.com/spring
tags: 后端框架

---

## Spring和SpringMVC：

1.Spring是一个一站式的轻量级Java开发框架，核心是**控制反转（IOC）和面向切面（AOP）**，针对于开发WEB层（SpringMVC）、业务层（IOC），持久层（JDBCTemplate）等都提供了多种配置解决方案；

2.SpringMVC是Spring基础之上的一个MVC框架。主要处理WEB开发的路径和视图渲染，属于Spring框架中WEB层开发的一部分。

## SpringMVC和Springboot：

1.SpringMVC属于一个企业级WEB开发的MVC框架，涵盖包括**前端视图开发、文件配置、后台接口逻辑开发**等，XML、config等配置相对于比较繁琐复杂；

2.Springboot框架相比较于SpringMVC来说，更专注于开发**微服务后台接口**，不开发前端视图，同时遵循**默认优于配置**，简化了插件开发的流程，不需要配置XML，相对于SpringMVC，大大简化了配置流程。

## 总结：

1.Spring框架就像一个家族，有众多衍生产品，如：boot、security、jpa等。但他们的基础都是Spring的IOC、AOP等；IOC提供了依赖注入的容器、AOP解决了面向切面编程、然后在此俩者的基础上实现了其他产品的高级功能；

2.SpringMVC主要解决了WEB开发问题，是基于Servlet的一个MVC框架、通过XML配置，**统一开发前端视图和后端逻辑**；

3.由于Spring的配置非常复杂，各种XML、JavaConfig、Servlet处理起来比较繁琐，为了简化开发者的使用，从而创造性的推出了Springboot框架，默认优于配置，简化了SpringMVC的流程；但区别于SpringMVC的是，SpringBoot专注于微服务后台接口的开发，**和前端解耦**，虽然Springboot也可以做成SpringMVC一样前后台一起开发，但是这就不符合Springboot框架的初衷了。