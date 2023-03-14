### 1、常量池 
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677201456164-438cb704-b7a2-4fdd-a00a-f642f1548bee.jpeg)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/29496365/1677288478048-43737706-1aa6-419a-850e-740b02ccef87.png#averageHue=%23c0c95a&clientId=udce58220-aa01-4&from=paste&height=343&id=u5b97382a&name=image.png&originHeight=515&originWidth=1017&originalType=binary&ratio=1.5&rotation=0&showTitle=false&size=157589&status=done&style=none&taskId=ua9a0ca0f-3050-49a7-b006-ba7c18ea39b&title=&width=678)
### 2、类的生命周期
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677204941588-5f560cfd-6f27-435b-b0d1-5f637433472c.jpeg)
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677205143705-ddfd18ee-e27d-46c3-80b8-7bf0e80bb1f1.jpeg)
### 3、类加载器
#### （1）类加载机制
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677208478460-f1315b65-c765-4951-84fc-fb29f63eea62.jpeg)
### 4、栈
栈的生命周期和所处线程的生命周期一致
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677212911712-684aa4e7-4a1b-43dc-841b-17b3965af059.jpeg)
### 5、java对象内存布局
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677289740872-6512b0e9-bc69-453b-90b8-33421a4d1eae.jpeg)
### 6、JVM堆
（1）young区划分：内存空间碎片造成空间足够时，占用大内存的数据无法加入内存；
（2）s区保留存活对象，另外一个s区保证空间连续性（两个s内存区来回倒置），s区两块内存一致
（3）Eden区中的对象，没用对象被回收，剩余存活对象到s区
（4）为防止s区一直被占用，相同年龄在总和在默认年龄上，s区大于相同年龄的所有对象进入old区
（5）担保机制：新生代空间不够，对象直接进入老年代
（6）hotspot gc：
①Partial GC：回收部分空间（young GC、old GC）
②Full GC：回收整个区域的空间（minor GC：Edgen区或S区空间（空间碎片）不够）
（7）可达性分析：当eden区满时，s0区也存不下元素，s0区和Eden区会进行可达性分析，找出活跃的对象，移除所有不可达的对象，并将s0区和s1区交换
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677291664165-9ebb4063-24a5-46ae-a5f9-3c29df0dfeb2.jpeg)
### 7、java对象生命周期
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677419386671-e9be83d5-5a5a-4ad9-9a5b-faf3f3aac13f.jpeg)
### 8、GC收集器
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677556476211-50c5286b-6f1c-475e-b3d5-9b4e6740c737.jpeg#averageHue=%23d9b9a3&clientId=ub8456eea-8a7e-4&from=paste&id=ue1ce42e4&originHeight=391&originWidth=646&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=ub2cdd789-f771-4063-9691-b6da2d554d4&title=)
#### （1）serial GC：
①单线程，标记复制算法
②Serial Old 单线程  标记整理算法
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677508116767-eed85032-85fa-4375-87ca-32df30bfbd2d.jpeg)
#### （2）ParNew GC
serial 多线程的版本的gc
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677508425667-d0457aa5-fd68-488a-a0ff-92a3c7db9ee6.jpeg)
#### （3）Parallel Scavenge GC
①复制算法，多线程，新生代垃圾收集器，吞吐量优先；
②-XX：MaxGCPauseMills （大于0）：控制最大gc停顿时间（空间换时间）
③-XX：GCTimeRatio（0-100）：控制吞吐量大小（19：1/（19+1））；
④-XX：+UserAdptiveSizePolicy ：true：不需要指定新生代大小（根据系统动态调整参数）
#### （4）Parallel OLd GC
①多线程，标记整理
#### （5）CMS GC
①background模式：1.7之前为串行，1.8后为并行     -XX：+CMSParallellninitialMarkEnable：并行串行开关
②foreground：切换其他垃圾收集器
③-XX：CMSlnitiatingQccupancyFraction=-1：设置回收阈值（0-100）
④-XX：+UserCMSlnitiatingQccupancyFractionOnly：辅助参数（③参数的持久化）
⑤CMSScheduleRemarkEdenSizeThreshold 2M：达到2M后进行预清理
CMSScheduleRemarkEdenPenetration 50%   ：预处理达到总的内存的50%，进行终止
⑥-XX：+UseCMSCompactAtFullCollection  开启手动full gc
-XX：UseFullGCsBeforeCompaction=0   
⑦缺陷：单线程单核效率低；并发失败；可终止预处理（5s）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677513603602-b97fbf51-a9b8-4ded-b1b1-87c72e7ce6f2.jpeg)
#### （6）G1 GC
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677553785140-c487d31a-1519-46f0-9892-c0d6845a986b.jpeg)
①设置可预期停顿时间，并发类的垃圾收集器，回收得到空间是连续的，采用标记复制算法；
②避免并发，降低CPU负担；
③分代收集，region（1-32M）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677547591666-fe5e57ac-33f4-4111-b97d-eb3896eb205a.jpeg)
④TLAB：堆内存划分的一块区域
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1677550008856-b07369f8-0d18-448a-bb7b-102d12a13cdc.jpeg)
### 9、JVM命令
（1）jps ：查看当前运行进程的进程号（pid）；
（2）jstack  【pid】：查看进程的所有信息（可以查看死锁的线程）；
（3）jmap -heap 【pid】：获取堆情况；


