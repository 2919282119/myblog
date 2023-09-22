---
title: apache dbutils
cover: https://cdn0.iconfinder.com/data/icons/badges-26/54/markdown-format-mark-down-arrow-sign-badge-1024.png
tags: javaweb

---

## Apache dbutils用法

```java
Connection conn = DBUtil.getConn("mysales");
        QueryRunner queryRunner = new QueryRunner();
        try {
            //这种是把结果放到Object数组中，不需要javabean
            List<Object[]> rs = queryRunner.query(conn,"select * from products", new ArrayListHandler());
            for(Object[] item:rs){
                System.out.println(item[0]+"-"+item[1]+"-"+item[2]);
            }
            //这种是把结果放到javabean中，得到一个list
            List<Product> products = queryRunner.query(conn, "select * from products", new BeanListHandler<Product>(Product.class));
            //注意这里是用的反射生成对象，必须要有无参构造方法
            for(Product p:products){
                System.out.println(p);
            }
            //这是增删改，比较简单
            queryRunner.update(conn,"update chess set point=250 where playername=?","蔡徐坤");

        } catch (SQLException e) {
            e.printStackTrace();
        }
```



