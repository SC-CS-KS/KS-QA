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

expect块比 then 块更有限，因为它可能只包含条件和变量定义。
在单个表达式中描述 stimulus 和 预期响应 情况下，expect 块非常有用，它的表述会更自然。
例如，比较以下两次描述 Math.max() 方法：
```groovy
when:
def x = Math.max(1, 2)

then:
x == 2
```
```groovy
expect:
Math.max(1, 2) == 2
```
尽管两个代码片段在语义上是等效的，但第二种表述显然更合适。
作为指导原则，一般使用when-then来描述具有副作用的方法，而 expect 用来描述纯粹的功能方法。

```md
建议： 利用像any（）和every（）这样的 Groovy JDK 方法来创建更具表现力和简洁的条件。
```
* Cleanup Blocks

```groovy
given:
def file = new File("/some/path")
file.createNewFile()

// ...

cleanup:
file.delete()
```
cleanup 块后面只能有where块，并且可能不会重复。
和 cleanup 方法一样，它被用户释放 feature method 使用的任何资源。
即使 在 cleanup 块 前面的 某个 feature method 部分产生了异常，cleanup 块也会运行。
因此必须对 cleanup 块进行防御性编码，在最坏的情况下，它必须优雅地处理feature method中的
第一个语句抛出异常的情况，并且所有局部变量仍然具有其默认值。

```md
提示：Groovy的安全解除引用运算符（foo？.bar（））简化了编写防御性代码的过程。
```

对象级 specifications 通常不需要清理方法，因为它们使用的唯一资源是内存，它由垃圾收集器自动回收。
但是，更粗粒度的 specifications 可能会使用clean块来清理文件系统，关闭数据库连接或关闭网络服务。

```md
如果规范的设计方式使其所有要素方法都需要相同的资源，请使用cleanup（）方法;否则，更喜欢清理块。
相同的权衡适用于setup（）方法和给定的块。
```

* Where Blocks

where块 始终位于方法的最后，并且可能不会重复。它用于编写数据驱动的特征方法。
为了让你了解如何完成此操作，请查看以下示例：
```groovy
def "computing the maximum of two numbers"() {
  expect:
  Math.max(a, b) == c

  where:
  a << [5, 3]
  b << [1, 9]
  c << [5, 9]
}
```
这个 where块 有效地创建了 feature method 的两个“版本”：一个是a是5，b是1，c是5，另一个a是3，b是9，c是9。
虽然 where块 是在最后声明的，但是是在包含它的 feature method 运行之前评估的。
where块 会在数据驱动测试章节中进一步说明。

### Helper Methods

有时，feature method 会变大而包含大量重复代码。在这种情况下，引入一个或多个辅助方法是有意义的。
辅助方法的两个好选择是 setup/cleanup 逻辑 和 复杂条件。前者比较简单，让我们来看看复杂条件：
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
如果你恰好是计算机爱好者，你喜欢的PC配置可能非常详细，或者你可能想要比较来自许多不同商店的优惠。
因此，让我们分解出条件：
```groovy
def "offered PC matches preferred configuration"() {
  when:
  def pc = shop.buyPc()

  then:
  matchesPreferredConfiguration(pc)
}

def matchesPreferredConfiguration(pc) {
  pc.vendor == "Sunny"
  && pc.clockRate >= 2333
  && pc.ram >= 4096
  && pc.os == "Linux"
}
```
新的辅助方法 matchesPreferredConfiguration（）返回一个布尔表达式的结果。(return 关键字在Groovy中是可选的。)
这很好，除了给出的结果不够明确：
```md
Condition not satisfied:

matchesPreferredConfiguration(pc)
|                             |
false 
```
这不是很有帮助。幸运的是，我们可以做得更好：
```groovy
void matchesPreferredConfiguration(pc) {
  assert pc.vendor == "Sunny"
  assert pc.clockRate >= 2333
  assert pc.ram >= 4096
  assert pc.os == "Linux"
}
```
将条件分解为辅助方法时，需要考虑两点：
首先，必须使用assert关键字将隐式条件转换为显式条件。
其次，辅助方法必须具有返回类型void。否则，Spock可能会将返回值解释为失败条件，这不是我们想要的。

正如期望，改进的辅助方法告诉我们详细的出错信息：
```md
Condition not satisfied:

assert pc.clockRate >= 2333
       |  |         |
       |  1666      false
       ...
```
最后的建议：尽管代码重用通常是件好事，但不要太过度。
请注意，使用fixture和helper方法会增加 feature methods 之间的耦合。
如果重用过多或错误的代码，specifications 会变得难以维护和修改。

### Using with for expectations

作为上述辅助方法的替代，可以使用with（target，closure）方法与待校验对象上进行交互，这在 then 和 expect 块中特别有用。
```groovy
def "offered PC matches preferred configuration"() {
  when:
  def pc = shop.buyPc()

  then:
  with(pc) {
    vendor == "Sunny"
    clockRate >= 2333
    ram >= 406
    os == "Linux"
  }
}
```
与使用辅助方法时不同，不需要显式的断言语句来进行正确的错误报告。

当验证 mock 时，with语句也可以避免冗长的验证语句。
```groovy
def service = Mock(Service) // has start(), stop(), and doWork() methods
def app = new Application(service) // controls the lifecycle of the service

when:
app.run()

then:
with(service) {
  1 * start()
  1 * doWork()
  1 * stop()
}
```
有时IDE会很难确定目标的类型，在这种情况下，可以使用 with(target，type，closure) 来手动指定目标类型。

### Using verifyAll to assert multiple expectations together

一般情况下，在第一次断言失败时我们就认为测试失败。
但有时候，在测试失败之前收集更多断言的失败信息是有帮助的，这种行为也称为（soft assertions）软断言。

verifyAll 的使用方式和 with 类似：
```groovy
def "offered PC matches preferred configuration"() {
  when:
  def pc = shop.buyPc()

  then:
  verifyAll(pc) {
    vendor == "Sunny"
    clockRate >= 2333
    ram >= 406
    os == "Linux"
  }
}
```
verifyAll 也可以不用绑定验证目标：
```groovy
​expect:
  verifyAll {
    2 == 2
    4 == 4
```

verifyAll 与 with 一样，也可以选择为IDE定义类型提示。

### Specifications as Documentation

精心编写的 Specifications 是宝贵的信息来源。
特别是高规格的 Specifications 不仅仅是开发人员（架构师，领域专家，客户等），而是面向更广泛受众的。
不仅仅从 Specifications的名字 和 功能 来提供信息，而以自然语言提供更多信息是有意义的。
因此，Spock提供了一种将文本描述附加到块的方法：
```groovy
given: "open a database connection"
// code goes here
```
用 and: 标签描述在逻辑上不相同的块（block）的各个部分。
```groovy
given: "open a database connection"
// code goes here

and: "seed the customer table"
// code goes here

and: "seed the product table"
// code goes here
```
可以在 feature method 的任何（顶层）位置，利用and:插入一段描述，这不会更改feature method的语义。
在BDD（Behavior Driven Development）中，面向客户的功能（称为故事）使用 given-when-then 格式描述。
Spock使用 given: 标签直接支持这种说明风格：
```groovy
given: "an empty bank account"
// ...

when: "the account is credited $10"
// ...

then: "the account's balance is $10"
// ...
```
块描述不仅存在于源代码中，还可用于Spock运行时。
规划好块描述能够增强诊断信息，以及所有利益相关者具有共同理解的文本报告。

### Extensions
正如我们所看到的，Spock提供了许多用于编写 Specification 的功能。
除了这些功能，Spock还提供了一种基于拦截的扩展机制。
扩展由称为指令（directives）的注释激活。目前，Spock支持以下指令注释：
* @Timeout
为 feature or fixture method 设置执行的超时时间。
* @Ignore
忽略带有此注解的任何 feature method。
* @IgnoreRest
将执行携带此注解的任何 feature method，忽略其他 feature methods。
对于快速运行单个方法很有用。
* @FailsWith
期望一个 feature method 突然完成。 
@FailsWith有两个使用场景：
第一，记录无法立即解决的已知错误。
第二，在某些 异常 conditions的无法使用的情况下（比如指定异常conditions的行为），使用 @FailsWith 作为替代。
在所有其他情况下，异常 conditions 更合适。

[Extensions](#extensions-1)章节讲解了如何自定义 指令注解 和 扩展。

### Comparison to JUnit

虽然Spock使用不同的术语，但它的许多概念和特性都受到JUnit的启发。
以下是一个粗略的比较：
| Specification       | Test class                         |
| ------------------- | ---------------------------------- |
| setup()             | @Before                            |
| cleanup()           | @After                             |
| setupSpec()         | @BeforeClass                       |
| cleanupSpec()       | @AfterClass                        |
| Feature             | Test                               |
| Feature method      | Test method                        |
| Data-driven feature | Theory                             |
| Condition           | Assertion                          |
| Exception condition | @Test(expected=…​)                  |
| Interaction         | Mock expectation (e.g. in Mockito) |

## Data Driven Testing 数据驱动测试
通常，我们会使用不同的输入和预期结果，多次运行相同的测试代码。 
DDT也成为了Spock最重要的功能之一。

### Introduction
假设我们要指定Math.max方法的行为：
```groovy
class MathSpec extends Specification {
  def "maximum of two numbers"() {
    expect:
    // exercise math method for a few different inputs
    Math.max(1, 3) == 3
    Math.max(7, 4) == 7
    Math.max(0, 0) == 0
  }
}
```
场景简单时，这种实现方式很好，但它也有一些潜在的缺点：
1. 代码和数据是耦合的，不能独立修改
2. 数据无法轻易地自动生成或从外部数据源提取
3. 为了多次执行相同的代码，必须将其复制或提取到单独的方法中
4. 如果发生失败，可能无法立即清楚地知道哪些输入导致失败
5. 多次执行相同的代码不会获得像单独隔离执行那样的好处。

Spock数据驱动测试功能试图解决这些问题。让我们将代码重构为数据驱动的 feature method。
首先，我们引入三个方法参数（称为数据变量）来替换硬编码的整数值：
```groovy
class MathSpec extends Specification {
  def "maximum of two numbers"(int a, int b, int c) {
    expect:
    Math.max(a, b) == c
    ...
  }
}
```
我们已经完成了测试逻辑，但仍然需要提供数据值。
这是在where：块中完成的，它始终位于方法的末尾。在最简单（也是最常见）的情况下，where：块会包含数据表。

### Data Tables 数据表格

数据表是使用一组固定数据集来运行 feature method 的便捷方法：
```groovy
class MathSpec extends Specification {
  def "maximum of two numbers"(int a, int b, int c) {
    expect:
    Math.max(a, b) == c

    where:
    a | b | c
    1 | 3 | 3
    7 | 4 | 7
    0 | 0 | 0
  }
}
```
该表的第一行称为表头，它声明了数据变量。后续行（称为表行）包含相应的值。
针对每一行数据，feature method 将执行一次;我们称之为方法的迭代。
如果迭代失败，仍将执行剩余的迭代，最后将报告所有故障。

数据表必须至少有两列。单列表可以写成：
```groovy
where:
a | _
1 | _
7 | _
0 | _
```

### Isolated Execution of Iterations

迭代与单独隔离执行 feature method 的方式相同，每次迭代彼此隔离，都会获得自己的规范类实例，
并且将分别在每次迭代之前和之后调用setup和cleanup方法。

### Sharing of Objects between Iterations

对象必须保存在@Shared或静态字段中，才能在迭代之间共享。

***注意***
只能在where：块中访问@Shared和static变量。

请注意，这些对象也将与其他方法共享。目前没有很好的方法只在同一方法的迭代之间共享对象。
如果你认为这是一个问题，请考虑将每个方法放入一个单独的 Specification 中，这些 Specifications 可以保存在同一个文件中。
这样可以以某些样板代码为代价实现更好的隔离。

### Syntactic Variations 

以前的代码可以通过几种方式进行调整。
首先，由于where：块已经声明了所有数据变量，因此可以省略方法参数。
其次，输入和预期输出可以用双管符号（||）分开，以便在视觉上有所区分。
经过调整之后的代码为：
```groovy
class MathSpec extends Specification {
  def "maximum of two numbers"() {
    expect:
    Math.max(a, b) == c

    where:
    a | b || c
    1 | 3 || 3
    7 | 4 || 7
    0 | 0 || 0
  }
}
```

### Reporting of Failures 

假设max方法的实现有一个缺陷，其中一个迭代会失败：
```md
maximum of two numbers   FAILED

Condition not satisfied:

Math.max(a, b) == c
    |    |  |  |  |
    |    7  4  |  7
    42         false
```
显而易见的问题是：哪个迭代失败了，它的数据值是多少？
在我们的示例中，不难发现它是第二次失败的迭代。在其他时候，则很难甚至无法确认。
因此，如果Spock不是仅仅报告失败，而能明确说明哪个迭代失败就更好了，这是@Unroll注释的目的。

### Method Unrolling

使用@Unroll注解的方法将独立报告其迭代：
```groovy
@Unroll
def "maximum of two numbers"() {
...
```
* 为什么方法不默认设置为 @Unroll？
```md
一个原因是某些执行环境（特别是IDE）期望被提前告知待测试方法的数量，如果实际数量有变化可能会出现某些问题。
另一个原因是@Unroll可能大大增加了需要报告的测试数量，这并不总是可取的。
```

请注意，unrolling 改变报告，对方法的执行方式没有任何影响。依赖执行环境，输出将类似于：
```md
maximum of two numbers[0]   PASSED
maximum of two numbers[1]   FAILED

Math.max(a, b) == c
    |    |  |  |  |
    |    7  4  |  7
    42         false

maximum of two numbers[2]   PASSED
```

这告诉我们第二次迭代（索引为1）失败。
只需要一点小小的改动，我们可以做得更好：
```groovy
@Unroll
def "maximum of #a and #b is #c"() {
...
```
此方法名称使用占位符（由前导哈希符号（＃）表示）来引用数据变量a，b和c。
在输出中，占位符将替换为具体值：
```md
maximum of 3 and 5 is 5   PASSED
maximum of 7 and 4 is 7   FAILED

Math.max(a, b) == c
    |    |  |  |  |
    |    7  4  |  7
    42         false

maximum of 0 and 0 is 0   PASSED
```
现在我们可以一目了然地看出输入7和4的最大方法失败了。

如果想对这部分内容有更多的了解，可以参考 [More on Unrolled Method Names](#more-on-unrolled-method-names)。

### Data Pipes

数据表不是向数据变量提供值的唯一方法。实际上，数据表只是一个或多个数据管道的语法糖：
```groovy
where:
a << [1, 7, 0]
b << [3, 4, 0]
c << [3, 7, 0]
```
由左移（<<）运算符指示的数据管道将数据变量连接到数据提供者。数据提供者保存变量所有的值，每个迭代一个。 
任何 Groovy 支持的可迭代对象都可以用作数据提供者。
包括Collection，String，Iterable类型的对象，以及实现 Iterable 契约的对象。
数据提供者不一定必须是数据（如集合），他们也可以从数据源（如文本文件，数据库和电子表格，或随机生成数据）获取数据。
数据提供者仅在需要时（在下一次迭代之前）用于查询下一个值。

### Multi-Variable Data Pipes

如果数据提供者每次迭代返回多个值（Groovy 支持的可迭代对象），它就可以同时连接到多个数据变量。
语法有点类似于Groovy多重赋值，但需要用中括号替代小括号：
```groovy
@Shared sql = Sql.newInstance("jdbc:h2:mem:", "org.h2.Driver")

def "maximum of two numbers"() {
  expect:
  Math.max(a, b) == c

  where:
  [a, b, c] << sql.rows("select a, b, c from maxdata")
}
可以使用下划线（_）忽略不感兴趣的数据值：
```groovy
where:
[a, b, _, c] << sql.rows("select * from maxdata")
```

### Data Variable Assignment

数据变量可以直接赋值：
```groovy
where:
a = 3
b = Math.random() * 100
c = a > b ? a : b
```
每次迭代都会重新评估分配。如上所示，赋值的右侧可能引用其他数据变量：
```groovy
where:
row << sql.rows("select * from maxdata")
// pick apart columns
a = row.a
b = row.b
c = row.c
```

### Combining Data Tables, Data Pipes, and Variable Assignments

可以根据需要组合数据表，数据管道和变量分配：
```groovy
where:
a | _
3 | _
7 | _
0 | _

b << [5, 0, 0]

c = a > b ? a : b
```

### Number of Iterations

迭代次数取决于可用的数据量。连续执行相同的方法可以产生不同数量的迭代。
如果数据提供者比其使用者更早耗尽值，则会发生异常。
变量赋值不会影响迭代次数。其中：仅包含赋值的块只产生一次迭代。

### Closing of Data Providers

完成所有迭代后，将对所有数据提供程序调用零参数close方法。

### More on Unrolled Method Names

展开的方法名称类似于Groovy GString，但以下区别除外：
1. 表达式用＃而不是$ 表示，并且${...}语法没有等价物。
2. 表达式仅支持属性访问和零arg方法调用。

给定Person类，具有性名称和年龄属性，以及Person类型的数据变量person，以下是有效的方法名称：
```groovy
def "#person is #person.age years old"() { // property access
def "#person.name.toUpperCase()"() { // zero-arg method call
```
根据Groovy语义，非字符串值（如上面的#person）将转换为字符串。

以下是无效的方法名称：
```groovy
def "#person.name.split(' ')[1]" {  // cannot have method arguments
def "#person.age / 2" {  // cannot use operators
```

如有必要，可以引入其他数据变量来保存更复杂的表达式：
```groovy
def "#lastName"() { // zero-arg method call
  ...
  where:
  person << [new Person(age: 14, name: 'Phil Cole')]
  lastName = person.name.split(' ')[1]
}
```

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
