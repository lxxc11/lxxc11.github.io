# 队列  
1.[Queue有哪几种分类](#Queue有哪几种分类)   
2.[ArrayBlockingQueue和LinkedBlockingQueue的区别是什么](#ArrayBlockingQueue和LinkedBlockingQueue的区别是什么)   
3.[队列在开源项目中的应用](#队列在开源项目中的应用)   

## Queue有哪几种分类  
`双端队列(Deque)`：双端队列是 Queue 的子类也是 Queue 的补充类，头部和尾部都支持元素插入和获取。具体实现有`LinkedList`  
`阻塞队列(BlockingQueue)`：阻塞队列指的是在元素操作时（添加或删除），如果没有成功，会阻塞等待执行。例如，当添加元素时，如果队列元素已满，队列会阻塞等待直到有空位时再插入。具体实现有`LinkedBlockingQueue`,`ArrayBlockingQueue`,
`DelayQueue`,`PriorityBlockingQueue` .   
`非阻塞队列(AbstractQueue)`：非阻塞队列和阻塞队列相反，会直接返回操作的结果，而非阻塞等待。双端队列也属于非阻塞队列。具体实现有`ConcurrentLinkedQueue`。  

## ArrayBlockingQueue和LinkedBlockingQueue的区别是什么  
1.ArrayBlockingQueue 使用时必须指定容量值，LinkedBlockingQueue 可以不用指定；  
2.ArrayBlockingQueue 的最大容量值是使用时指定的，并且指定之后就不允许修改；而 LinkedBlockingQueue 最大的容量为 Integer.MAX_VALUE；  
3.ArrayBlockingQueue 数据存储容器是采用数组存储的；而 LinkedBlockingQueue 采用的是 Node 节点存储的。    

## 队列在开源项目中的应用  
1.Redisson  
2.消息中间件  