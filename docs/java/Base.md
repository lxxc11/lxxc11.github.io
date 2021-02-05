# 基础知识  
1.[String,StringBuffer和StringBuilder的区别](#String,StringBuffer和StringBuilder的区别)   


## String,StringBuffer和StringBuilder的区别<span id="String,StringBuffer和StringBuilder的区别"></span>   
(1).String类型中使用final关键字修饰来保存字符串，所以String对象是不可变的；而StringBuffer与StringBuilder都继承自AbstractStringBuilder类，而此类没有用final关键字修饰，所以这两种对象是可变的。  
(2).String中的对象是不可变的，也就是可以理解为常量，线程安全；StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。StringBuilder并没有对方法进行同步加锁，所以是非线程安全的。  
(3).每次对String类型进行改变时，都会生成一个新的String对象，然后将指针指向新的String对象；StringBuffer每次都会对StringBuffer对象本身进行操作，而不是生成新的对象并改变对象引用；相同情况下使用StringBuilder比StringBuffer仅能获得10%~15%左右的性能提升，但是却要冒多线程不安全的风险。  
