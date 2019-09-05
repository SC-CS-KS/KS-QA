# 网络


## 统计指标
* 数据源: /proc/net/dev

* 网络IO
```md
采集方式：累计值，每10秒采集一次取差值； 指标: net.dev (key: system)；
rxbytes: 入口字节数，rxbytes*8/10 -> bit/s;
txbytes: 出口字节数，txbytes*8/10 -> bit/s;
```

### 
* [网卡](network-card.md)
* [TCP](TCP.md)
* [网络协议](network-protocol.md)