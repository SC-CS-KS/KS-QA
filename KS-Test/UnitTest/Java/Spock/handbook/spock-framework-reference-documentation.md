# [Spock Framework Reference Documentation](http://spockframework.github.io/spock/docs)
```
Peter Niederwieser, Leonard Brünings, The Spock Framework Team Version 1.3
```

Table of Contents
=================

   * [<a href="http://spockframework.github.io/spock/docs" rel="nofollow">Spock Framework Reference Documentation</a>](#spock-framework-reference-documentation)
   * [Table of Contents](#table-of-contents)
      * [Introduction 【Spock 介绍】](#introduction-spock-介绍)
      * [Getting Started](#getting-started)
         * [Spock Web Console【Spock 在线控制台】](#spock-web-consolespock-在线控制台)
         * [Spock Example Project【Spock 样例工程】](#spock-example-project-spock-样例工程)
      * [Spock Primer [Spock 进阶]](#spock-primer-spock-进阶)
         * [Terminology 术语](#terminology-术语)
         * [Imports 导入](#imports-导入)
         * [Specification](#specification)
         * [Fields](#fields)
         * [Fixture Methods](#fixture-methods)
            * [Invocation Order](#invocation-order)
         * [Feature Methods](#feature-methods)
            * [Blocks](#blocks)
         * [Helper Methods](#helper-methods)
         * [Using with for expectations](#using-with-for-expectations)
         * [Using verifyAll to assert multiple expectations together](#using-verifyall-to-assert-multiple-expectations-together)
         * [Specifications as Documentation](#specifications-as-documentation)
         * [Extensions](#extensions)
         * [Comparison to JUnit](#comparison-to-junit)
      * [Data Driven Testing 数据驱动测试](#data-driven-testing-数据驱动测试)
         * [Introduction](#introduction)
         * [Data Tables 数据表格](#data-tables-数据表格)
         * [Isolated Execution of Iterations](#isolated-execution-of-iterations)
         * [Sharing of Objects between Iterations](#sharing-of-objects-between-iterations)
         * [Syntactic Variations](#syntactic-variations)
         * [Reporting of Failures](#reporting-of-failures)
         * [Method Unrolling](#method-unrolling)
         * [Data Pipes](#data-pipes)
         * [Multi-Variable Data Pipes](#multi-variable-data-pipes)
         * [Data Variable Assignment](#data-variable-assignment)
         * [Combining Data Tables, Data Pipes, and Variable Assignments](#combining-data-tables-data-pipes-and-variable-assignments)
         * [Number of Iterations](#number-of-iterations)
         * [Closing of Data Providers](#closing-of-data-providers)
         * [More on Unrolled Method Names](#more-on-unrolled-method-names)
      * [Interaction Based Testing 基于交互的测试](#interaction-based-testing-基于交互的测试)
         * [Creating Mock Objects 创建Mock对象](#creating-mock-objects-创建mock对象)
         * [Default Behavior of Mock Objects](#default-behavior-of-mock-objects)
         * [Injecting Mock Objects into Code Under Specification](#injecting-mock-objects-into-code-under-specification)
         * [Mocking](#mocking)
            * [Interactions](#interactions)
            * [Cardinality](#cardinality)
            * [Target Constraint](#target-constraint)
            * [Method Constraint](#method-constraint)
            * [Argument Constraints](#argument-constraints)
            * [Matching Any Method Call](#matching-any-method-call)
            * [Strict Mocking](#strict-mocking)
            * [Where to Declare Interactions](#where-to-declare-interactions)
            * [Declaring Interactions at Mock Creation Time](#declaring-interactions-at-mock-creation-time)
            * [Grouping Interactions with Same Target](#grouping-interactions-with-same-target)
            * [Mixing Interactions and Conditions](#mixing-interactions-and-conditions)
            * [Explicit Interaction Blocks](#explicit-interaction-blocks)
            * [Scope of Interactions](#scope-of-interactions)
            * [Verification of Interactions](#verification-of-interactions)
            * [Invocation Order](#invocation-order-1)
            * [Mocking Classes](#mocking-classes)
         * [Stubbing](#stubbing)
            * [Returning Fixed Values](#returning-fixed-values)
            * [Returning Sequences of Values](#returning-sequences-of-values)
            * [Computing Return Values](#computing-return-values)
            * [Performing Side Effects](#performing-side-effects)
            * [Chaining Method Responses](#chaining-method-responses)
         * [Combining Mocking and Stubbing](#combining-mocking-and-stubbing)
         * [Other Kinds of Mock Objects](#other-kinds-of-mock-objects)
            * [Stubs](#stubs)
            * [Spies](#spies)
            * [Partial Mocks](#partial-mocks)
         * [Groovy Mocks](#groovy-mocks)
            * [Mocking Dynamic Methods](#mocking-dynamic-methods)
            * [Mocking All Instances of a Type](#mocking-all-instances-of-a-type)
            * [Mocking Constructors](#mocking-constructors)
            * [Mocking Static Methods](#mocking-static-methods)
         * [Advanced Features](#advanced-features)
            * [A la Carte Mocks](#a-la-carte-mocks)
            * [Detecting Mock Objects](#detecting-mock-objects)
         * [Further Reading](#further-reading)
      * [Extensions](#extensions-1)
         * [Spock Configuration File](#spock-configuration-file)
         * [Built-In Extensions](#built-in-extensions)
         * [Third-Party Extensions](#third-party-extensions)
         * [Writing Custom Extensions](#writing-custom-extensions)
      * [Modules](#modules)
         * [Guice Module](#guice-module)
         * [Spring Module](#spring-module)
         * [Tapestry Module](#tapestry-module)
         * [Unitils Module](#unitils-module)
         * [Grails Module](#grails-module)
      * [Release Notes](#release-notes)
      * [Migration Guide](#migration-guide)

## Introduction 【Spock 介绍】
Spock 是运用于 Java and Groovy 应用程序的测试框架。
它美丽而富有表现力的规范说明语言使得它从众多的测试框架中脱颖而出。
由于基于JUnit执行器，使得Spock与大多数IDE，构建工具和持续集成服务器保持兼容。
Spock的灵感来自JUnit，jMock，RSpec，Groovy，Scala，Vulcans 和其他一些优秀的框架。

## Getting Started
这部分会展示 Spock 如何起步，可以说是比较简单的。

### Spock Web Console【Spock 在线控制台】
[Spock Web Console](http://meetspock.appspot.com/) 是一个在线 查看、编辑、运行、发布 Spock 测试脚本的网站，
它是一个不用做任何付出就能玩转Spock的完美场所。
所以赶紧去运行一下 [“Hello, Spock!” ](http://meetspock.appspot.com/edit/9001)吧！

### Spock Example Project【Spock 样例工程】
如果想在本地环境尝试 Spock，可以从 GitHub 下载[ “ Spock Example Project”](https://github.com/spockframework/spock-example)，
它无需你做任何的设置，就可用使用 Ant，Gradle和Maven运行。
使用一个简单的命令就可以使用Gradle启动或者在Eclipse和IDEA中运行。具体可以查看README文件中的详细介绍.

## Spock Primer [Spock 进阶]
本章假定你有一定的 Groovy 和 单元测试 基础。
如果你是一个Java开发者而没有听说过 Groovy，别担心 —— 你会觉得 Groovy 十分熟悉。
事实上，Groovy一个主要的设计目标就是成为与Java兼容的脚本语言。
只要你查阅下 [Groovy 官方文档](http://groovy-lang.org/documentation.html)，你就会喜欢上它。

本章的目标是教会你编写一些真实的 Spock 描述脚本（specification），并激起你更大的兴趣。

参考：
[Groovy](http://groovy-lang.org/)
[单元测试](http://en.wikipedia.org/wiki/Unit_testing)

### Terminology 术语
首先让我们来做一些定义：Spock 让你编写 描述性脚本 来描述 某个被测系统的期望功能（属性、性质）。
被测系统可以是一个类或一个应用，也被称为 基于描述的系统（system under specification or SUS）。
对于一个功能的描述从SUS及其协作者的特定快照开始;此快照被称为这个功能的 fixture。

以下部分将引导你完成可能组成Spock描述脚本的所有构建块。典型描述性脚本一般仅使用它们的子集。

### Imports 导入
```java
import spock.lang.*
```
包 spock.lang 包含了编写描述性脚本的大部分重要的类。

### Specification
```groovy
class MyFirstSpecification extends Specification {
  // fields
  // fixture methods
  // feature methods
  // helper methods
}
```
一个测试描述对应于一个 Groovy 类，这个类必须继承 spock.lang.Specification。
测试描述的按照它所描述的功能来命名。
例如：CustomerSpec, H264VideoPlayback, and ASpaceshipAttackedFromTwoSides，
对于一个测试描述这些都是合理的命名。

测试描述类通常包含许多对于编写描述性脚本有用的方法，同时它也指明了 JUnit 如何 Sputnik 来运行描述性脚本。
Sputnik 使得 Spock specifications 可以运行于 大多数现代 Java 集成开发环境 和 构建工具。
### Fields
```groovy
def obj = new ClassUnderSpecification()
def coll = new Collaborator()
```

```groovy
@Shared res = new VeryExpensiveResource()
```
有时你可能需要在几个功能方法之间共享对象。
例如，对象创建很昂贵时，或者你需要功能方法之间有交互。这时可以使用 @Shared 标记字段。
最好能在定义字段的同时初始化。（从语义上讲，这相当于在setupSpec（）方法的最开始初始化字段。）

```groovy
static final PI = 3.141592654
```
静态字段应用只用于常量，共享字段是最优的选择，因为他们对共享语法的定义更明确。

### Fixture Methods
```groovy
def setupSpec() {}    // runs once -  before the first feature method
def setup() {}        // runs before every feature method
def cleanup() {}      // runs after every feature method
def cleanupSpec() {}  // runs once -  after the last feature method
```
固定方法（Fixture Methods）负责配置或清除测试环境。
通常最好为每个功能方法都增加 setup() and cleanup() 固定方法。

所有的固定方法都是可选的。

有时候，多个功能方法共享一个 Fixture 是有意义的，通过共享字段和setupSpec()、cleanupSpec() 方法的结合来实现。
注意，setupSpec() 和 cleanupSpec() 方法中不能引用实例字段，除它们非被 @Shared 标记。

#### Invocation Order
如果在子类中重写了 setUp()方法，父类的setup（）将在子类的setup（）之前运行。
而 cleanup() 则是相反的，子类cleanup()将先执行。
setupSpec() 和 setUp()一致，cleanupSpec()和cleanup()一致。
不需要显式调用super.setup（）或super.cleanup（），因为Spock将默认会按照继承的层次结构查找和执行fixture方法。

调用顺序：
super.setupSpec
sub.setupSpec
super.setup
sub.setup
feature method
sub.cleanup
super.cleanup
sub.cleanupSpec
super.cleanupSpec

### Feature Methods
```groovy
def "pushing an element on the stack"() {
  // blocks go here (块结构)
}
```
Feature methods 是 specification 的核心。它描述了你期望的系统功能，一般情况下用一个字符串来命名。
可以使用你喜欢的任意字符为 Feature methods 取一个最合适的名字。

从概念上讲，一种 Feature method 包括四个阶段：
1. Set up
2. 为被测对象提供一个激励（stimulus）
3. 描述期望的响应
4. Clean up

第一个和第四个阶段是可选的，除非是在交互式Feature Method中，否则第二、三个阶段一般都存在，并且有可能出现不止一次。

#### Blocks 
Spock 内置支持 Feature method 的每个阶段。为此，Feature method 被结构化为 多个块结构。
块结构以一个标签开始，并延伸到下一个块结构开始或方法的结尾。
有6种块结构：
given, when, then, expect, cleanup, where
方法开头和第一个显式块之间的任何语句都属于隐式 given 块。

Feature method 必须至少有一个显式（即标记）块。
实际上，显式块的存在才使得一个方法成为 feature method。块将方法划分为不同的部分，并且不能嵌套。

![](_pic/Spock-blocks-phases.png) 

上图展示了块 和 各个 概率阶段 的映射，where 块比较特别，后续你会看到，我们先来详细了解下其他块。

* Given Blocks (given 块结构)
```groovy
given:
def stack = new Stack()
def elem = "push me"
```
given块 是为要描述的功能进行设置的地方。在它之前可能没有其它块，也可能不会重复。
given块 没有任何特殊的语义。
given: 标志可以省略，从而产生一个隐式的given块。
期初，别名 setup:是首选的块名称，但是使用 given: 常常更能得到一个更可读的  Feature method 描述。
(参考 [Specifications as Documentation](#specifications-as-documentation))

* When and Then Blocks
```groovy
when:   // stimulus
then:   // response
```
when 和 then 块常常一起出现，它们描述了一个 stimulus 和一个期望的响应。
而when块可能包含任意代码时，then 块仅限于条件，异常条件，交互和变量定义。
一个 feature method 可能包含多组 when-then。

* Conditions
条件（Conditions ）描述一个期望的状态，比较像JUnit的断言。
但是，条件是作为普通布尔表达式编写的，不需要断言API。
（更确切地说，条件也可能产生非布尔值，然后根据Groovy真值进行评估。）
让我们看一些conditions的实例：
```groovy
when:
stack.push(elem)

then:
!stack.empty
stack.size() == 1
stack.peek() == elem
```
小建议 :
尽量保持每个Feature method的较少的条件。1-5个是一个很好的实践。
如果多于这个范围，问问自己是否一次指定了多个不相关的功能。如果是的，则需要对 feature method  进行分解。
如果你的条件仅在值上有所不同，请考虑使用[数据表](#data-tables-数据表格)。

如果违反条件，Spock会提供什么样的反馈？
让我们来尝试改变第二个条件为 stack.size() == 2，以下是结果：

```md
Condition not satisfied:

stack.size() == 2
|     |      |
|     1      false
[push me]
```
你会看到，在验证条件期间，Spock会捕获产生的所有值，并以易读的形式呈现它们。看起来很不错，是不是？

* * Implicit and explicit conditions 隐式和显式条件 

条件是then块和expect块的基本要素。
除了调用 void方法 和 被分类为交互的表达式 之外，这些块中的所有顶级表达式都被隐式地视为条件。
要在其他地方使用条件，需要使用Groovy的assert关键字指定它们：
```groovy
def setup() {
  stack = new Stack()
  assert stack.empty
}
```
如果一个显式条件被违反，它将产生与隐式条件相同的良好的诊断消息。

* * Exception Conditions 异常条件

异常条件用于描述when块应该抛出异常。它们使用thrown()方法定义，传入预期的异常类型。
例如，如果从空堆弹出元素，应该抛出 EmptyStackException，要描述这个场景，可以编写以下内容：
```groovy
when:
stack.pop()

then:
thrown(EmptyStackException)
stack.empty
```
你看到，异常条件可能会跟随其他条件（甚至其他块），这对于具体说明异常的预期内容特别有用。
要访问异常，首先将其绑定到变量：
```groovy
when:
stack.pop()

then:
def e = thrown(EmptyStackException)
e.cause == null
```
或者可以对上面的语法做一些改变：
```groovy
when:
stack.pop()

then:
EmptyStackException e = thrown()
e.cause == null
```
上面的语法有两个小优点：
首先，异常变量是强类型的，这使IDE更容易提供代码补全。
其次，条件语句读起来更像一个句子（'然后 一个 EmptyStackException 异常被抛出'）。
请注意，如果没有向thrown()方法传递异常类型，则从左侧的变量类型推断出它。

有时候我们需要传达不应该抛出异常，例如，让我们尝试表示HashMap应该接受一个空键：
```groovy
def "HashMap accepts null key"() {
  setup:
  def map = new HashMap()
  map.put(null, "elem")
}
```
以上的方法有效，但没有透露代码的意图。
Did someone just leave the building before he had finished implementing this method?
条件在哪里？实际上可以做的更好：
```groovy
def "HashMap accepts null key"() {
  given:
  def map = new HashMap()

  when:
  map.put(null, "elem")

  then:
  notThrown(NullPointerException)
}
```
通过使用 notThrown()，使得对 NullPointerException 异常不应该被抛出的描述更加清晰。
（根据Map.put()的契约，对于不支持 null 值作为键的map，这样描述条件是正确的做法。）[？？？]
然而，如果Map.put()抛出任何其他异常，该方法还是会失败。

* * Interactions

条件描述对象的状态，而交互则描述对象如何相互通信。
交互和基于交互的测试在单独的章节中描述，因此我们仅在此给出一个快速示例：
假设我们想要描述从发布者到其订阅者的事件流。
```groovy
def "events are published to all subscribers"() {
  given:
  def subscriber1 = Mock(Subscriber)
  def subscriber2 = Mock(Subscriber)
  def publisher = new Publisher()
  publisher.add(subscriber1)
  publisher.add(subscriber2)

  when:
  publisher.fire("event")

  then:
  1 * subscriber1.receive("event")
  1 * subscriber2.receive("event")
}
```

* Expect Blocks

* Cleanup Blocks

* Where Blocks


### Helper Methods
```groovy
def "offered PC matches preferred configuration"() {
  when:
  def pc = shop.buyPc()

  then:
  pc.vendor == "Sunny"
  pc.clockRate >= 2333
  pc.ram >= 4096
  pc.os == "Linux"
}
```
### Using with for expectations
### Using verifyAll to assert multiple expectations together
### Specifications as Documentation
### Extensions
### Comparison to JUnit

## Data Driven Testing 数据驱动测试
### Introduction
### Data Tables 数据表格
### Isolated Execution of Iterations
### Sharing of Objects between Iterations
### Syntactic Variations 
### Reporting of Failures 
### Method Unrolling
### Data Pipes
### Multi-Variable Data Pipes
### Data Variable Assignment
### Combining Data Tables, Data Pipes, and Variable Assignments
### Number of Iterations
### Closing of Data Providers
### More on Unrolled Method Names

## Interaction Based Testing 基于交互的测试
### Creating Mock Objects 创建Mock对象
### Default Behavior of Mock Objects
### Injecting Mock Objects into Code Under Specification

### Mocking
#### Interactions
#### Cardinality
#### Target Constraint
#### Method Constraint
#### Argument Constraints
#### Matching Any Method Call
#### Strict Mocking
#### Where to Declare Interactions
#### Declaring Interactions at Mock Creation Time
#### Grouping Interactions with Same Target
#### Mixing Interactions and Conditions
#### Explicit Interaction Blocks
#### Scope of Interactions
#### Verification of Interactions
#### Invocation Order
#### Mocking Classes

### Stubbing
#### Returning Fixed Values
#### Returning Sequences of Values
#### Computing Return Values
#### Performing Side Effects
#### Chaining Method Responses

### Combining Mocking and Stubbing
### Other Kinds of Mock Objects
#### Stubs
#### Spies
#### Partial Mocks

### Groovy Mocks
#### Mocking Dynamic Methods
#### Mocking All Instances of a Type
#### Mocking Constructors
#### Mocking Static Methods

### Advanced Features
#### A la Carte Mocks
#### Detecting Mock Objects

### Further Reading

## Extensions
### Spock Configuration File
### Built-In Extensions
### Third-Party Extensions
### Writing Custom Extensions

## Modules
### Guice Module
### Spring Module
### Tapestry Module
### Unitils Module
### Grails Module

## Release Notes

## Migration Guide
