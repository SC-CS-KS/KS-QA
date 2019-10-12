# 智能单元测试

## [jCUTE - Java Concolic Unit Testing Engine](https://github.com/osl/jcute)
```md
自动为Java程序生成单元测试。 
Concolic执行将随机的具体执行与符号执行和自动约束求解相结合。
通过符号执行，jCUTE 可以辨别导致不同执行路径的输入。
随机具体执行有助于克服约束求解器的局限性，例如无法分析系统调用或无法求解非线性整数方程的一般系统。
通过这种组合，jCUTE 能够生成在实际Java程序中执行许多不同执行路径的测试用例。
```
```md
jCUTE 支持多线程程序。
它可以通过系统的时间表探索来发现种族状况和僵局。
```
## [Symbolic PathFinder](https://github.com/SymbolicPathFinder/jpf-symbc)

## [Java PathFinder](https://github.com/javapathfinder/jpf-core)

## [JCrasher - An automatic robustness tester for Java](http://ranger.uta.edu/~csallner/jcrasher/)
```md
JCrasher是用于Java代码的自动鲁棒性测试工具。 
JCrasher检查一组Java类的类型信息，并构建代码片段，这些代码片段将创建不同类型的实例，以测试随机数据下公共方法的行为。
JCrasher试图通过使被测程序“崩溃”来检测错误-引发未声明的运行时异常。
尽管一般而言，随机测试方法有很多局限性，但它也具有全自动的优势：
    除了在线检查已导致崩溃的测试用例之外，无需任何监督。
与其他类似的商业和研究工具相比，JCrasher提供了一些新颖之处：
JCrasher过渡性地分析方法，确定每个测试方法的参数空间的大小，并选择参数组合，从而随机选择测试用例，并考虑分配给测试的时间
JCrasher定义了启发式方法，用于确定应将Java异常视为程序错误还是JCrasher提供的输入违反了代码的前提条件
JCrasher包括对有效撤销先前测试引入的所有状态更改的支持
JCrasher为流行的Java测试工具JUnit生成测试文件
JCrasher可以集成在Eclipse IDE中
```

## [RecGen](https://sites.google.com/site/recgentool/)
```md
RecGen是具有MUT感知序列推荐功能的随机单元测试生成工具。 
RecGen以JUnit格式自动为Java类创建单元测试。
```

## [ReCrash - 通过保留对象状态使软件故障可重现](http://groups.csail.mit.edu/pag/reCrash/)
```md
如果无法重现软件故障，很难修复。然而，再现故障通常是困难且耗时的。
本文提出了一种新颖的技术ReCrash，该技术可生成可重现给定程序故障的多个单元测试。
在目标程序的每次执行期间，ReCrash都会将方法参数的部分副本存储在内存中。
如果程序失败（例如崩溃），则ReCrash使用保存的信息来创建重现失败的单元测试。

我们介绍ReCrashJ，这是Java的ReCrash的实现。 
ReCrashJ从Javac，SVNKit，Eclipsec和BST复制了真实的崩溃。 
ReCrashJ是高效的，产生了13％-64％的性能开销。
如果此开销是不可接受的，则ReCrashJ的另一模式的开销可忽略不计，直到发生崩溃为止，而开销为0％-1.7％，直到再次发生崩溃为止，此时将生成测试用例。
```

## [JWalk](http://staffwww.dcs.shef.ac.uk/people/A.Simons/jwalk/)
```md
JWalk是用于懒惰，系统的单元测试的工具套件。
功能强大的JWalkTester工具对程序员提供的任何已编译Java类进行有边界的详尽测试。
它测试是否完全符合惰性规范，该规范是通过静态，动态分析以及程序员提供的提示从代码中即时推断出来的。

懒惰的系统单元测试基于懒惰规范的两个概念，其中随着类设计的发展，类的预期规范会逐渐稳定；
系统测试是对对象的整个状态空间进行详尽测试符合规范。
测试方法针对敏捷方法社区，对于他们而言，生产代码和保存的测试是唯一持久的工件。无需预先生成正式规范。
与其他测试方法相比，JWalking的优势在于，该工具可以自动推断程序员需要提供的测试用例，以确保推断出的规范的完整状态和过渡范围。
这些工具会自动构造并显示这些测试用例，从而节省了程序员的时间和精力。
```
* JWalk与JUnit
```md
通过与JUnit专业测试人员的测试创作进行直接比较，JWalk工具可以在相同的投入时间和精力下测试多达两个数量级的案例！
这是因为JWalk更好地利用了测试自动化：
JUnit测试人员必须手工设计合适的测试，这很困难且容易出错；
JUnit工具仅使测试的重复执行自动化；
保存的回归测试无法执行稍后介绍的新行为。

JWalk工具系统地提出了所有重要的测试案例；
JWalk测试人员只需确认测试结果的一部分即可；
JWalk工具可以预测更多测试用例的测试结果；
类的行为发生更改后，JWalk工具会生成新的测试。
```
```md
JWalk工具通过提出甚至专家都无法发现的案例，努力从测试人员那里思考正确的测试案例。
当通过子类修改或扩展测试类时，JWalk会准确地生成本地和继承方法的所有新颖交错组合所需要的那些新测试用例。
这比使用保存的JUnit测试套件进行回归测试更具区分性。
最终，训练有素的测试Oracle能够检测到对测试类代码进行的每个突变。 
JWalk为不想编写正式规范的程序员提供了基于规范的一致性测试的全部功能！
```
## [Korat](http://korat.sourceforge.net/)
```md
Korat 用于基于约束的Java程序生成结构复杂的测试输入。

结构复杂意味着输入是结构性的（例如，用链接的数据结构表示），
并且必须满足与该结构的各个部分相关的复杂约束。例如，链接的数据结构的不变量。
```