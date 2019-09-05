# IOPS
```md
 (Input/Output Per Second)即每秒的输入输出量(或读写次数)，是衡量磁盘性能的主要指标之一。
 随机读写频繁的应用，如OLTP(Online Transaction Processing)，IOPS是关键衡量指标。
```

## IOPS 细分指标
* Toatal IOPS，混合读写和顺序随机I/O 负载情况下的磁盘 IOPS，这个与实际I/O情况最为相符，大多数应用关注此指标。
* Random Read IOPS，100%随机读负载情况下的IOPS。
* Random Write IOPS，100%随机写负载情况下的IOPS。
* Sequential Read IOPS，100%顺序负载读情况下的IOPS。
* Sequential Write IOPS，100%顺序写负载情况下的IOPS。

# IOPS 计算
```md
IO Time = Seek Time + 60 sec/Rotational Speed/2 + IO Chunk Size/Transfer Rate //单次IO时间
IOPS = 1/IO Time = 1/(Seek Time + 60 sec/Rotational Speed/2 + IO Chunk Size/Transfer Rate)
```
```md
理论上可以计算出磁盘的最大IOPS，即 IOPS = 1000 ms/ (寻道时间 + 旋转延迟)，忽略数据传输时间。
假设磁盘平均物理寻道时间为3ms, 磁盘转速为7200rpm，则磁盘IOPS理论最大值分别为，
IOPS = 1000 / (3 + 60000/7200/2) = 140
```
```md
固态硬盘SSD是一种电子装置， 避免了传统磁盘在寻道和旋转上的时间花费，存储单元寻址开销大大降低，
因此 IOPS 可以非常高，能够达到数万甚至数十万。
```
```md
实际测量中，IOPS数值会受到很多因素的影响，包括I/O负载特征(读写比例，顺序和随机，工作线程数，队列深度，数据记录大小)、
系统配置、操作系统、磁盘驱动等等。
因此对比测量磁盘IOPS时，必须在同样的测试基准下进行，即便如何也会产生一定的随机不确定性。
```

## Tools
* Iometer
* IoZone
* FIO

## IOPS 测试
```md
对于应用系统，需要首先确定数据的负载特征，然后选择合理的IOPS指标进行测量和对比分析，据此选择合适的存储介质和软件系统。
```
