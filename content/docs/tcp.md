
#可靠
	不丢、不重、不乱
信道不可靠性决定了可靠数据传输协议的复杂性
校验、接收方反馈信息（ACK/NAK）、重传


#滑动窗口
SNR协议 停等操作性能太慢
Selective Repeat协议
接收方对每个分组单独确认
设置缓存，缓存乱序到达的分组

TCP 
流水线机制
累计确认
单一定时器重传

触发重传事件:
定时器超时
收到重复ack
* 如何设置超时时间
	根据EstimatedRTT+4*DEVRTT，如何计算RTT，指数加权平均EstimatedRTT = (1-a)EstimatedRTT + SampleRTT (a = 0.125)
	DEVRTT = (1-b)DEVRTT+ b|SampleRTT - EstimatedRTT| (b=0.25)

* 快速重传
重复收到三次重复ack触发

* 流量控制
RcvWindow
buffer中可用的空间 RecvBuff - (LastByteRecvd - LastByteRead)
接收方通过segment头部传递给发送者,发送者要控制已经发送未确认的数据不能超过RcvWindow
表示的接收方的处理能力
通告窗口(awnd)

* 连接建立
	三次握手 传递seq，窗口大小
	* 为什么不是两次握手或者四次？
	** 无法避免历史连接的初始化，浪费接收方资源
	** TCP可用同时传递seq和syn信息，三次足够满足，不需要更多次通信传递相同信息。	

# 网络拥塞
表示中间网络的处理能力
拥塞窗口(cwnd)

慢启动
刚开始启动，带宽远大于初始速率，希望快速增长
cwnd < ssthresh 慢启动(指数增长)

拥塞控制
cwnd > ssthresh 拥塞避免(cwnd+1)

* 如何感知网络拥塞
	3个重复确认
	超时
快速恢复 收到3个重复确认 ssthresh = cwnd/2,cwnd = ssthresh 拥塞避免;
超时 ssthresh = cwnd/2 cwnd = 1 慢启动


	
