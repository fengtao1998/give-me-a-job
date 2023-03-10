# Java和C++的区别
* Java不提供指针来直接访问内存，程序内存更加安全；
* Java的类是单继承的，C++支持多重继承；但是Java的接口可以多继承；
* Java有自动内存管理垃圾回收机制（GC），不需要程序员手动释放无用内存；
* C++同时支持方法重载和操作符重载，但是Java只支持方法重载
# 方法的重写要遵循“两同两小一大”
* “两同”即方法名相同、形参列表相同；
* “两小”指的是子类方法返回值类型应比父类方法返回值类型更小或相等，子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等；
* “一大”指的是子类方法的访问权限应比父类方法的访问权限更大或相等。
# 常用字符编码所占字节数
utf8 :英文占 1 字节，中文占 3 字节，unicode：任何字符都占 2 个字节，gbk：英文占 1 字节，中文占 2 字节。
# ArrayList和LinkedList的区别
* ArrayList是基于数组实现的，适合随机查找
* 频繁访问列表中的某一个元素。只需要在列表末尾进行添加和删除元素操作。
* LinkedList是基于链表实现的，适合删除和添加
* 你需要通过循环迭代来访问列表中的某些元素。
    需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。
# 线程池的类型
* FixedThreadPool：固定线程数量，队列无限长
* SingleThreadPool：单一线程数量，队列无限长
* CachedThreadPool：线程无限加，没有缓冲队列
* ScheduledThreadPool：任务队列无限长
# 线程池的核心参数有哪些
* corePoolSize 队列不满时线程最大并发数
* maximumPoolSizes 队列满后最大并发数
* keepAliveTime 空闲线程多久被回收的时间限制
* unit keep的时间单位
* workQueue 阻塞的队列类型
* RejectedExecutionHandler 超限制处理
# sleep()和wait()对比
* 共同点：两者都可以暂停线程
* 区别：
  * sleep没有释放锁，wait释放锁
  * wait通常用于线程的通信，sleep常用于线程的暂停
  * wait方法调用后，线程不会自动苏醒，需要别的线程调用notify方法。sleep可以自动苏醒
  * sleep是Thread类的静态本地方法，wait是object类的本地方法：sleep为暂停线程，不涉及对象类，wait是让获得对象锁的线程等待，每个对象都有锁，释放对象锁操作的对象。
# Java中的volatile变量是什么
* volatile是一个特殊的修饰符，只有成员变量（类的成员变量、类的静态成员变量）才能使用它。被volatile修饰后，变量具备两层语义:
  * 保证不同线程对这个变量进行操作时的可见性（即某个线程修改了这个变量的值，对其他线程来说是可见的）
  * 禁止进行指令重排序
# synchronized 和volatile的区别
两者是互补的存在，不是对立存在的
* volatile关键字是线程同步的轻量级实现，比synchronized性能优。但是volatile只能用于变量，而synchronized可修饰方法和代码块
* volatile关键字能保证数据的可见性，但不能保证数据的原子性，synchronized可以保证
* volatile主要解决变量在多个线程的可见性，而synchronized解决多个线程访问资源的同步性
# synchronized 和 lock的区别
* Lock是一个接口，而synchronized是java关键字，synchronized为java内置的语言实现。
* synchronized在发生异常时会自动释放锁，而lock不会释放锁，必须手动unlock才可以，通常在try-finally 中，finally加入unlock
* lock等待过程中可以响应中断，而synchronized是原子性的，只能等待锁的释放
* synchronized采用的CPU悲观锁的机制，线程获得独占锁，lock采取的乐观锁的方式，CAS操作
* synchronized 可重入，不可中断，非公平 ； lcok 可重入，可中断，可公平
