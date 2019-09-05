## 应用程序


## 进程

### 统计指标
* /proc/${fd}/stat

#### 指标
* CPU User Time
```md
数据源: /proc/${fd}/stat; 采集方式: 累计值，每10秒采集一次取差值； 指标：process.stat (key: system); 备注：所有相同名称的进程会累加在一起计算；
cpu.utime_all_cores/10: cpu.utime_all_cores(所有cpu核的用户态时间/总核数)/10
```
* CPU System Time
```md
cpu.stime_all_cores/10: cpu.stime_all_cores(所有cpu核的内核态时间/总核数)/10
```
* 内存使用
```md
数据源: /proc/${fd}/stat; 采集方式: 直接使用当前值； 指标：process.stat (key: system); 备注：所有相同名称的进程会累加在一起计算；
mem.rss*1024: mem.rss为物理地址空间的大小，单位为KB，乘以1024后为bytes
```
* 线程数
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