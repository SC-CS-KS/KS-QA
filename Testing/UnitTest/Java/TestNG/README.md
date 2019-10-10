# [TestNG](https://testng.org)
相比junit增加了更多注解形式，可以使用XML文件配置参数化测试。


## [WhatIs](WhatIs.md)

## 依赖测试
```md
指测试的方法是有依赖的，在执行的测试之前需要执行的另一测试。
```
```java
@Test
public void method1() {
System.out.println("This is method 1");
}

@Test(dependsOnMethods={"method1"})
public void method2() {
System.out.println("This is method 2");
}
```
```md
如果method1()成功执行，那么method2()也将被执行，否则method2()将会被忽略。
```

## Reference
* [TestNG Tutorials](https://howtodoinjava.com/java-testng-tutorials/)
* [TestNG教程](https://www.yiibai.com/testng/)

* [《Java测试新技术TestNG和高级概念》](https://testng.org/doc/book.html)