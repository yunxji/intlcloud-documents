云数据库（SQL Server）系统监控支持 SQL Server 常见的25种参数，您可以通过配置 SSMS 的计数器，额外统计其他参数。
## 目前已经支持的参数如下
<body>

### 常见参数

|指标|描述（/单位）|五分钟指标取值|指标优化建议|
|:----:|----|:-----:|--------|
|CPU 利用率<br>（Total Processor Time）|实际 CPU 消耗的百分比（%）|max| < 30% 好<br>< 60% 好<br>> 60% 需关注|
|事务数<br>（Transaction/sec）|平均每秒的事务数（次/秒）|max|参考业务需要|
|连接数<br>（User Connection）|平均每秒用户连接数据库的个数（个）|max|参考业务需要|
|请求数<br>（Batch Requests/sec）|-（次/秒）|max|参考业务需要|
|每秒登录次数<br>（Logins/sec）|每秒登录次数（次/秒）|max|参考业务需要|
|每秒登出次数<br>（Logouts/sec）|每秒登出次数（次/秒）|max|参考业务需要|
|已用存储空间<br>（Storage Space）|实例数据库文件和日志文件占用的空间总和（GB）|max| <30% 好<br><60%好<br>>60% 需关注|
|输入流量<br>（Network Receive Throughput）|所有连接输入包大小总和（MB/s）|max|参考业务需要|
|输出流量<br>（Network Transmit Throughput）|所有连接输出包大小总和（MB/s）|max|参考业务需要|
|磁盘 IOPS<br>（IPOS）|磁盘读写次数（次/秒）|max|根据实例规格中心 IOPS 建议<br>< 30% 好<br>< 60% 好<br>> 60% 需关注|
|读取磁盘次数<br>（Read IOPS）|每秒读取磁盘次数（次/秒）|max|参考业务需要|
|写入磁盘次数<br>（Write IOPS）|每秒写入磁盘次数（次/秒）|max|参考业务需要|
</body>
<body>

### 性能优化参数

|指标|描述（/单位）|五分钟指标取值|指标优化建议|
|:----:|----|:-----:|--------|
|慢查询<br>（SlowQuery）|运行时间超过一秒的查询数量（个）|avg| < 1 好<br>< 10 正常<br>> 10 需关注|
|阻塞数<br>（Processes blocked）|当前阻塞数量（个）|avg|参考业务需要|
|锁请求次数<br>（Lock Requests/sec）|平均每秒锁请求的次数（次/秒）|avg|参考业务需要|
|用户错误数<br>（User Error/sec）|平均每秒错误数（次/秒）|avg|0 good<br>> 0 attention|
|锁等待次数<br>（Lock waits）|每秒要求调用者等待的锁请求数（次/秒）|avg|参考业务需要|
|SQL 编译数<br>（SQL Compilation/sec）|平均每秒 SQL 编译次数（次/秒）|avg|参考业务需要|
|SQL 重编译数<br>（SQL Re-Compilation/sec）|平均每秒 SQL 重编译次数（次/秒）|avg|参考业务需要|
|输入流量<br>（Network Receive Throughput）|所有连接输入包大小总和（MB/s）|avg|参考业务需要|
|输出流量<br>（Network Transmit Throughput）|所有连接输出包大小总和（MB/s）|avg|参考业务需要|
|每秒钟 SQL 做全表扫描数目<br>（Full Scans/sec）|磁盘读写次数（次/秒）|avg|根据实例规格中心 IOPS 建议<br>< 30% 好<br>< 60% 好<br>> 60% 需关注|
|缓存区缓存命中率<br>（Buffer cache hit ratio）|数据缓存（内存）命中率（%）|avg|>= 95% 好<br>>= 90% 正常<br>< 90% 需关注|
|每秒闩锁等待数量<br>（Latch Waits/sec）|每秒闩锁等待数量（次/秒）|avg|参考业务需要|
|平均锁等待延迟<br>（Average Wait Time）|每个导致等待的锁请求的平均等待时间（ms）|max|参考业务需要|
|平均网络 IO 延迟<br>（Network IO waits）|平均网络 IO延迟时间（ms）|max|参考业务需要|
|执行缓存缓存命中率<br>（Plan Cache：Cache Hit Ratio）|每个 SQL 有一个执行计划，执行计划的命中率（%）|max|>= 95% 好<br>>= 90% 正常<br>< 90% 需关注|
</body>

>由于 SQL Server 的内存为全部占满使用的机制，因此无需监控直接内存容量指标，可以通过缓存命中率来查看内存使用情况。


## 目前已经支持的可告警指标
目前支持关键的系统性能指标的告警，其他指标暂不支持通过腾讯云云监控告警，您可以在腾讯云"管理中心>云监控>我的告警>告警策略"里面配置告警能力。
目前已经支持对以下监控指标进行告警，告警建议阈值详见上文（表1）

- CPU 利用率
- 连接数
- 输入流量
- 输出流量
- IOPS
- 存储空间
