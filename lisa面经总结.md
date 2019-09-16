# lisa面经总结
@(面试笔试整理)

[TOC]

### 头条提前批JAVA一面面经
> 面试时长一个小时，30min手撕了两道代码，但是通过后面试官没有讲题了
> 面试官应该有一个题库 = = 
> 设计模式没答好 = =
> 算法题：[加油站](https://leetcode-cn.com/problems/gas-station/)  [最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

##### 对JAVA最熟悉哪些框架？  
MVC／Spring／SpringBoot

##### SpringBoot和MVC最主要的差别是什么？ 
Spring 框架就像一个家族，有众多衍生产品例如 `boot`、`security`、`jpa`等等。但他们的基础都是Spring 的 ioc和 aop。`ioc` 提供了依赖注入的容器 `aop` ，解决了面向横切面的编程，然后在此两者的基础上实现了其他延伸产品的高级功能。Spring MVC是基于 Servlet 的一个 MVC 框架 主要解决 WEB 开发的问题，因为 Spring 的配置非常复杂，各种XML、 JavaConfig、hin处理起来比较繁琐。于是为了简化开发者的使用，从而创造性地推出了Spring boot，约定优于配置，简化了spring的配置流程。

说得更简便一些：Spring 最初利用“工厂模式”（DI）和“代理模式”（AOP）解耦应用组件。大家觉得挺好用，于是按照这种模式搞了一个 MVC框架（一些用Spring 解耦的组件），用开发 web 应用（ `SpringMVC` ）。然后有发现每次开发都写很多样板代码，为了简化工作流程，于是开发出了一些“懒人整合包”（`starter`），这套就是 `Spring Boot`。


##### IOC 软件的六大设计原则？
1. 开闭原则
2. 里氏代换原则
3. 依赖倒转原则
4. 接口隔离原则
5. 迪米特法则，又称最少知道原则：一个实体应当尽量少地与其他实体之间发生相互作用，使得**系统功能模块相对独立**。
6. 合成复用原则

##### 谈谈设计模式？
按照设计模式的目的进行划分，现有的设计模式可以分为创建型、结构型和行为型三种模式。设计模式具有适应需求变化的优点。
* 创建型模式：abstractfactory抽象工厂模式、builder构造器模式、factorymethod工厂方法模式、prototype原型模式、singleton单例等，
* 结构型模式：adaptor适配器模式、bridge桥接模式、composite组合模式、decorator装饰器模式、facade外观模式、flyweight享元模式和proxy代理模式，
* 行为型模式：chain of responsibility责任链、command命令模式、interpreter解释器模式、iterator迭代器模式、mediator中介者模式、memento备忘录模式、observer观察者模式、state状态模式、strategy策略模式、template method模板方法、visitor访问者模式等。

##### 讲一下进程和线程的概念，区别？再讲一下进程之间是怎么通信的？  ：信号量机制／管道通信
进程间怎么通信的？
- 管道：半双工，只能用于有亲缘关系的进程间的通信
- FIFO：命名管道，可以在无关的进程之间交换数据
- 消息队列：面向记录
- 信号量：用于进程间同步。基于操作系统的PV操作
- 共享内存：指两个或多个进程共享一个给定的存储区

##### 网络的七层架构／五层架构？  ：物理层／数据链路层／网络层／传输层／应用层

##### TCP／UDP／IP／HTTP之间的区别？

##### 讲一下HTTPS？加密的简单工作过程是怎样的？
1. 认证服务器。浏览器内置一个受信任的CA机构列表，并保存了这些CA机构的证书。第一阶段服务器会提供经CA机构认证颁发的服务器证书，如果认证该服务器证书的CA机构，存在于浏览器的受信任CA机构列表中，并且服务器证书中的信息与当前正在访问的网站（域名等）一致，那么浏览器就认为服务端是可信的，并从服务器证书中取得服务器公钥，用于后续流程。否则，浏览器将提示用户，根据用户的选择，决定是否继续。当然，我们可以管理这个受信任CA机构列表，添加我们想要信任的CA机构，或者移除我们不信任的CA机构。

2. 协商会话密钥。客户端在认证完服务器，获得服务器的公钥之后，利用该公钥与服务器进行加密通信，协商出两个会话密钥，分别是用于加密客户端往服务端发送数据的客户端会话密钥，用于加密服务端往客户端发送数据的服务端会话密钥。在已有服务器公钥，可以加密通讯的前提下，还要协商两个对称密钥的原因，是因为非对称加密相对复杂度更高，在数据传输过程中，使用对称加密，可以节省计算资源。另外，会话密钥是随机生成，每次协商都会有不一样的结果，所以安全性也比较高。

3. 加密通讯。此时客户端服务器双方都有了本次通讯的会话密钥，之后传输的所有Http数据，都通过会话密钥加密。这样网路上的其它用户，将很难窃取和篡改客户端和服务端之间传输的数据，从而保证了数据的私密性和完整性。

##### 讲一下最常用的HTTP状态。
- 200 - 请求成功
- 301 - 资源（网页等）被永久转移到其它URL
- 404 - 请求的资源（网页等）不存在
- 500 - 内部服务器错误，无法完成请求
- 502 - Bad Gateway，作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应

|  状态码  |  含义  |
| ---- | ---- |
| 1**	| 信息，服务器收到请求，需要请求者继续执行操作
| 2**	| 成功，操作被成功接收并处理
| 3**	| 重定向，需要进一步的操作以完成请求
| 4**	| 客户端错误，请求包含语法错误或无法完成请求
| 5**	| 服务器错误，服务器在处理请求的过程中发生了错误

##### HTTP断点续传？传一个文件怎么做？
1. 新建一个temp文件，记录断点的位置，也就是上次下载的数量。
2. 采用RandomAccessFile来进行文件读写，RandomAccessFile相当于是一个文件输入输出流的结合。提供了一些在文件中操作位置的方法，比如定位用的getFilePointer( )，在文件里移动用的seek( )，以及判断文件大小的length( )、skipBytes()跳过多少字节数。

##### 讲一下JAVA的GC的算法。

##### 单例模式一般有哪些实现方式？
1. 饿汉式（静态变量）

```
public class Singleton1 {

    private static final Singleton1 INSTANCE = new Singleton1();
    //静态工厂
    public static Singleton1 getInstance(){
        return INSTANCE;
    }

}
```

2. 饿汉式（静态代码块）

```
public class Singleton2 {

    private static Singleton2 instance = null;
    //静态代码块
    static {
        instance = new Singleton2();
    }

    public Singleton2 getInstance(){
        return instance;
    }

}
```

3. 懒汉式（多线程下不可用）

```
public class Singleton3 {

    private static Singleton3 instance = null;

    public static Singleton3 getInstance(){
        if (null == instance){       //（1）
            instance = new Singleton3();   //（2）
        }
        return instance;
    }

}
```

4. 懒汉式（多线程下可用，但效率低）

```
public class Singleton4 {

    private static Singleton4 instance = null;

    public static synchronized Singleton4 getInstance() {
        if (null == instance){
            instance = new Singleton4();
        }
        return instance;
    }
}
```

5. 静态内部类

```
public class Singleton5 {

    private static class insideClass{
        private static final Singleton5 instance = new Singleton5();
    }

    public static Singleton5 getInstance(){
        return insideClass.instance;
    }

}
```

6. 双重检查

```
public class Singleton6 {

    private static volatile Singleton6 instance = null;   //（1）

    private Singleton6(){}

    public static Singleton6 getInstance(){
        if (null == instance){
            synchronized (Singleton6.class){
                if (null == instance){
                    instance = new Singleton6();
                }
            }
        }
        return instance;
    }
}
```

##### 设计一个电商秒杀系统，会有哪些知识点？你会怎么去做？

##### 数据库的索引原理？MYSQL的索引用什么数据结构实现的？为什么用B+树？

##### 对微服务架构你有什么了解？有几个主要的组成部分？

##### 悲观锁和乐观锁的概念？

##### 乐观锁有哪两种实现方式？



----------


### 网易严选提前批JAVA一面面经
> 面试官人很好，一直在微笑。首先问项目，然后问数据库，然后问JAVA基础，然后问JAVA底层，然后问操作系统（linux），然后问计网。
> 面试大概40min。首先从项目开始问，所以一定一定一定要好好准备自己项目里的内容。

##### 1. 详细介绍一下Spring。

**SpringBoot** 就是一个大框架里面包含了许许多多的东西，其中spring就是最核心的内容之一，当然就包含spring mvc。spring boot 我理解就是把 `spring`，`spring mvc`，`spring data`，`jpa` 等等的一些常用的常用的基础框架组合起来，提供默认的配置，然后提供可插拔的设计，就是各种 `starter` ，来方便开发者使用这一系列的技术，套用官方的一句话， `spring` 家族发展到今天，已经很庞大了，作为一个开发者，如果想要使用 `spring` 家族一系列的技术，需要一个一个的搞配置，然后还有个版本兼容性问题，其实挺麻烦的，偶尔也会有小坑出现，其实蛮影响开发进度， `spring boot` 就是来解决这个问题，提供了一个解决方案吧，可以先不关心如何配置，可以快速的启动开发，进行业务逻辑编写，各种需要的技术，加入 `starter` 就配置好了，直接使用，可以说追求开箱即用的效果吧.因为 Spring 的配置太复杂了，各种 `XML` `JavaConfig` 很麻烦，于是懒人改变世界推出了 `Spring boot` 约定优于配置 简化了 spring 的配置流程.

**Spring** 框架有超多的延伸产品例如 boot security jpa etc... 但它的基础就是 spring 的 `ioc` 和 `aop`。`ioc` 提供了依赖注入的容器，`aop` 解决了面向横切面的编程，然后在此两者的基础上实现了其他延伸产品的高级功能。

**spring mvc** 是只是spring 处理web层请求的一个模块。Spring MVC 是基于 `Servlet` 的一个 `MVC` 框架 主要解决 `WEB` 开发的问题 

因此他们的关系大概就是这样： **spring mvc < spring < springboot**。Spring 最初利用**“工厂模式”（ DI ）**和**“代理模式”（ AOP ）**解耦应用组件。大家觉得挺好用，于是按照这种模式搞了一个 MVC 框架（一些用 Spring 解耦的组件），用开发 web 应用（ SpringMVC ）。然后有发现每次开发都要搞很多依赖，写很多样板代码很麻烦，于是搞了一些懒人整合包（ starter ），这套就是 `Spring Boot` 。

##### 2. Spring整个启动的初始化流程介绍一下。
**初始化环境—>加载配置文件—>实例化Bean—>调用Bean显示信息** 

IOC容器的启动是`refresh()`方法开始的。
这个启动包含BeanDefinition的**Resource定位**，**载入**和**注册**三个基本过程。
1. **Resource定位**：即BeanDefinition的资源定位，通过ResourceLoaader的Resource接口完成。
   Spring启动一般是通过加载Sping.xml文件启动，我们以ClassPathXmlApplicationContext为例，一般启动方式为：

```
public class SpringDemoMain {

    public static void main(String[] args) {
        ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("application.xml");
        context.start();
    }
}
```

ClassPathXmlApplicationContext 通过继承实现ResourceLoader已经具备了读取Resource资源的能力。ClassPathXmlApplicationContext通过以下方法初始化`BeanDefinition`资源调用，其中refresh()为具体BeanDefinition的载入过程：

2. **BeanDefinition的载入**：把用户定义的Bean表示成IOC容器的数据结果BeanDefinition。

3. **向IOC容器中注入这些BeanDefinition**的过程：通过调用BeanDefinitionRegistry接口来完成。
   这只是IOC容器初始化过程，不包括Bean依赖注入的过程。在Spring中依赖注入一般发生在应用第一次通过getBean向容器索取Bean的时候。当然也可以配置lazyinit属性决定是否懒加载bean。

##### 3. Spring除了单例模式还有什么其他模式吗？
- **简单工厂**
  spring中的BeanFactory就是简单工厂模式的体现，根据传入一个唯一的标识来获得bean对象，但是否是在传入参数后创建还是传入参数前创建这个要根据具体情况来定。

- **工厂方法**
  一般情况下,应用程序有自己的工厂对象来创建bean.如果将应用程序自己的工厂对象交给Spring管理,那么Spring管理的就不是普通的bean,而是工厂Bean。在各种`BeanFactory`以及`ApplicationContext`创建中都用到了

- **单例模式**：保证一个类仅有一个实例，并提供一个访问它的全局访问点
  spring中的单例模式完成了后半句话，即提供了全局的访问点`BeanFactory`。但没有从构造器级别去控制单例，这是因为spring管理的是是任意的java对象。核心提示点：Spring下默认的bean均为`singleton`，可以通过singleton=“true|false” 或者 scope=“？”来指定。

- **包装器**：在spring的`applicationContext`中配置所有的`dataSource`。这些`dataSource`可能是各种不同类型的，比如不同的数据库：Oracle、SQL Server、MySQL等，也可能是不同的数据源：比如apache 提供的org.apache.commons.dbcp.BasicDataSource、spring提供的org.springframework.jndi.JndiObjectFactoryBean等。然后`sessionFactory`根据客户的每次请求，将`dataSource`属性设置成不同的数据源，以到达切换数据源的目的。spring中用到的包装器模式在类名上有两种表现：一种是类名中含有`Wrapper`，另一种是类名中含有`Decorator`。基本上都是动态地给一个对象添加一些额外的职责。

- **代理模式**：
  在Spring的Aop中，使用的Advice（通知）来增强被代理类的功能。Spring实现这一**AOP功能**的原理就使用代理模式（1、JDK动态代理。2、CGLib字节码生成技术代理。）对类进行方法级别的切面增强，即，生成被代理类的代理类， 并在代理类的方法前，设置拦截器，通过执行拦截器重的内容增强了代理方法的功能，实现的面向切面编程。

- 策略模式：定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可独立于使用它的客户而变化。 
  spring中在**实例化对象**的时候用到Strategy模式

- 观察者模式：定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。spring中Observer模式常用的地方是listener的实现。如ApplicationListener。

- 模板方法：


##### 4. 讲一讲Spring的事务。
事务有四个特性：ACID。
Spring事务管理器的接口是`org.springframework.transaction.PlatformTransactionManager`，通过这个接口，Spring为各个平台如JDBC、Hibernate等都提供了对应的事务管理器，但是具体的实现就是各个平台自己的事情了。
- **JDBC事务**：如果应用程序中直接使用JDBC来进行持久化，`DataSourceTransactionManager`会为你处理事务边界。
- **Hibernate事务**：如果应用程序的持久化是通过Hibernate实习的，那么你需要使用`HibernateTransactionManager`。
- **Java持久化API事务（JPA）**：Hibernate多年来一直是事实上的Java持久化标准，但是现在Java持久化API作为真正的Java持久化标准进入大家的视野。如果你计划使用JPA的话，那你需要使用Spring的`JpaTransactionManager`来处理事务。
- **Java原生API事务**：如果你没有使用以上所述的事务管理，或者是跨越了多个事务管理源（比如两个或者是多个不同的数据源），你就需要使用`JtaTransactionManager`

##### 5. MongoDB配置使用的流程（因为我做了相关项目）。
1. 下载mongodb
2. 配置存放日志和数据的目录（要手动创建文件路径）
3. 创建一个`mongodb.config` 配置文件，有两个属性logpath和dbpath，分别设定值，就是刚才我们配置的路径
4. 运行`mongo`命令测试以下链接
5. 安装`mongo-connector`实现二者数据同步，命令： pip install mongo-connector, 自动会安装相应的组件，例如pysolr，pymongo。

##### 6. 怎么配置MongoDB的管理节点。（没用过）

##### 7. MongoDB的查询方式。

mongoDB中的collection相当于数据库中的表。

```
// 通过连接字符串得到一个数据库实例的连接
Mongo mongo = new Mongo("127.0.0.1", 27017);

// 获得一个数据库对象
DB db = mongo.getDB("solrdata");

// 声明一个collection1对象
DBCollection coll = db.getCollection("collection1");
```

solrj进行查询：

```
// 查询的时候直接生成一个HttpSolrClient客户端
private static final String SOLR_URL = "http://localhost:8080/solr/collection1";
// 执行查询返回QueryResponse
QueryResponse response = client.query(query);
// 获取doc文档
SolrDocumentList documents = response.getResults();
System.out.println("查询结果的总数量：\n" + documents.getNumFound());
```

##### 8. 介绍一下Restful（因为我做了相关项目）。
RESTful是一种软件架构风格、设计风格，而不是标准，只是提供了一组设计原则和约束条件。它主要用于客户端和服务器交互类的软件。基于这个风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。

在服务器端，应用程序状态和功能可以分为各种资源。资源是一个有趣的概念实体，它向客户端公开。资源的例子有：应用程序对象、数据库记录、算法等等。每个资源都使用 URI (Universal Resource Identifier) 得到一个唯一的地址。所有资源都共享统一的接口，以便在客户端和服务器之间传输状态。使用的是标准的 HTTP 方法，比如 GET、PUT、POST 和 DELETE。

要让一个资源可以被识别，需要有个唯一标识，在Web中这个唯一标识就是URI(Uniform Resource Identifier)。

URI既可以看成是资源的地址，也可以看成是资源的名称。如果某些信息没有使用URI来表示，那它就不能算是一个资源， 只能算是资源的一些信息而已。URI的设计应该遵循可寻址性原则，具有自描述性，需要在形式上给人以直觉上的关联。

RESTful架构应该遵循**统一接口原则**，统一接口包含了一组受限的预定义的操作，不论什么样的资源，都是通过使用相同的接口进行资源的访问。接口应该使用标准的HTTP方法如GET，PUT和POST，并遵循这些方法的语义。**统一资源接口**要求使用**标准的HTTP方法**对资源进行操作，所以URI只应该来表示资源的名称，而不应该包括资源的操作。客户端通过HTTP方法可以获取资源，是吧? 不，确切的说，**客户端获取的只是资源的表述**而已。 资源在外界的具体呈现，可以有多种表述(或成为表现、表示)形式，在客户端和服务端之间传送的也是资源的表述，而不是资源本身。 

##### 9. MySQL默认的隔离级别？
`innodb` 默认是可重复读隔离级别.
- 数据库默认隔离级别:  `mysql : repeatable` ; `oracle,sql server : read commited`
- 为什么mysql用的是`repeatable`而不是`read committed`: 在 5.0之前只有`statement`一种格式，而**主从复制**存在了大量的不一致，故选用repeatable
- 为什么默认的隔离级别都会选用`read commited` 原因有二：repeatable存在**间隙锁**会使**死锁的概率增大**，在RR隔离级别下，条件列未命中索引会锁表！而在RC隔离级别下，只锁行

项目中是不用读未提交(Read UnCommitted)和串行化(Serializable)两个隔离级别，原因有二:
- 采用读未提交(Read UnCommitted),一个事务读到另一个事务未提交读数据，这个不用多说吧，从逻辑上都说不过去！
- 采用串行化(Serializable)，每个次读操作都会加锁，快照读失效，一般是**使用mysql自带分布式事务功能时才使用串行化隔离级别**！(笔者从未用过mysql自带的这个功能，因为这是XA事务，是强一致性事务，性能不佳！互联网的分布式方案，多采用最终一致性的事务解决方案！)

##### 10. 讲一讲事务的四个隔离级别。
| 事务隔离级别  | 脏读  | 不可重复读 |   幻读
| ---- | ---- | ---- | ---- |
| 读未提交（read-uncommitted）|   是 |   是 |   是
| 读已提交/不可重复读（read-committed）  |  否 |   是 |   是
| 可重复读（repeatable-read）  |  否  |  否 |   是
| 串行化（serializable）  |  否  |  否 |   否

##### 11. 讲一讲幻读是什么。
指的是一个事务在前后两次查询同一个范围的时候，后一次查询看到了前一次查询没有看到的数据行。幻读引发的问题：(1)语义有问题.(2)数据不一致性。


##### 12. 讲一讲MySQL的索引的底层原理。（B+树索引）
1. MyISAM引擎使用**B+Tree**作为索引结构，叶节点的data域存放的是数据记录的地址；
   MyISAM主索引和辅助索引在结构上没有任何区别，只是主索引要求key是唯一的，而辅助索引的key可以重复。Myisam 引擎是采用的 `B+Tree` 结构来作为索引结构。由于 Myisam 中的索引和数据分别存放在不同的文件，所以在索引树中的叶子节点中存的数据是该索引对应的数据记录的地址，由于数据与索引不在一起，所以 `Myisam` 是非聚簇索引。

2. InnoDB的数据文件本身就是**索引文件**，叶节点包含了完整的数据记录，这种索引叫做**聚集索引**。
   因为InnoDB的数据文件本身要按主键聚集，所以InnoDB要求表必须有主键（MyISAM可以没有），如果没有显式指定，则MySQL系统会自动选择一个可以唯一标识数据记录的列作为主键，如果不存在这种列，则MySQL自动为InnoDB表生成一个隐含字段作为主键。
   InnoDB的**辅助索引data域**存储相应记录主键的值而不是地址；
   辅助索引搜索需要检索两遍索引：首先检索辅助索引获得主键，然后用主键到主索引中检索获得记录；
   InnoDB 是通过 `B+Tree` 结构**对 ID 建索引**，然后**在叶子节点中存储记录**。采用 InnoDB 引擎的数据存储文件有两个，一个**定义文件**，一个是**数据文件**。

##### 13. 聚簇索引和非聚簇索引有什么区别？
在MySQL中，最常用的两个存储引擎是MyISAM和InnoDB，它们对索引的实现方式是不同的。
- **MyISAM**：data存的是**数据地址**。索引是索引，数据是数据。索引放在XX.MYI文件中，数据放在XX.MYD文件中，所以也叫**非聚集索引**。
- **InnoDB**：data存的是**数据本身**。索引也是数据。数据和索引存在一个XX.IDB文件中，所以也叫**聚集索引**。

两种存储引擎的区别：
1. MyISAM是**非事务安全**的，而InnoDB是**事务安全**的
2. MyISAM锁的粒度是**表级**的，而InnoDB支持**行级锁**
3. MyISAM支持**全文类型索引**，而InnoDB**不支持全文索引**
4. MyISAM相对简单，效率上要优于InnoDB，**小型应用可以考虑使用MyISAM**
5. MyISAM表保存成**文件形式**，跨平台使用更加方便
6. MyISAM管理**非事务表**，提供高速存储和检索以及全文搜索能力，如果在应用中执行大量select操作可选择。
7. InnoDB用于**事务处理**，具有ACID事务支持等特性，如果在应用中执行大量insert和update操作，可选择。

##### 14. B+树叶子结点
B树是一种多路搜索树。

B树和B+树的区别：
- B+树的非叶子结点只包含导航信息，不包含实际的值，所有的叶子结点和相连的节点使用链表相连，便于区间查找和遍历。
- B树每个节点都存储key和data，所有节点组成这棵树，并且叶子节点指针为null。B+树只有叶子节点存储data，叶子节点包含了这棵树的所有键值，叶子节点不存储指针。后来，在B+树上增加了顺序访问指针，也就是每个叶子节点增加一个指向相邻叶子节点的指针。

用过MySQL的同学都知道高效查询需要走索引，否则全表读取会导致慢SQL。`InnoDB`的索引是采用**B+树**实现的。B+树是B树的一种变形，它把所有的卫星数据都存储在叶节点中，内部节点只存放关键字和孩子指针，因此最大化了内部节点的分支因子，所以B+树的遍历也更加高效(B树需要以中序的方式遍历节点，而B+树只需把所有叶子节点串成链表就可以从头到尾遍历)。

B+树还有一个最大的好处，**方便扫库**，B树必须用中序遍历的方法按序扫库，而B+树直接从叶子结点挨个扫一遍就完了，B+树支持`range-query`非常方便，而B树不支持。这是数据库选用B+树的最主要原因。

##### 15. 怎么建立联合索引？有什么建议。有什么约束。使用的时候有什么建议？
怎么创建联合索引：
创建单个索引的语法：`create index 索引名 on 表名（字段名）`
创建联合索引的语法：`create index 索引名 on 表名（字段名1，字段名2）`

索引的最左原则（左前缀原则），如（c1,c2,c3,c4....cN）的联合索引，where 条件按照索引建立的字段顺序来使用（不代表and条件必须按照顺序来写），如果中间某列没有条件，或使用like会导致后面的列不能使用索引。

组合索引注意事项：
- 索引应该建在**选择性高的字段上**（键值唯一的记录数/总记录条数），选择性越高索引的效果越好、价值越大，唯一索引的选择性最高；
- 组合索引中字段的顺序，**选择性越高的字段排在最前面**；
- where条件中包含两个选择性高的字段时，可以考虑**分别创建索引**，引擎会同时使用两个索引（在OR条件下，应该说必须分开建索引）；
- **不要重复创建彼此有包含关系的索引**，如index1(a,b,c) 、index2(a,b)、index3(a)；
- **组合索引的字段不要过多**，如果超过4个字段，一般需要考虑拆分成多个单列索引或更为简单的组合索引；

##### 16. 垃圾回收。四个垃圾回收机制的算法。
垃圾收集器是垃圾回收算法（标记-清除算法、复制算法、标记-整理算法、火车算法）的具体实现，不同商家、不同版本的JVM所提供的垃圾收集器可能会有很在差别，本文主要介绍HotSpot虚拟机中的垃圾收集器。
Serial、ParNew、Parallel Scavenge、Serial Old、Parallel Old、CMS、G1；

**新生代收集器**：Serial、ParNew、Parallel Scavenge；
**老年代收集器**：Serial Old、Parallel Old、**CMS**；
**整堆收集器**：G1；

四个垃圾回收机制的算法：
1. **标记清除**：缺点 1）产生大量不连续的内存碎片 2）标记和清除效率都不高
2. **复制**：它将可用内存按照容量划分为大小相等的两块，每次只使用其中一块。当这一块的内存用完了，则就将还存活的对象复制到另一块上面，然后再把已经使用过的内存空间一次清理掉。
3. **标记整理**：标记过程和“标记-清除”算法一样，但后续步骤不是直接对可回收对象进行清除，而是让 all 存活对象都向一端移动，然后直接清理掉端边界以外的内存。
4. **分代回收**：新生代 停止-复制算法 ，老年代 标记-清理或标记-清除

##### 17. 讲一讲CMS的原理和G1的原理。G1相对于CMS的优点。
并发标记清理（Concurrent Mark Sweep，CMS）收集器也称为并发低停顿收集器（Concurrent Low Pause Collector）或低延迟（low-latency）垃圾收集器；

1. 初始标记：标记老年代中所有的GC Roots引用的对象，标记老年代中被年轻代中活着的对象引用的对象。
2. 并发标记：从初始化标记阶段找到的GC Roots开始进行Tracing，找到所有的存活对象。
3. 重新标记：标记在并发标记阶段引用发生变化的对象，如果发现对象的引用发生变化，则JVM会标记堆的这个区域为Dirty Card。
4. 并发清除：移除那些不同的对象，并回收占用的内存空间。

cms只会回收**老年代和永久带**（1.8开始为元数据区，需要设置CMSClassUnloadingEnabled），不会收集年轻带；cms是一种**预处理垃圾回收器**，它不能等到old内存用尽时回收，**需要在内存用尽前，完成回收操作，否则会导致并发回收失败**；所以cms垃圾回收器开始执行回收操作，有一个触发阈值，默认是老年代或永久带达到92%；

G1垃圾收集器：
1. 分代： CMS中，堆被分为PermGen，YoungGen，OldGen；而YoungGen又分了两个survivo区域。在G1中，**堆被平均分成几个区域**(region)，在每个区域中，虽然也保留了新老代的概念，但是收集器是**以整个区域为单位收集**的。 
2. 算法： 相对于CMS的“标记——清理”算法，G1会使用**压缩算法，保证不产生多余的碎片**。收集阶段，G1会将某个区域存活的对象拷贝的其他区域，然后将整个区域整个回收。 
3. **停顿时间可控**： 为了缩短停顿时间，G1建立可预存停顿模型，这样在用户设置的停顿时间范围内，G1会选择适当的区域进行收集，确保停顿时间不超过用户指定时间。



##### 18. 线程池的实现，有哪些接口，常数，怎么控制。讲一讲线程池的参数。
当一个任务提交至线程池之后， 
1. 线程池首先判断核心线程池里的线程是否已经满了。如果不是，则创建一个新的工作线程来执行任务。否则进入2. 
2. 判断工作队列是否已经满了，倘若还没有满，将线程放入工作队列。否则进入3. 
3. 判断线程池里的线程是否都在执行任务。如果不是，则创建一个新的工作线程来执行。如果线程池满了，则交给饱和策略来处理任务。

线程池的六个参数：
1. corePoolSize：核心线程数
* 核心线程会一直存活，即使没有任务需要执行
* 当线程数小于核心线程数时，即使有线程空闲，线程池也会优先创建新线程处理
* 设置allowCoreThreadTimeout=true（默认false）时，核心线程会超时关闭

2. queueCapacity：任务队列容量（阻塞队列）
    * 当**核心线程数达到最大时**，新任务会放在**队列中**排队等待执行

3. maxPoolSize：最大线程数
    * 当线程数>=核心线程数corePoolSize，且任务队列已满时。线程池会**创建新线程**来处理任务
    * 当线程数=最大线程数maxPoolSize，且任务队列已满时，线程池会**拒绝处理任务**而抛出异常

4. keepAliveTime：线程空闲时间
    * 当线程空闲时间达到keepAliveTime时，线程会退出，默认情况下直到线程数量=corePoolSize
    * 如果allowCoreThreadTimeout=true，则会直到线程数量=0

5. allowCoreThreadTimeout：允许核心线程超时
    * 默认情况下核心线程不会退出，可通过将该参数设置为true，让核心线程也退出。

6. rejectedExecutionHandler：任务拒绝处理器
    * ThreadPoolExecutor.AbortPolicy: 丢弃任务并抛出RejectedExecutionException异常。
    * ThreadPoolExecutor.DiscardPolicy：也是丢弃任务，但是不抛出异常。
    * ThreadPoolExecutor.DiscardOldestPolicy：丢弃队列最前面的任务，然后重新尝试执行任务（重复此过程）
    * ThreadPoolExecutor.CallerRunsPolicy：由调用线程处理该任务

##### 19. 核心队列，最大线程数在什么时候会生效，会触发。
临时线程就是除了核心线程之外的线程
等待队列里放的是任务不是线程。
**JDK中线程池**是优先加入队列，当队列满了，且当前线程数量没有达到最大线程的时候，会优先创建临时线程。JDK下的临时线程创建是在：新任务加入时，队列已被填满，同时核心线程数没有达到最大线程数的时候。
**Tomcat的线程池**是优先创建临时线程，当临时线程达到最大值才会加入队列。

##### 20. 讲讲java的锁机制。CAS。
`Synchronized`关键字会让没有得到锁资源的线程进入`BLOCKED`状态，而后在争夺到锁资源后恢复为`RUNNABLE`状态，这个过程中涉及到操作系统用户模式和内核模式的转换，代价比较高。尽管Java1.6为`Synchronized`做了优化，增加了**从偏向锁到轻量级锁再到重量级锁**的过度，但是在最终转变为重量级锁之后，性能仍然较低。

所谓原子操作类，指的是`java.util.concurrent.atomic`包下，一系列以Atomic开头的包装类。例如`AtomicBoolean`，`AtomicInteger`，`AtomicLong`。它们分别用于Boolean，Integer，Long类型的原子性操作。`Atomic`操作类的底层，正是利用了**CAS机制**。

CAS属于乐观锁，乐观地认为程序中的并发情况不那么严重，所以让线程不断去尝试更新。这个重新尝试的过程被称为自旋。在Java1.6以上版本，Synchronized转变为重量级锁之前，也会采用CAS机制。CAS就是 有3个操作数，**内存值V**，**旧的预期值A**，**要修改的新值B**。当且仅当预期值A和内存值V相同时，将内存值V修改为B，否则什么都不做。 如何保证获得的当前值是内存中的最新值呢？很简单，用`volatile`关键字来保证。真正要做到严谨的CAS机制，我们在Compare阶段不仅要比较期望值A和地址V中的实际值，还要比较**变量的版本号是否一致**。（防止ABA问题）

CAS的缺点：
1. CPU开销较大：在并发量比较高的情况下，如果许多线程反复尝试更新某一个变量，却又一直更新不成功，循环往复，会给CPU带来很大的压力。
2. 不能保证代码块的原子性：CAS机制所保证的只是一个变量的原子性操作，而不能保证整个代码块的原子性。比如需要保证3个变量共同进行原子性的更新，就不得不使用Synchronized了。
3. ABA问题

##### 21. volatile的实现原理。
Java语言提供了volatile，在某些情况下比锁更加方便。如果一个字段被声明成volatile，java线程内存模型确保所有线程看到这个变量的值是一致的。
对volatile变量的写操作与普通变量的主要区别有两点： 
1. 修改volatile变量时会强制将修改后的值刷新的主内存中。 
2. 修改volatile变量后会导致其他线程工作内存中对应的变量值失效。因此，再读取该变量值的时候就需要重新从读取主内存中的值。 
   通过这两个操作，就可以解决volatile变量的可见性问题。

##### 22. currentHashMap具体怎么使用
JDK1.8的currentHashMap参考了1.8HashMap的实现方式,采用了数组,链表,红黑树的实现方式,其中大量的使用CAS操作.CAS(compare and swap)的缩写,也就是我们说的比较交换.CAS是一种基于锁的操作,而且是乐观锁.
java的锁中分为乐观锁和悲观锁.悲观锁是指将资源锁住,等待当前占用锁的线程释放掉锁,另一个线程才能够获取线程.乐观锁是通过某种方式不加锁,比如说添加version字段来获取数据
CAS操作包含三个操作数-----**内存位置,预期的原值,和新值**.如果内存的值和预期的原值是一致的,那么就转化为新值.CAS是通过不断的循环来获取新值的,如果线程中的值被另一个线程修改了,那么A线程就需要**自旋**,到下次循环才有可能执行

以下是jdk1.8中的Node结点,其中的val和next都通过可见性修饰。

```
static class Node<K,V> implements Map.Entry<K,V> {
        final int hash;
        final K key;
        volatile V val;
        volatile Node<K,V> next;

        Node(int hash, K key, V val, Node<K,V> next) {
            this.hash = hash;
            this.key = key;
            this.val = val;
            this.next = next;
        }
}
```

##### 23. CAS check的字段是哪里，set到哪里去？
CAS check的字段是预期的原址和内存中的实际值，set到预期的原址和内存中的实际值。

##### 24. synchronize的以前到现在的过程。（轻量级锁等）
jdk1.6对锁的实现引入了大量的优化，如**自旋锁、适应性自旋锁、锁消除、锁粗化、偏向锁、轻量级锁**等技术来减少锁操作的开销。
锁主要存在四种状态，依次是：**无锁状态**、**偏向锁状态**、**轻量级锁状态**、**重量级锁状态**，他们会随着竞争的激烈而逐渐升级。注意锁可以升级不可降级，这种策略是为了提高获得锁和释放锁的效率。

- 所谓**自旋锁**，就是让该线程等待一段时间，不会被立即挂起，看持有锁的线程是否会很快释放锁。怎么等待呢？执行一段无意义的循环即可（自旋）。
- JDK 1.6引入了更加聪明的自旋锁，即**自适应自旋锁**。所谓自适应就意味着自旋的次数不再是固定的，它是由前一次在同一个锁上的自旋时间及锁的拥有者的状态来决定。
- **锁消除**：对不可能存在共享数据竞争的锁进行消除。
- **锁粗化**：将连续的加锁 精简到只加一次锁
- 引入**偏向锁**主要目的是：为了在无多线程竞争的情况下尽量减少不必要的轻量级锁执行路径。**无竞争条件下 消除整个同步互斥，连CAS都不操作。**当线程访问同步块时，首先会使用 `CAS`将线程 ID 更新到锁对象的 `Mark Word`中，如果**更新成功则获得偏向锁**，并且之后每次进入这个对象锁相关的同步块时都不需要再次获取锁了。 
- 引入**轻量级锁**的主要目的是在多没有多线程竞争的前提下，减少传统的重量级锁使用操作系统互斥量产生的性能消耗。**无竞争条件下，通过CAS消除同步互斥。**当关闭偏向锁功能或者多个线程竞争偏向锁导致偏向锁升级为轻量级锁，则会尝试获取轻量级锁。线程进入同步代码块之前，线程会在栈帧中记录锁信息的区域`Lock Record`，同时将锁的对象头`Mark Word`拷贝到`Lock Record`，使用`CAS`将`Mark Word`更新为指向锁记录的指针：如果更新成功，**当前线程获取锁**。如果失败，表示其他线程竞争锁，当前线程尝试**使用自旋来获取锁**。

##### 25. 类加载的机制/双亲委派。
在完成代码的编写之后，编译器会将我们的java文件编译成对应的class文件（二进制字节码文件），而类加载器的作用便是在用到这些class的时候将其加载到JVM中，生成对应的class对象。类加载的过程：**加载->链接->初始化**。链接分为3个小部分，**验证、准备、解析**。

1. **加载**：加载是类加载的第一个阶段，通过类的全限定名来找到对应的class文件，将此class文件生成一个class对象。
2. **验证**：验证的目的在于确保class文件的字节流中包含信息符合当前虚拟机要求，不会危害虚拟机自身安全。主要包括四种验证，文件格式验证，元数据验证，字节码验证，符号引用验证；
3. **准备**：给静态方法和静态变量赋予初值，比如static int a；给其中的a赋予初值为0，但是这里不会给final修饰的静态变量赋予初值，因为被final修饰的静态变量在编译期间就已经被赋予初值了；
4. **解析**：主要将常量池中的符号引用替换为直接引用的过程。
5. **初始化**：类加载最后阶段，若该类具有超类，则对其进行初始化，执行静态初始化器和静态初始化成员变量(如前面只初始化了默认值的static变量将会在这个阶段赋值，成员变量也将被初始化。

执行以上类加载过程的就是类加载器。系统给我们提供的类加载器有三种：**启动类加载器**、**扩展类加载器**和**系统类加载器**。
1. **启动类（Bootstrap）加载器**：主要被用于加载java所需的核心jar包，它负责将 `<JAVA_HOME>/lib`路径下的核心类库或`-Xbootclasspath`参数指定的路径下的jar包加载到内存中，属于顶级类加载器。
2. **扩展类（Extension）加载器**：它负责加载`<JAVA_HOME>/lib/ext`目录下或者由系统变量`-Djava.ext.dir`指定位路径中的类库。
3. **系统类（System）加载器**：它负责加载系统类路径`java -classpath`或`-D java.class.path` 指定路径下的类库，也就是我们经常用到的`classpath`路径，开发者可以直接使用系统类加载器，一般情况下该类加载是程序中默认的类加载器，通过`ClassLoader#getSystemClassLoader()`方法可以获取到该类加载器。

说到类加载器就不得不说到其**双亲委派模式**，类加载器在加载类的时候如果有父加载器，会优先将加载任务委托给父类加载器执行，若父类加载还有父类加载器，则进一步委托给上层的父类加载器，直到委托给顶层类加载器（Bootstrap ClassLoader），因为顶层类加载器已经没有父类加载器了。然后由父类加载器进行类的加载，**若加载失败，则逐级向下由子加载器类进行加载**。
1. 双亲委派模式**使得类的加载有了层级优先级**，通过这种层级的优先级来保证加载过的类**不会被重复加载**，父类已经加载过的类，子类没有必要再去加载一次。
2. 其次是为了**安全**，比如`Bootstrap ClassLoader`会加载JVM需要的核心java包，这时候网络上传来了一个名字是`java.lang.Integer`的类，Bootstrap ClassLoader检测到该类已经被加载过了，所以直接返回Class，而不是重新加载，便可以**防止核心API库被随意篡改**。

##### 26. 破坏双亲委派的场景。加载同一个类怎么做。
破坏双亲委派的场景：
1. 双亲委派模型的第一次“被破坏”其实发生在双亲委派模型出现之前--即JDK1.2发布之前。由于双亲委派模型是在JDK1.2之后才被引入的，而类加载器和抽象类`java.lang.ClassLoader`则是JDK1.0时候就已经存在，面对**已经存在的用户自定义类加载器的实现代码**，Java设计者引入双亲委派模型时不得不做出一些妥协。
2. 双亲委派模型的第二次“被破坏”是这个模型自身的缺陷所导致的，双亲委派模型很好地解决了各个类加载器的基础类统一问题(越基础的类由越上层的加载器进行加载)，基础类之所以被称为“基础”，是因为它们总是作为被调用代码调用的API。但是，如果**基础类又要调用用户的代码**，那该怎么办呢？为了解决这个困境，Java设计团队只好引入了一个不太优雅的设计：**线程上下文件类加载器(Thread Context ClassLoader)**。这个类加载器可以通过java.lang.Thread类的setContextClassLoader()方法进行设置，如果创建线程时还未设置，它将会从父线程中继承一个；如果在应用程序的全局范围内都没有设置过，那么这个类加载器默认就是应用程序类加载器。
3. 双亲委派模型的第三次“被破坏”是由于**用户对程序的动态性的追求**导致的，例如**OSGi**的出现。在OSGi环境下，类加载器不再是双亲委派模型中的树状结构，而是进一步发展为网状结构。

**沿用双亲委派机制自定义类加载器**很简单，只需继承ClassLoader类并重写findClass方法即可。
怎么**打破双亲委派机制**？
1. 继承一个类加载器
2. 重写loadclass方法，重写了这个方法以后就能自己定义加载的方式了。没有优先交给父类加载器，这就打破了双亲委派机制。
3. 重写findclass方法

##### 27. 遇到了死锁，死循环该怎么办。该怎么查询？JAVA自带的命令知道吗？
主要方法：`top` 、`jstack`
1. 找到java进程的pid。打开cmd，输入`jps`命令，jps很简单可以直接显示java进程的pid。`jps` 命令类似与 linux 的 `ps` 命令，但是它**只列出系统中所有的 Java 应用程序**。 通过 `jps` 命令可以方便地查看 Java 进程的启动类、传入参数和 Java 虚拟机参数等信息。或者输入`tasklist`，找到javaw.exe的PID。
2. 输入`jstack 7588`命令，找到跟我们自己代码相关的线程。
3. 写个小程序，调用wait使其中一线程等待。同样我们先找到javaw.exe的PID，再利用`jstack`分析该PID，很快我们就找到了一个线程处于WAITING状态，在Test.java文件13行处，正是我们调用wait方法的地方，说明该线程目前还没等到notify

##### 28. TCP和HTTP了解过吗？time_wait状态讲一下。

si

- 什么时候会TIME_WAIT？
  TCP在关闭的时候有个四次挥手的过程，主动关闭方在四次挥手的最后一个ACK发送之后会变成`TIME_WAIT`状态。我们必须假象网络是不可靠的，有可以最后一个ACK丢失。所以`TIME_WAIT`状态就是用来**重发可能丢失的ACK报文**。在Client发送出最后的ACK回复，但该ACK可能丢失。Server如果没有收到ACK，将不断重复发送FIN片段。所以Client不能立即关闭，它必须确认Server接收到了该ACK。

- TIME_WAIT状态存在的理由：
1. 可靠地实现**TCP全双工连接**的终止。
   TCP在关闭的时候有个四次挥手的过程，主动关闭方在四次挥手的最后一个ACK发送之后会变成TIME_WAIT状态。
2. 允许老的重复分节在网络中消逝。
   TCP分节可能由于路由器异常而“迷途”， 在迷途期间，TCP发送端可能因确认超时而重发这个分节，迷途的分节在路由器修复后也会被送到最终目的地，这个原来的迷途分节就称为lost duplicate。为了避免这个情况，TCP不允许处于`TIME_WAIT`状态的连接启动一个新的化身，因为`TIME_WAIT`状态持续2MSL，就可以**保证当成功建立一个TCP连接的时候，来自连接先前化身的重复分组已经在网络中消逝。**

- 为什么TIME_WAIT状态需要经过2MSL(最大报文段生存时间)才能返回到CLOSE状态？
  Server如果没有收到ACK，将不断重复发送FIN片段。所以Client不能立即关闭，它必须确认Server接收到了该ACK。Client会在发送出ACK之后进入到TIME_WAIT状态。Client会设置一个计时器，等待2MSL的时间。如果在该时间内再次收到FIN，那么Client会重发ACK并再次等待2MSL。所谓的2MSL是两倍的**最长分节生命期**(Maximum Segment Lifetime)。MSL指一个片段在网络中最大的存活时间，2MSL就是一个发送和一个回复所需的最大时间。如果直到2MSL，Client都没有再次收到FIN，那么Client推断ACK已经被成功接收，则结束TCP连接。

##### 29. 如果有大量的有很多time_wait怎么办？
在**高并发短连接**的TCP服务器上，当服务器处理完请求后立刻主动正常关闭连接。这个场景下会出现大量socket处于TIME_WAIT状态。如果客户端的并发量持续很高，此时部分客户端就会显示连接不上。
1. **高并发**可以让服务器在短时间范围内同时占用大量端口，而端口有个0~65535的范围，并不是很多，刨除系统和其他服务要用的，剩下的就更少了。
2. 在这个场景中，**短连接**表示“业务处理+传输数据的时间 远远小于 TIMEWAIT超时的时间”的连接。

如何尽量处理TIMEWAIT过多？
1. `echo "1" > /proc/sys/net/ipv4/tcp_tw_reuse`  让`TIME_WAIT`状态可以重用，这样即使TIME_WAIT占满了所有端口，也不会拒绝新的请求造成障碍。不建议打开的。不能重用端口可能会造成系统的某些服务无法启动
2. `echo "1" > /proc/sys/net/ipv4/tcp_tw_recycle` 让`TIME_WAIT`尽快回收
3. 编辑内核文件，修改系统默认的TIMEOUT时间。然后执行 `/sbin/sysctl -p` 让参数生效.
4. 修改`ipv4.ip_local_port_range`，增大可用端口范围，但只能缓解问题，不能根本解决问题


----------


### 网易严选提前批JAVA二面面经
> 面试官人很好，一直在微笑。首先问项目，然后问数据库，然后问JAVA基础，然后问JAVA底层，然后问操作系统（linux），然后问计网。
> 面试大概40min。首先从项目开始问，所以一定一定一定要好好准备自己项目里的内容。





### 猿辅导提前批JAVA一面凉经

> 15min自我介绍+项目介绍+基础知识
>
> 40min代码

1. 详细讲一下你的项目
2. 详细说一下gc，gc的算法，垃圾回收收集器
3. 如果在整理的过程中，还可以再分配内存吗？
4. 算法题：int [] arr = {1,2,2,3,3,3,3,4,4,4,5,5,10}. k = 2.    如果次数大于2就删除。返回{1,2,2,5,5,10}
5. 算法题：一个双向链表，拆成奇数链表和偶数链表。


### 猿辅导提前批JAVA二面凉经

> 自我介绍+介绍项目+基础知识+手撕代码
> 一共40min

1. 说说乐观锁、悲观锁、可重入锁、公平锁
2. 讲讲你对数据库事务的理解（我讲了ACID和四大隔离机制）
3. 加入一个事务中第三个操作失败会怎么办？
4. 数据库查询的连接，左连接和右连接。
5. 说说DNS服务，DNS服务想解决什么问题？
6. 手撕代码：用一个链表实现入队和出队两个操作，用O(1)的时间复杂度。


### 京东校招JAVA一面凉经

> 自我介绍+介绍项目+基础知识
> 一共40min
> 因为是电面记不清问了啥了 = =

1. Spring的启动过程
2. 数据库中的索引
3. java的反射机制，怎么改变private。
4. 讲讲线程池的六个参数。
5. 类加载的整个生命周期。
6. 场景题：共享汽车有一个黑名单，如何在海量数据中查出该人是否在黑名单中？（面试官提示用位图法bitmap）