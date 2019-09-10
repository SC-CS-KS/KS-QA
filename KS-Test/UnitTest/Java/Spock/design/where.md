# where
## 参数化测试
### 表格化的测试数据
```md
其中表头为测试方法中要用在断言中的变量名称或者表达式，用|分隔输入参数，用||分隔输入与输出。
这些参数，可以用#参数名的方式在@Unroll描述或者测试方法名里定义，或者在测试方法的参数列表里定义，然后在where块中使用。
```
```groovy
@Unroll
class DataDrivenTest extends Specification {
def "minimum of #a and #b is #c"() {
    expect:
    Math.min(a, b) == c

    where:
    a | b || c
    3 | 7 || 3
    5 | 4 || 5
    9 | 9 || 9
}
```
* @Unroll
```md
1. 每行输入都会被当成一个独立的测试来运行，甚至可以让每个测试运行单独使用自定义字符串进行命名
2. 如果不加注解，则是在一个测试中循环执行这些输入。
```
### 数据管道
```md
它是表格数据迭代存取的另一种方式，对管道数据用一次，将会跳到下一个值。
通过left-shift (<<) 操作符号，连接一个数据变量到一个数据提供者。
```
```groovy
def "maximum of two numbers"() {
    expect:
    Math.max(a, b) == c

    where:
    a << [3, 5, 9]
    b << [7, 4, 9]
    c << [3, 5, 9]
}
```