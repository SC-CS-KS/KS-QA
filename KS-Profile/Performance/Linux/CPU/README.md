# CPU


## 统计指标
* CPU使用率
```md
该值为cpu tick累计值，每10秒采集一次，获取差值后将 cputick总时间(0.01s)换算为自然时间，与10s求比例，
得到0-100的百分比； measurement: cpu.usage (key: system);
```
```md
user: 用户态时间占比(执行应用程序代码的时间);
system: 内核态时间占比(分配内存、io操作、创建子进程等，如果该值较高，可能是系统调用过多);
idle: 空闲状态时间占比：
iowait: cpu等待io且该时间段其他无就绪任务的时间占比(iowait较高不一定有问题，cpu在等待io的过程中无事可做)；
steal: 虚拟化环境下，被同一宿主机上其他虚拟机系统占用的时间占比(虚拟机超卖)；
irq: cpu处理硬件中断的时间占比；
softirq: cpu处理软中断的时间占比；
```
* CPU Load Average
```md
last1min：过去1分钟正在运行或等待运行的进程数；
last5min：过去5分钟正在运行或等待运行的进程数；
last15min：过去15分钟正在运行或等待运行的进程数；
num_cpu： cpu核数，将以上数值除以核数，可以衡量单个cpu核心的负载；
```
