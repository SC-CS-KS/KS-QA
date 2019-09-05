# 网络协议


## 统计指标
* /proc/net/snmp
```md
数据源: /proc/net/snmp; 采集方式：累计值，每10秒采集一次取差值； 指标：net.snmp.tcp (key: system);
```
* /proc/net/netstat
```md
数据源: /proc/net/netstat; 采集方式：累计值，每10秒采集一次取差值； 指标：net.netstat.tcp (key: system);
```

### 指标
* In Segs - tcp协议层收到的数据包个数
* Out Segs
* Syn Ack Timeout -  tcp数据在指定时间内没有受到应答 ack 而超时的次数
* Listen Overflow(backlog full): Listen状态的端口因syn过多导致请求数量超过了sock的最大可积压数量的次数
* Listen drops: 请求数量超出或者是其他错误原因例如内存不足等导致监听新端口失败的次数
* Syn Cookies: SYN cookie是用于阻止SYN flood攻击的技术
* Syn Drops: syn_table过载，丢掉SYN的次数
* Passive Opens: 被动发送SYN包完成三次握手成功建立连接的次数
* Active Opens: 主动发送SYN包完成三次握手成功建立连接的次数
* Out of order packets received: 接收到的乱序包的数量
* Out of order packets drop(no space): 因空间不足进入乱序队列被丢弃的包数量
* Out of order packets merge(received before): 乱序包被合并的次数（重复接收）
* Duplicate sack received: 接收到相同sack包的次数
* Duplicate sack receive(out of order packet): 接收到相同的乱序sack包次数
* Duplicate sack sent(out of order data receive): 发送乱序sack包的次数
* Undo cwnd reduction(duplicate sack acked all retransmitted data): 撤销了发送DSACK包的次数
* Duplicate sack sent(old data receive): 发送过期DSACK包的次数
* Delayed acks: 发送延迟ACK包的次数
* Delayed ack locked by user: 发送延迟ACK时，用户已经锁定socket而导致ACK再次延迟发送的次数
* Delayed ack lost: 因为延迟ACK包丢失而再次发送的次数
* Retransmit segs: tcp层重传的数据包数量
* Prune called(no space): 由于接收缓冲区空间不足而进行tcp内存回收的次数
* Receive pruned(purge failed): 由于接收缓冲区空间不足而进行tcp内存回收后但空间还是不够的次数
* tcp_fast_retrans: tcp快速重传的包数量
* Time waited: timewait状态sock超时后被回收的个数
* Time wait killed: 使用PAWS机制后释放timewait状态sock的个数
* Time wait recycle: 试图进行timewait状态sock回收的次数，当新sock进行connect而hash时与原有的sock或timewait状态的sock冲突时，会触发回收工作
* Abort on timeout: tcp协议栈各定时器超时重复次数超过最大限制而关闭sock的次数
* Abort on close(data was unread): 当sock关闭时还有相关数据未读的次数
* Abort on syn: 接收到错误的syn包(序号错误)导致连接被reset的次数
* Abort on data: 当sock状态在TCP_FIN_WAIT1或TCP_FIN_WAIT2状态已经进入半连接但还是接收到数据而引起连接被reset的次数
* Abort on linger2(fin-wait2 with tcp_linger2): 当sock关闭时状态是TCP_FIN_WAIT2状态直接被reset的次数
* Abort on memory(out of memory. should tuning tcp_mem): 当sock关闭时由于内存不足而直接被reset的次数
* Abort failed(alloc/transmit skb failed): tcp协议栈在发送reset包而发送失败的次数
* Out rst: tcp协议层发送的reset数据包的个数
* Attempt failed: tcp syn_recv状态被reset的次数
* In checksum errors: tcp协议层接收校验失败的数据包的个数
* In error: tcp协议层接收出错的数据包的个数
