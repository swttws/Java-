### 1、spring编程思想
（1）OOP：面向对象编程（封装，继承，多态），用程序来描述生活中的一切事务；写出人更容易理解的设计；
（2）BOP：面向Bean编程，解放程序员双手，提出一种代码的管理理念，Spring理念一切从Bean开始；
（3）AOP：面向切面编程（面向规则编程），找出多个Bean中有一定规律的代码，开发时，将其拆开，运行时合并；（解耦）
①切面（Aspect）：通常是一个类，里面可以定义切入点和通知；
②JoinPoint（连接点）：程序执行过程中明确的点，一般是方法的调用；
③Advice（通知）：回调，在特定切入点上执行增强处理；
④Pointcut（切入点）：带有通知的连接点，程序中主体书写表达式；
（4）IOC：控制反转，控制权反转，创建对象的控制权反转给Spring（BeanFactory），我们只需要使用即可；
（5）DI：依赖注入，Spring不仅能创建对象，他能够保存对象语对象之间的关联关系，自动赋值，主要三种赋值方式：构造方法，set赋值，直接赋值；

---

### 2、Spring相关信息
#### （1）BeanFactory
为Ioc容器的顶层设计，提供能够管理任何类型对象的高级配置机制；
#### （2）ApplicationContext
①继承BeanFactory，一般默认为Ioc容器，容器负责创建，配置和管理bean；
②实现类一般为ClassPathXmlApplicationContext or FileSystemXmlApplicationContext；
③T getBean(String name, Class<T> requiredType) 可以获取bean的实例；

---

### 3、Spring核心类容器类图
#### （1）BeanFactory
① HierarchicalBeanFactory 表示的是 这些 Bean 是有继承关系的，也就是每个 Bean 有可能有父 Bean；
② ListableBeanFactory 接口表示这些 Bean 是可列表化的  ；
③  AutowireCapableBeanFactory 接 口定义 Bean 的自动装配规则  
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1672389029018-a5ff4395-2ee0-4d05-9889-cb16b06fcee3.png#averageHue=%232e2e2e&clientId=u66b2c34a-0825-4&from=paste&height=413&id=uf40e80c0&name=image.png&originHeight=619&originWidth=1216&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35285&status=done&style=none&taskId=u950a3a64-276f-4d8a-866c-261d5b5aed2&title=&width=810.6666666666666)
#### （2）BeanDefinition
  SpringIOC 容器管理了我们定义的各种 Bean 对象及其相互的关系，Bean 对象在 Spring 实现中是 以 BeanDefinition 来  
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1672390208337-99087bf7-aa8f-4cba-bb9d-28173da9276f.png#averageHue=%232f2e2e&clientId=u66b2c34a-0825-4&from=paste&height=375&id=u82df0628&name=image.png&originHeight=563&originWidth=954&originalType=binary&ratio=1&rotation=0&showTitle=false&size=31046&status=done&style=none&taskId=ue736f060-7a4d-4201-863b-b98446a2754&title=&width=636)
#### （3） BeanDefinitionReader  
     Bean 的解析主要就是对 Spring 配置文件的解析，这个解析过程主要通过 BeanDefintionReader 来完成；  
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1672390410298-655be351-c99c-4737-8c9a-802946293d38.png#averageHue=%23302f2f&clientId=u66b2c34a-0825-4&from=paste&height=232&id=u597b78db&name=image.png&originHeight=348&originWidth=781&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18183&status=done&style=none&taskId=u4a1d69b7-a5e9-4928-842c-f7b8357ea10&title=&width=520.6666666666666)

---

### 4、仿写spring
#### （1）ioc中三个重要的类
①调用servlet的init（）方法，创建ApplicationContext；
②读取配置文件；
③扫描相关类，配置文件保存到内存中的BeanDefinition；
④初始化ioc容器，并且实例化对象（BeanWrapper）；
⑤完成依赖（DI）注入
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672633880022-3273922b-c66b-4ee1-a5d1-1bd004d1f31d.jpeg)
#### （2）ioc工作流程
①读取配置文件；
②解析配置文件，并且封装成BeanDefinition；
③把beanDefinition对应的实例放入容器缓存（（存储到map中，key为beanName，value为BeanDefinition））；
#### （3）DI工作流程
①循环读取BeanDefinition的缓存信息；
②调用geBean（）方法创建对象实例；
③将创建好的对象封装成BeanWrapper对象；
④将BeanWrapper缓存到ioc容器中；
⑤循环ioc容器执行依赖注入；
#### （4）springMVC工作流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672728815782-63368940-824d-4d51-81fb-e9a75543bc7f.jpeg)
#### （5）AOP设计
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672802950198-9d7da857-83b3-4998-9891-efad8f6e2eb5.jpeg)

---

### 5、SpringIOC容器的初始化
#### （1）定位：定位配置文件和扫描相关注解；
#### （2）加载：将配置信息载入到内存中；
#### （3）注册：根据载入的信息，将对象初始化到IOC容器中
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672388165705-55bf370b-4c06-40ac-8f33-be01636a445a.jpeg)
#### （4）基于XML的IOC容器初始化（ClassPathXmlApplicationContext ）
##### 【1】时序图
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672409267941-f2b7f9fd-8bde-4dff-82c9-95400fb4b648.jpeg)
##### 【2】为容器设置Bean资源加载器
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1672397511939-8f4ce8f7-0298-4234-b3fd-15786151f47b.png#averageHue=%23312b2a&clientId=u66b2c34a-0825-4&from=paste&height=223&id=u390e5992&name=image.png&originHeight=335&originWidth=1161&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42800&status=done&style=none&taskId=uf7c1bbc2-8283-47e1-9bc6-004afc2626a&title=&width=774)
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672399046303-4119c352-c233-44d5-a9a9-73d7e728074b.jpeg)
##### 【3】创建ioc容器
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672410257707-5270e410-5bb1-4138-881a-9086479e656c.jpeg)
##### 【4】载入配置文件
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672462112954-b3b6785c-83b5-409e-aaec-1b11925720e8.jpeg)
##### 【5】分配路径处理策略
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672464425161-7362e20d-fb98-470c-8fbf-4e807c14a952.jpeg)
##### 【6】解析配置文件路径
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672464032595-7c353d8a-ac29-42fe-b3a9-3a832c5926f1.jpeg)
##### 【7】开始读取配置文件
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672465018065-689da30e-6e33-4fa4-965d-e01011441fdf.jpeg)
##### 【8】准备文档对象
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672465908712-a0466690-81bb-4842-9f85-6aa3e1e8245e.jpeg)
##### 【9】分配解析策略
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672466570182-7adbeb74-73ba-4889-971e-3dce81240d43.jpeg)
##### 【10】将配置载入内存
spring首先会将导入元素加载进入bean容器中， 使用别名时，Spring IOC 容器首先将别名元素所 定义的别名注册到容器中 ；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672467674162-fc87af1e-e60b-4828-a6a4-9dd01f652226.jpeg)
##### 【11】载入bean, property , list元素
 在解析元素过程中没有创建和实例化 Bean 对象，只是创建了 Bean 对象的定义类 BeanDefinition，将元素中的配置信息设置到 BeanDefinition 中作为记录，当依赖注入时才 使用这些记录信息创建和实例化具体的 Bean 对象。 
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672468825989-c491d7ce-a412-4269-b868-9d2ae41d8992.jpeg)
##### 【12】分配注册策略
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672471162944-ee86c32e-45a9-4c26-be96-529994961b9d.jpeg)
##### 【13】向容器注册
 DefaultListableBeanFactory 中 使 用 一 个 HashMap 的 集 合 对 象 存 放 IOC 容 器 中 注 册 解 析 的 BeanDefinition；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672473225584-5c1b7cee-570f-41ed-b2ec-e00c9de8bec1.jpeg)
#### （5）基于Annotation的ioc容器初始化（AnnotationConfigApplicationContext）
##### 【1】定位ean的扫描路径
① 直接将注解 Bean 注册到容器中  ；
② 通过扫描指定的包及其子包下的所有类  ；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672477304232-da948dab-d5a0-45c4-b28e-f042eca06f9e.jpeg)
##### 【2】 读取 Annotation 元数据  
传入初始参数为具体Bean定义的注解类时，注解容器读取并配置
###### ① AnnotationConfigApplicationContext 通过调用注解 Bean 定义读取器  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672478735216-a90c5137-706e-4277-b1ac-3b06a27bad67.jpeg)
###### ② AnnotationScopeMetadataResolver 解析作用域元数据  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672480396962-21658552-13d1-45f1-a609-9164f50f88a4.jpeg)
###### ③ AnnotationConfigUtils 处理注解 Bean 定义类中的通用注解  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672481832076-83626a1e-3d29-411e-bd3a-28a09177f0a7.jpeg)
###### ④ AnnotationConfigUtils 根据注解 Bean 定义类中配置的作用域为其应用相应的代理策略  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672483421728-cef4997d-0912-450a-a7fc-e3953f3bbc64.jpeg)
###### ⑤ BeanDefinitionReaderUtils 向容器注册 Bean  
将Bean添加到hashmap容器中
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672484337629-308c50c0-7c05-443a-961e-59a210168f1c.jpeg)
##### 【3】 扫描指定包并解析为 BeanDefinition  
当创建注解容器时，传入的初始参数为注解Bean所在包时，注解容器将扫描给定包以及子包，将扫描到的注解Bean注册到容器中。
###### ① ClassPathBeanDefinitionScanner 扫描给定的包及其子包  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672485730035-5ce58bcd-e35c-4281-98dd-0985b4cccc93.jpeg)
###### ② classPathScanningCandidateComponentProvider 扫描给定包及其子包的类  
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1672487512507-7263819e-2d3c-45c9-b640-2e1fb02bd5aa.jpeg)
### 6、Sprin自动装配——依赖注入（DI）
#### （1）说明
①实例化：目标类配置aop，实例化代理类对象；目标类没有配置aop，实例化原生对象；
②BeanWrapper统一封装实例化对象信息，统一对外访问对象的入口，扩展一些功能，缓存一些配置信息；
#### （2）依赖注入执行细节
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672900378959-b64d3104-614e-4102-9bb8-16cac6ea5c1f.jpeg)
#### （3）时序图
①createBeanInstance（）：反射创建一个对象实例，封装为BeanWrapper；
②populateBean（）：根据beanName，BeanDefinition，BeanWrapper找到需要赋值的属性，把需要赋值的属性封装成一个集合，集合的元素PropertyValue，PropertyValue保存需要赋值的bean，赋值需要调用的方法，要赋什么值；
③applyPropertyValues（）：循环PropertyValue，挨个调用BeanWrapper的setValue（）方法，用反射调用setter方法完成注入；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672914427409-8a8b1178-40e2-4ac4-bd1b-e47c09dba5b0.jpeg)

---

### 7、SpringAOP
#### （1）流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672983220478-d52fc1f4-cda5-4095-9c9b-76d92288d2cb.jpeg)
#### （2）时序图
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1672995183729-164f69a6-6fa1-4fb6-be92-1d5097fb4a33.jpeg)

---

### 8、SpringMVC
#### （1）请求处理流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673101476795-dcae3245-f7ab-4849-ad14-24ef9d9e6b46.jpeg)
#### （2）时序图
①DispatcherServlet：init（）方法，初始化九大组件；
②DispatcherServlet：doService（）方法：
getHandler（）方法获取HandlerMapping
getHandlerAdapter（HandlerMapping）获取Adapter
adapter.handler（）获取ModelAndView
processDispathRequest（） view.render（）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673086635542-1cc48d3c-1f3a-45e9-b208-b230397c0afc.jpeg)
#### （3）核心组件关联关系
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673104690948-aef5286a-8848-4ba2-8d9a-2186f099da41.jpeg)

---

### 9、Spring事务
#### （1）Connection
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673331494760-a9106a7f-ca1a-43d6-844e-8fb319ba0f7c.jpeg)
#### （2）事务流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673330390182-0b8f752b-d6ed-49a0-9843-729fb2123910.jpeg)
#### （3）事务原理
①将满足条件的数据放入内存中；
②对数据进行操作，并检查是否有错；
③没有错误，写入持久化空间；
④有错误，返回异常，并且终止持久化操作；
⑤结果返回客户端；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673335216139-9583eeb9-277a-49af-9574-7bd6aaca6d64.jpeg)
### 10、Spring经典面试题
#### （1）Spring框架好处
①提供内置的解决方案BOP（面向Bean编程），IOC（控制反转），AOP（面向切面编程）；
②声明式事务管理，TransactionManager；
③简化开发，解放双手；
④提供诸多工具类，围绕Spring生态，如JdbcTemplate
#### （2）BeanFactory和ApplicationContext区别
①ApplicationContext是BeanFacctory的子接口；
②BeanFactory是顶层设计，而ApplicationContext是用户接口；
③一般认为ApplicationContext就是IOC，IOC的功能是在DefaultListableBeanFactory类实现的，有共同接口BeanFactory；
![image.png](https://cdn.nlark.com/yuque/0/2023/png/29496365/1673508140640-54a706fa-c0fa-4f09-bbf1-cac824eef216.png#averageHue=%232f2f2e&clientId=ue36cf5e4-2f7a-4&from=paste&height=278&id=u425585bb&name=image.png&originHeight=417&originWidth=1180&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30375&status=done&style=none&taskId=u50669a0d-c408-462b-8703-36c08727957&title=&width=786.6666666666666)
④BeanFactory包含各种Bean的定义，以便在收到客户端请求时将对应的Bean实例化；
⑤ApplicationContext除具有BeanFactory功能外，还提供统一资源读取方式，提供支持国际化文本信息；
#### （3）Spring Bean生命周期
①如果是单例，从spring容器的启动到spring容器的销毁，如果是延时加载，则是在调用前创建对象；
②如果是prototype，在调用前创建，调用后销毁；
③createBeanInstance() -> 实例化，populateBean() -> 属性赋值，initializeBean() -> 初始化，销毁 Destruction
#### （4）Spring Bean各种作用域之间区别
①singleton作用域全局，在任何地方可以通过ioc容器拿到它,只会拿到唯一实例；在容器创建时同时主动创建bean对象，每次获取对象都是同一个对象；
②prototype全局的，在创建容器时并没有实例化，在获取bean时才会去创建一个对象，每次获取的对象都不一样；
③request在一次请求发起和结束之间；
④session 一个session创建和session失效之间，默认30分钟；同一个session共享一个bean；
#### （5）Spring中的Bean是线程安全吗
spring中Bean是否线程安全与Spring无关，和你自己写的代码有关
#### （6）Spring中用到那些设计模式
工厂模式、单例模式（容器式单例）、原型模式（容器式多例）、代理模式、享元模式，门面模式，适配器模式、委派模式（DispatcherServlet对请求进行分发）、装饰器模式，责任链模式、解释器模式
#### （7）Spring，SpringBoot，SpringCloud区别
①Spring为已有生态，它能够完成日常开发的所有功能。
②SpringBoot简化开发，Spring简不够，配置文件多，配置管理，维护麻烦；springboot内置配置，需要配的覆盖，不需覆盖实现零配置；全面servlet化，能够自运行，部署也简单了，一个jar包可以到处运行；提供一套脚手架，一键搭建，节省时间；
③SpringCloud：正式进入分布式，注册中心，服务发现，监控，配置中心，负载，熔断，链路追踪..；不需要自己整合，一站式；
④springcloud依赖springboot，springboot依赖spring；
#### （8）Spring事务怎么传播
①execute（）原始的逻辑，拿到DataSource，Connection；
②一个方法A调用同一个类的另外一个方法B，B的事务不会生效
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673522159160-3a3ccc36-e683-4120-87ee-646f68625001.jpeg)
#### （9）BeanFactory和FactoryBean区别
①BeanFactory是ioc容器的顶层设计；
②FactoryBean用来构建Bean的包装类；
#### （10）对AOP的理解
①在原始的OOP编程中，允许定义从上到下的功能，但对从左到右的定义则是无能为力，像日志功能代码，往往是遍布所有对象层面中，这些代码与业务方法无关，这样将会导致大量重复代码的出现；
②在AOP编程中，提供一种横切技术，将封装的对象切开，将影响多个类的公共行为封装到一个公共类中，这个称为切面，切面即为与业务代码无关，却为业务模块所共同调用的逻辑封装起来，便于减少代码的重复性，降低代码之间的耦合度，并利于未来的可维护性（切面方法修改时，只用修改切面中的方法即可，不用到调用该方法的业务逻辑中修改）；在spring中，aop的主要是在实例化bean（initializeBean()）时实现的，将被代理类方法与切面方法存储到一个methodCache，被代理类方法为key，切面方法封装为InterceptorAndDynamicMethodMatcher对象作为value，在实例化时判断是否需要代理，需要的话，通过动态代理，将切面方法织入业务方法中，并生成代理类，保存到ioc容器中。
#### （11）对IOC的理解
①ioc就是将对象的管理权交给spring来管理；传统的开发方式是通过new进行对象创建，是由程序主动创建；而ioc是有专门的一个容器来创建这些对象；
②控制反转，主要控制外部资源的获取；传统程序是我们在对象中主动控制去获取依赖对象，即正转，反转则是由容器来创建以及注入依赖对象，ioc容器帮我们查找及注入依赖对象，对象是被动接受依赖对象（依赖对象获取被反转）；
③ioc可以使用代码解耦传统开发中，对象A需要对象B，A对象实例化B对象，A对象就对B对象产生依赖；而使用spring后，对象创建好后保存在ioc容器中，A对象需要B对象时，由容器进行注入，A对象无需关心容器是如何创建B对象，控制权在ioc容器上，从而达到松耦合。
#### （12）依赖注入的理解
①组件之间的依赖关系由容器运行期决定的，即由容器动态的将某个依赖对关系注入到组件中；通过依赖注入，我们只需通过简单的配置文件，而无需代码就可以指定目标需要的资源，完成自身逻辑，不需要关心具体的资源来自何处；
②谁依赖谁：应荣程序依赖于ioc容器；
③为什么需要依赖：应用程序需要ioc容器来提供对象需要的外部资源；
④谁注入谁：ioc容器注入应用程序某个对象，应用程序依赖的对象；
⑤注入什么：注入对象所需的外部资源（对象，资源，常量数据）；
#### （13）Spring如何解决循环依赖
①出现循环依赖的bean必须是单例（原型会诬陷创建bean，spring会直接抛出异常）；
②不全是构造器注入的方式，；
③一级缓存（singletonObjects）：单例bean实例化+初始化完成后，会加入一级缓存；
④二级缓存（singletonFactories）：用于存放实例化完成，未初始化的bean，用于解决循环依赖问题
⑤三级缓存（earlySingletonObjects）：存放单例对象工厂ObjectFactory，与二级缓存不同的是，它可以应对产生代理对象；
⑥流程：【1】A首先getBean（），开始在容器中获取单例A，第一次容器不存在，开始创建A；
【2】A实例化完后，但未初始化，将A与对应的ObjectFactory存入三级缓存，若A被Aop代理，使用ObjectFactory获取到的是A的代理对象，否则未实例对象；
【3】A初始化（A属性赋值），需要注入B，找不到B，B调用getBean（）；
【4】B已被实例化完，但未初始化，将B与ObjectFactory存入三级缓存中；
【5】初始化B（B对象属性赋值），需要注入A，三级缓存找到A，得到A的引用（A的代理类），将B加入二级缓存，从三级缓存删除；
【6】B注入从对象工厂获得的A的引用，此时B已经初始化完成，将B加入到一级缓存，并将B在二级缓存、三级缓存中的玩意清除，返回
【7】回到初始化A，在一级缓存找到B，注入B，将A加入一级缓存，从二三级缓存删除；
⑦使用三级缓存原因：延迟实例化后生成代理对象的，如果使用二级缓存，意味bean实例化完后，就要创建代理类，违背spring的执行流程，spring是在bean声明周器的最后一步来完成AOP代理，而不是在实例化后创建代理类；

