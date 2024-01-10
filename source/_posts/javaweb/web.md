---
title: web期末复习
cover: https://pic3.zhimg.com/80/v2-04cba14fab1fdca4e0f298b1c3043f7e_720w.webp
tags: [javaweb,期末复习]
---



## 琐碎知识

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
                    return cookie.getValue();
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

- **lib：** 外部JAR包

- **META-INF：** 项目元数据



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
- `ServletContext getServerContext()`
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
        req.setCharsetEncoding("utf-8");
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

主要概念和实现方式：

1. **切面（Aspect）：** 切面是横切关注点的模块化，它封装了横切关注点的行为。例如，一个日志切面可以定义在方法执行前后记录日志的行为。
2. **连接点（Join Point）：** 连接点是在应用程序执行过程中能够插入切面的点。例如，方法的调用、异常的抛出等。
3. **通知（Advice）：** 通知是切面在连接点处执行的动作，包括 "before"、"after"、"around" 等。
4. **切点（Pointcut）：** 切点是一组连接点的集合，用于定义切面的执行位置。
5. **引入（Introduction）：** 引入允许向现有的类添加新方法或属性。

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