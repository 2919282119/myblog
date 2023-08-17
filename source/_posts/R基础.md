---
title: R语言基础
cover: https://afly-0321.oss-cn-hangzhou.aliyuncs.com/img/Rstudio
tag: 数据统计
---

### W3C教程

- https://www.w3cschool.cn/r/



### 快捷键

```R
X<-3 #alt+-:快速打出<-
#ctrl+L清除控制台
```



### 数据类型

- 矢量
- 列表
- 矩阵
- 数组
- 因子
- 数据帧



### 循环

```R
while(条件){
    
}
for(x in 可迭代对象){
    
}
```



### 函数

- 内置函数

```R
mean(1:4)   #求1-4的均值
sum(1:6)    #1-6的和
ls()   #列出变量
ls.str()  #列出变量详细内容
rm(a,b,……)  #删除变量
rm(list=ls())  #删除所有变量

help("函数名")   #了解函数用法
?函数名  #了解函数用法
args(函数名)  #显示函数参数
example("函数名")  #给一个函数使用例子
demo(graphics) #显示绘图的例子

print(x)  #打印单个
cat(x,y,z)  #组合打印
```

- 自定义函数

```R
function_name<-function(arg1,arg2,...){
    #函数体
}
```



### 安装包

```R
install.packages("包名")  #注意要加引号
library()  #列出当前已经安装的包

library(包名)  
require("package:包名")   #加载包
```



