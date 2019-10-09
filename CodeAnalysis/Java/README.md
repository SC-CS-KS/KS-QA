# Java Code Analysis

=================

   * [Java Code Analysis](#java-code-analysis)
      * [Java 静态代码分析理论基础和主要技术](#java-静态代码分析理论基础和主要技术)
         * [缺陷模式匹配](#缺陷模式匹配)
         * [类型推断](#类型推断)
         * [模型检查](#模型检查)
         * [数据流分析](#数据流分析)
      * [CheckStyle](#checkstyle)
      * [<a href="http://findbugs.sourceforge.net/manual/index.html" rel="nofollow">FindBugs</a>](#findbugs)
      * [<a href="https://pmd.github.io" rel="nofollow">PMD</a>](#pmd)
      * [Jtest](#jtest)
      * [NPE](#npe)
         * [<a href="https://github.com/uber/NullAway">NullAway - NPE 检测工具</a>](#nullaway---npe-检测工具)

## Java 静态代码分析理论基础和主要技术
### 缺陷模式匹配
```md
事先从代码分析经验中收集足够多的共性缺陷模式
	将待分析代码与已有的共性缺陷模式进行模式匹配
	从而完成软件的安全分析
这种方式的优点是简单方便，但是要求内置足够多缺陷模式，且容易产生误报
```
### 类型推断
```md
通过对代码中运算对象类型进行推理
	从而保证代码中每条语句都针对正确的类型执行
这种技术首先将预定义一套类型机制
	包括类 型等价、类型包含等推理规则
		而后基于这一规则进行推理计算
类型推断可以检查代码中的类型错误，简单，高效，适合代码缺陷的快速检测
```
### 模型检查
```md
模型检验建立于有限状态自动机的概念基础之上
	这一理论将被分析代码抽象为一个自动机系统，并且假设该系统是有限状态的、或者是可以通过抽象归 结为有限状态
模型检验过程中
	首先将被分析代码中的每条语句产生的影响抽象为一个有限状态自动机的一个状态
	而后通过分析有限状态机从而达到代码分析的 目的
模型检验主要适合检验程序并发等时序特性
	但是对于数据值域数据类型等方面作用较弱
```
### 数据流分析
```md
数据流分析也是一种软件验证技术
	这种技术通过收集代码中引用到的变量信息，从而分析变量在程序中的赋值、引用以及传递等情况
对数据流进行 分析
	可以确定变量的定义以及在代码中被引用的情况，同时还能够检查代码数据流异常，如引用在前赋值在后、只赋值无引用等。
数据流分析主要适合检验程序中的 数据域特性。
```
## CheckStyle
```md
结果分析
	25 First sentence should end with a period.
		解决方法：你的注释的第一行文字结束应该加上一个"."。
```
```md
Javadoc 注释：检查类及方法的 Javadoc 注释
命名约定：检查命名是否符合命名规范
标题：检查文件是否以某些行开头
Import 语句：检查 Import 语句是否符合定义规范
代码块大小，即检查类、方法等代码块的行数
空白：检查空白符，如 tab，回车符等
修饰符：修饰符号的检查，如修饰符的定义顺序
块：检查是否有空块或无效块
代码问题：检查重复代码，条件判断，魔数等问题
类设计：检查类的定义是否符合规范，如构造函数的定义等问题
```
## [FindBugs](http://findbugs.sourceforge.net/manual/index.html)
```md
WhatIs
	Find Bugs in Java Programs
	 It looks for instances of "bug patterns" --- code instances that are likely to be errors.
```
* Bugs
```md
"Boxed value is unboxed and then immediately reboxed"
	装箱的值被拆箱，然后立刻重新装箱了
		常见的是三目运算时，同时存在基本类型和包装类型
Reliance on default encoding
	依赖于系统编码，虽然方便，但是一旦使用就变成了一个技术债务，因为系统的默认编码是不可预知的
	实例
		
			 String jobSql = new String(BaseEncoding.base64Url().decode(jobSqlEnc));
			 String jobSql = new String(BaseEncoding.base64Url().decode(jobSqlEnc), StandardCharsets.UTF_8);
		str.getBytes()
```
```md
Bad practice 坏的实践：常见代码错误，用于静态代码检查时进行缺陷模式匹配
Correctness 可能导致错误的代码，如空指针引用等
国际化相关问题：如错误的字符串转换
可能受到的恶意攻击，如访问权限修饰符的定义等
多线程的正确性：如多线程编程时常见的同步，线程调度问题。
运行时性能问题：如由变量定义，方法调用导致的代码低效问题。
```
## [PMD](https://pmd.github.io)
```md
可能的 Bugs：检查潜在代码错误，如空 try/catch/finally/switch 语句
未使用代码（Dead code）：检查未使用的变量，参数，方法
复杂的表达式：检查不必要的 if 语句，可被 while 替代的 for 循环
重复的代码：检查重复的代码
循环体创建新对象：检查在循环体内实例化新对象
资源关闭：检查 Connect，Result，Statement 等资源使用之后是否被关闭掉
```
```md
Intellij
	右击项目，并选择“Analyze” > "Analyze Code"
```
```md
An extensible cross-language static code analyzer.
sh /Users/didi/WorkPlace/tools/pmd/pmd-bin-6.9.0/bin/run.sh pmd -d ../../dev/dididata/dp_jobcenter/jobcenter-server/src -R rules.xml -f text
```
## Jtest
```md
可能的错误：如内存破坏、内存泄露、指针错误、库错误、逻辑错误和算法错误等
未使用代码：检查未使用的变量，参数，方法
初始化错误：内存分配错误、变量初始化错误、变量定义冲突
命名约定：检查命名是否符合命名规范
Javadoc 注释：检查类及方法的 Javadoc 注释
线程和同步：检验多线程编程时常见的同步，线程调度问题
国际化问题：
垃圾回收：检查变量及 JDBC 资源是否存在内存泄露隐患
```
## NPE
### [NullAway - NPE 检测工具](https://github.com/uber/NullAway)
