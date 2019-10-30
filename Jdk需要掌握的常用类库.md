
**Java 类库概念：** Java 的应用程序接口 (API) 以包的形式来组织，每个包提供了大量的相关类、接口和异常处理类，这些包的集合就是 Java 的类库

包名以 Java 开始的包是 Java 核心包 (Java Core Package) ；

包名以 Javax 开始的包是 Java 扩展包 (Java Extension Package) ，例如 javax.swing 包；

**常用的 Java 核心包 (Java Core Package)**

java.lang Java 编程语言的基本类库

java.applet 创建 applet 需要的所有类

java.awt 创建用户界面以及绘制和管理图形、图像的类

java.io 通过数据流、对象序列以及文件系统实现的系统输入、输出

java.net 用于实现网络通讯应用的所有类

java.util 集合类、时间处理模式、日期时间工具等各类常用工具包

**其它还有**

java.sql 访问和处理来自于 Java 标准数据源数据的类

java.test 以一种独立于自然语言的方式处理文本、日期、数字和消息的类和接口

java.security 设计网络安全方案需要的一些类

java.beans 开发 Java Beans 需要的所有类

java.math简明的整数算术以及十进制算术的基本函数

java.rmi 与远程方法调用相关的所有类

**常用的 Java 扩展包 (Java Extension Package)**

javax.accessibility 定义了用户界面组件之间相互访问的一种机制

javax.naming.* 为命名服务提供了一系列类和接口

javax.swing.* 提供了一系列轻量级的用户界面组件，是目前 Java 用户界面常用的包

注 1 ：最重要且常用的是 1 和 6 ，已用黑体标出的为，需重点掌握

注 2 ：在使用 Java 时，除了 java.lang 外，其他的包都需要 import 语句引入之后才能使用。

重点讲解内容：java.lang和java.util。

**java.lang 包**

这个包称为 java 语言包，是由编译器自动引入的。程序中不必用 import 语句就可以使用。它所包含的类和接口对所有实际的 Java 程序都是必要的。

object 类

数学类 (Math)

数据类型类

线程类

字符串类 (String 类和 StringBuffer 类 )

系统及运行类 (System 类和 Runtime 类 )

错误和异常处理类 (Throwable 、 Exception 、 Error)

过程类 (process)

**java.util 包**

日期类、日历类（ Data 、 Calendar 、 GregorianCalendar ）

随机数类（ Random ）

位运算类（ BitSet ）

矢量类（ Vector ）

数据结构类（ Stack ）

散列表类（ Hashtable ）

StringTokenizer类（与String.split 的功能类似）

|包名|主要功能|
|:-:|:-:|
|java.applet|提供了创建applet需要的所有类|
|java.awt.*|提供了创建用户界面以及绘制和管理图形、图像的类|
|java.beans.*|提供了开发Java Beans需要的所有类|
|java.io|提供了通过数据流、对象序列以及文件系统实现的系统输入、输出|
|java.lang.*|Java编程语言的基本类库|
|java.math.*|提供了简明的整数算术以及十进制算术的基本函数|
|java.rmi|提供了与远程方法调用相关的所有类|
|java.net|提供了用于实现网络通讯应用的所有类|
|java.security.*|提供了设计网络安全方案需要的一些类|
|java.sql|提供了访问和处理来自于Java标准数据源数据的类|
|java.test|包括以一种独立于自然语言的方式处理文本、日期、数字和消息的类和接口|
|java.util.*|包括集合类、时间处理模式、日期时间工具等各类常用工具包|
|javax.accessibility|定义了用户界面组件之间相互访问的一种机制|
|javax.naming.*|为命名服务提供了一系列类和接口|
|javax.swing.*|提供了一系列轻量级的用户界面组件，是目前Java用户界面常用的包|
