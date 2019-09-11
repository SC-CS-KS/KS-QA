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
         * [<a href="http://meetspock.appspot.com/" rel="nofollow">Spock Web Console</a>【Spock 在线控制台】](#spock-web-consolespock-在线控制台)
         * [Spock Example Project 【Spock 样例工程】](#spock-example-project-spock-样例工程)
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

### [Spock Web Console](http://meetspock.appspot.com/)【Spock 在线控制台】
Spock Web 控制台是一个在线 查看、编辑、运行、发布 Spock 测试脚本的网站，
它是一个不用做任何付出就能玩转Spock的完美场所。
所以赶紧去运行一下 [“Hello, Spock!” ](http://meetspock.appspot.com/edit/9001)吧！

### Spock Example Project 【Spock 样例工程】
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

### Fields

### Fixture Methods

#### Invocation Order

### Feature Methods

#### Blocks

### Helper Methods
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
