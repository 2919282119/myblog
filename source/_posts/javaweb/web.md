---
title: web期末复习
cover: https://pic3.zhimg.com/80/v2-04cba14fab1fdca4e0f298b1c3043f7e_720w.webp
tags: [javaweb,期末复习]
---



## 名词解释
- 设计模式（工厂或单例）:
  - 工厂模式：创建对象的模式，通过一个工厂类来生成具体的对象。
  - 单例模式：确保一个类只有一个实例，并提供全局访问点。
- Restful风格API:
一种基于HTTP协议的设计理念，强调资源的表现层状态转化。通过GET、POST、PUT、DELETE等HTTP方法进行交互。
- CGI:
通用网关接口，一种用于在Web服务器和应用程序之间传递信息的标准接口。
- LAMP:
Linux（操作系统）、Apache（Web服务器）、MySQL（数据库）、PHP（编程语言）的组合，用于搭建动态Web应用的开发环境。
- C/S B/S:
  - C/S（客户端/服务器）：应用程序分为客户端和服务器，通过网络进行通信。
  - B/S（浏览器/服务器）：应用程序通过Web浏览器访问，服务器提供服务。
- MVC架构（或三层架构）:
  - MVC：模型-视图-控制器，一种将应用程序分成三个组件的设计模式，有助于代码的组织和维护。
  - 三层架构：将应用程序划分为表示层、业务逻辑层和数据访问层，提高可维护性和灵活性。
- 依赖倒置原则（DIP）:
高层模块不应依赖于低层模块，两者都应该依赖于抽象。抽象不应依赖于细节，细节应该依赖于抽象。
- 依赖注入
依赖注入是一种通过外部容器将对象所需的依赖关系传递给对象的设计模式，有助于降低代码耦合度和提高可维护性。
- 过滤器（或监听器）:
  - 过滤器：用于在请求或响应被处理前后执行过滤任务的组件。
  - 监听器：用于监听事件，执行相应的业务逻辑。
- IOC或AOP:
  - IOC（控制反转）：由容器控制对象的创建和管理，而不是由应用程序代码直接控制。
  - AOP（面向切面编程）：通过将横切关注点（如日志、事务）从主业务逻辑中分离出来，提高代码的可维护性。
- ORM:
对象关系映射，用于将对象模型和数据库模型进行映射，简化数据库操作。
- 硬编码:
在代码中直接使用明确的数值或字符串，而不是通过变量或配置文件进行管理。
- 会话:
在Web开发中，会话用于跟踪用户的状态，存储用户信息，以确保用户在多个请求之间保持一致性。
- Web容器:
一种运行Web应用程序的环境，负责处理HTTP请求、调用应用程序代码并返回响应（运行servlet）。
- www：world wide web

## 碎片知识
- url组成部分(contextpath+servletpath+pathInfo)

- CGI:`common gateway interface`公共网关接口（把html字符串嵌入各种语言）
  - 1994:PHP
  - 1996:ASP
  - 1998:JSP

- LAMP:`linux apache mysql php`

- C/S与B/S的比较
  - C/S更早，
    - 优点：稳定，性能好，不依赖网络，安全性好
    - 缺点：维护更新麻烦
  - B/S现在是趋势
    - 优点：维护更新方便，跨平台
    - 缺点：依赖网络，性能相对较差，安全性相对较差

- EJB(enterprise javabean):过度设计，废弃



## MVC架构

- **模型（Model）:**

  - **职责：** 模型表示应用程序的数据和业务逻辑。它负责管理数据的状态、规则和行为，确保数据的一致性和有效性。

  - **特点：** 模型不直接处理用户界面或用户输入，而是通过控制器来更新状态。通常包括数据存储、检索和处理的方法。

- **视图（View）:**

  - **职责：** 视图负责展示数据给用户，并接收用户的输入。它将模型的数据渲染成用户可以理解的形式，通常是用户界面的一部分。

  - **特点：** 视图不应包含业务逻辑，它只负责显示数据和将用户的操作传递给控制器。

- **控制器（Controller）:**

  - **职责：** 控制器充当模型和视图之间的中介，处理用户的输入并相应地更新模型的状态。它负责协调应用程序的流程，将用户的请求映射到相应的模型操作和视图更新。

  - **特点：** 控制器不处理业务逻辑，而是委托给模型。它接收来自视图和模型的通知，并采取适当的行动。



## 三层架构

- **数据访问层(dao,原子性的,不可拆)**

dao层叫数据访问层，全称为data access object，数据访问层处理与数据库的交互，负责从数据库中读取和写入数据。它包括了数据库连接、数据查询、持久化以及数据校验等功能。

- **业务逻辑层(可拆的,对dao层的逻辑组装)**

这一层负责处理应用程序的业务逻辑。它包含了处理业务规则、业务流程以及数据处理的代码。在这一层，您可以编写处理用户请求的业务逻辑，例如计算、数据处理、验证等。通过将业务逻辑与表示层和数据访问层分开，可以使代码更具可维护性和可测试性

- **表示层**

这是用户与应用程序交互的界面部分。它负责接收用户的请求并将结果呈现给用户。通常，这一层包括了Web页面、用户界面元素以及与用户交互的控制器（例如Servlet）。在这一层，您会处理用户输入、验证数据，然后将请求传递给业务逻辑层来处理。



#### 面向接口编程有以下几点好处：

在java中接口是多继承的，而类是单继承的，如果你需要一个类实现则基隐多个service，你用接口可以实现，用类定义service就没那么灵活，要提供不同的数据库的服务时，我们只需要面对接口用不同的类实现即可，而不用重复地定义类，接口化的编程为的就是将实现封装起来，然调用者只关心接口不关心实现，也就是“高内聚，低耦合”的思想。



#### **依赖倒置原则（DIP）简化：**

1. **高层模块不应该依赖于底层模块。**
2. **抽象不应该依赖于细节。**
3. **细节应该依赖于抽象。**

##### 依赖

B是A的依赖可以理解为：

①A持有B作为成员变量

②有A的前提是有B



### **int、Integer、String之间的两两相互转换**

- int和Integer之间可以自动装拆箱
- int(Integer)转String用`String.valueOf()`
- String转int(Integer)用`Integer.parseInt()`



## cookie

- 保存在客户端

服务器通过`Set-Cookie`响应头在浏览器中创建Cookie，浏览器存储并在后续请求中自动发送。服务器通过`HttpServletRequest`读取请求中的Cookie，实现跟踪用户状态和数据传递。

- 写cookie

```java
Cookie cookie = new Cookie("username", "john_doe");
cookie.setMaxAge(3600); // 设置Cookie的生存期，单位为秒,若不设置,为会话cookie
response.addCookie(cookie); // 将Cookie添加到HTTP响应中
```

- 读cookie

```java
Cookie[] cookies = request.getCookies();

        if (cookies != null) {
            for (Cookie cookie : cookies) {
                if (cookie.getName().equals(cookieName)) {
                    System.out.println(cookie.getValue())
                }
            }
        }
```



## Session

- Session和用户有关，每个用户不一样
  - Session在用户第一次访问服务器的时候自动创建，生成一个JsessionID,然后通过cookie存到客户端，客户端下一次访问服务器时，会查看cookie中的JsessionID判断用户是否已经成功登陆。
  - 需要注意只有访问JSP、Servlet等程序时才会创建Session，只访问HTML、IMAGE等静态资源并不会创建Session。
- 保存在服务器端
- servlet中通过`request.getSession()`拿到session
- 通过`setMaxInactiveInterval(1000)`设置session的最大活跃有效期
- 通过`invalidate()`方法使session失效
- `getAttribute(String name)`取属性
- `setAttribute(String name,Object obj)`设置属性



## web项目结构

- **src：** Java源代码

- **webapp**：Web资源
  - WEB-INF：配置文件、依赖、编译后的类
    - web.xml
    - lib
    - classes

- **META-INF：** 项目元数据
- **其他**



## 请求与响应

### 请求

- 两种跳转方式

**request.getRequestDispatcher**

```java
request.getRequestDispatcher("B.java").forward(request,response)
```

**response.sendRedirect**

```java
response.sendRedirect("B.java")
```

- 区别

|                          | 请求转发 |      重定向      |
| :----------------------: | :------: | :--------------: |
|      地址栏是否改变      |   不变   |        变        |
| 是否保留第一次请求时数据 |   保留   |      不保留      |
|         请求次数         |    1     |        2         |
|      跳转发生的位置      | 服务器端 | 客户端第二次跳转 |



#### Request对象

##### 常用方法

- `String getParameter(String name)`
  - 拿到表单元素的值
- `String[] getParameterValues(String name)`
  - 拿到数组类表单元素(如checkbox)的值
- `void setCharacterEncoding("UTF-8")`
  - 设置编码方式
- `getRequestDispatcher("b.jsp").forward(request,response) `
  - 请求转发
- `ServletContext getServletContext()`
  - ServletContext是全局共用的对象，有以下几个常用方法
    - `setAttribute(name,value)`
    - `getAttribute(name)`
    - `removeAttribute(name)`

#### getRequestDispatcher的include和forward区别
- `getRequestDispatcher("B").include(request,response)`
  - A会保留原来的响应体,也就是说A也可以进行响应
- `getRequestDispatcher("B").forward(request,response)`(常用)
  - A只保留请求体，完全由B完成响应工作

**www.zstu.edu.cn**

- www不是world wide web,而是一个主机名，也可以叫别的名字

- 从后往前看

### 响应

#### Response对象

**常用方法**

- `void addCookie( Cookie cookie )`
  - 服务端向客户端增加cookie对象
- `void sendRedirect(String location )`
  - 重定向
- `void setContetType(String type)`
  - 置服务端响应的编码，一般为`text/html;charset=UTF-8`
  - 可修改设置得到pdf或excel文件
    - `response.setContentType("application/pdf");`pdf文件

**处理请求参数**

- getParameter()

  - 获取表单项的值

- getParameterValues()

  - 获取复选表单项的值，得到一个String数组

- getParameterNames()

  - 获取全部的请求参数名称，返回Erumeration<String>对象

    ```java
    Erumeration<String> e=req.getParameterNames()
    while(e.hasMoreElements()){
        String param=e.nextElements();
        ...
    }//这样来遍历
    //Erumeration是个从JDK1.0就存在的古老接口，功能与Iteration重叠，如果可以，建议使用Collection.list()将之转换为ArrayList,以便使用增强的for语法,Lambda,Stream API
    ```

- getParameterMap()

  - 返回Map<String,String[]>

**处理请求标头**

- getHeader()
  - 指定标头名称后可返回字符串值，代表浏览器发送的标头信息
- getHeaderNames()
  - 返回Erumeration<String>
- setHeader(k,v)





#### urlPatterns
- 配置要拦截的资源
  - 以指定资源匹配。例如"/index.jsp"
  - 以目录匹配。例如"/servlet/*"
  - 以后缀名匹配，例如"*.jsp"
  - 通配符，拦截所有web资源。"/*"


#### http状态码
- 100类状态码：属于信息型状态码，表达服务器正在处理请求
- 200类状态码：成功状态码，表达请求已经正常处理完毕
- 300类状态码：重定向状态码，需要进行额外操作以完成请求。
- 400类状态码：客户端错误状态码，导致服务器无法处理请求。
  - 404状态码：表示未找到，表示没有找到文件或目录。
- 500类状态码：服务器错误状态码，服务器原因导致处理请求出错。
- 设置状态编码：`response.setStatus()`但一般不会手动设置

##### 配置参数一般要写在配置文件里面，而不是写在源代码里，避免“硬编码”问题



#### get和post请求区别

- **GET：**
  - 参数通过 URL 传递（地址栏可见）
  - 对数据长度有限制。
  - 幂等操作，多次请求不会产生不同结果。
- **POST：**
  - 参数在请求体中传递。
  - 对数据长度无限制（表单提交，上传文件要用post）
  - 非幂等操作，多次请求可能产生不同结果。



## druid连接池

#### 1.在`pom.xml`中添加`druid`依赖

```java
<dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>druid</artifactId>
      <version>1.0.18</version>
</dependency>
```

#### 2.在`resources`文件夹下创建`properties`文件

```java
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://127.0.0.1:3306/mysales?useSSLuseSSL=false&serverTimezone=GMT&characterEncoding=utf-8&allowPublicKeyRetrieval=true
username=root
password=sql2008
```

- 以上四个属性是必要的，还有以下其他属性可以设置
  - `name`：用来区分不同数据源
  - `maxActive`：最大连接数量

#### 3.在工具类`DBUtil`中写一个静态方法用以获取连接

```java
public static Connection getDruidConn() throws Exception {
        Properties prop = new Properties();
        InputStream is = JdbcUtils.class.getResourceAsStream("/druid.properties");
        prop.load(is);
        DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
        return dataSource.getConnection();
}
```



### 原生JDBC

```java
Class.forName("com.mysql.cj.jdbc.driver")
String url="jdbc:mysql://localhost:3306/mydatabase";
String user="root";
String password="sql2008";
Connection conn = DriverManager.getConnection(url, user, password);
// 创建 Statement 对象
Statement statement = connection.createStatement();
// 执行 SQL 语句
ResultSet rs = statement.executeQuery("SELECT * FROM mytable");
```







## 设计模式

### 单例模式

1. **私有构造函数：** 将类的构造函数设为私有，防止外部直接实例化该类。
2. **静态实例：** 在类内部创建一个私有的静态成员变量，用于存储类的唯一实例。
3. **公共访问方法：** 提供一个公共的静态方法，用于获取该类的唯一实例。这个方法会在实例不存在时创建一个新的实例，否则返回已有的实例。

```java
public class Singleton {
    // 私有静态成员变量，存储唯一实例
    private static Singleton instance;//懒汉式

    // 私有构造函数，防止外部直接实例化
    private Singleton() {
        // 初始化操作
    }

    // 公共静态方法，获取唯一实例
    public static Singleton getInstance() {
        // 延迟加载，当实例不存在时再创建
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```





### 工厂模式

- **封装性：** 客户端无需关心对象的创建过程，只需通过工厂来获取所需对象。
- **灵活性：** 可以通过改变工厂来改变具体产品的创建方式，而不需要修改客户端代码。
- **可扩展性：** 新增产品时只需增加相应的产品类和工厂类，而不需要修改已有代码。

```java
// 产品接口
interface Product {
    void display();
}

// 具体产品A
class ConcreteProductA implements Product {
    @Override
    public void display() {
        System.out.println("This is Product A");
    }
}

// 具体产品B
class ConcreteProductB implements Product {
    @Override
    public void display() {
        System.out.println("This is Product B");
    }
}

// 工厂类
class SimpleFactory {
    // 根据参数创建不同的产品实例
    public static Product createProduct(String productType) {
        if ("A".equals(productType)) {
            return new ConcreteProductA();
        } else if ("B".equals(productType)) {
            return new ConcreteProductB();
        }
        return null;
    }
}

// 客户端
public class Client {
    public static void main(String[] args) {
        // 使用工厂创建产品
        Product productA = SimpleFactory.createProduct("A");
        productA.display();

        Product productB = SimpleFactory.createProduct("B");
        productB.display();
    }
}
```





## servlet

- web.xml

```xml
<servlet>
    <servlet-name>aaa</servlet-name>
    <servlet-class>java.servlet.Aservlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>aaa</servlet-name>
    <url-pattern>/Aservlet</url-pattern>
</servlet-mapping>
```

- 注解（@WebServlet）

```java
@WebServlet("/Aservlet")
public class Aservlet extends HttpServlet{
    public void doGet(HttpServletRequest req,HttpServletResponse res){
        //...
    }
    public void doPost(){
        doGet(req,res)
    }
}
```

- 优先级：web.xml>注解
#### Servlet继承树
- Servlet接口
  - ServletRequest接口
    - HttpServletRequest接口
  - ServletResponse接口
    - HttpServletResponse接口
  - GenericServlet抽象类实现了Servlet接口
    - HttpServlet抽象类继承了GenericServlet类

- Servlet接口定义了5个方法
  - init()
  - service()
  - destroy()
  - getServiceConfig()
  - getServletInfo()
- GenericServlet这个抽象类中对除了service方法之外的4个方法进行了简单实现
- HttpServlet是专门处理HTTP请求的，其他的网络请求不用管
- service()方法会调用子类重写的doGet()或doPost(),所以我们只需要重写doGet和doPost，不要重写service()


## 过滤器

- web.xml

```xml
<filter>
    <filter-name></filter-name>
    <filter-class></filter-class>
</filter>
<filter-mapping>
    <filter-name></filter-name>
    <url-pattern></url-pattern>
</filter-mapping>
```

- 注解（@WebFilter）

```java
@WebFilter("/*")
public class CorsFilter extends HttpFilter{
    public void doFilter(HttpServletRequest req,HttpServletResponse res,FilterChain chain){
        req.setCharacterEncoding("utf-8");
        req.setContentType("text-html;chartset=utf-8");
         // 允许跨域访问的域名，可以使用通配符"*"表示允许任意域名
        response.setHeader("Access-Control-Allow-Origin", "*");
        response.setHeader("Access-Control-Allow-Methods", "*");
        response.setHeader("Access-Control-Allow-Headers", "*");
        chain.doFilter(req,res);
         //...
    }
}
```

- 可用于处理跨域问题



## 监听器

- web.xml(注意这个不需要mapping)

```xml
<listener>
    <listener-class></listener-class>
</listener>
```

- 注解(@WebListner)

```java
@WebListener
public class AListener implements HttpSessionListener {

    public AListener() {
    }

    @Override
    public void sessionCreated(HttpSessionEvent se) {
        /* Session is created. */
    }

    @Override
    public void sessionDestroyed(HttpSessionEvent se) {
        /* Session is destroyed. */
    }

}
```



## JSP

#### 常用域对象(除了response之外都有setAttribute和getAttribute方法)

- pageContext
- request
- response
- session
- application

#### 语法

```jsp
<% ... %>：用于插入Java代码块。
<%= ... %>：用于在页面中输出表达式的值。等价于out.print()
<%! ... %>：用于定义页面级别的变量和方法。
${user.id} el语句
<%@ page ... %>：包含页面指令，用于设置页面的属性，如导入包、设置语言等。

循环和html嵌套
<%
	for(int i=0;i<list.length;i++){
%>
	<div>${list[i]}</div>
	或者<div><%=list[i]%></div>
<%
	}
%>
例：九九乘法表
<%
    for(int i = 1; i < 10; i++){
        for(int j = 1; j <=i; j++){
            out.println(j+"×"+i+"="+(i*j));
        }
        out.println("<br>");
    }
%>
```



## IOC和AOP（spring核心思想）

#### **IoC（Inversion of Control）- 控制反转：**

IoC 的核心思想是反转对象的创建和管理权。传统的程序设计中，开发者负责创建对象、组织对象之间的关系，控制对象的生命周期等。而在 IoC 容器中，这些责任被反转了，容器负责对象的创建、组织关系、生命周期管理，开发者只需专注于业务逻辑。

主要体现在以下两种形式：

1. **依赖注入（DI）：** 由 IoC 容器负责将依赖关系注入到对象中。这消除了对象主动查找或创建依赖的需求，对象只需声明它需要的依赖，由容器来提供。

   ```
   javaCopy code// 传统方式
   class Car {
       Engine engine = new Engine();
   }
   
   // IoC方式（依赖注入）
   class Car {
       Engine engine;
   
       Car(Engine engine) {
           this.engine = engine;
       }
   }
   ```

2. **控制反转：** 对象的创建和生命周期由容器来控制，而不是由对象自己。开发者不再直接调用构造函数或工厂方法来创建对象，而是通过 IoC 容器来获取所需的对象。

   ```
   javaCopy code// 传统方式
   class MyApp {
       public static void main(String[] args) {
           Car car = new Car();
           car.start();
       }
   }
   
   // IoC方式（控制反转）
   class MyApp {
       public static void main(String[] args) {
           IoCContainer container = new IoCContainer();
           Car car = container.getBean(Car.class);
           car.start();
       }
   }
   ```

**AOP（Aspect-Oriented Programming）- 面向切面编程：**

AOP 的核心思想是通过将横切关注点（cross-cutting concerns）从主业务逻辑中分离出来，以便更好地模块化和复用。横切关注点是那些跨越应用程序多个模块的关注点，例如日志、事务管理、安全等。

#### 核心概念
- **连接点**(JoinPoint)：原始方法
- **切入点**(PointCut)：选择要追加功能的方法，切入点可定义多个
- **通知**(Advice)：共性功能
  - 通知类：java中方法不能独立存在，要写一个通知类

- **切面**(Aspect)：通知和切入点的关系(要如何扩展)

AOP 的主要目标是解耦关注点，使代码更易于维护和理解。通过 AOP，我们可以将横切关注点集中管理，提高代码的模块化程度。



## javaweb后续学习方向

### ssm

- spring
- springMVC
- mybatis

### springboot



### 右键新建没有servlet的解决办法

- 首先确保`pom.xml`里面添加了servlet依赖

- 去项目结构里面勾选`Resource Roots`(`Facets`或者`Modules`)


### Restful风格

- RESTful (Representational State Transfer) 是一种设计和构建网络应用程序的架构风格。它通常用于创建 Web 服务，使系统之间的通信更加简单和可伸缩。以下是关于RESTful的一些基本概念：

**资源 (Resource)**: 在RESTful架构中，一切都被视为资源。资源可以是任何可以通过网络访问的实体，比如数据对象、服务、或者整个应用程序。

**表现层 (Representation)**: 资源的表现层是指资源在特定时间点的状态以及与其他资源之间的关系。常见的表现层格式包括JSON和XML。

**状态转移 (State Transfer)**: 客户端通过与资源的表现层交互，实现状态的转移。这通常是通过HTTP方法（GET、POST、PUT、DELETE等）来实现的。

**统一接口 (Uniform Interface)**: RESTful接口应该是统一和简单的，以提高系统的可见性、简化客户端的实现，同时降低了服务器的性能开销。

**无状态性 (Statelessness)**: 每个请求都应该包含服务器处理该请求所需的所有信息。服务器不应该保存关于客户端状态的信息。

- 以一个简单的图书管理系统为例来说明RESTful的概念。

假设我们有一个图书馆的Web服务，我们想要管理图书的信息。在RESTful设计中，我们可以将图书视为资源，每本书都有一个唯一的标识符（URI）。

**获取特定图书信息（GET请求）:**

请求：GET /books/{bookId}

响应：返回特定图书的详细信息

**添加新图书（POST请求）:**

请求：POST /books

数据：包含新书信息的JSON或XML

响应：返回新书的URI以及状态码

**更新图书信息（PUT请求）:**

请求：PUT /books/{bookId}

数据：包含更新后的书籍信息的JSON或XML

响应：返回更新后的图书信息

**删除图书（DELETE请求）:**

请求：DELETE /books/{bookId}

响应：返回删除的图书信息或者一个成功的状态码


---
## cgx整理的

一、填空选择简答
1.Servlet的继承树？为什么需要定义那么多接口（利用什么原则）？
Servlet<<interface>> ——>  GenericServlet ——> HttpServlet ——> MyServlet
Servlet<<interface>>中包含了ServletRequest<<interface>>、ServletResponse<<interface>>
HttpServlet<<interface>>包含HttpServletRequest<<interface>>与		HttpServletResponse<<interface>>

2.HttpServlet在哪个包里面？GenericServlet在哪个包里面？
Javax.servlet.http
Javax.servlet
3.Servlet的生命周期？
（init service（doGet、doPost） destroy）更详细一点就是包括加载程序、初始化（init）、服务(service)、销毁(destroy)、卸载5个部分。
4.servlet定义的两种方式（注解和web.xml定义）
(1)@WebServlet(name=””,urlPattern=””)
(2)在web.xml里面
<servlet>
<servlet-name>w</servlet-name>
<servlet-class>A.B.Servlet1</servlet-class>
<load-on-startup>1</load-on-startup>  大于0即可加载后立即初始化
</servlet>
<servlet-mapping>
<servlet-name>w</servlet-name>
<url-pattern>/xxx</url-pattern>
</servlet-mapping>
5.web-INF里面的资源可以被读取吗？
如果用URI直接访问的话不行，但是可以利用流getResourceAsStream去读取）

6.init方法，只在第一个用户的第一次访问某个Servlet时执行该方法，它也有一个重载方法的参数是ServletConfig，如何在init阶段获得servlet设置的初始参数呢？
@WebServlet(“/h”,@WebInitParam(name=”par1”,value=”hello”))
~
~
 @Override
    public void init() throws ServletException {
        String par1 = getInitParameter("par1");  
 //或者      String par1 = getServletConfig().getInitParameter("par1"); 
}
（还有一种在web.xml中的
<servlet>
<servlet-name>w</servlet-name>
<servlet-class>A.B.Servlet1</servlet-class>
<init-param>
<param-name></param-name>
<param-value></param-value>
</init-param>
</servlet>
）
7.service方法是用户的每一次访问都会执行，并且会调用doXXX方法。（是否要重写此方法呢？）
不建议重写service方法，有可能会打乱HttpServlet的调用流程
8.destroy方法什么时候调用呢？
Servlet销毁的时候（一般是浏览器关闭或者是web容器关闭）
9.如何在doGet/doPost方法中将请求的参数一次全部取出呢？
利用工具类
Map<String,Object> map = new HashMap<String,Object>();
Enumeration<String> names = request.getParameterNames();
while(names.hasMoreElements()){
            String name = names.nextElement();
            map.put(name,request.getParameter(name));
        }
10.servlet定义了几种doXXX方法？多样的请求处理方法适用于什么风格的编程？
(1)七种（doGet doPost doPut doPatch doDelete doOptions doTrace）
(2)Restful
11.一个请求包含哪些部分？
请求行（GET /index.html HTTP/1.1）
请求头（key value 形式）
请求体 包括请求数据和空行
12一个响应包含哪些部分？
状态行
消息报头
响应正文
13状态行的响应码
1xx	指示信息–表示请求已接收，继续处理
2xx	成功–表示请求已被成功接收、理解、接受
3xx	重定向–要完成请求必须进行更进一步的操作。
4xx	客户端错误–请求有语法错误或请求无法实现。
5xx	服务器端错误–服务器未能实现合法的请求。
200 成功
301 永久更换资源链接 302临时更换资源链接 304重定向
400 客户端出错 403被禁止 404 Not Found
500 服务器端出错

14.Servlet如何保证在接收请求或者响应时可以使中文正确显示？
（1）在每个Servlet中定义请求和响应的编码
（2）直接定义过滤器
15.request调派请求常用方法
(1) request.getRequestDispatcher(“想转的servlet路径”).include(requse,response)
(2) request.getRequestDispatcher(“想转的servlet路径”).forward(requse,response)
Include将转的servlet内容代码包含进来，原有的servlet代码不去掉
Forward将原有的servlet代码去掉，转的servlet内容代码替换进来
16.请求可以进行多次转发（forward）吗？
可以，并且浏览器标签栏中的路径认为第一次请求的路径
17.多次重定向后的浏览器标签栏中的路径还是第一次的吗？
不是，是最后一次的请求的路径
18.什么是Cookie？
Cookie是一种文本信息，Web服务器将它发送给浏览器，而用户再次访问同一个服务器时，这些文本信息将被浏览器原封不动地返回给服务器。
19. 读取Cookie操作
Cookie cookies = request.getCookies();
If(cookies!=null){
For(String cookie:cookies){
String name = cookie.getName();
String value = cookie.getValue();
}
}
20. 增加Cookie操作
Cookie newcookie = new Cookie(“name”,”value”);
Response.addCookie(newcookie);
21.如何修改Cookie
直接在新增时利用同名Cookie即可
22.如何删除Cookie
直接将这个cookie.setMaxAge(0)
23.ServletContext对象用哪个方法获得
用ServletConfig的getServletContext()方法
24.HttpSessionListener这个生命周期监听器接口的常用方法
(1)sessionCreated(HttpSessionEvent se){}
(2)sessionDestroyed(HttpSessionEvent se){}
25.HttpSession什么时候创建呢?
在Servlet中，session不会主动创建，第一次使用时才创建。JSP默认会创建session。
26.过滤器的继承树(与Servlet基本一致)
Filter<<interface>> ——>  GenericFilter ——> HttpFilter ——> MyFilter
27.会话管理的实现方式
(1)隐藏域(古董方法,用input表单type的hidden属性)
(2)使用Cookie
(3)URL重写
28.servlet与servletConfig servletContext的对应关系
一个servlet对应一个servletConfig
一个web应用中的servlet共享一个servletContext
29.JSP与Servlet的域对象
JSP: application       servlet: ServletContext
Session				  HttpSession
Request				  request
Page                  page
两者是相互对应的
30.jsp的三种脚本写法
<%
Java代码
%>

<%!
声明的属性与方法将被提升到成员变量
%>

<%=”hello” 									相当于直接响应字符串hello
%>
31. JSP与Servlet的关系
Jsp本质上就是servlet
二 名词解释
WWW
JavaSE
JavaEE
MVC架构
依赖注入
控制反转
会话管理
面向切片编程(AOP)
Web容器
BS
CS
Cookie
Session
JsessionID
Spring