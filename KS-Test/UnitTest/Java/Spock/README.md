# [Spock](http://spockframework.org)

* [Spock Framework Reference Documentation](http://spockframework.github.io/spock/docs)

## [WhatIs](WhatIs.md)

## 构造块
```java
class TestCase extends Specification {
    @Shared //在测试方法之间共享的数据
    SomeClass sharedObj

    def setupSpec() {
        //TODO: 设置每个测试类的环境,相当于Junit中的 @BeforeClass
    }

    def setup() {
        //TODO: 设置每个测试方法的环境，每个测试方法执行一次,相当于Junit中的 @Before
    }

    @Ignore("忽略这个测试方法")
    @Issue(["问题#23","问题#34"])
    def "测试方法1" () {
        given: "给定一个前置条件"
        //TODO: code here
        and: "其他前置条件"

        expect: "随处可用的断言"
        //TODO: code here

        when: "当发生一个特定的事件"
        //TODO: code here
        and: "其他的触发条件"

        then: "产生的后置结果"
        //TODO: code here
        and: "同时产生的其他结果"

        where: "不是必需的测试数据"
        input1 | input2 || output
        ...   |   ...  ||   ...
    }

    @IgnoreRest //只测试这个方法，而忽略所有其他方法
    @Timeout(value = 50, unit = TimeUnit.MILLISECONDS)  // 设置测试方法的超时时间，默认单位为秒
    def "测试方法2"() {
        //TODO: code here
    }

    def cleanup() {
        //TODO: 清理每个测试方法的环境，每个测试方法执行一次,相当于Junit中的 @After
    }

    def cleanupSepc() {
        //TODO: 清理每个测试类的环境,相当于Junit中的 @AfterClass
    }
}
```
* [where: 以表格的形式提供测试数据集合](design/where.md)
* when: 触发行为，比如调用指定方法或函数
* then: 做出断言表达式
* expect: 期望的行为，when-then的精简版
* given: mock单测中指定mock数据
* thrown: 如果在when方法中抛出了异常，则在这个子句中会捕获到异常并返回
* def setup() {} ：每个测试运行前的启动方法
* def cleanup() {} : 每个测试运行后的清理方法
* def setupSpec() {} : 第一个测试运行前的启动方法
* def cleanupSpec() {} : 最后一个测试运行后的清理方法

## Mock
* [Mocking](design/Mocking.md)
* [Stubing](design/Stubing.md)

## 实践
## expect-where

## Reference
* [《Java Testing with Spock》](https://www.manning.com/books/java-testing-with-spock)
* [Github unit-testing 实例代码](https://github.com/mpredli01/unit-testing)

