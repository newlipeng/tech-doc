## GO CHANNEL 使用总结

### 前言
Go: Share Memory By Communicating
章节建议使用Sync.Once和WaitGroup进行协程间通讯，其中Sync.Once采用atomic实现，WaitGroup采用channel实现，详细了解Channel会对协程间通讯很有好处

### CSP 模型
CSP 模型全称为 communicating sequential processes，CSP 模型由并发执行实体(进程，线程或协程)，和消息通道组成，实体之间通过消息通道发送消息

### Channel
并发（concurrency）是GO语言的重要特征，完成并发功能的是协程（goroutines），在协程间通信，父协程和子协程见通讯都可以通过通道（Channel）来完成。
Channel具备几个特征
* 协程安全的
* 存储和传输协程间的数据
* 用FIFO队列实现
* 可以控制协程的阻塞和运行

### Channel的用法
```
    ch := make (chan int, 3)  //创建带有缓冲的管道
    ch := make (chan int)     //创建不带缓冲的管道
```

###标题
* 内容
> 引用 
```
    code
```
| 表--------格 | 左--------对--------齐 | 右--------对--------齐 |
| :-: | :-- | --: |
| 居中 | 左对齐 | 左对齐 |
| 居中 | 左对齐 | 左对齐 |