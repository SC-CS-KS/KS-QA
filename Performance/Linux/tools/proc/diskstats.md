# /proc/diskstats
```md
对所有块设备的IO统计信息。
```
## fields:
```md
1 - major number 主设备号
2 - minor number 次设备号
3 - device name 设备名称
4 - reads completed successfully 成功完成的读请求次数
5 - reads merged 读合并次数
6 - sectors read 读取的扇区数（单位是扇区，默认扇区大小512Byte）
7 - time spent reading (ms) 读请求花费的时间（单位是ms）
8 - writes completed 成功完成的写请求次数
9 - writes merged 写合并次数
10 - sectors written 写入的扇区数
11 - time spent writing (ms) 写请求花费的时间
12 - I/Os currently in progress 设备队列中的IO请求数
13 - time spent doing I/Os (ms) 花费在I/O操作上的时间（单位ms，不包含队列等待）
14 - weighted time spent doing I/Os (ms) 花费在I/O操作上的总时间（单位ms，包括队列等待）
```
```md
统计项中除正在处理的输入/输出请求数项是非累积值外，其他磁盘统计都是累积值。
```
## 统计
* 磁盘使用率
```md
两次采集的输入/输出操作花费的毫秒数之差 / 采集间隔时间

例如：第一次采集输入/输出操作花费的毫秒数为90258834，间隔10秒后采集的值为90258710
那么磁盘使用率为 （90258710ms - 90258834ms）/ 10*1000ms = 0.0124，也就是1.24%
```
