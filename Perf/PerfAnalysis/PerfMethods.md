# [Performance Analysis Methodology](http://www.brendangregg.com/methodology.html)

## [USE 方法：查找资源瓶颈](http://www.brendangregg.com/usemethod.html)
```md
Utilization Saturation and Errors (USE) Method
是一种用于分析任何系统性能的方法。它指导构建检查表，该检查表可用于服务器分析，以快速识别资源瓶颈或错误。
它从提出问题开始，然后寻找答案，而不是从给定的指标（部分答案）开始并尝试倒退。
```
## [TSA 方法：用于分析申请时间](http://www.brendangregg.com/tsamethod.html)
```md
Thread State Analysis (TSA) Method
对于大多数性能问题，可以使用两种基本的性能分析方法。第一种是面向资源的USE方法，它提供了一个清单，用于识别常见的瓶颈和错误。
第二种是面向线程的TSA方法，用于识别导致线程性能不佳的问题。
《系统性能》一书的“应用程序”一章中介绍了TSA方法。
```
```md
TSA方法是USE方法的补充，因为它具有不同的观点：线程而不是资源。
与USE方法类似，它提供了分析的起点，然后将调查范围缩小到问题区域。
它也可以应用于任何OS，因为它是根据我们想回答的问题开发的：每个线程在哪里花费时间？
```
## [Off-CPU 分析：用于分析任何类型的线程等待延迟](http://www.brendangregg.com/offcpuanalysis.html)
```md
On-CPU：线程在CPU上运行花费的时间。
Off-CPU：在等待I / O，锁定，计时器，分页/交换 花费的时间。
```
```md
Off-CPU分析 测量和研究 Off-CPU时间 以及 堆栈跟踪等。它与On-CPU分析不同，后者仅检查线程是否在CPU上执行。
在这里，目标是处于阻塞状态且已关闭CPU的线程状态
```
```md
Off-CPU 分析是对 On-CPU 分析的补充，因此可以理解100％的线程时间。
```
## [主动基准测试：准确，成功地进行基准测试](http://www.brendangregg.com/activebenchmarking.html)


## Anti-Methodologies
