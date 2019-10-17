# Tools

* ngrep – Network grep
```md
是一个网络数据包分析器。 它遵循GNU grep的大多数常用功能，将它们应用于网络层。
过滤来自eth0接口上的网络流量的所有HTTP GET或POST请求:
sudo ngrep -l -q -d eth0 "^GET |^POST " tcp and port 80
```
* dstat - 多功能资源统计工具
```md
克服了vmstat的一些限制。 它增加了一些额外的功能。 它允许我立即查看我的所有系统资源。
```
* mtr - 综合的网络排错、诊断工具
```md
结合了traceroute和ping程序的功能。 使用mtr监控网络中的传出带宽，延迟和抖动。 一个很好的小应用程序来解决网络问题。 
如果您看到数据包丢失突然增加或响应时间通常表示链路不良或流量过载。
```
