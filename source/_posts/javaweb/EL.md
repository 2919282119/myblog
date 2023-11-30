---
title: EL&JSTL
cover: 
tag: javaweb

---

# EL是什么？

### 全称：

Expression Language，可以替代jsp页面的java代码

### 操作符：

```jsp
${requestScope.student.name}
<!--
${域对象.属性.级联属性}
${requestScope.student[list]}
[]里面可以用变量或特殊字符，.操作符不可以
-->
```

### 隐式对象

- 作用域访问对象（如果不指定域对象，将会从小到大取）

  - pageScope
  - requestScope
  - sessionScope
  - applicationScope

- 参数访问对象（用于获取表单数据或者地址栏数据/超链接数据）

  ```jsp
  <!--
  这是原本在jsp获取表单数据的方式
  -->
  request.getParameter()
  request.getParameterValues()<!--如果是数组，如checkbox-->
  <!--
  这是用el的方式
  -->
  ${ param.username }
  ${ paramValues.hobbies[0] }
  ```

- jsp隐式对象（pageContext,可以用来拿到jsp的session,application,request,response等对象）

```jsp
${pageContext.getSession()}
<!--
其实不是这么写的，直接变成属性的写法
-->
${pageContext.session}
${pageContext.request}
```



# JSTL

## 介绍

比EL功能更加强大,但是需要引入jar(用maven即可)

## 引入方式(tablib)

```jsp
<%@ tablib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
```

## 核心标签库

- 通用标签库

  ```jsp
  <!--
  c:set用于在某个作用域内给某个变量赋值，或者给某个对象的某个属性赋值
  -->
  <c:set var="studentname" value="张三" scope="request"/>
  <c:set target="${requestScope.student}" property="name" value="张三"/>
  
  <!--
  c:out用于显示变量值，好处是若某个变量不存在时可以指定显示默认值
  -->
  <c:out value="${requestScope.student}" default="张三"/>
  
  <!--
  c:remove用于在某个作用域中删除某个变量
  -->
  <c:remove var="student" scope="request"/>
  ```

- 条件标签库

  ```jsp
  <!--
  c:if用于条件显示
  -->
  <c:if test="${age>18}">
      
  </c:if>
  ```

- 迭代标签库

```jsp
<!--
c:forEach用于循环显示,也可遍历集合或数组
-->
<c:forEach begin="0" end="5" step="1" varStatus="status">
	${status.index}
</c:forEach>
<c:forEach var="stu" items="${requestScope.stulist}">
	${stu.name}
</c:forEach>
```

