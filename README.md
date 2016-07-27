# TPS
Tool for testing program TPS

2016/7/27

 【原子变量(AtomicLong, AtomicInteger, AtomicReference) 】
 
J2SE 5.0提供了一组atomic class来帮助我们简化同步处理。基本工作原理是使用了同步synchronized的方法实现了对一个long,integer,对象的增、减、赋值（更新）操作. 比如对于++运算符AtomicInteger可以将它持有的integer 能够atomic 地递增。在需要访问两个或两个以上 atomic变量的程序代码（或者是对单一的atomic变量执行两个或两个以上的操作）通常都需要被synchronize以便两者的操作能够被当作是一个atomic的单元。
 对array atomic变量来说，一次只有一个索引变量可以变动，并没有功能可以对整个array做atomic化的变动。
 关于Atomic的几个方法
 getAndSet() : 设置新值，返回旧值.
 compareAndSet(expectedValue, newValue) : 如果当前值(current value)等于期待的值(expectedValue), 则原子地更新指定值为新值(newValue), 如果更新成功，返回true, 否则返回false, 换句话可以这样说: 将原子变量设置为新的值, 但是如果从我上次看到的这个变量之后到现在被其他线程修改了(和我期望看到的值不符), 那么更新失败
 
 【CyclicBarrier】
 
 一个同步辅助类，它允许一组线程互相等待，直到到达某个公共屏障点 (common barrier point)。在涉及一组固定大小的线程的程序中，这些线程必须不时地互相等待，此时 CyclicBarrier 很有用。因为该 barrier 在释放等待线程后可以重用，所以称它为循环 的 barrier。CyclicBarrier 支持一个可选的 Runnable 命令，在一组线程中的最后一个线程到达之后（但在释放所有线程之前），该命令只在每个屏障点运行一次。若在继续所有参与线程之前更新共享状态，此屏障操作 很有用。 
 
 应用场景
 
在某种需求中，比如一个大型的任务，常常需要分配好多子任务去执行，只有当所有子任务都执行完成时候，才能执行主任务，这时候，就可以选择CyclicBarrier了。
