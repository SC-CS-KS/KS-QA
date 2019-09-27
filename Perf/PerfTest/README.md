# Performance Test



## Web 性能测试工具
### Apache Bench
### Jmeter
### Gatling
```md
Gatling是一款基于Scala 开发的高性能服务器性能测试工具
Gatling主要用于测量基于HTTP的服务器，比如Web应用程序，RESTful服务等
```
* 特点
```md
支持Akka Actors 和 Async IO，从而能达到很高的性能
支持实时生成Html动态轻量报表，从而使报表更易阅读和进行数据分析
支持DSL脚本，从而使测试脚本更易开发与维护
支持录制并生成测试脚本，从而可以方便的生成测试脚本
支持导入HAR（Http Archive）并生成测试脚本
支持Maven，Eclipse，IntelliJ等，以便于开发
支持Jenkins，以便于进行持续集成
支持插件，从而可以扩展其功能，比如可以扩展对其他协议的支持
开源免费
```
* 场景
```md
测试需求经常改变，测试脚本需要经常维护；测试环境的客户机性能不强，但又希望发挥硬件的极限性能；
能对测试脚本进行很好的版本管理，并通过CI进行持续的性能测试；希望测试结果轻量易读等。
```
### Sniper
```md
Sniper是一个功能强大、高性能的HTTP负载工具,采用Golang编写
利用协程并发优势，实现海量并发、超低内存占用、丰富图表展示。
```