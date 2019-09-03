# [Spock](http://spockframework.org)
* [Spock Framework Reference Documentation](http://spockframework.org/spock/docs/1.3/index.html)

## [WhatIs](WhatIs.md)

## 构造块
where: 以表格的形式提供测试数据集合
when: 触发行为，比如调用指定方法或函数
then: 做出断言表达式
expect: 期望的行为，when-then的精简版
given: mock单测中指定mock数据
thrown: 如果在when方法中抛出了异常，则在这个子句中会捕获到异常并返回
def setup() {} ：每个测试运行前的启动方法
def cleanup() {} : 每个测试运行后的清理方法
def setupSpec() {} : 第一个测试运行前的启动方法
def cleanupSpec() {} : 最后一个测试运行后的清理方法

## 实践
## expect-where


## Reference
* [《Java Testing with Spock》](https://www.manning.com/books/java-testing-with-spock)

* [Github unit-testing 实例代码](https://github.com/mpredli01/unit-testing)

