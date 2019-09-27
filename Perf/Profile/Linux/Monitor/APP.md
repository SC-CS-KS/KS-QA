# 应用程序

## 进程
* /proc/${fd}/stat

### CPU User Time
```md
数据源: /proc/${fd}/stat; 采集方式: 累计值，每10秒采集一次取差值； 指标：process.stat (key: system); 备注：所有相同名称的进程会累加在一起计算；
cpu.utime_all_cores/10: cpu.utime_all_cores(所有cpu核的用户态时间/总核数)/10
```
### CPU System Time
```md
cpu.stime_all_cores/10: cpu.stime_all_cores(所有cpu核的内核态时间/总核数)/10
```
### 内存使用
```md
数据源: /proc/${fd}/stat; 采集方式: 直接使用当前值； 指标：process.stat (key: system); 备注：所有相同名称的进程会累加在一起计算；
mem.rss*1024: mem.rss为物理地址空间的大小，单位为KB，乘以1024后为bytes
```
### 监控工具
#### pidstat
```md
介绍
	用于监控全部或指定进程占用系统资源的情况，如CPU，内存、设备IO、任务切换、线程等
	pidstat首次运行时显示自系统启动开始的各项统计信息
		之后运行pidstat将显示自上次运行该命令以后的统计信息
	用户可以通过指定统计的次数和时间来获得所需的统计信息。
语法
	pidstat  [ -C comm ] [ -d ] [ -h ] [ -I ] [ -l ] [ -p { pid [,...] | SELF | ALL } ] [ -r ] [ -s ] [ -t ] [ -T { TASK | CHILD | ALL } ] [ -u ] [ -V ] [ -w ] [ interval [ count ] ]
参数
	-u
		cpu使用情况统计(-u)
		    When reporting statistics for individual tasks, the following values are displayed: 
		    PID
		    %usr			#用户层任务正在使用的CPU百分比（with or without nice priority ，NOT include time spent running a virtual processor）
		    %system			#系统层正在执行的任务的CPU使用百分比
		    %guest			#运行虚拟机的CPU占用百分比
		    %CPU			#所有的使用的CPU的时间百分比
		    CPU			        #处理器数量
		    Command			#命令
		    When reporting global statistics for tasks and all their children, the following values are displayed:
		    PID			        #PID号
		    usr-ms			#在指定时间内收集的在用户层执行的进程和它的子进程占用的CPU时间（毫秒）{with or without nice priority，NOT include time spent running a virtual processor)
		    system-ms			#在指定时间内收集的在系统层执行的进程和它的子进程占用的CPU时间（毫秒）
		    guest-ms			#花在虚拟机上的时间
		    Command			#命令
	-r
		内存使用情况统计(-r)
			# pidstat -r -p 13084 1
		    When reporting statistics for individual tasks, the following values are displayed:
		    PID			        #进程号
		    minflt/s			#每秒次缺页错误次数(minor page faults)，次缺页错误次数意即虚拟内存地址映射成物理内存地址产生的page fault次数
		    majflt/s			#每秒主缺页错误次数(major page faults)，当虚拟内存地址映射成物理内存地址时，相应的page在swap中，这样的page fault为major page fault，一般在内存使用紧张时产生
		    VSZ			        #该进程使用的虚拟内存(以kB为单位)
		    RSS			        #该进程使用的物理内存(以kB为单位)
		    %MEM			#当前任务使用的有效内存的百分比
		    Command			#任务的命令名             
		    When reporting global statistics for tasks and all their children, the following values are displayed:
		    PID			        #PID号
		    minflt-nr			#在指定的时间间隔内收集的进程和其子进程的次缺页错误次数
		    majflt-nr			#在指定的时间间隔内收集的进程和其子进程的主缺页错误次数
		    Command			#命令名
	-d
		IO情况统计(-d)
			# pidstat -d 1 2
		    PID			        #进程号
		    kB_rd/s			#每秒此进程从磁盘读取的千字节数
		    kB_wr/s			#此进程已经或者将要写入磁盘的每秒千字节数
		    kB_ccwr/s			#由任务取消的写入磁盘的千字节数
		    Command			#命令的名字
	-p
		针对特定进程统计(-p)
	-C comm		#只显示那些包含字符串（可是正则表达式）comm的命令的名字
	 -I
		#在SMP环境，指出任务的CPU使用（等同于选项-u）应该被除于cpu的总数
	 -h
		#显示所有的活动的任务
	 -p { pid [,...] | SELF | ALL }	
		#指定线程显示其报告
	 -s
		#堆栈的使用
	-t
		#显示与所选任务相关的线程的统计数据
	 -T { TASK | CHILD | ALL }
		#指定必须监测的内容：TASK是默认的，单个任务的报告；CHILD：指定的进程和他们的子进程的全局报告，ALL：相当于TASK和CHILD
	 -w
		#报告任务切换情况
		    PID			        #PID号
		    cswch/s			#每秒自动上下文切换
		    nvcswch/s			#每秒非自愿的上下文切换
		    Command			#命令
应用
	 # pidstat
		将输出系统启动后所有活动进程的cpu统计信息
	# pidstat -r 2 5
		监测内存使用
	# pidstat -T CHILD -C mysql
		显示所有mysql服务器的子进程
	# pidstat -urd -h
		将所有的统计数据结合到一个便于阅读的单一报告中
	pidstat -p 37645 -u -d -t -w -h 1 1
		显式进程所有线程的资源使用信息
输出
	PID - 被监控的任务的进程号
	%usr - 当在用户层执行(应用程序)时这个任务的cpu使用率，和 nice 优先级无关。注意这个字段计算的cpu时间不包括在虚拟处理器中花去的时间。
	%system - 这个任务在系统层使用时的cpu使用率。
	%guest - 任务花费在虚拟机上的cpu使用率（运行在虚拟处理器）。
	%CPU - 任务总的cpu使用率。在SMP环境(多处理器)中，如果在命令行中输入-I参数的话，cpu使用率会除以你的cpu数量。
	CPU - 正在运行这个任务的处理器编号。
	Command - 这个任务的命令名称。
```
### 分析
```md
将 cpu 占用率高的线程找出来
	 ps H -eo user,pid,ppid,tid,time,%cpu,cmd --sort=%cpu
```
## 线程
### 线程数
```md
nums.thread: 总线程数
```
* 磁盘写
* 磁盘读
* IO写
* IO读
* System Call Write
* System Call Read
```md
数据源: /proc/${fd}/stat; 采集方式: 累计值，每10秒采集一次取差值； 指标：process.stat (key: system); 备注：所有相同名称的进程会累加在一起计算；
io.write_bytes0.8: io.write_bytes为实际写入到磁盘中的字节总数，io.write_bytes8/10 -> bit/s;
io.read_bytes0.8: io.read_bytes为实际从磁盘读取的字节总数，io.read_bytes8/10 -> bit/s;
io.wchar0.8: io.wchar为进程写入的总字节数，io.wchar8/10 -> bit/s;
io.rchar0.8: io.rchar为进程读取的总字节数，io.rchar8/10 -> bit/s;
io.syscw/10: io.syscw为write()或者pwrite()总的调用次数, io.syscw/10 -> op/s;
io.syscr/10: io.syscr为read()或者pread()总的调用次数, io.syscr/10 -> op/s;
```
#### 线程数与多核CPU的关系
[参考](https://juejin.im/entry/5b77c798f265da43296c3b96)
```md	
对于计算密集型的任务，一般建议将线程数设置为物理核数
具体的，还需要针对不同的程序，做对应压力测试得到合适的参数选择。
```
