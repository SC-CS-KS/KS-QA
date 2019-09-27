# CPU


## 性能计数
* CPU使用率 - 显示的是程序在运行期间实时占用的CPU百分比
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
* CPU Load Average - 显示的是一段时间内正在使用和等待使用CPU的平均任务数
```md
last1min：过去1分钟正在运行或等待运行的进程数；
last5min：过去5分钟正在运行或等待运行的进程数；
last15min：过去15分钟正在运行或等待运行的进程数；
num_cpu： cpu核数，将以上数值除以核数，可以衡量单个cpu核心的负载；
```

## 监控工具
### mpstat
```md
MultiProcessor Statistics
	报告与CPU的一些统计信息，这些信息存放在/proc/stat文件中
	在多CPUs系统里，其不但能查看所有CPU的平均状况信息，而且能够查看特定CPU的信息。
语法
	mpstat [-P {|ALL}] [internal [count]]
		-P {|ALL} 表示监控哪个CPU， cpu在[0,cpu个数-1]中取值
		internal 相邻的两次采样的间隔时间
		count 采样的次数，count只能和delay一起使用
		当没有参数时，mpstat则显示系统启动以后所有信息的平均值。
		有interval时，第一行的信息自系统启动以来的平均信息。
应用
	average mode (粗略信息)
		$ mpstat
			Linux 2.6.32-573.18.1.el6.toav2.x86_64 (dataplatform-dps-det01.xg01)    08/10/2017      _x86_64_        (12 CPU)

11:26:43 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
11:26:43 AM  all    3.35    0.00    0.31    0.00    0.00    0.01    0.00    0.00   96.33
	每2秒产生了2个处理器的统计数据报告
		# mpstat -P ALL 2 3
输出
	user 在internal时间段里，用户态的CPU时间（%），不包含 nice值为负 进程 (usr/total)*100  
	nice 在internal时间段里，nice值为负进程的CPU时间（%）   (nice/total)*100  
	system 在internal时间段里，核心时间（%）   (system/total)*100
	iowait 在internal时间段里，硬盘IO等待时间（%） (iowait/total)*100
	irq 在internal时间段里，硬中断时间（%）      (irq/total)*100
	soft 在internal时间段里，软中断时间（%）    (softirq/total)*100
	idle 在internal时间段里，CPU除去等待磁盘IO操作外的因为任何原因而空闲的时间闲置时间（%）(idle/total)*100
	intr/s 在internal时间段里，每秒CPU接收的中断的次数intr/total)*100
	CPU总的工作时间=total_cur=user+system+nice+idle+iowait+irq+softirq
	total_pre=pre_user+ pre_system+ pre_nice+ pre_idle+ pre_iowait+ pre_irq+ pre_softirq
	user=user_cur – user_pre
	total=total_cur-total_pre
	其中_cur 表示当前值，_pre表示interval时间前的值。上表中的所有值可取到两位小数点。
```
### vmstat
```md
CPU上下文切换、运行队列、利用率 
```
### sar
```md
来查看一定世界范围内以及历史的CPU消耗情况信息 
```
