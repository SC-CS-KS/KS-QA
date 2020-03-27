# Unit Test

根据 [2019 Stack Overflow 年度开发者调查报告](https://insights.stackoverflow.com/survey/2019#work-_-code-review)，
国外 41.8% 的公司把 UT 作为工作流程，20.5% 开发者自行完成，33.2% 没有做单元测试，但觉得应该做，只有4.4%认为没有必要做单元测试。

## Java 
### 数据准备
#### [easy-random - Easy Random是一个生成随机Java Bean的库](https://github.com/j-easy/easy-random)
* DbUnit - JUnit的一个扩展

### Runner
#### [JUnit](Java/JUnit/README.md)
#### [TestNG](Java/TestNG/README.md)
#### [Spock](Java/Spock/README.md)
* Spring-Test
```md
Spring和JUnit的整合，提供了对应的Runner和Rule，使用的比较多的是Spring的Runner。
```

### Mock
```md
场景
外部依赖的应用的调用，比如WebService等服务依赖
DAO层（访问MySQL、Oracle、Emcache等底层存储）的调用等
系统间异步交互通知消息
methodA里面调用到的methodB
一些应用里面自己的Class(abstract，final，static）、Interface、Annotation、Enum和Native等。
```
#### [Mockito](Mockito/README.md)
#### JMockit

## [AI in UT](AI/README.md)
### [EvoSuite](AI/EvoSuite.md)
### [Randoop](AI/Randoop.md)
* JCrasher
* Symbolic PathFinder
* Java PathFinder
* jCute - Java Concolic Unit Testing Engine
* RecGen

## Reference
* [JUnit4 和 TestNG](https://www.yiibai.com/testng/junit-vs-testng-comparison.html)
