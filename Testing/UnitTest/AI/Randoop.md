# [Randoop](https://github.com/randoop/randoop)

[Randoop Home](https://randoop.github.io/randoop/)

```md
Randoop 是Java的单元测试生成器，它会自动以JUnit格式为被测试类创建单元测试。
Randoop 使用反馈导向的随机测试生成方法。
Randoop 可以同时进行回归测试和错误查找测试。
该工具自2007年问世以来一直在不断发展。这是一个强大且可靠的命令行工具，并且还存在Eclipse插件。
```
## How does Randoop work?
```md
Randoop 使用反馈定向的随机测试生成来生成单元测试。
    该技术伪随机地但巧妙地为被测类生成了方法/构造函数调用的序列。 
Randoop 执行所创建的序列，并使用执行结果来创建断言来捕获程序的行为。 
Randoop 根据代码序列和断言创建测试。

Randoop 可用于两个目的：在程序中查找错误，以及创建回归测试以警告您将来是否更改程序的行为。

Randoop 将测试生成和测试执行相结合，从而产生了一种高效的测试生成技术。 
Randoop 甚至在包括Sun和IBM的JDK和核心.NET组件在内的广泛使用的库中也揭示了以前未知的错误。 
Randoop 继续用于工业领域，例如ABB公司。
```


