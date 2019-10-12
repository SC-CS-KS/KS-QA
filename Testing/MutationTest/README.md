# 变异测试（Mutation Testing）
```md
怎么知道您的测试套件“足够好”？
最好的方法之一就是突变测试，变异测试将人为的缺陷（变异）植入程序中，并检查您的测试套件是否找到了它们，如果不是，则表明您的测试套件还不够。
```
```md
变异测试通过将小故障插入程序并测量测试套件检测到它们的能力来评估测试套件的效率。

```
```md
尽管有效，但突变测试有两个问题。
首先，它需要大量的计算资源才能一次又一次地运行测试套件。
其次，更糟糕的是，对程序进行的更改可以使程序的语义保持不变-从而无法通过任何测试检测到。
    此类等效突变体可作为假阳性。必须手动评估和隔离它们，这是非常繁琐的任务。
```

## [Javalanche - Efficient Mutation Testing for Java ](http://javalanche.org/)
[Javalanche - Github](https://github.com/david-schuler/javalanche)
```md
用于Java程序变异测试的Javalanche框架解决了效率问题和等效变异问题。
avalanche是专为从根本上提高效率而构建的，可以直接处理字节代码，并可以对比早期研究对象大几个数量级的程序进行突变测试。
```

## MuTest
```md
使用突变分析来推动自动测试用例的生成。
使用结构覆盖率和突变分析来指导测试用例生成的主要区别是，突变不仅表明测试位置，还有助于确定应检查的内容。
MuTest 生成测试套件，其中包括有效检测突变体的断言。
MuTest 已集成到 EvoSuite 工具中。
```

## [PITest](http://pitest.org/)
[PITest - Github](https://github.com/hcoles/pitest)
```md
PIT 是最先进的突变测试系统，为 Java 和 jvm 提供金标准测试覆盖。它快速、可扩展，并与现代测试和构建工具集成。
```
[Mutation Testing with PITest](https://www.baeldung.com/java-mutation-testing-with-pitest)

## Reference
### [Awesome Mutation testing](https://github.com/theofidry/awesome-mutation-testing)
