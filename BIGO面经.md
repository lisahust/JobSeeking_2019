# BIGO面经
@(面试笔试整理)

[TOC]

### BIGO面经JAVA一面

> 作者：村口美丽的二丫
>
> 链接：[https://www.nowcoder.com/discuss/243323?type=post&order=time&pos=&page=1](https://www.nowcoder.com/discuss/243323?type=post&order=time&pos=&page=1)
>
> 来源：牛客网

数据结构了解吗  说下栈和队列的区别说说常用的树 二叉树、二叉搜索树和红黑树的区别
红黑树的优势在哪？怎么实现这个优势的
堆和栈的区别（不是JVM中的）

常用的排序算法有哪些
 说下快排的原理
 快排分到最后是几个元素
 说下堆排序的原理
 final关键字了解吗？说说你对他的理解和原理
 String是不变的吗？怎么实现不变的
 ==和equals的区别
 说一下Java的集合框架
 Arraylist和LinkedList的区别
 说一说Arraylist的扩容原理
 Arraylist和Linkedlist线程安全吗？
 Java中有没有提供线程安全的版本
 说一下CopyonWriteArraylist线程安全的原理
 CopyonWriteArraylist的lock用的是哪个锁
 Hashmap了解吗？说一说他的结构
 说一说HashMap的扩容原理
 说下HashMap在JDK1.7和1.8中的区别
 Hashmap线程安全吗？不安全会带来什么问题？怎么实现线程安全
 ConcurrentHashmap在JDK1.7和1.8中线程安全的原理
 ConcurrentHashmap在JDK1.7中是用什么锁的segment
 sychronized关键字的原理
 sychronized是重量级锁。Java有没有对其做一些优化
 说一下偏向锁、轻量级锁和重量级锁的原理，升级过程
 ReentrantLock是用什么实现的。
 说下AQS的原理。
 CAS的缺点，怎么解决ABA问题
 CAS必须和自旋一起用吗
 说一下JVM的内存模型
 方法区是做什么的
 说一下常用的垃圾收集算法
 说一下标记-清除算法和复制算法以及他们的缺点
 那标记整理算法把他们的缺点解决掉了吗
 垃圾收集器了解哪些？
 说下CMS收集器用的什么算法以及CMS的缺点
 CMS对产生内存碎片的问题有什么解决方案吗
 说下G1收集器的优点
 说下类加载过程，初始化阶段是干什么的
 MySQL索引的原理及实现
 说一下聚族索引和非聚族索引的区别
 like关键字进行查找会用到索引吗
 为什么like后跟%不走索引
 网络有了解吗？说下TCP四次挥手的过程
 哪一方分别能进入TIME-WAIT和CLOSE-WAIT，TIME-WAIT和CLOSE-WAIT分别是做什么的
 什么原因会导致服务端一直CLOSE-WAIT
 说下HTTP协议以及1.0和1.1的区别
 TCP和HTTP的keepalive分别是什么
 说下Spring的IOC，IOC的实现原理
 说下Spring的AOP，AOP的实现原理
 说下Spring有哪几种作用域
 CGLIB和JDK动态代理的区别
 Spring提供事务操作了吗？说下Spring的事务传播等级
 Linux了解吗？说下常用的linux命令
 chmod 777代表什么意思？忘了。那说下chmod有哪几种改变权限的字母
 如果要查看服务器中各个进程CPU的状态用什么命令

### BIGO JAVA一面

作者：wxmnq
链接：[https://www.nowcoder.com/discuss/243661?type=post&order=time&pos=&page=0](https://www.nowcoder.com/discuss/243661?type=post&order=time&pos=&page=0)
来源：牛客网

求一元一次方程的求法，    折半查找，    3.这种解法太慢继续优化，没想出来，最后问了下怎么解，面试官说用牛顿迭代法，啊，一点都没想到！    4.进程和线程之间的区别    5.进程之间的通信    6.消息队列的底层怎么实现，请设计一个BlockQueue    7.HashMap源码讲讲    8.NIO底层实现    9.两个数组求交集，时间复杂度和空间复杂度    10.归并排序实现一下，给你多个排好序的数组，和成一个。    11.TCP拥塞控制原理，滑动窗口具体实现和作用    12.网络拥塞怎么控制

### BIGO JAVA一面

作者：念你成疾LHJ
链接：[https://www.nowcoder.com/discuss/236485?type=post&order=time&pos=&page=1](https://www.nowcoder.com/discuss/236485?type=post&order=time&pos=&page=1)
来源：牛客网

1. ThreadLocal   
2. SpringBoot和Spring的区别，SpringBoot开箱即用怎么说    
3. 强引用、弱引用....    
4. 设计模式    
5. 垃圾回收    
6. volatile    
7. 死锁的条件、解决方法   
8. 数据库并发操作的问题、隔离级别、并发操作怎么解决幻读问题



### BIGO JAVA一面 作者：a少年郎

链接：[https://www.nowcoder.com/discuss/248212?type=post&order=time&pos=&page=1](https://www.nowcoder.com/discuss/248212?type=post&order=time&pos=&page=1)
来源：牛客网

1、自我介绍
 2、深拷贝，浅拷贝
 3、list，set，map的区别
 4、说一下list、map的扩容
 5、set保证不重复的原理
 6、Java内存模型
 7、垃圾收集算法，详细介绍分代收集
 8、计算机网络五层模型
 9、HTTP和HTTPS的区别
 10、HTTPS的加密发生在那一层
 11、tcp和UDP的区别
 12、三次握手四次挥手
 13、tcp保证可靠传输的方法
 14、流量控制和拥塞控制
 15、线程和进程的区别
 16、进程的特点
 17、进程的内存（这个问题可能是我理解错了）
 18、操作系统的内存管理
 19、死锁
 20、多线程一定比单线程快吗
 21、程序执行的过程
 22、从1-12中取至少要取多少个数才能保证其中一定有两个数的差为4