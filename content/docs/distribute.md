
# 分布式id
* uuid 没法排序，趋势地址，海量id考虑存储量
* 数据库 
* redis 引入额外系统组件
* 雪花算法 经典解决方案，存在系统时钟回拨的问题
  ** 最高位0 
  ** 时钟毫秒（41bit）
  ** 机器编号 1024
  ** 计数编号(同一个毫秒内产生的唯一id) 4096
  
# 分布式锁



# 限流算法
计数器算法
滑动窗口算法
令牌桶
漏桶