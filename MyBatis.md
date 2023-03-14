### 1、特性
（1）使用连接池对连接进行管理；
（2）SQL和代码分离，集中管理；
（3）参数映射和动态SQL;
（4）结果集映射；
（5）缓存管理；
（6）重复SQL提取<sql>；
（7）插件机制；
### 2、工作流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674623806507-d24dcbe7-615d-4bbb-adb4-137393d002d1.jpeg)
### 3、缓存工作机制
#### （1）一级缓存
①一级缓存的作用域为session，修改操作会清空一级缓存；
②一级缓存在Executor中，是在一个SqlSession层面进行缓存的，默认是开启一级缓存的；
③在同一个SqlSession（会话）中，多次查询相同的结果，会直接从一级缓存中取出返回，但如果在不同会话中查询相同结果，不会使用一级缓存；
④一级缓存不能跨会话共享，不同的会话之间对于相同的数据可能有不同的缓存结果；
#### （2）二级缓存
①二级缓存作用范围是namespace，可以被多个SqlSession共享；
②二级缓存工作在一级缓存之前，二级缓存封装在CachingExecutor，启用二级缓存，会在创建Executor时对其进行装饰；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674103865373-c5faa590-1eeb-4dee-b716-4dd5a7735a1d.jpeg)
### 4、时序图
```java
InputStream in=Resource.getResourceAsStream(resource);
SqlSessionFactory sqlSessionFactory=new SqlSessionFactoryBuilder().build(in);
SqlSession sqlSession= sqlSessionFactory.openSession();
BlogMapper mapper=sqlSession.getMapper(BlogMapper.class);
Blog blog=mapper.selectBlogById();
sqlSession.close();
```
#### （1）创建会话工厂类，解析配置文件
①创建一个XmlConfigBuilder（同时创建Configuration），用于解析mybtis-config.xml；
②调用parse（）方法，解析xml配置文件（所有mapper.xml和mybatis-config.xml），封装成一个Configuration；
③调用build（）方法，返回一个SqlSessionFactory的默认实现类DefaultSqlSessionFactory
```java
SqlSessionFactory sqlSessionFatory=new 
    SqlSessionFactoryBuilder().build(inputStream);
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674448936681-f8748a74-3223-4732-a102-dbbf1eb5fdeb.jpeg)
#### （2）创建会话（SqlSession）
①创建事务Transaction；
②调用newExecutor(tx, execType)，创建Executor（创建执行器、缓存修饰器装饰、插件代理），Executor是SQL的执行对象;
③返回SqlSession的实现类DefaultSqlSession；
```java
SqlSession sqlSession= sqlSessionFactory.openSession();
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673946787216-97b468a0-d3cd-4cda-8213-2b3073e35064.jpeg)
#### （3）获取代理对象（Mapper对象）
getMapper（）返回一个JDK动态代理类，直接对接口进行代理
```java
BlogMapper mapper=sqlSession.getMapper(BlogMapper.class);
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1673947337018-4b35b32a-a8d7-41e8-8a84-954bb6bb25eb.jpeg)
#### （4）调用代理对象方法，执行SQL
①MethodProxy.inovke()；
②MapperMethod.execute();
③DfaultSqlSession.selectOne();
④CacheExecutor.query（），创建二级缓存CacheKey（使用Hash码快速判重），处理二级缓存；
⑤BaseExecutor.query()；
⑥SimpleExecutor.doQuery()
```java
Blog blog=mapper.selectBlogById();
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674459644947-1dd69a0a-3c0c-4a5c-986b-64c4731b2fff.jpeg)
### 5、Mybatis核心对象
| 对象 | 相关对象 | 作用 |
| --- | --- | --- |
| Configuration | MapperRegistry
TypeAliasRegistry（结构为
map（string,Class<?>））
TypeHandlerRegistry | 包含mybatis所有配置信息 |
| SqlSession | SqlSessionFactory
DefaultSqlSession | 对数据库的增删改查的API进行封装，提供给应用层使用 |
| Executor | BaseExecutor
SimpleExecutor
BatchExecutor
ResueExecutor | Mybatis执行器，调度中心，负责SQL语句的生成和查询缓存以及维护 |
| StatmentHandler | BaseStatmentHandler
SimpleStatmentHandler
PreparedStatmentHandler
CallableStatmentHandler | 封装JDBC的Statment操作，如设置参数，将Statment结果集转换为list |
| ParameterHandler | DefaultParameterHandler | 把用户传入参数转换你为JDBC的参数 |
| ResultSetHandler | DefaultResultSetHandler | 把JDBC的ResultSet结果集转换为list |
| MapperProxy | MapperProxyFactory | 代理Mapper接口 |
| MappedStatment | SqlSource
BoundSql | 维护一条SQL语句，包括Sql的信息，入参，出参 |

### 6、Mybatis插件原理
#### （1）工作流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674628830100-322d13ab-9332-4173-942a-ef66619327c8.jpeg)
#### （2）核心对象
①Interceptor接口：自定义拦截器（实现类）；
②InterceptorChain：存放插件的容器；
③Plugin：h对象，提供创建代理类的方法；
④Invocation：对被代理对象的封装；
### 7、仿写mybatis
#### （1）流程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1674713930297-d079ae8e-7e3a-447e-b038-8ffd1147b0ed.jpeg)
### 8、面试题
#### （1）MyBatis是什么？
①mybatis是开源的数据持久层框架；
②它内部封装了通过JDBC访问数据库的操作，支持普通SQL查询，存储过程和高级映射，几乎消除了所有JDBC代码和参数的手工设置；
③主要的核心思想是将Sql语句与代码分离开来，将SQL语句放置在配置文件中，实现SQL语句的灵活配置，这样可以在不修改代码的情况下，通过修改配置文件来修改SQL语句；
#### （2）Mybatis的工作原理
①读取MyBatis配置文件：mybatis-config为全局配置文件，配置mybatis的运行环境信息；
②加载映射文件：映射文件即SQL映射文件，改文件配置了操作数据库的SQL语句，映射文件需要在mybatis-config文件中加载（XMlConfigBuilder.pareConfiguration中的mapperElement中加载），mybaits-config可以加载多个映射文件，一个映射文件对应一张数据库中的表；
③创建会话工厂：通过配置文件信息构建会话工厂DefaultSqlSessionFactory；
④创建会话对象：调用会话工厂的openSession（）方法创建Sqlsession对象，改对象包含执行SQL语句的所有方法；
⑤创建Executor执行器：Mybatis底层定义了一个接口来操作数据库，它根据sqlsession传入的参数动态的生成sql语句，同时负责查询缓存的维护，在创建Executor过程中，若有外部插件，会执行pluginAll，依次生成代理对象（即多个插件，会生成代理对象的代理对象），所有插件都会实现InvocationHandler接口，执行sql语句时，会调用插件中的invoke（）方法中的代码；
⑥MapperStatment对象：在Executor执行方法中有一个Statment类型的参数，该参数是对映射信息的封装，一个MapperStatment对象对应一条sql语句，它包含sql语句的id等相关信息；
⑦输入参数映射：输入参数映射过程类似于 JDBC 对 preparedStatement 对象设置参数的过程；
⑧输出参数映射：调用handlerResultsets（）方法将数据库类型的数据转换为java类型的数据；
#### （3）Mybatis中的Executor执行器有那些，区别？
①SimpleExecutor：每执行一次update或select，都会创建一个statement对象，用完后就关闭；
②ReuseExecutor：执行update或select，以sql作为key，取statementMap中查找是否存在statement对象,存在就使用，不存在则创建，用完不关闭，存入statementMap中，即重复使用statement对象；
③BatchExecutor：执行update时，将所有的sql通过addBatch（）添加到批处理中，等待统一执行（executeBatch），它缓存多个statement对象，每个statement对象都是addBatch（）执行后，等待统一执行；
#### （4）Mybatis的预编译
①数据库接受sql语句之后，需要词法和语义解析，优化sql语句，若sql语句需要重复执行，每次都要进行语法检查和优化，会浪费大量时间；
②预编译就是将sql语句中的值用占位符替代，生成模板化sql，一次编译，多次运行，省去解析优化过程；
③mybatis底层使用PrepareStatment，默认情况下，将对所有sql语句进行预编译，将#{}替换为？，然后将带有？的sql模板发送至数据库服务器，有数据库服务器对无参的sql语句进行编译后，将编译结果缓存，然后直接执行带有参数的sql语句
④预编译开启后还需要在url中指定useServerPrepStmts=true
#### （5）#{}和${}的区别
①#{}是预编译处理，${}是字符串替换；
②mybatis在处理#{}时，将#{}替换为？，使用PrepareStatement中的set方法来赋值，在处理${}时，会将${}替换为变量；
③#{}可以预防sql注入，采用预编译机制，提前将sql语句进行预编译，在传入参数时，不会对sql进行重新编译
#### （6）通常一个 Xml 映射文件，都会写一个 Dao 接口与之对应， 请问，这个 Dao 接口的工作原理是什么？Dao 接口里的方法， 参数不同时，方法能重载吗？
①dao接口的全类名即为mapper映射文件的namespace值，接口方法名就是MapperStatement的id值，
方法参数即为传递给sql的参数；
②Mapper接口没有实现类，当调用接口时，接口全类名+方法名作为key值，可以寻找MapperStatement对象，MapperStatement对应一个映射文件中的一条sql语句；
③Mapper接口方法不能重载，因为mybatis是以接口全类名+方法名的保存和寻找策略，Mapper接口通过JDK动态代理，生成代理对象，在执行时，代理对象会拦截接口方法，执行MapperStatement代表的sql，然后返回执行结果；
#### （7）Mybatis如何进行分页的？分页插件原理？
①使用mybatis内部的RowBound对象进行分页，他是争对ResultSet结果集进行的内存分页，并非数据库分页；
②使用开源插件Mybatis-PageHelper，该插件实现了Interceptor接口，重写intercept方法，在创建执行器Executor时，通过JDK的动态代理生成Executor的代理类，执行时，先执行分页插件的invoke逻辑，对sql语句进行重写，添加对应的分页语句，最后执行sql语句；

