# 网卡

## 统计指标

*  /proc/net/dev

### 指标
* 网卡入口流量
* 网卡出口流量
```md
数据源: /proc/net/dev; 采集方式：累计值，每10秒采集一次取差值； 指标: net.dev (key: system)；
rxbytes0.8: 网卡入口流量，rxbytes8/10 -> bit/s;
txbytes0.8: 网卡出口流量，txbytes8/10 -> bit/s;
```
* 网卡入口包量
* 网卡出口包量
```md
数据源: /proc/net/dev; 采集方式：累计值，每10秒采集一次取差值； 指标: net.dev (key: system)；
rxpackets/10: 网卡入口包量，rxpackets/10 -> op/s;
txpackets/10: 网卡出口包量，txpackets/10 -> op/s;
```
* 网卡入口丢包
* 网卡出口丢包
```md
数据源: /proc/net/dev; 采集方式：累计值，每10秒采集一次取差值； 指标: net.dev (key: system)；
rxdrop/10: 网卡入口丢包量，rxdrop/10 -> op/s;
txdrop/10: 网卡出口丢包量，txdrop/10 -> op/s;
```
* 网卡入口收包出错数
* 网卡出口发包出错数
```md
数据源: /proc/net/dev; 采集方式：累计值，每10秒采集一次取差值； 指标: net.dev (key: system)；
rxerrs/10: 网卡每秒入口收包错误数，rxerrs/10 -> op/s;
txerrs/10: 网卡每秒出口丢包错误数，txerrs/10 -> op/s;
```
