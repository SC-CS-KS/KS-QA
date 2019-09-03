# TCP

## 统计指标
* /proc/net/tcp
```md
数据源: /proc/net/tcp; 采集方式: 对该状态tcp连接进行统计后输出； 指标: tcp.stat (key: system);
```

### 指标
* Listen
* Established
* Time Wait
* Close Wait
* Sync Send
* Syn Receive
* Fin Wait 1
* Fin Wait 2
* Closing
* Last Ack
```md
listen: 
    处于监听状态的端口数；
established: 
    TCP建立完成后的稳定状态；
syn_sent: 
    发送SYN后，尚未完成三次握手；
syn_recv: 
    对方发送SYN后，返回了SYN，但未收到对方最后一个SYN包，还未完成三次握手；
fin_wait1: 
    设备可能处在等待接收对方回应收到 FIN的ACK，也可能处在等待接收对方发送的FIN；
fin_wait2: 
    设备已经发送了FIN，并且收到了对方回应的 ACK，还在等待对方发送 FIN；
time_wait: 
    设备处于 TIME-WAIT 状态表明设备收到了对方的 FIN，并且回应了 ACK，设备发送了 FIN，也收到了对方回应的 ACK。
    此时可以关闭连接。不过我们还是要倒计一段时间再关闭，防止影响连接端接收这边发送过去的 ACK。也防止和新连接产生冲突；
close_wait: 
    设备接收到连接方传来的FIN，现在需要等待设备上的程序为关闭连接做相应的工作；
last_ack: 
    设备已经接收了另一端发送过来的 FIN，并回应了ACK。
    也向对方发送了 FIN，此时还需等待接收对方回应的 ACK，以确认对方成功接收了这边发送过去的 FIN；
closing: 
    设备已经接收到了对方的FIN，自己也回应了ACK，还需等待接收对方回应自己FIN的ACK；
```
