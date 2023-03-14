### 一、集合体系结构
1、单列集合:单个元素存放
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662299852938-b021d31f-08de-4b4b-9b0c-a9fdbad38a43.png#averageHue=%23fdfdfc&clientId=u152b0d7a-93af-4&from=paste&height=336&id=uaa1f059a&name=image.png&originHeight=504&originWidth=1018&originalType=binary&ratio=1&rotation=0&showTitle=false&size=23003&status=done&style=none&taskId=u1e729537-c62c-4de5-9e2b-c040622cdec&title=&width=678.6666666666666)
2、双列集合：键值对存放
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662300068523-d94893c5-97bc-48d8-9664-90323e8345c5.png#averageHue=%23fdfdfd&clientId=u152b0d7a-93af-4&from=paste&height=273&id=ue1920ad8&name=image.png&originHeight=409&originWidth=1058&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16302&status=done&style=none&taskId=ucc537f98-ef0d-4965-85ee-36b24b41d30&title=&width=705.3333333333334)

### 二、List接口
#### 1、ArrayList
（1）是线程不安全，维护一个Object数组；（transient表示不会被序列化）
（2）创建ArrayList对象时，若使用无参构造，初始容量为0，第一次添加扩容为10，再次扩容，则扩容为数组长度的1.5倍；
（3）使用指定大小构造器，初始化数组长度为指定大小，扩容直接扩容为原来的1.5倍

无参构造器创建和使用：
1、创建空的elementData数组
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662386035438-8199bb19-392f-4995-b856-372bc06e8f27.png#averageHue=%23fcfcfb&clientId=udc8353da-3e74-4&from=paste&height=75&id=u52f09d88&name=image.png&originHeight=112&originWidth=946&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15189&status=done&style=none&taskId=u3c453871-1b60-4d8a-a498-03d56418e8f&title=&width=630.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662386005349-7d93a9e1-361d-4dc7-93fb-e73222619e04.png#averageHue=%23f9f8f3&clientId=udc8353da-3e74-4&from=paste&height=61&id=u36962b30&name=image.png&originHeight=92&originWidth=1067&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15908&status=done&style=none&taskId=u48b208bb-c865-438b-a68a-ecf2079a4ed&title=&width=711.3333333333334)
2、执行添加方法list.add()源码分析：
（1）ensureCapacityInternal（）方法，先确定是否需要扩容；
（2）然后执行赋值操作![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662386299483-3ef4736b-8c55-4f8a-8651-d70304f863d9.png#averageHue=%23fcfbfa&clientId=udc8353da-3e74-4&from=paste&height=134&id=u6a7a3990&name=image.png&originHeight=201&originWidth=1147&originalType=binary&ratio=1&rotation=0&showTitle=false&size=28875&status=done&style=none&taskId=uf1a20c8c-9ad9-4de1-a110-0b6fca46970&title=&width=764.6666666666666)
该方法确定minCapacity最小容量，第一次扩容miniCapacity默认为10
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662386499377-15961b9c-27a3-4d4e-9046-6c48d7f29a3f.png#averageHue=%23faf9f8&clientId=udc8353da-3e74-4&from=paste&height=154&id=f7GqC&name=image.png&originHeight=231&originWidth=975&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36992&status=done&style=none&taskId=u7a301a4d-83be-4fd9-8d5e-f3316ecd915&title=&width=650)
判断是否需要扩容：
（1）modCount++记录集合修改次数
（2）如果数组elementData大小不够，则进行扩容grow（）方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662386726286-589c6d99-586f-4a99-a80e-34854418fca9.png#averageHue=%23fbfaf8&clientId=udc8353da-3e74-4&from=paste&height=155&id=u10b72327&name=image.png&originHeight=233&originWidth=888&originalType=binary&ratio=1&rotation=0&showTitle=false&size=33746&status=done&style=none&taskId=u81a38c90-d3b4-45ec-b400-4d00571b666&title=&width=592)
扩容：
（1）oldCapacity记录原先数组大小；
（2）newCapacity记录扩容后数组的长度，相当于扩容1.5倍；
（3）判断是否为第一次扩容，若第一次扩容，newCapacity-minCapacity<0，则默认扩容长度为10；
（4）数组扩容，使用Arrays.copyof（）扩容，原先保存数据保留。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662387031579-3988e52a-72c6-4911-b5ca-e628fd2634bb.png#averageHue=%23faf8f7&clientId=udc8353da-3e74-4&from=paste&height=248&id=uf1cbd045&name=image.png&originHeight=372&originWidth=1077&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75677&status=done&style=none&taskId=u2cb3974b-fe2f-41b6-9bb2-cfe9c9bc5db&title=&width=718)
注意：idea默认情况下，debug显示数据为简化后，看完整数据需要设置
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662388460316-c77bd9c3-cdea-4ca1-9967-e1fa95341bf6.png#averageHue=%23d2a563&clientId=udc8353da-3e74-4&from=paste&height=430&id=u67b2e503&name=image.png&originHeight=645&originWidth=1454&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75265&status=done&style=none&taskId=u1bc30cc5-c613-4ab2-9837-0c099e074a4&title=&width=969.3333333333334)

有参构造器的创建和使用：
创建一个指定大小的数组initialCapacity,扩容直接按照1.5倍扩容，其余机制与无参构造一致。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662429984328-9b51535a-ad05-4121-977a-2eb1a7db55f9.png#averageHue=%23fafaf8&clientId=u65903592-72b9-4&from=paste&height=221&id=u6dca5310&name=image.png&originHeight=332&originWidth=1015&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53127&status=done&style=none&taskId=ub0f0f079-982c-4bcc-a30f-ab628776196&title=&width=676.6666666666666)


#### 2、Vector（线程安全）
初始化，按照10个空间大小分配
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662431317628-c46c02f2-d6c6-44c8-ad2d-5ce90f80edcb.png#averageHue=%23fbfafa&clientId=u65903592-72b9-4&from=paste&height=72&id=u38af0f24&name=image.png&originHeight=108&originWidth=696&originalType=binary&ratio=1&rotation=0&showTitle=false&size=11520&status=done&style=none&taskId=u31cdfdf7-3ac3-48ac-9a84-b86ab0a1da3&title=&width=464)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662431362379-8e62e50e-6798-4404-ae62-3cafe59dc16e.png#averageHue=%23fafaf9&clientId=u65903592-72b9-4&from=paste&height=79&id=udb425016&name=image.png&originHeight=118&originWidth=817&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15910&status=done&style=none&taskId=u78ec0246-5245-4274-a585-ddf21aedca8&title=&width=544.6666666666666)
vector.add()
添加数据到vector
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662431571363-0263ab51-4fc6-4da5-b1d5-416026582236.png#averageHue=%23fbfaf7&clientId=u65903592-72b9-4&from=paste&height=137&id=u94a3d56b&name=image.png&originHeight=206&originWidth=902&originalType=binary&ratio=1&rotation=0&showTitle=false&size=28233&status=done&style=none&taskId=u6463364d-c3b4-4baf-b72c-4a031f93d21&title=&width=601.3333333333334)
确定是否需要扩容
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662431624572-f928664a-0822-42fc-b399-3037a81de2f4.png#averageHue=%23fbfaf9&clientId=u65903592-72b9-4&from=paste&height=117&id=u10c077b8&name=image.png&originHeight=175&originWidth=953&originalType=binary&ratio=1&rotation=0&showTitle=false&size=29373&status=done&style=none&taskId=u8dd0e649-a7f5-42dd-8147-fbb013940a5&title=&width=635.3333333333334)
数组扩容，扩容两倍
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662431656165-5caf1930-0fea-4cea-9632-eb3fb79c2543.png#averageHue=%23faf9f7&clientId=u65903592-72b9-4&from=paste&height=240&id=ua57bccd8&name=image.png&originHeight=360&originWidth=1046&originalType=binary&ratio=1&rotation=0&showTitle=false&size=78442&status=done&style=none&taskId=ub2c5e4ea-4daf-4f70-95fb-622c9a69712&title=&width=697.3333333333334)


#### 3、LinkedList
1、特点：
（1）底层实现了双向链表和双端队列；
（2）可以添加任意元素，包括null；
（3）没有线程安全。
2、add（）源码
执行add方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662434998426-ecdf79ed-0a51-4ee1-88e6-64d52d451545.png#averageHue=%23fbfaf7&clientId=u65903592-72b9-4&from=paste&height=95&id=uda0eed42&name=image.png&originHeight=142&originWidth=692&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13494&status=done&style=none&taskId=u405f4472-4f33-4cd3-b396-f6bf56fecd5&title=&width=461.3333333333333)
linkLast(E e)方法：将新节点加入链表最后
（1）用l记录尾节点；
（2）创建新节点存储插入值，前指向，后指向；
（3）尾指针指向插入节点；
（4）判断原来是否为第一次插入，l==null为第一次插入，头指针指向插入节点，若不是第一次插入，插入元素之前链表的尾元素的后指针指向插入元素；
（5）长度+1，修改次数+1；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662435061751-3c2a4dfc-8249-41e1-bb00-dd1eed6ea6e8.png#averageHue=%23fcfbfa&clientId=u65903592-72b9-4&from=paste&height=243&id=uc909f7c0&name=image.png&originHeight=364&originWidth=971&originalType=binary&ratio=1&rotation=0&showTitle=false&size=41029&status=done&style=none&taskId=uf7226580-d311-4f2d-a7f9-2d283ae041d&title=&width=647.3333333333334)
3、remove（）源码
执行remove（），默认删除第一个节点
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662468863028-ef4fb6b8-c447-4f92-9ec5-ffa54ae26fb3.png#averageHue=%23fbfaf9&clientId=u96efbd4d-3dfc-4&from=paste&height=81&id=u67613e46&name=image.png&originHeight=122&originWidth=726&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12139&status=done&style=none&taskId=u41b6baac-1db6-4a25-b725-3179b48a290&title=&width=484)
removeFirst（）判断链表是否为空，为空抛出异常，不为空进入删除操作
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662468917000-3d94ca88-3cfe-4b3b-98f1-c4b990ccb325.png#averageHue=%23fbfafa&clientId=u96efbd4d-3dfc-4&from=paste&height=137&id=u5b9458ee&name=image.png&originHeight=206&originWidth=1003&originalType=binary&ratio=1&rotation=0&showTitle=false&size=27301&status=done&style=none&taskId=u2398f972-3e8c-4594-8aa0-ee8c8a8e071&title=&width=668.6666666666666)
unlinkFirst（）方法执行删除
（1）使用element记录删除元素的值；
（2）使用next记录删除节点的下一个节点；
（3）删除节点；
（4）头指针指向删除节点的下一个节点；
（5）判断删除节点的下一个节点是否为空·，为空，尾指针指向null，不为空，next节点的前指针指向null
（6）链表长度减一，修改次数+1，返回删除的元素
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662469137995-6b579fb2-709e-4cdd-b6dc-7c3555bdbfc2.png#averageHue=%23fbfbfa&clientId=u96efbd4d-3dfc-4&from=paste&height=332&id=u4eebe714&name=image.png&originHeight=498&originWidth=926&originalType=binary&ratio=1&rotation=0&showTitle=false&size=56828&status=done&style=none&taskId=u434166d0-aec0-4903-a55c-a68c934d59f&title=&width=617.3333333333334)

#### 4、ArrayList和LinkedList比较
|  | 底层 | 增删效率 | 改查效率 |
| --- | --- | --- | --- |
| ArrayList | 可变数组 | 较低，数组扩容 | 较高 |
| LinkedList | 双向链表 | 较高 | 较低 |

（1）改查多，使用ArrayList；
（2）增删多，使用LinkedList


### 三、Set接口
#### 1、HashSet
（1）底层是一个HashMap，如下图
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662471441466-5ee4428c-01d0-44f5-8b5f-1891a94f859f.png#averageHue=%23fbfaf9&clientId=u96efbd4d-3dfc-4&from=paste&height=85&id=u5fbcc602&name=image.png&originHeight=127&originWidth=826&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13391&status=done&style=none&taskId=u92683339-7755-4296-803c-075c9302851&title=&width=550.6666666666666)
（2）HashSet不保证元素是有序的；
（3）HashSet存放元素不能重复。
（4）底层数组一个链表元素达到8个，且数组大小为64，进行树化
（5）去重机制：hashCode（）+equals（），底层通过存入对象，进行运算得到一个hash值，通过hash值得到对应索引，如果发现索引所在位置没有数据，直接存放，如果存在数据，进行equals（）比较【遍历比较】，比较不相同，就加入，否则不加入
add（）源码：
执行add（）添加方法，为空表明添加成功
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662516119824-37048afb-3904-4aa0-8ccd-c525fac11a5c.png#averageHue=%23fbfbf9&clientId=ue3c169ae-56ca-4&from=paste&height=80&id=ub125c9b1&name=image.png&originHeight=120&originWidth=777&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14815&status=done&style=none&taskId=u6f0dfe31-d697-42af-9069-caa57784bbc&title=&width=518)
执行put（）方法，value为PRESENT共享
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662516199187-2d88adfe-102c-4711-a0c1-e47199414eae.png#averageHue=%23f9f8f4&clientId=ue3c169ae-56ca-4&from=paste&height=92&id=u33ffdb1c&name=image.png&originHeight=138&originWidth=1120&originalType=binary&ratio=1&rotation=0&showTitle=false&size=23318&status=done&style=none&taskId=ua3ef91a7-ac71-4492-8087-1bbb9717d48&title=&width=746.6666666666666)
hash（）方法计算hash值，hash值无符号右移16位，hash值不是hashCode
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662516943945-2032da8b-4f30-4e3a-8c6f-135713e61f78.png#averageHue=%23fafaf9&clientId=ue3c169ae-56ca-4&from=paste&height=115&id=ufac59ec0&name=image.png&originHeight=173&originWidth=1036&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22929&status=done&style=none&taskId=u2b92e6a0-f548-4752-ba7a-703a9157f59&title=&width=690.6666666666666)
putVal（）方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662523165026-73fa24e6-be6f-460c-9dbd-59bc93b7c096.png#averageHue=%23fcfbfb&clientId=ue3c169ae-56ca-4&from=paste&height=421&id=u7bf9834e&name=image.png&originHeight=631&originWidth=1252&originalType=binary&ratio=1&rotation=0&showTitle=false&size=152648&status=done&style=none&taskId=udc9d61be-a18b-4b91-b761-f7ae1ddbfce&title=&width=834.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662523186562-2a22df41-7207-4d39-b831-d683631fc2f5.png#averageHue=%23fcfbfb&clientId=ue3c169ae-56ca-4&from=paste&height=440&id=u304181db&name=image.png&originHeight=660&originWidth=1209&originalType=binary&ratio=1&rotation=0&showTitle=false&size=133144&status=done&style=none&taskId=u083e7bf5-c4a6-4e06-94f9-f6d3598190e&title=&width=806)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662553054152-64fd8dbd-f8d8-4b20-a6cf-39f61cec0951.png#averageHue=%23fdfcfc&clientId=u739331e1-3a19-4&from=paste&height=383&id=u10eebd5b&name=image.png&originHeight=574&originWidth=1132&originalType=binary&ratio=1&rotation=0&showTitle=false&size=70312&status=done&style=none&taskId=u978fe65a-21ec-4804-b8a0-d05d63838ce&title=&width=754.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662517376625-1e5d1ade-6942-4706-bbb2-3da75aa338c0.png#averageHue=%23fbfaf9&clientId=ue3c169ae-56ca-4&from=paste&height=471&id=u83fd51f1&name=image.png&originHeight=706&originWidth=1252&originalType=binary&ratio=1&rotation=0&showTitle=false&size=125104&status=done&style=none&taskId=u1714f1af-4d16-473a-9703-f043bc5ef98&title=&width=834.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662517397782-35282dea-85dc-4e17-ba21-d0aeb9b5a721.png#averageHue=%23fcfbfb&clientId=ue3c169ae-56ca-4&from=paste&height=431&id=u25ae35b0&name=image.png&originHeight=646&originWidth=1285&originalType=binary&ratio=1&rotation=0&showTitle=false&size=79028&status=done&style=none&taskId=ubb1e309a-8e7b-49ca-85c9-b5d763baeb1&title=&width=856.6666666666666)
重写对象hash与equals方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662558103137-3e9155b3-a629-4db0-9fe1-cab19d18c595.png#averageHue=%23f3f0ef&clientId=u739331e1-3a19-4&from=paste&height=240&id=u70d953c7&name=image.png&originHeight=360&originWidth=900&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25476&status=done&style=none&taskId=ub9dd272c-f1de-4e41-97df-fdfb5ea7546&title=&width=600)

#### 2、LinkedHashSet（HashSet子类）
（1）底层维护数组+双向链表；
（2）使用链表维护元素次序，看起来为按顺序插入；
（3）不允许重复添加元素。
（4）底层是LinkedHashMap，LinkedHashSet底层为HashMap
添加元素源码与HashSet相同；

#### 3、TreeSet
（1）特点
①使用无参构造，创建TreeSet，依旧是无序的；
②使用TreeSet提供构造器可以传入一个比较器，底层就是TreeMap
③去重机制：如果传入一个Compartor匿名对象，使用compare去重，如果方法返回0，认为是相同元素，就不添加，若没有传入Comparator匿名对象，则以添加对象实现的Compareable接口中的compareTo去重
（2）源码
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662688914507-c5ff0370-85b6-4bec-8097-142105da9944.png#averageHue=%23f7f0e0&clientId=u79a4c84a-e13a-4&from=paste&height=91&id=u2f6a3225&name=image.png&originHeight=136&originWidth=974&originalType=binary&ratio=1&rotation=0&showTitle=false&size=17487&status=done&style=none&taskId=u99cc352e-b896-4249-b607-9f2159b4eaf&title=&width=649.3333333333334)
添加元素源码
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662689077711-6370d302-55d6-43bf-ad9f-5cbed9b50001.png#averageHue=%23fcfcfa&clientId=u79a4c84a-e13a-4&from=paste&height=78&id=u7ff65dbf&name=image.png&originHeight=117&originWidth=920&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14374&status=done&style=none&taskId=u8d1f0ac3-8f0d-484f-b604-29216ba30d1&title=&width=613.3333333333334)
在调用add方法时，在底层执行到下面。
①cpr为匿名内部类，动态绑定到我们自定义的comapre方法；
②如果数据相等，数据不添加
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662689222252-6b3f05e1-2889-4218-96b9-9acf308b68c6.png#averageHue=%23fcfcfb&clientId=u79a4c84a-e13a-4&from=paste&height=257&id=u868bea6b&name=image.png&originHeight=385&originWidth=1131&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53101&status=done&style=none&taskId=uf8fe4fcb-3e72-45bc-b8da-85d45e7cbf3&title=&width=754)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662689389077-2da21c31-255a-4b98-8b3c-2c8d82a79165.png#averageHue=%23fbf8f6&clientId=u79a4c84a-e13a-4&from=paste&height=155&id=u15ac55ee&name=image.png&originHeight=233&originWidth=1089&originalType=binary&ratio=1&rotation=0&showTitle=false&size=34479&status=done&style=none&taskId=u1bc7339e-ef48-4b39-a5b8-fb72895ed88&title=&width=726)

### 四、Map接口
#### 1、map存储特点：
（1）k-v存储，最后是存储在HashMap$Node=newNode（hash，key，value，null）；
（2）k-v为方便遍历，还会创建EntrySet集合，该集合存放Entry，一个Entry对象就有k-v；
（3）当把HashMap$Node对象存放到entrySet就方便我们遍历，因为Map.Entry提供了getKey（）方法和getValue（）方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662620355713-bf224060-70bc-46ad-8e84-a49ba57ed7e7.png#averageHue=%23f7f5ef&clientId=uf87dc5ed-f79c-4&from=paste&height=51&id=u0f06231b&name=image.png&originHeight=76&originWidth=826&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12621&status=done&style=none&taskId=u6fefc20d-4464-4fa9-a048-e9a32d040ee&title=&width=550.6666666666666)
（4）map中，key相同，值覆盖，如下方法：
①记录旧值；
②值替换为新加入的值
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662625239000-346f455f-8f0b-4bb8-ad66-64478a1e7060.png#averageHue=%23fbfaf9&clientId=uf87dc5ed-f79c-4&from=paste&height=159&id=uc92635e7&name=image.png&originHeight=238&originWidth=920&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36290&status=done&style=none&taskId=u715722e9-ae65-41cc-96cf-4051b8cbd20&title=&width=613.3333333333334)
（5）HashMap没有实现同步，不是线程安全，底层是以hash表来存储（数组+链表+红黑树）
#### 2、hashMap底层
（1）执行构造器，初始化加载因子loadfactor=0.75
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662626493216-44e83766-949c-4c2b-8b11-e8a53582a58f.png#averageHue=%23fcfbf7&clientId=uf87dc5ed-f79c-4&from=paste&height=79&id=u0118fdd6&name=image.png&originHeight=118&originWidth=1192&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18697&status=done&style=none&taskId=ucf55c0db-a7c5-4dd4-ada5-a3ad2ca0f05&title=&width=794.6666666666666)
（2）执行put（）方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662626543655-e8ed7ae9-a998-4120-a6fa-5b71d3c0e3a3.png#averageHue=%23fbfafa&clientId=uf87dc5ed-f79c-4&from=paste&height=77&id=ua00706c2&name=image.png&originHeight=116&originWidth=1258&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19391&status=done&style=none&taskId=ucc9ad663-440d-4345-86a2-08642b94356&title=&width=838.6666666666666)
（3）计算key的hash值
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662626645071-bd88b076-7d73-457b-8875-27946341bdcc.png#averageHue=%23fbfbf9&clientId=uf87dc5ed-f79c-4&from=paste&height=102&id=u268e037c&name=image.png&originHeight=153&originWidth=1101&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20882&status=done&style=none&taskId=ua4a480db-324f-4ecc-8a65-aed4cc41f74&title=&width=734)
（4）执行putVal（）方法
①判断表是否为空，为空
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662626765833-e8508b5a-86ab-4cf9-9238-7f7a5c13f365.png#averageHue=%23faf9f8&clientId=uf87dc5ed-f79c-4&from=paste&height=73&id=ueed3ba06&name=image.png&originHeight=109&originWidth=1023&originalType=binary&ratio=1&rotation=0&showTitle=false&size=17708&status=done&style=none&taskId=ue919f8df-38ab-4284-bdf5-244f9a42811&title=&width=682)
②判断该hash位置是否为空，为null，将添加值放入
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662626979444-95aeac0d-6e66-4b76-aef5-716396940688.png#averageHue=%23f9f8f7&clientId=uf87dc5ed-f79c-4&from=paste&height=55&id=u523c0f89&name=image.png&originHeight=82&originWidth=926&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14726&status=done&style=none&taskId=uaa6ab6b6-e887-406f-8afa-8ab279755a4&title=&width=617.3333333333334)
③判断table的索引位置的key的hash值和新的key的hash值相同相同，并且满足现有的节点的key和准备添加节点的key是同一个对象||equals相同，就只能替换key-value；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662627350878-d87969ab-6245-4c76-956a-7ecdfb5ebc4f.png#averageHue=%23fbfaf9&clientId=uf87dc5ed-f79c-4&from=paste&height=85&id=u414c3cf1&name=image.png&originHeight=127&originWidth=1041&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18688&status=done&style=none&taskId=ua47aa586-956f-4aea-ae8d-fbffacfb4bf&title=&width=694)
④如果当前table的节点已经是红黑树，就按照红黑树方法处理
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662630333882-3cd6f148-b321-4317-b7c5-df9ae460a274.png#averageHue=%23f9f7f1&clientId=u427c3d73-e01b-4&from=paste&height=50&id=u094f1120&name=image.png&originHeight=75&originWidth=1198&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16692&status=done&style=none&taskId=u9df25f42-7950-41be-acc7-a13c0218e26&title=&width=798.6666666666666)
⑤如果找到的节点后面是链表，就循环比较：
A、若整个链表没有和他相同，加到该链表的最后，加入后，判断当前链表个数是否已经8个，超过后进行红黑树树化treeifBin（）；
B、如果在循环比较中，发现有相同，不添加break，只是替换value
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662630412502-33bae533-9e4f-4888-8699-8784e2c23b2c.png#averageHue=%23fcfbfa&clientId=u427c3d73-e01b-4&from=paste&height=302&id=ub5831b7c&name=image.png&originHeight=453&originWidth=1294&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62161&status=done&style=none&taskId=u2ebb705b-a4e2-4e37-a6d1-dee76247cd6&title=&width=862.6666666666666)
树化，若表为空或表长小于64，就不会树化，而是进行扩容
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662630785049-449cef6a-d89b-42e6-95b1-8fdb0307d7c0.png#averageHue=%23fcfbfb&clientId=u427c3d73-e01b-4&from=paste&height=432&id=ude2b763c&name=image.png&originHeight=648&originWidth=1298&originalType=binary&ratio=1&rotation=0&showTitle=false&size=89233&status=done&style=none&taskId=u57de5561-cd34-4645-99f5-0238bee602e&title=&width=865.3333333333334)
⑥增加修改次数和数组大小，判断是否需要扩容
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662627087575-8a6258c5-49e1-4172-a7ce-d177efe3ed95.png#averageHue=%23fcfcfc&clientId=uf87dc5ed-f79c-4&from=paste&height=65&id=ua3c73b77&name=image.png&originHeight=97&originWidth=1077&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10409&status=done&style=none&taskId=u28d7f8f8-0abf-4524-a649-24f46e1bf5b&title=&width=718)
#### 3、hashTable
（1）特点：
①键和值不能为null；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662633394857-434e8a47-5911-4de8-b8ef-627874145560.png#averageHue=%23fbfbfa&clientId=u427c3d73-e01b-4&from=paste&height=67&id=u3520ba96&name=image.png&originHeight=101&originWidth=999&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12658&status=done&style=none&taskId=ub8bb1ff6-6863-469f-8cb0-5628ef45243&title=&width=666)
②是线程安全；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662632340790-91eddba0-a2e8-4fc4-bedb-75e23f4e401a.png#averageHue=%23faf4ef&clientId=u427c3d73-e01b-4&from=paste&height=73&id=uc0abc9e5&name=image.png&originHeight=110&originWidth=802&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20100&status=done&style=none&taskId=u36f37d69-70f6-4840-84dc-db24de9bfeb&title=&width=534.6666666666666)
③底层是一个数组，HashTable$Entry，初始化大小为11；
（2）底层：
执行addEntry（）添加k-v封装到Entry
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662633602232-e3aa8301-8261-4c74-932d-e5e56d26335c.png#averageHue=%23fcfbfb&clientId=u427c3d73-e01b-4&from=paste&height=398&id=ufb3e656d&name=image.png&originHeight=597&originWidth=1215&originalType=binary&ratio=1&rotation=0&showTitle=false&size=80866&status=done&style=none&taskId=ue375b207-b90f-4c71-8c14-def727be0b3&title=&width=810)
rehash（）方法扩容，按照两倍+1扩容
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662633674394-91ead139-460c-4986-8dad-b6d120e08cee.png#averageHue=%23fbfbf9&clientId=u427c3d73-e01b-4&from=paste&height=358&id=u4fb293c3&name=image.png&originHeight=537&originWidth=1184&originalType=binary&ratio=1&rotation=0&showTitle=false&size=101245&status=done&style=none&taskId=ud09ad363-e08a-43a8-a544-f3004a7ab41&title=&width=789.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662633692329-440c7a4c-7b92-42d0-8aed-864d1fc88091.png#averageHue=%23fbfbfa&clientId=u427c3d73-e01b-4&from=paste&height=251&id=uc0d9ede0&name=image.png&originHeight=377&originWidth=1122&originalType=binary&ratio=1&rotation=0&showTitle=false&size=50809&status=done&style=none&taskId=u0e1fa4aa-b16d-427e-a4a9-3fdb172f2bb&title=&width=748)

#### 4、Properties
（1）特点：
①用于从xxx.properties中读取文件；
②也是一种键值对形式，继承hashtable，实现Map接口

#### 5、TreeMap源码
把传入的实现Comparator接口的匿名内部类，传给TreeMap
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662690521702-4dcea0ec-b1e1-4c7d-a420-7707abca9901.png#averageHue=%23f6f0df&clientId=u79a4c84a-e13a-4&from=paste&height=68&id=u816f7261&name=image.png&originHeight=102&originWidth=998&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14441&status=done&style=none&taskId=u1e773beb-483b-4cbc-b107-186fd083e2c&title=&width=665.3333333333334)
添加的元素
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662691120182-9ce2646d-c3c5-4042-8214-c8b5cc85d030.png#averageHue=%23fbfbfa&clientId=u79a4c84a-e13a-4&from=paste&height=280&id=u1df2ef2f&name=image.png&originHeight=420&originWidth=1038&originalType=binary&ratio=1&rotation=0&showTitle=false&size=77397&status=done&style=none&taskId=u356048be-4b19-41f2-af23-0939d1f13ff&title=&width=692)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662691080418-559d3327-573a-415d-85d4-9f8790b6a0f6.png#averageHue=%23fbfaf9&clientId=u79a4c84a-e13a-4&from=paste&height=289&id=udcbdc76e&name=image.png&originHeight=433&originWidth=963&originalType=binary&ratio=1&rotation=0&showTitle=false&size=61670&status=done&style=none&taskId=u28d03271-89db-440f-9f63-f1c91d3ac5a&title=&width=642)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662691147372-28798254-af6d-457f-bf8a-f55670989214.png#averageHue=%23fbfbfa&clientId=u79a4c84a-e13a-4&from=paste&height=342&id=ua6c783ab&name=image.png&originHeight=513&originWidth=1044&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59798&status=done&style=none&taskId=ud52b0e6b-d8bb-4af1-9bfb-2b081dfe557&title=&width=696)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662691174792-72db40a5-f560-4e09-8573-887ca3fea0bc.png#averageHue=%23fcfcfc&clientId=u79a4c84a-e13a-4&from=paste&height=187&id=ud063d746&name=image.png&originHeight=280&originWidth=1087&originalType=binary&ratio=1&rotation=0&showTitle=false&size=26649&status=done&style=none&taskId=ua80c0d91-53c6-4ffa-a661-ce112c66bf6&title=&width=724.6666666666666)


