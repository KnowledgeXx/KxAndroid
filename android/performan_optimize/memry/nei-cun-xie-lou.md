# 内存泄漏

## 常见内存泄漏场景

* 集合类泄漏\(集合一直引用着被添加进来的元素对象\)
* 单例/静态变量造成的内存泄漏\(生命周期长的持有了生命周期短的引用\)
* 匿名内部类/非静态内部类
* 资源未关闭造成的内存泄漏
* 网络，文件等流忘记关闭
* 手动注册广播时，退出时忘记unregisterReceiver\(\)
* Service执行完成后忘记stopSelf\(\)
* EventBus等观察者模式的框架忘记手动解除注册

## 

## App 线程优化？

线程池避免存在大量的Thread，重用线程池内部的线程，从而避免了线程的创建和销毁带来的性能开销，同时能有效控制线程池的最大并发数，避免大量线程因互相抢占系统资源而导致阻塞线现象发生。推荐阅读《Android开发艺术探索》 第11章。

**分类**

* FixedThreadPool 数量固定的线程池
* CachedThreadPool 只有非核心线程，数量不定，空闲线程有超时机制，比较适合执行大量耗时较少的任务
* ScheduledThreadPool 核心线程数量固定，非核心线程没有限制。主要用于执行定时任务和具有固定中周期的重复任务。
* SingleThreadPool 只有一个核心线程，确保所有的任务在同一个线程顺序执行，统一外界任务到一个线程中，这使得在这些任务之间不需要处理线程同步的问题。

**优点**

* 减少在创建和销毁线程上所花的时间以及系统资源的开销
* 不使用线程池有可能造成系统创建大量的线程而导致消耗完系统内存以及"过度切换"

**注意点**

* 如果线程池中的数量未达到核心线程的数量,则直接启动一个核心线程来执行任务
* 如果线程池中的数量已经达到或超过核心线程的数量,则任何会被插入到任务队列中等待执行
* 如果2中的任务无法插入到任务队列中,由于任务队列已满,这时候如果线程数量未达到线程池规定的最大值,则会启动一个非核心线程来执行任务
* 如果3中的线程数量已经达到线程池最大值,则会拒绝执行此任务,ThreadPoolExecutor会调用RejectedExecutionHandler的rejectedExecution\(\)方法通知调用者

