# 锁  
1.[各种锁的解释](#各种锁的解释)  
## 各种锁的解释   
(1).`可重入锁`:指的是以线程为单位，当一个线程获取对象锁之后，这个线程可以再次获取本对象上的锁，而其他的线程是不可以的。synchronized 和   ReentrantLock 都是可重入锁。可重入锁的意义之一在于防止死锁。  
           实现原理实现是通过为每个锁关联一个请求计数器和一个占有它的线程。当计数为0时，认为锁是未被占有的；线程请求一个未被占有的锁时，JVM将记录锁的占有者，并且将请求计数器置为1 。
           如果同一个线程再次请求这个锁，计数器将递增；
           每次占用线程退出同步块，计数器值将递减。直到计数器为0,锁被释放。  
(2).`自旋锁`:是指当一个线程在获取锁的时候，如果锁已经被其它线程获取，那么该线程将循环等待，然后不断的判断锁是否能够被成功获取，直到获取到锁才会退出循环。  
(3).`互斥锁`:是指当一个线程在获取锁的时候，如果锁已经被其它线程获取，那么该线程将会释放 CPU ，给其他线程.  
(4).`读写锁`:分为读锁和写锁，多个读锁不互斥，读锁与写锁互斥，这是由jvm自己控制的，我们只要上好相应的锁即可。如果你的代码只读数据，可以很多人同时读，但不能同时写，那就上读锁；如果你的代码修改数据，只能有一个人在写，且不能同时读取，那就上写锁。总之，读的时候上读锁，写的时候上写锁！   