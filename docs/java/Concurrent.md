# 并发  
1.[并发编程的优缺点](#并发编程的优缺点)   
2.[新建线程有哪几种方式](#新建线程有哪几种方式)     
3.[线程有哪几种状态](#线程有哪几种状态)   
4.[synchronized(this)和synchronized(.class)的理解](#synchronized(this)和synchronized(.class)的理解)  
5.[如果你提交任务时,线程池队列已满,这时会发生什么](#如果你提交任务时,线程池队列已满,这时会发生什么)  

## 并发编程的优缺点  
优点：(1).并发编程的形式可以将多核CPU的计算能力发挥到极致，性能得到提升。  
      (2).面对复杂业务模型，并行程序会比串行程序更适应业务需求，而并发编程更能吻合这种业务拆分  
缺点：(1).频繁的上下文切换会损耗性能。  
      (2).会出现线程安全问题，造成死锁。   
      
## 新建线程有哪几种方式  
(1).通过继承Thread类，重写run方法  
(2).通过实现Runnable接口  
(3).通过实现Callable接口这三种方式    

## 线程有哪几种状态  
(1).NEW:初始状态,线程被构建,但是还没有调用start()方法    
(2).RUNNABLE:运行状态,Java线程将操作系统中的就绪和运行两种状态统称"运行中"  
(3).BLOCKED:阻塞状态,表示线程阻塞于锁  
(4).WAITING:等待状态,表现线程进入等待状态,进入该状态表示当前线程需要等待其他线程做出一些特定动作(通知或中断)  
(5).TIME_WAITING:等待超时状态,该状态不同于WAITING,它是可以在指定的时间执行返回的  
(6).TERMINATED:终止状态,表示当前线程已经执行完毕   

## synchronized(this)和synchronized(.class)的理解  
(1).synchronized(this)锁的是当前对象，this代表了对象锁，此时被synchronized锁住的代码块只在当前对象同步，如果有其他对象就不会同步了。  
(2).synchronized(.class)是对整个类进行加锁。该类的不同对象，在类锁下会同步。 

## 如果你提交任务时,线程池队列已满,这时会发生什么  
这里区分一下：  
(1).如果使用的是无界队列LinkedBlockingQueue，也就是无界队列的话，没关系，继续添加任务到阻塞队列中等待执行，因为LinkedBlockingQueue可以近乎认为是一个无穷大的队列，可以无限存放任务  
(2).如果使用的是有界队列比如ArrayBlockingQueue，任务首先会被添加到ArrayBlockingQueue中，ArrayBlockingQueue满了，会根据maximumPoolSize的值增加线程数量，如果增加了线程数量还是处理不过来，ArrayBlockingQueue继续满，那么则会使用拒绝策略RejectedExecutionHandler处理满了的任务，默认是AbortPolicy  


