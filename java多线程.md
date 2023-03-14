## 一、概念
#### 1、进程：
（1）运行的程序，例如使用QQ，就启动一个进程，操作系统为该进程分配内存空间；
（2）进程是程序的一次执行过程，是动态过程；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663502108860-029182f5-a632-4594-8d5d-a95489a2cf49.jpeg)
#### 2、线程
（1）线程有进程创建，是进程实体；
（2）一个进程可以拥有多个线程；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663502442484-8da0e273-e153-4005-919c-94d056a9d2c6.jpeg)
#### 3、并发
同一时刻，多个任务交替执行，单核CPU实现任务就是并发；
#### 4、并行
同一时刻，多个任务同时执行，多核CPU可以实现并行；
#### 5、线程执行机制
（1）主线程结束，其他子线程还在运行，进程就会继续存活；
（2）所有线程挂掉，进程才会挂掉；
（3）run()方法为一个普通方法，并不会真正启动线程，会等run执行完毕后才会继续执行下面代码；
（4）start（）方法才会启动线程；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663510202959-81b17f93-e80b-475b-8f79-3d32945b8f2f.jpeg)
#### 6、线程启动
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1675921004476-191fe4bf-a9fd-456d-b3b2-ce8711101ad1.jpeg)
（1）执行start（）方法
同时执行两个线程，一个执行start的线程，一个执行run的线程
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1668933231131-9e69bc0b-feb2-4d2b-aacd-8f135f185e12.png#averageHue=%232b2b2b&clientId=u8c8a5ee7-839c-4&from=paste&height=264&id=u6d50ab56&name=image.png&originHeight=396&originWidth=910&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59271&status=done&style=none&taskId=ue4d16cbf-5695-485e-8a6c-306d464d026&title=&width=606.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663511217989-0a8f9a0d-f8e0-44b5-a514-cd43cbb58efd.png#averageHue=%23fbfaf9&clientId=u48bda465-906f-4&from=paste&height=426&id=u723e9e47&name=image.png&originHeight=639&originWidth=1065&originalType=binary&ratio=1&rotation=0&showTitle=false&size=96955&status=done&style=none&taskId=u712867e4-1c94-412e-9315-95342ba1041&title=&width=710)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663511247004-8f806ac2-c60f-4a3a-bc2d-044bb11984c5.png#averageHue=%23fcfbfa&clientId=u48bda465-906f-4&from=paste&height=246&id=u3f9dbdce&name=image.png&originHeight=369&originWidth=1140&originalType=binary&ratio=1&rotation=0&showTitle=false&size=44539&status=done&style=none&taskId=u094b05e5-5c49-4004-b0f1-609511aa80a&title=&width=760)
（2）本地方法，JVM调用，底层为c/c++实现，真正实现多线程
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663511271789-b3b372af-64f1-42ef-bcd8-17f86744965f.png#averageHue=%23fcfbf6&clientId=u48bda465-906f-4&from=paste&height=60&id=uef1dd131&name=image.png&originHeight=90&originWidth=1038&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8310&status=done&style=none&taskId=uceb0a19b-f029-4589-aa50-64f9ab29a23&title=&width=692)
#### 7、线程终止唤醒阻塞状态线程
（1）interrupt：设置共享变量为true，唤醒阻塞线程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1675926364932-6eacf187-9efa-4710-bf45-445546682238.jpeg)
#### 8、join方法
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676267502535-9309d534-a412-430c-b201-642bc2e27446.jpeg)
## 二、Thread线程常用方法
1、join（）方法：线程插队，线程一旦插队成功，肯定先执行完插入的线程的所有任务；
2、yield：让出CPU，让其他1线程执行，礼让时间不确定，不一定礼让成功
3、守护线程：当所有的用户线程结束，守护线程就会结束；
例：垃圾回收机制
## 三、线程状态
（1）java线程中有6种状态；
（2）操作系统中有5种状态；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1675920420437-7282ca5d-d62d-4a3f-a13a-53265fc34c67.jpeg)

## 四、线程同步与锁
1、线程同步机制：使用同步机制保证数据在任何同一时刻，最多只有一个线程访问，以保证数据完整；
2、Synchronized同步原理：
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663597347225-6a950e69-21b7-46ad-8398-a80b91508881.jpeg)
3、互斥锁：
（1）每个对象都有一个可称为“互斥锁”的标记，这个标记只能保证任意时刻只有一个线程访问该对象；
（2）影响程序执行效率；
（3）同步方法（非静态的）的锁可以是this对象，也可以是其他对象；
（4）同步方法（静态的）的锁为当前类本身；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663598355812-9c4ba65e-e464-45ba-8edd-2de7ff8a31c0.png#averageHue=%23fdf7f6&clientId=ud347ab26-9edb-4&from=paste&height=322&id=u50b3b34e&name=image.png&originHeight=483&originWidth=864&originalType=binary&ratio=1&rotation=0&showTitle=false&size=50106&status=done&style=none&taskId=ub5a5ae6b-b36a-4564-9c05-4bf59d289ed&title=&width=576)
4、线程死锁：多个线程占用对方资源，不肯相让，导致形成死锁；
5、释放锁：
（1）线程同步方法，同步代码块执行结束；
（2）线程同步方法、同步代码块遇到break、return；
（3）出现未处理的error或Exception，导致异常结束；
（4）执行线程中wait（）方法，线程暂停，释放锁
sleep（），yield（），suspend（）不会释放锁

---

## 1、Object.wait()
（1）一定要持有到调wait方法那个对象的锁，wait代码段放在synchronized块中；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669012336135-927735dd-d945-4708-a036-21b644198a2a.png#averageHue=%23322b2a&clientId=u29abe8d5-ad10-4&from=paste&height=95&id=u398bb217&name=image.png&originHeight=143&originWidth=698&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20713&status=done&style=none&taskId=uf7b75fbc-2889-4a20-a90d-5b0e524e20b&title=&width=465.3333333333333)
（2）持有该对象锁的线程，执行notify或notifyAll方法可以唤醒等待线程；
（3）调用wait后，会将该对象锁释放，进入等待状态，线程加入waitSet集合，waitSet底层是双向链表；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669277852051-6501a786-7fe1-4771-a09e-57976b5c7c3f.png#averageHue=%23f6f5f3&clientId=u503e4b85-1a4e-4&from=paste&height=77&id=uf78a2668&name=image.png&originHeight=115&originWidth=797&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14728&status=done&style=none&taskId=ue4b79aa7-be5f-4e10-af7f-8081cc278fd&title=&width=531.3333333333334)
（4）该线程被唤醒后，会与其他线程公平竞争该对象锁，只有该线程获取到对象锁后，才会继续往下执行；

---

## 2、Object.notify()、notifyAll（）
（1）当调用对象notify方法时，会随机唤醒等待集合中一个线程，唤醒线程与其他线程公平竞争锁；
  从WaitSet集合中选出一个线程，加入到EntryLsit集合中
（2）当调用notifyAll方法时，唤醒等待集合所有线程；
（3）在某一时刻，只有唯一线程可以获取对象锁；

---

## 3、synchronized关键字
（1）同一个对象，多个synchronized方法，多个线程某一个时刻同时访问，只能先执行一个方法；（锁为对创建的对象锁）
（2）synchronized修饰的静态方法，多个对象中，多个线程只能访问一个线程去访问（对该对象的Class对象加锁）；
（3）synchroinzed修饰代码块，通过 monitorenter和monitorexit来获取锁和释放锁；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669273053301-3d2cf3c2-41ba-458b-a1c1-64cb4c82eff5.png#averageHue=%23464a4c&clientId=u503e4b85-1a4e-4&from=paste&height=195&id=u159bd0a5&name=image.png&originHeight=292&originWidth=469&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38141&status=done&style=none&taskId=u7c119d1c-ffbe-438d-b2ad-aecf95710ea&title=&width=312.6666666666667)
（4）JVM同步基于进入与退出监视器对象（Monitor）来实现，每个对象实例·会有个Monitor对象，monitor对象和java对象一并创建并销毁，monitor由c++创建；
（5）多个线程访问一段同步代码块，获取不到锁的线程会放入Entrylist集合，处于阻塞的线程会被放入该集合中，当线程获取到Monitor对象时，monitor对象依赖于底层操作系统的mutex_lock（互斥锁），线程获取成功后，会持有mutex，其他线程无法获取mutex；
（6）基于底层操作系统的mutex_Lock来实现，每次锁的获取与释放都会带来用户态与内核态的切换，并发量高时，synchronized锁性能非常差；
（7）调用wait方法的线程会进入waitset集合，处于阻塞状态的线程会进入EntryList集合中，waitset中的线程被notify唤醒后，若争抢不到锁，线程会加入EntryList集合，进而进入内核状态；
解决上述方法：自旋，其原理：发生岁monitor的争用时，若Owner能够很短时间内释放该锁，则那些正在争用的线程可以自旋，在Owner释放锁后，会立即获取到锁，从而避免阻塞，争用一段时间后若无法获取锁，则进入阻塞状态。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669278054710-22a6c144-7d13-49ee-9b43-b2478c102282.png#averageHue=%23f4f2f1&clientId=u503e4b85-1a4e-4&from=paste&height=107&id=uefb485c1&name=image.png&originHeight=160&originWidth=965&originalType=binary&ratio=1&rotation=0&showTitle=false&size=21825&status=done&style=none&taskId=u6ef43aec-822a-46ad-ada2-ca0deb50d71&title=&width=643.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669278235515-1e534b92-6898-4549-812b-433bedf282cb.png#averageHue=%23f5edec&clientId=u503e4b85-1a4e-4&from=paste&height=153&id=ue5894cfa&name=image.png&originHeight=230&originWidth=663&originalType=binary&ratio=1&rotation=0&showTitle=false&size=26270&status=done&style=none&taskId=u611fc02d-582e-40e9-b48c-f68037d4858&title=&width=442)
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669340997918-00e443eb-c5fb-4a70-8903-f9ad350b62f9.jpeg)
（8）互斥锁属性
【1】P_THREAD_MUTEX_TMIED_NP：普通锁，当一个线程加锁后，其余线程进入等待队列，并且在解锁后按照优先级获取锁，从而确保资源分配的公平性；
【2】P_THREAD_MUTEX_RECURSIVE_NP：嵌套锁，允许一个线程对同一个锁成功获取多次，并通过unlock进行解锁，如果是不同新城请求，可通过加锁线程解锁后重新进行竞争；
【3】P_THREAD_MUTEX_ERRORCHECK_NP：检错锁，一个线程请求同一个锁，则返回EDEADLK，否则与【1】锁一样，不允许多次加锁时不会出现死锁；
【4】P_THREAD_MUTEX_ADAPTIVE_NP：适应锁，仅仅等待解锁后重新竞争；

---

## 4、锁
（1）对于锁的访问与java对象头相关，java对象头包括Mark Word、指向类指针、数组长度；
（2）Mark Word记录了对象、锁及垃圾回收相关信息，包括如下组成部分：
【1】无锁标记
【2】偏向锁标记
【3】轻量级锁标记
【4】重量级锁标记：synchroinzed标记
【5】GC标记
（3）锁演化阶段：无锁->偏向锁->轻量级锁->重量级锁
（4）偏向锁：
对于一个线程，主要作用是优化同一个线程多次获取同一个一个锁的情况，如果一个synchroinzed方法被一个线程访问，synchroinzed方法所在对象就会在起Mark Word中将偏向锁标记，同时还有一个字段存储线程id，，当这个线程继续访问同一个synchroinzed方法时，他会检查这个对象的Mark Word偏向锁标记以及是否指向该id：(建议关闭偏向锁)
【1】如果是同一个线程，线程无须进入内核态，而是直接进入方法中；
【2】如果是另外一个线程访问synchroinzed方法，偏向锁取消；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669343590093-fc6e0478-40d7-4e43-bdb7-b99ee97ce6b6.jpeg)
（5）轻量级锁：（适合两个线程轮流访问），如自旋锁
若第一个线程已经获取到当前对象锁，这时第二个线程尝试争抢该对象锁，由于该对象的锁已经被第一个线程获取到，因此他是偏向锁。第二个线程在争抢时，会发现对象头中的Mark Word已经是偏向锁标记，，但里面存储的id并不是自己，则会进行CAS，从而获取到锁。两种情况：
【1】获取锁成功：会将Mark Word里的线程id由第一个线程变成自己的，这样对象依旧保持偏向锁状态；
【2】获取失败：则表示这可能有多个线程争抢对象锁，那么偏向锁升级，升级为轻量锁；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669356490091-2362fe46-20c5-4611-ab43-3f7366e53d79.jpeg)
（6）重量级锁
若自旋失败，锁会转换为重量级锁，无法获取到锁的对象都会进入Monitor（内核态）；自旋可以避免线程从用户态进入内核态；

---

## 5、死锁
（1）死锁线程1等待线程2互斥持有的资源，线程2等待线程1互斥持有的资源，两个线程无法继续执行；
（2）活锁：线程持续重试一个总是失败的操作，导致无法继续操作；
（3）饿死：线程一直被调度器延迟访问其可执行的资源，调度器先于优先级低的线程而执行高优先级线程，则总是执行高优先级线程，导致该线程一直无法执行；

---

## 6、Lock锁机制
（1）lock与synchroinzed区别：
【1】锁释放：lock必须通过unlock方法在finally中手动释放，synchroinzed通过jvm释放，synchroinzed锁的释放是按照加锁时的相反顺序释放，如加A锁，再加B锁，先释放B锁，再释放A锁，Lock锁的释放可以以任意顺序释放；
【2】锁获取：lock通过代码手工获取锁，synchroinzed通过jvm获取锁，无需开发者干预；
【3】具体实现方式：lock通过java代码实现，synchroinzed通过jvm底层实现；
【4】锁类型：lock提供多种，如公平锁，非公平锁，synchroinzed与lock均提供可重入锁；
（2）tryLock（）方法：获取到锁会返回true，获取不到则会放回false
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669427639306-f74f3a7f-d3dd-4319-96d8-a00d7142df08.png#averageHue=%232b2b2b&clientId=u503e4b85-1a4e-4&from=paste&height=181&id=u6a8d9373&name=image.png&originHeight=271&originWidth=672&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18993&status=done&style=none&taskId=u00f9a3bd-395e-40b8-b812-3732e596ff4&title=&width=448)
（3）ReentrantLock 可重入锁：一个线程可以重复获取同一个锁，即使锁没有释放；

---

## 7、Condition
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676446706496-9fe24858-050a-4d89-81a8-b6a35dc737ec.jpeg)
（1）await
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676442911205-bb46214b-e047-4888-b157-32af1e23b508.jpeg)
（2）condition.signal()
①原tail结点是CANCELLED状态；
②condition的结点transfer到AQS队列之后，通过lock.unlock()去唤醒；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676443832559-c3dc6db0-cc75-41f7-bae9-999d954b3322.jpeg)
（3）传统可以通过synchroinzed+wait+notify/notigyAll来实现多个线程之间的通信，整个过程由JVM实现，开发者无需了解底层实现细节；
（4）从jdk1.5后，并发包提供lock和Condition（await与signal/signalAll）来实现多个线程之间通信，整个过程由开发者控制；
（5）Conditidion支持一个对象拥有多个waitset等待集合，而传统方式只允许有一个waitset集合；
（6）Condition必须关联一个lock,一个lock可以生成多个condition对象；
（7）await（）方法为避免被假唤醒，应当放入while循环中，调用await后会释放锁，需要signal（）方法唤醒才能继续执行；

---

## 8、volatile关键字（保证可见性）
（1）实现long/double类型变量的原子操作，变量不会从寄存器获取变量，而是从内存（高速缓存）中获取；要实现原子性，等号右侧的赋值变量中不能出现被多线程所共享的变量，即使这个变量被volatile修饰也不行；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669623594040-8db80380-2767-44c7-89ec-603f0abe83c0.jpeg)
（2）指令重排序
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676095797644-f2f37d2a-e6a4-4dcf-9f90-163e5a393e05.jpeg)
（3）内存屏障
```java
volatile int a=0;//volatile会自动生成屏障

CPU0{
	a=1;
	//storeMemoryBarrier()写屏障，写入到内存中
	b=1;
}

CPU1{
	while(b==1){//true
        //loadMemoryBarrier();读屏障
        assert(a==1)//false
    }
}
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676103938473-c284c76a-55f8-4587-8366-871c3d20b310.jpeg)
（4）防止指令重排序，实现变量的可见性的手段：内存屏障
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669626324264-4afc3f12-5530-4ac0-85ee-21f73bba08bd.jpeg)

---

## 9、java内存模型（JMM）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676179306578-a5ebf24b-92e7-4ef0-96da-7dff44a0ca29.jpeg)
（1）顺序执行（限定在当个线程之上）:该线程的每个动作都happen-before它的后面动作；
（2）隐式锁（monitor）规则：unlock happen-before lock，之前的线程对于同步代码块的所有执行结果对于后序获取锁的线程来说都是可见的；
（3）volatile读写规则：对于一个volatile变量的写操作一定会happen-before后续对该变量的读操作；
（4）多线程启动规则：Thread对象的start方法happen-before该线程run方法中的任何一个动作，包括其中启动的任何子线程；
（5）多线程的终止规则：一个线程启动一个子线程，并且调用子线程join方法等待其结束那么当子线程结束后，父线程接下来的所有操作都可以看到子线程run方法中的执行结果；
（6）线程中断规则:可以用interrupt方法来中断线程，这个调用happen-before对该线程中断的检查；

---

## 10、CountDownLatch
（1）countDown（）方法：计数器不为0，计数器值减减，计数器最小值为0；
（2）await（）方法：调用该方法的线程，判断计数器是否为0，不为0，则阻塞，为0，直接继续执行线程；
（3）计数器为一次性的；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669773465087-ff2b5371-a20f-4b4a-ab52-66f4b3871b04.jpeg)
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676530914333-3cbc0448-497a-407a-9a14-ef2d3737778b.jpeg)
（4）唤醒线程源码
```java
 private void unparkSuccessor(Node node) {
        int ws = node.waitStatus;
        if (ws < 0)
            compareAndSetWaitStatus(node, ws, 0);
        Node s = node.next;
    	//s为null，并行操作中，添加时，可能还没有执行next=线程，导致head.next=null
        if (s == null || s.waitStatus > 0) {
            s = null;
            //往尾结点找head.next
            for (Node t = tail; t != null && t != node; t = t.prev)
                if (t.waitStatus <= 0)
                    s = t;
        }
        if (s != null)
            LockSupport.unpark(s.thread);
    }
```

---

## 11、CyclicBarrier
（1）await（int count）方法，等待线程达到指定数量count，才能继续执行；
（2）计数器可以重用，计数器值为0后，值置为初始值；
（3）CyclicBarrier(int parties, Runnable barrierAction)，barrierAction在最后一个线程抵达屏障后，会执行；
（4）会出现并发情况；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669773652009-849f8573-34cf-4ad4-882e-e8080b58c463.jpeg)
（4）底层执行流程：
【1】初始化各种成员变量，包括parties，count以及Runable；
【2】调用await方法时，底层会先检查是否已经归0，如果是，执行可选的Runable，接下来进行下一个generation；
【3】在下一个分代中，将会重置count为parties，并且创建新的Generation实例；
【4】接下来signalAll方法，唤醒所有在屏障前面等待线程，让其继续开始执行；
【5】计数器没有归0，调用线程将会通过Condition的await方法在屏障前等待；
【6】执行过程在lock锁内，不会出现并发情况；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669776732350-2baa3e99-946f-4d5a-888d-4f33d5f1d0f5.png#averageHue=%232f2d2c&clientId=u255c88af-d038-4&from=paste&height=137&id=H8ua4&name=image.png&originHeight=206&originWidth=775&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32179&status=done&style=none&taskId=ue00e1972-ebe1-4d27-be1f-70ecff5c3a3&title=&width=516.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669776837579-e5e891d5-3201-450b-80f2-10cf851d5bc8.png#averageHue=%232f2d2c&clientId=u255c88af-d038-4&from=paste&height=50&id=SlaN9&name=image.png&originHeight=75&originWidth=523&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8589&status=done&style=none&taskId=u4a463ed0-db26-4720-887d-01f5542d916&title=&width=348.6666666666667)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669776861471-7e8ecde2-bc57-42bc-94a8-97fa218a33d2.png#averageHue=%232c2b2b&clientId=u255c88af-d038-4&from=paste&height=51&id=djdl2&name=image.png&originHeight=77&originWidth=580&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5695&status=done&style=none&taskId=u28e3a00c-65ef-4e6b-bf3f-73090ab3043&title=&width=386.6666666666667)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669777390385-be76dc98-8844-40c2-9f58-1254eaae2327.png#averageHue=%232f2b2a&clientId=u255c88af-d038-4&from=paste&height=329&id=UwEG2&name=image.png&originHeight=494&originWidth=854&originalType=binary&ratio=1&rotation=0&showTitle=false&size=55092&status=done&style=none&taskId=u8b0bac8d-476e-4690-b20b-b133ce97207&title=&width=569.3333333333334)

---

**12、CAS（Compare And Swap）**
（1）synchronized关键字与lock锁等锁机制都是悲观锁：无论任何操作，首先要获取锁，再执行后续操作，从而确保所有操作都是由当前这个线程来执行的；
（2）乐观锁：线程操做之前不会做任何预先处理，而是直接执行，当在最后执行变量更新的时候，当前线程需要由一种机制确保当前被操作的变量没有被其他线程修改；
（3）CAS为乐观锁的一种实现方式，比较与交换，不断循环，直到变量被成功修改为止，CAS本身通过硬件指令来提供支持，硬件通过一个指令来实现交换与比较，因此CAS可以确保变量操作的原子性；
（4）CAS操作数涉及如下：
【1】需要被操作的内存值V；
【2】需要进行比较的值A；
【3】需要进行写入的值B；
【4】只有当V==A时，CAS才会通过原子操作的手段来将V的值更新为B；
（5）问题：
【1】循环开销问题：并发量大的情况下会导致线程一直自旋；
【2】只能保证一个变量的原子操作：可以通过AtomicReference来实现对多个变量的原子操作；
【3】ABA问题：1->3->1

---

## 13、CompletableFuture
异步执行，whenComplete（）等待任务执行返回结果，不会阻塞主线程的执行
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669795981615-1f60179e-d4af-4969-b037-2e87542845e9.png#averageHue=%232c2c2c&clientId=u255c88af-d038-4&from=paste&height=425&id=uf945a856&name=image.png&originHeight=638&originWidth=1300&originalType=binary&ratio=1&rotation=0&showTitle=false&size=89049&status=done&style=none&taskId=ucb2a8134-421f-425a-bb83-7a52866bf5f&title=&width=866.6666666666666)

---

## 14、ThreadLocal
（1）本质上·，ThreadLocal是通过空间换取时间，从而实现每一个线程中间都会有一个变量的副本，这样每个线程都会操作该变量副本，从而避免多线程并发问题；
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676275172642-7ff5f4cd-b8a4-4f95-a50a-7efc6dbaf132.jpeg)
（2）ThreadLocl与该运行的线程相绑定，每个线程对应不同ThreadLocal；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669861193612-a0decb5a-f8e4-430b-9010-fe0c801ae751.jpeg)
（3）java四种类型引用
【1】强引用：new一个实例，GC不会回收new出来实例对象；
【2】软引用：如果GC内存空间回收时，空间不够，会清除软引用，空间够，则不会清楚；
【3】弱引用：下一次GC回收，会被清理；
【4】虚引用：指向队列的元素被清理时，会收到通知
（4）Entry使用弱引用为了避免内存泄漏
【1】若Entry中使用强引用，当栈中ThreadLocal引用销毁时，Entry中的kv一直存在，导致Entry的kv一直增加，导致内存泄漏；
【2】使用弱引用可以保证，当堆中的ThreadLocal对象只被弱引用所指向，会被GC回收，Entry中的Key置为null；
【3】当调用ThreadLocal的set和get方法时，会清除键为null的Entry对象；也可以通过调用remove方法删除指定key的Entry对象
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669863366146-b975518c-7640-45eb-bc64-ede5c7b1cd70.jpeg)

---

## 15、AQS（AbstractQueuedSynchronizer）
#### （1）组成
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669885825342-d8d20b6d-e45c-43c2-a0ce-2899b952687d.jpeg)
#### （2）可重入锁（ReentrantLock）源码分析
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676359742239-7ac39c9d-6e61-407a-bee8-e1b7f61c72a3.jpeg)
【1】尝试获取对象锁，获取不到（其他线程已经持有锁，并且尚未释放）,该线程会进入AQS阻塞队列中；
【2】如果获取到锁，那么根据是公平锁还是非公平锁进行不同处理：
①如果是公平锁，线程直接放入AQS队列尾部；
②如果是非公平锁，线程会先进行CAS计算，，如果成功直接获取锁，如果失败，则与公锁一致，被放入阻塞队列末尾；
③当锁被释放（调用unlock），那么会调用release方法对static成员变量值一直减一操作，如果减一后，state为0，那么relaease执行完毕，并且调用LockSupport的unpark方法唤醒该线程后的等待队列中的第一个后继线程，将其唤醒，使之获取到对象锁；锁可以重入，多次调用lock锁，导致每一次调用，state都会加1；
【3】本质上是对AQS的state成员变量操作，对该成员变量加1，表示上锁，减1，表示释放锁；
公平锁上锁
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669868498270-1d53cf93-b0e2-477b-a24c-0a5109039412.png#averageHue=%23332b2a&clientId=u71c289cb-14c3-4&from=paste&height=407&id=uac7065cb&name=image.png&originHeight=610&originWidth=1081&originalType=binary&ratio=1&rotation=0&showTitle=false&size=97569&status=done&style=none&taskId=ue687876f-ceaa-4a43-a350-b90212ddb44&title=&width=720.6666666666666)
非公平锁上锁
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669868633448-3fbc5163-e744-4f67-bead-ce858e75f66d.png#averageHue=%23312b2b&clientId=u71c289cb-14c3-4&from=paste&height=396&id=u8b9bb789&name=image.png&originHeight=594&originWidth=1075&originalType=binary&ratio=1&rotation=0&showTitle=false&size=86832&status=done&style=none&taskId=ucb5596fa-1380-4a80-ac34-aff6353ef64&title=&width=716.6666666666666)
#### （3）可重入读写锁（ReentrantReadWriteLock）
【1】读锁：获取读锁时，会尝试判断当前对象是否拥有写锁，如果已经拥有写锁，直接失败，如果没有写锁，则表示当前对象没有排他锁，则当前线程会尝试对象加锁，，如果当前线程已经拥有该对象的锁，直接将读锁数量加1；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669879276855-302eebb7-3980-463a-9676-6668aeb219c6.png#averageHue=%23705439&clientId=u71c289cb-14c3-4&from=paste&height=81&id=ub5d2c37f&name=image.png&originHeight=121&originWidth=1048&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32782&status=done&style=none&taskId=u3901d3dc-65d8-475b-9196-29f839172c9&title=&width=698.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669879601438-67d9a47d-2b25-4574-b860-8e3fe9fd6f46.png#averageHue=%232f2b2b&clientId=u71c289cb-14c3-4&from=paste&height=299&id=u9fcd4dad&name=image.png&originHeight=448&originWidth=997&originalType=binary&ratio=1&rotation=0&showTitle=false&size=61815&status=done&style=none&taskId=u17d05c4b-47b2-4a98-8cf6-aaec828fb8c&title=&width=664.6666666666666)
【2】写锁：获取写锁时，会尝试当前对象是否拥有锁（读锁与写锁），如果已拥有锁并且线程并非当前线程，直接失败；如果当前对象没有加锁，就会为当前对象上锁，并且将写锁数量加1，将当前对象的排他锁线程持有者设为自己；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669879840178-ad194c35-e241-4f8c-be8e-2af8466c9f99.png#averageHue=%23372b2a&clientId=u71c289cb-14c3-4&from=paste&height=221&id=ue74210e6&name=image.png&originHeight=331&originWidth=1070&originalType=binary&ratio=1&rotation=0&showTitle=false&size=66640&status=done&style=none&taskId=udfb2ee38-2fcd-4650-aaa5-d4f1987e937&title=&width=713.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669880085073-b255c06a-0db2-4c6b-970e-cadffc662561.png#averageHue=%233a2a29&clientId=u71c289cb-14c3-4&from=paste&height=59&id=u5755f595&name=image.png&originHeight=88&originWidth=1026&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16144&status=done&style=none&taskId=u5902bb6e-9e0a-4f0c-8c80-9610fe86ccc&title=&width=684)
【3】读锁释放：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669881180052-96edc6c8-520d-4a2e-9874-303509917b38.png#averageHue=%233a2c2a&clientId=u71c289cb-14c3-4&from=paste&height=137&id=u6e319411&name=image.png&originHeight=205&originWidth=1116&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53965&status=done&style=none&taskId=uebfffe4e-8a74-4706-87ee-4f6cc4d7691&title=&width=744)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669881660126-5a88cfac-c7d5-41de-b9c6-61f3b8a19ee8.png#averageHue=%23342b2a&clientId=u71c289cb-14c3-4&from=paste&height=259&id=u9335c009&name=image.png&originHeight=389&originWidth=1133&originalType=binary&ratio=1&rotation=0&showTitle=false&size=68097&status=done&style=none&taskId=u83989128-13f6-46c7-94f8-7d60de9adec&title=&width=755.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669881934552-8e172bc4-ff56-4db6-947f-0e48a8824398.png#averageHue=%23322c2b&clientId=u71c289cb-14c3-4&from=paste&height=205&id=u89dabdb5&name=image.png&originHeight=299&originWidth=978&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42573&status=done&style=none&taskId=u22f90868-7505-4960-adf2-6fe5e1c83dd&title=&width=670)
【4】写锁释放
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669883725695-5e6d16ff-829a-44e8-84de-4ade94c25a0e.png#averageHue=%23342b2a&clientId=u71c289cb-14c3-4&from=paste&height=234&id=u8e4bf411&name=image.png&originHeight=351&originWidth=1160&originalType=binary&ratio=1&rotation=0&showTitle=false&size=66039&status=done&style=none&taskId=u9b2a6204-0c74-466b-8109-f51a9bf36c4&title=&width=773.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669883823728-8c3d6ad0-ca10-4599-b0f3-6e97ca05df18.png#averageHue=%23322c2a&clientId=u25dde710-cfe6-4&from=paste&height=208&id=ud1b2ed7b&name=image.png&originHeight=289&originWidth=913&originalType=binary&ratio=1&rotation=0&showTitle=false&size=43747&status=done&style=none&taskId=u2447ee7c-6d64-4f7a-8194-5eb8f773845&title=&width=658.6666870117188)
#### （4）条件队列与阻塞队列
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669888497977-2462c318-5983-427e-b146-9ea3ba7341c6.jpeg)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669886246010-cd214b97-2e63-4867-bbf6-2e53e2f27bb9.png#averageHue=%232f2c2b&clientId=u25dde710-cfe6-4&from=paste&height=331&id=u6944d053&name=image.png&originHeight=497&originWidth=1041&originalType=binary&ratio=1&rotation=0&showTitle=false&size=66147&status=done&style=none&taskId=u3f267e99-63ac-45aa-9c9a-046a4b89c5e&title=&width=694)
#### （5）阻塞队列（BlockingQueue）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676527231792-13a49395-1971-453e-88ea-c020570fdc5b.jpeg)
#### （5）AQS与synchronized关系
【1】synchronized在实现
①存在两个数据结构：waitset，EntryList，waitset中存放的是调用了Object的wait方法的线程对象，EntryList存放的陷入到阻塞状态，需要获取monitor线程对象
②当一个线程被notify后，线程会从waitset中移动到EntryList中，进入到EntryList后，该线程依旧需要与其他线程争抢monitor对象，如果争抢到，就获取到锁，可以执行；
【2】AQS实现
①存放两种数据结构：Conditiojn对象上的条件队列，以及AQS的阻塞队列，这两个对象每一个都是Node实例（封装线程对象）
②当位于condition条件队列的线程被其他线程signal后，该线程会被移动到阻塞队列中，位于AQS阻塞队列中的Node对象本质上由一个双向队列构成；
③在获取AQS锁中，这些进入阻塞队列的线程会按照队列顺序先后尝试获取；
④当AQS阻塞队列中线程获取到锁后表示该线程可以正常执行；
⑤陷入对等或阻塞状态的线程，依然需要进入操作系统内核态，进入阻塞（park方法实现）；

---

## 16、ConcurrentHashMap
### （1）结构
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676613284516-be0880d7-422a-4c51-8a08-8dafbba78574.jpeg)
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676613581440-5c976a2e-6ae1-429c-ab86-7cc79e45a93d.jpeg)
### （2）put方法
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676616320722-ee1e5594-ac45-4580-8c5f-126e6d545ecf.jpeg)
#### （1）初始化
```java
if (key == null || value == null) throw new NullPointerException();
        int hash = spread(key.hashCode());
        int binCount = 0;
        for (Node<K,V>[] tab = table;;) {
            Node<K,V> f; int n, i, fh;
            if (tab == null || (n = tab.length) == 0)
                tab = initTable();//初始化
              else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {//添加位置结点为空
               		 if (casTabAt(tab, i, null,
                             new Node<K,V>(hash, key, value, null)))//添加结点
                   		 break;                  
              }
```
```java
 private final Node<K,V>[] initTable() {
        Node<K,V>[] tab; int sc;
         //多个线程操作，需要不断自旋判断数组是否尾空
        while ((tab = table) == null || tab.length == 0) {
            if ((sc = sizeCtl) < 0)
                Thread.yield(); 
            else if (U.compareAndSwapInt(this, SIZECTL, sc, -1)) {//只有一个线程进入
                try {
                    if ((tab = table) == null || tab.length == 0) {
                        int n = (sc > 0) ? sc : DEFAULT_CAPACITY;//默认长度16
                        @SuppressWarnings("unchecked")
                        Node<K,V>[] nt = (Node<K,V>[])new Node<?,?>[n];
                        table = tab = nt;
                        sc = n - (n >>> 2);//扩容因子  16*0.75
                    }
                } finally {
                    sizeCtl = sc;
                }
                break;
            }
        }
        return tab;
    }
```
#### （2）put阶段存在hash冲突
```java
     if (fh >= 0) {
            binCount = 1;//记录链表长度，用于后面判断是否需要树华
            for (Node<K,V> e = f;; ++binCount) {
                K ek;
                if (e.hash == hash &&
                    ((ek = e.key) == key ||
                     (ek != null && key.equals(ek)))) {//key的值与存在结点的key一样，直接替换
                    oldVal = e.val;
                    if (!onlyIfAbsent)
                        e.val = value;
                    break;
                }
                Node<K,V> pred = e;//记录前驱结点
                if ((e = e.next) == null) {//直到下一个结点为null，添加新结点到位部
                    pred.next = new Node<K,V>(hash, key,
                                              value, null);
                    break;
                }
            }
    }
```
#### （3）元素个数统计与更新（addCount）
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676619132077-b168b9cf-e8c9-4904-98f6-2b28e39d3e53.jpeg)
##### ①初始化
> private transient volatile long baseCount; 没有竞争情况下，通过CAS更新元素个数
> private transient volatile CounterCell[] counterCells;  多线程竞争情况下，存储元素个数

```java
 @sun.misc.Contended static final class CounterCell {
        volatile long value;
        CounterCell(long x) { value = x; }
    }

	//求总和
    final long sumCount() {
        CounterCell[] as = counterCells; CounterCell a;
        long sum = baseCount;
        if (as != null) {
            for (int i = 0; i < as.length; ++i) {
                if ((a = as[i]) != null)
                    sum += a.value;
            }
        }
        return sum;
    }
```
> 1. 直接访问baseCount累加元素个数；
> 2. 找到CounterCell[]随机下标位置，累加个数
> 3. 如果前面失败，进入fullAddCount（）

```java
 if ((as = counterCells) != null ||
     //CAS修改元素个数，修改成功则不进入if
    !U.compareAndSwapLong(this, BASECOUNT, b = baseCount, s = b + x)) {
    CounterCell a; long v; int m;
    boolean uncontended = true;
     //counterCells数组为空
    if (as == null || (m = as.length - 1) < 0 ||
        (a = as[ThreadLocalRandom.getProbe() & m]) == null ||
        //CAS修改对应CounterCells，修改成功，不进入if
        !(uncontended =
          U.compareAndSwapLong(a, CELLVALUE, v = a.value, v + x))) {
        fullAddCount(x, uncontended);
        return;
    }
    if (check <= 1)
        return;
    s = sumCount();
}
```
##### ②元素个数并发更新（fullAddCount）
> 1. CountCell为null
> 2. 已经初始化，然后存在竞争，CAS进行更新->失败触发CounterCell扩容

```java
CounterCell[] as; CounterCell a; int n; long v;
if ((as = counterCells) != null && (n = as.length) > 0) {
    if ((a = as[(n - 1) & h]) == null) {
        if (cellsBusy == 0) {            
            CounterCell r = new CounterCell(x); 
            //修改cellBusy为1，表示只有一个线程操作
            if (cellsBusy == 0 && 
                U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {
                boolean created = false;
                try {               // Recheck under lock
                    CounterCell[] rs; int m, j;
                    if ((rs = counterCells) != null &&
                        (m = rs.length) > 0 &&
                        rs[j = (m - 1) & h] == null) {
                        rs[j] = r;
                        created = true;
                    }
                } finally {
                    cellsBusy = 0;
                }
                if (created)
                    break;
                continue;           // Slot is now non-empty
            }
        }
        collide = false;
    }
    else if (!wasUncontended)       // CAS already known to fail
        wasUncontended = true;      
    //存在，CAS修改
    else if (U.compareAndSwapLong(a, CELLVALUE, v = a.value, v + x))
        break;
    else if (counterCells != as || n >= NCPU)
        collide = false;            // At max size or stale
    else if (!collide)
        collide = true;
    //容量不够，需要扩容
    else if (cellsBusy == 0 &&
             U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {
        try {
            if (counterCells == as) {
                CounterCell[] rs = new CounterCell[n << 1];
                for (int i = 0; i < n; ++i)//n为原本as的长度
                    rs[i] = as[i];
                counterCells = rs;
            }
        } finally {
            cellsBusy = 0;
        }
        collide = false;
        continue;                   // Retry with expanded table
    }
    h = ThreadLocalRandom.advanceProbe(h);
}
```
```java
 else if (cellsBusy == 0 && counterCells == as && //cellsBusy互斥变量
         U.compareAndSwapInt(this, CELLSBUSY, 0, 1)) {//类似加锁
    boolean init = false;
    try {                          
        if (counterCells == as) {
            CounterCell[] rs = new CounterCell[2];
            rs[h & 1] = new CounterCell(x);//x元素个数
            counterCells = rs;
            init = true;
        }
    } finally {
        cellsBusy = 0;//释放
    }
    if (init)
        break;
}
```
```java
 else if (U.compareAndSwapLong(this, BASECOUNT, v = baseCount, v + x))
        break;    
```
#### （4）扩容阶段
> - 元素个数大于数组长度
> - 此时正在扩容，扩容阶段进入的线程会协助扩容
> - 数组长度大于64，链表长度大于等于8

![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676623721593-aa8ae0d6-3506-4f56-bb2b-83a03790508c.jpeg)
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676625648415-a3614e4e-425d-4dda-bde7-8566d7b696f7.jpeg)
```java
 if (check >= 0) {
    Node<K,V>[] tab, nt; int n, sc;
     //添加元素大于阈值，需要扩容
    while (s >= (long)(sc = sizeCtl) && (tab = table) != null &&
           (n = tab.length) < MAXIMUM_CAPACITY) {
        /*
    	rs二进制：
	    0000 0000 0000 0000  1000 0000 0001 1100
        rs << RESIZE_STAMP_SHIFT) + 2：
        1000 0000 0001 1100（扩容标记）  0000 0000 0000 0010（参与扩容线程数）
        */
        int rs = resizeStamp(n);
        //表示已经有线程正在扩容
        if (sc < 0) {
            //表示不需要协助扩容
            if ((sc >>> RESIZE_STAMP_SHIFT) != rs || sc == rs + 1 ||
                sc == rs + MAX_RESIZERS || (nt = nextTable) == null ||
                transferIndex <= 0)
                break;
            //需要协助扩容，sc记录参与扩容的线程数
            if (U.compareAndSwapInt(this, SIZECTL, sc, sc + 1))//sc二进制运算
                transfer(tab, nt);
        }
        //没有线程在扩容，第一次扩容+2
        else if (U.compareAndSwapInt(this, SIZECTL, sc,
                                     (rs << RESIZE_STAMP_SHIFT) + 2))//左移16位，最高位为1
            transfer(tab, null);//第一次扩容
        s = sumCount();
    }
}
```
```java
if (i < 0 || i >= n || i + n >= nextn) {
    int sc;
    if (finishing) {
        nextTable = null;
        table = nextTab;
        sizeCtl = (n << 1) - (n >>> 1);
        return;
    }
    if (U.compareAndSwapInt(this, SIZECTL, sc = sizeCtl, sc - 1)) {
        if ((sc - 2) != resizeStamp(n) << RESIZE_STAMP_SHIFT)
            return;
        finishing = advance = true;
        i = n; // recheck before commit
    }
}
```
```java
//tab获取数组下标
else if ((f = tabAt(tab, i)) == null)
    advance = casTabAt(tab, i, null, fwd);
```


---

## 17、线程池
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676881404884-9dabf803-5f24-4524-bfbf-a229ae7ebc26.jpeg)
#### （1）线程池构建（ThreadPoolExecutor）
```java
public ThreadPoolExecutor(int corePoolSize,
                              int maximumPoolSize,
                              long keepAliveTime,
                              TimeUnit unit,
                              BlockingQueue<Runnable> workQueue,
                              ThreadFactory threadFactory,
                              RejectedExecutionHandler handler){}
```
【1】int corePoolSize：线程池中一直维护的线程数量，如果线程池处于任务空闲期间，该线程不会被回收调掉；
【2】int maximumPoolSize：线程池中所维护线程数的最大数量；
【3】long keepAlivePoolSize：临时线程存活时间，超过corePoolSize的线程在金经过KeepAliveTime时间后如果一直处于空闲状态，那么超过的线程将会被回收掉；
【4】TimeUnit unit： keepAlivePoolSize的时间单位；
【5】BlockingQueue<Runable> workQueue：向先池所提交的任务位于的阻塞队列，实现有多种；
【6】ThreadFactory threadFactory：线程工厂，用于创建新的线程并被线程池管理，默认线程工厂所创建的线程都是用户线程且优先级为正常优先级；
【7】RejectdExecutionHandler hadler：表示当前线程都在忙于执行任务，并且阻塞队列已满的情况下,新到来的任务该如何对待和处理（拒绝策略）；
#### （2）拒绝策略：
【1】AbortPolicy：直接抛出一个运行异常；
【2】DiscardPolicy：默默丢弃提交任务，不做任何处理，且不抛出异常
【3】DiscardOldestPolicy：丢弃阻塞队列中存放时间久的任务（队头元素），并且为当前所提交的任务留出一个队列空闲空间，将其放入队列；
【4】CallerRunsPolicy：直接由提交任务的线程来运行这个提交的任务（调用run方法）；
#### （3）线程池总体策略
【1】如果线程池正在执行的线程数<corePoolSize，那么线程池就会优先选择新创建的线程来执行任务，而非将提交的任务加到阻塞队列中；
【2】如果线程中正在执行的线程数>=corePoolSize，那么线程池就会优先选择对提交的任务进行阻塞排队，而非创建新的线程；
【3】如果提交的任务无法加入到阻塞队列中，那么线程池就会创建新的线程，如果创建的线程数超过maximumPoolSize，那么拒绝策略起作用；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1670121958931-07f8a0f8-28a7-4e81-825c-8232593fd147.jpeg)
#### （4）线程池维护状态
【1】线程池本身状态：ctl高三位来表示
【2】线程池中所运行线程数量：ctl其余29位表示；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669970187950-8b76846b-f686-4037-badc-f4697b6876e2.png#averageHue=%23312c2b&clientId=u25dde710-cfe6-4&from=paste&height=333&id=u636c975e&name=image.png&originHeight=499&originWidth=1236&originalType=binary&ratio=1&rotation=0&showTitle=false&size=111066&status=done&style=none&taskId=u267e61fc-3ef3-4514-b2bb-b43dc75876e&title=&width=824)
【3】RUNNING ：线程池可以接收新的任务提交，并且可以正常处理阻塞队列中的任务；
【4】SHUTDOWN ：不再接收新的任务提交，不过线程池可以正常处理阻塞队列中的任务；
【5】STOP ：不在接收新的任务，同时丢弃阻塞队列中的任务，中断正在处理中的任务；
【6】TIDYING ：所有任务都执行完毕后（包括阻塞队列中的任务），当前线程中的活动的线程数量降为0，调用terminated方法；
【7】TERMINATED ：线程终止状态，当terminated方法执行完毕后，线程池会处于该状态之下；
【8】RUNNING  ->  SHUTDOWN :当调用线程池shutdown方法时，或者调用finalize方法后（该放啊内部调用shutdown方法）；
【9】RUNNING， SHUTDOWN  -> STOP：当调用线程池shutdownNow方法；
【10】SHUTDOWN -> TIDYING：在线程池与阻塞队列均为空时；
【11】STOP -> TIDYING：线程池为空时；
【12】TIDYING -> TERMINATED：在terminated方法执行完毕后。
#### （5）线程池任务提交
![](https://cdn.nlark.com/yuque/0/2023/jpeg/29496365/1676965819589-aaa286ce-593a-4435-bd3e-d076f839f7ed.jpeg)
【1】两种提交方式：submit和execute
【2】submit三种提交方式，无论哪种方式，最终将转换来的任务转换为一个Callable对象来处理；
【3】当Callable对象构造完毕后，最终会调用Executor接口声明的execute方法执行；
【4】execute方法源码分析
```java
public void execute(Runnable command) {
    if (command == null)
    throw new NullPointerException();

    int c = ctl.get();
    if (workerCountOf(c) < corePoolSize) {
        //创建线程
        if (addWorker(command, true))
            return;
        c = ctl.get();
    }
	//线程执行体添加到阻塞队列
    if (isRunning(c) && workQueue.offer(command)) {
        int recheck = ctl.get();
        //线程没有running，移除任务成功
        if (! isRunning(recheck) && remove(command))
            reject(command);
        else if (workerCountOf(recheck) == 0)
            addWorker(null, false);
    }
    //队列满，线程超过最大值，拒绝策略
    else if (!addWorker(command, false))
        reject(command);
}
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669972706060-70e0316e-8a01-4138-9039-84cba22e6e6a.png#averageHue=%233c2a29&clientId=u25dde710-cfe6-4&from=paste&height=156&id=VmxPh&name=image.png&originHeight=213&originWidth=902&originalType=binary&ratio=1&rotation=0&showTitle=false&size=52387&status=done&style=none&taskId=ucad5ed71-b5c3-4d53-937d-038bdb194c4&title=&width=661.3333740234375)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669972977105-1a7e85dc-8dea-45c3-86b9-1ea70124e53b.png#averageHue=%233b2b29&clientId=u25dde710-cfe6-4&from=paste&height=151&id=SsQps&name=image.png&originHeight=226&originWidth=1072&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59038&status=done&style=none&taskId=uba3cdabc-b359-48a7-81e9-18a38f7addf&title=&width=714.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669973182483-f35fa7c7-4537-4e6b-b1bf-7379e7e274ce.png#averageHue=%23372b29&clientId=u25dde710-cfe6-4&from=paste&height=66&id=Ek0b3&name=image.png&originHeight=99&originWidth=1022&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16832&status=done&style=none&taskId=uba6cafc1-343d-4e26-997e-5a678a0d8f7&title=&width=681.3333333333334)
【5】addWorker（）方法分析：创建线程并启动
```java
private boolean addWorker(Runnable firstTask, boolean core) {
    //增加线程数量
    retry:
    for (;;) {
        int c = ctl.get();
        //获取线程池状态
        int rs = runStateOf(c);

        //判断线程是否处于终止状态
        if (rs >= SHUTDOWN &&
            ! (rs == SHUTDOWN &&
               firstTask == null &&
               ! workQueue.isEmpty()))
            return false;

        for (;;) {
            int wc = workerCountOf(c);//获取线程数量
            //判断线程数量是否超出
            if (wc >= CAPACITY ||
                //false表示阻塞队列满
                wc >= (core ? corePoolSize : maximumPoolSize))
                return false;
            //修改线程数量
            if (compareAndIncrementWorkerCount(c))
                break retry;
            c = ctl.get();  // Re-read ctl
            if (runStateOf(c) != rs)
                continue retry;
        }
    }

    boolean workerStarted = false;
    boolean workerAdded = false;
    Worker w = null;
    try {
        //创建一个线程
        w = new Worker(firstTask);
        final Thread t = w.thread;
        if (t != null) {
            final ReentrantLock mainLock = this.mainLock;
            //加锁
            mainLock.lock();
            try { 
                int rs = runStateOf(ctl.get());

                if (rs < SHUTDOWN ||
                    (rs == SHUTDOWN && firstTask == null)) {
                    if (t.isAlive()) // precheck that t is startable
                        throw new IllegalThreadStateException();
                    //hashSet存储工作线程
                    workers.add(w);
                    //更新线程最大数量
                    int s = workers.size();
                    if (s > largestPoolSize)
                        largestPoolSize = s;
                    workerAdded = true;
                }
            } finally {
                mainLock.unlock();
            }
            if (workerAdded) {
                t.start();
                workerStarted = true;
            }
        }
    } finally {
        if (! workerStarted)
            //添加失败，删除线程
            addWorkerFailed(w);
    }
    return workerStarted;
}
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669974720384-49450031-dcaa-4579-83dc-62fa3ed22396.png#averageHue=%23372b2a&clientId=u25dde710-cfe6-4&from=paste&height=249&id=KT9nk&name=image.png&originHeight=373&originWidth=1112&originalType=binary&ratio=1&rotation=0&showTitle=false&size=69700&status=done&style=none&taskId=u3612d9df-1a11-4d2a-bac1-130d37a1634&title=&width=741.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669975033802-f68e03ba-5035-48c1-af9f-20b4e2becb7b.png#averageHue=%23342b2a&clientId=u25dde710-cfe6-4&from=paste&height=293&id=nywvK&name=image.png&originHeight=440&originWidth=1045&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75543&status=done&style=none&taskId=u35c54005-91fa-4368-ad0d-07cd1ce7ea8&title=&width=696.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669975635302-eee9bee7-0f10-4533-9d38-72e5dfc618e9.png#averageHue=%232e2b2b&clientId=u25dde710-cfe6-4&from=paste&height=424&id=RZKrH&name=image.png&originHeight=636&originWidth=1193&originalType=binary&ratio=1&rotation=0&showTitle=false&size=91649&status=done&style=none&taskId=u78e95b9c-c07c-4c0a-984a-d6a3fee5d8f&title=&width=795.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669975684605-f54f5a24-406e-4efc-8673-edc291cb42a1.png#averageHue=%23362a29&clientId=u25dde710-cfe6-4&from=paste&height=104&id=fKjf8&name=image.png&originHeight=137&originWidth=878&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18171&status=done&style=none&taskId=u0fbc3536-6ec0-4bb0-89a0-707c0040c9e&title=&width=663.3333740234375)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1669975879037-41800bed-72a5-4871-862f-ff0015da6f7e.png#averageHue=%23352a29&clientId=u25dde710-cfe6-4&from=paste&height=95&id=Yayxy&name=image.png&originHeight=143&originWidth=1073&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20417&status=done&style=none&taskId=u03fd4db4-a20b-439b-accf-423bb8ed569&title=&width=715.3333333333334)
#### （6）线程池任务的执行流程（Worker的run方法）
getTask（）从阻塞队列获取队头任务
```java
private Runnable getTask() {
    boolean timedOut = false; // Did the last poll() time out?

    for (;;) {
        int c = ctl.get();
        int rs = runStateOf(c);

        // Check if queue empty only if necessary.
        if (rs >= SHUTDOWN && (rs >= STOP || workQueue.isEmpty())) {
            decrementWorkerCount();
            return null;
        }

        int wc = workerCountOf(c);

        // 线程数量大于核心数量，返回null，回收线程
        boolean timed = allowCoreThreadTimeOut || wc > corePoolSize;

        //工作线程大于最大线程或核心线程数，工作线程减1
        if ((wc > maximumPoolSize || (timed && timedOut))
            && (wc > 1 || workQueue.isEmpty())) {
            //工作线程减一
            if (compareAndDecrementWorkerCount(c))
                return null;
            continue;
        }

        try {
            Runnable r = timed ?
                //阻塞队列为空，
                workQueue.poll(keepAliveTime, TimeUnit.NANOSECONDS) :
                //获取不到数据，线程阻塞（工作线程数小于核心线程数）
                workQueue.take();
            if (r != null)
                return r;
            timedOut = true;
        } catch (InterruptedException retry) {
            timedOut = false;
        }
    }
}
```
runWorker（）执行任务
```java
final void runWorker(Worker w) {
    Thread wt = Thread.currentThread();
    Runnable task = w.firstTask;
    w.firstTask = null;
    w.unlock(); // allow interrupts
    boolean completedAbruptly = true;
    try {
        //任务不为空，为空，线程结束（线程销毁）
        while (task != null || (task = getTask()) != null) {
            w.lock();
            // If pool is stopping, ensure thread is interrupted;
            // if not, ensure thread is not interrupted.  This
            // requires a recheck in second case to deal with
            // shutdownNow race while clearing interrupt
            if ((runStateAtLeast(ctl.get(), STOP) ||
                 (Thread.interrupted() &&
                  runStateAtLeast(ctl.get(), STOP))) &&
                !wt.isInterrupted())
                wt.interrupt();
            try {
                beforeExecute(wt, task);
                Throwable thrown = null;
                try {
                    //任务执行，任务为实现Runable的run方法
                    task.run();
                } catch (RuntimeException x) {
                    thrown = x; throw x;
                } catch (Error x) {
                    thrown = x; throw x;
                } catch (Throwable x) {
                    thrown = x; throw new Error(x);
                } finally {
                    afterExecute(task, thrown);
                }
            } finally {
                task = null;
                w.completedTasks++;
                w.unlock();
            }
        }
        completedAbruptly = false;
    } finally {
        processWorkerExit(w, completedAbruptly);
    }
}
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670121153322-91d2184e-9a45-45c6-b35e-4c66ff5b3ec7.png#averageHue=%233a2c2a&clientId=ubcda59a6-d1c5-4&from=paste&height=199&id=u3abb8469&name=image.png&originHeight=298&originWidth=993&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62143&status=done&style=none&taskId=u3fce06dd-00b4-4f62-9c88-88c127b8497&title=&width=662)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670122455105-ab6ac25b-633b-4324-b43b-1313b310f505.png#averageHue=%23312b2a&clientId=ubcda59a6-d1c5-4&from=paste&height=308&id=u718ffaac&name=image.png&originHeight=462&originWidth=1026&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62175&status=done&style=none&taskId=ued251ef2-cd84-4d8f-b7ee-1fbd88b9eca&title=&width=684)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670123734061-0fbc2d42-05be-4eea-8cd7-e6e0bb3c6cb3.png#averageHue=%232e2b2a&clientId=ubcda59a6-d1c5-4&from=paste&height=217&id=u26b22d8f&name=image.png&originHeight=326&originWidth=1054&originalType=binary&ratio=1&rotation=0&showTitle=false&size=33992&status=done&style=none&taskId=u0bcb28bf-4b7b-471f-b600-f34f5a70292&title=&width=702.6666666666666)
#### （7）线程池终止
【1】shutdown（）方法：拒绝新任务提交，会继续执行完阻塞队列中的任务后，才会进入终止状态；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670125866010-06fdfda4-bda2-4ed8-83d8-f15e216282ac.png#averageHue=%232f2c2b&clientId=ubcda59a6-d1c5-4&from=paste&height=280&id=u0e003a91&name=image.png&originHeight=420&originWidth=1046&originalType=binary&ratio=1&rotation=0&showTitle=false&size=55027&status=done&style=none&taskId=ua49fff4b-fec8-448d-be72-8455a5a4317&title=&width=697.3333333333334)interruptIdleWorkers()方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670125977119-c29d7e86-a4e1-4e42-b476-5c39a9e680c4.png#averageHue=%232f2b2b&clientId=ubcda59a6-d1c5-4&from=paste&height=451&id=u2356a4d6&name=image.png&originHeight=676&originWidth=1154&originalType=binary&ratio=1&rotation=0&showTitle=false&size=74959&status=done&style=none&taskId=uc392fc02-be34-4d33-86d4-525f7ff978d&title=&width=769.3333333333334)
tryTerminate()方法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670126228798-5b52b5b0-ceb4-4702-a4eb-7aeb3502881b.png#averageHue=%232e2b2a&clientId=ubcda59a6-d1c5-4&from=paste&height=326&id=uf9eb4599&name=image.png&originHeight=489&originWidth=974&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53626&status=done&style=none&taskId=u367c06ff-b236-45a9-921b-8c0bb5a3abb&title=&width=649.3333333333334)
【2】shutdownNow（）方法：拒绝新任务提交，停止所有正在执行任务的线程；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670126474385-b007a026-dbc2-49ff-91fe-d80ace8924de.png#averageHue=%23322b2b&clientId=ubcda59a6-d1c5-4&from=paste&height=327&id=u015ac2e6&name=image.png&originHeight=491&originWidth=1137&originalType=binary&ratio=1&rotation=0&showTitle=false&size=71222&status=done&style=none&taskId=u212a5099-ea0a-486f-85c7-79074cbfffb&title=&width=758)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670126529629-af783a19-dcf5-4ea9-9a7b-e0515dfef822.png#averageHue=%232f2c2b&clientId=ubcda59a6-d1c5-4&from=paste&height=255&id=u61f23055&name=image.png&originHeight=383&originWidth=1043&originalType=binary&ratio=1&rotation=0&showTitle=false&size=50889&status=done&style=none&taskId=u5d8a8c88-816a-4e83-ae60-07254063ba7&title=&width=695.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670126587417-9f6e2672-0fb3-4262-85a7-f8fe9e1ffd60.png#averageHue=%23302b2a&clientId=ubcda59a6-d1c5-4&from=paste&height=221&id=u0b432a74&name=image.png&originHeight=331&originWidth=1034&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38267&status=done&style=none&taskId=u76298200-be9c-42bb-aa8e-12731c88adc&title=&width=689.3333333333334)
#### （8）ForkJoinPool线程池
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1670139123804-e4dec0e9-c1dd-421b-b116-0eeb1b740a41.jpeg)
#### （9）CompletableFuture
##### ①thenApply源码
```java
public <U> CompletableFuture<U> thenApply(
    Function<? super T,? extends U> fn) {
    return uniApplyStage(null, fn);
}
```
```java
private <V> CompletableFuture<V> uniApplyStage(
    Executor e, Function<? super T,? extends V> f) {
    if (f == null) throw new NullPointerException();
    CompletableFuture<V> d =  new CompletableFuture<V>();
    //e:一步调用直接执行
    //uniApply任务执行失败，需要入栈
    if (e != null || !d.uniApply(this, f, null)) {
        UniApply<T,V> c = new UniApply<T,V>(e, d, this, f);
        push(c);
        //尝试执行任务
        c.tryFire(SYNC);
    }
    return d;
}
```
```java
final <S> boolean uniApply(CompletableFuture<S> a,
                           Function<? super S,? extends T> f,
                           UniApply<S,T> c) {
    Object r; Throwable x;
    if (a == null || (r = a.result) == null || f == null)
        return false;
    tryComplete: if (result == null) {
        if (r instanceof AltResult) {
            if ((x = ((AltResult)r).ex) != null) {
                completeThrowable(x, r);
                break tryComplete;
            }
            r = null;
        }
        try {
            if (c != null && !c.claim())
                return false;
            @SuppressWarnings("unchecked") S s = (S) r;
            //执行任务，并将结果写入result
            completeValue(f.apply(s));
        } catch (Throwable ex) {
            completeThrowable(ex);
        }
    }
    return true;
}
```
##### ②thenAcceptAsync源码（异步执行）
```java
public CompletableFuture<Void> thenAcceptAsync(Consumer<? super T> action) {
    return uniAcceptStage(asyncPool, action);
}
```
```java
private CompletableFuture<Void> uniAcceptStage(Executor e,
                                               Consumer<? super T> f) {
    if (f == null) throw new NullPointerException();
    CompletableFuture<Void> d = new CompletableFuture<Void>();
    //异步调用，e不为null，执行压入栈顶
    if (e != null || !d.uniAccept(this, f, null)) {
        UniAccept<T> c = new UniAccept<T>(e, d, this, f);
        push(c);
        c.tryFire(SYNC);
    }
    return d;
}
```
```java
static final class UniAccept<T> extends UniCompletion<T,Void> {
    Consumer<? super T> fn;
    UniAccept(Executor executor, CompletableFuture<Void> dep,
              CompletableFuture<T> src, Consumer<? super T> fn) {
        super(executor, dep, src); this.fn = fn;
    }
    final CompletableFuture<Void> tryFire(int mode) {
        CompletableFuture<Void> d; CompletableFuture<T> a;
         //dep为null，任务已经执行过
        //uniAccept为false表示任务可能已被其他线程执行
        if ((d = dep) == null ||
            !d.uniAccept(a = src, fn, mode > 0 ? null : this))
            return null;
        dep = null; src = null; fn = null;
        //任务已经完成，继续执行前一个任务
        return d.postFire(a, mode);
    }
}
```
```java
final CompletableFuture<T> postFire(CompletableFuture<?> a, int mode) {
    if (a != null && a.stack != null) {
        //前一个任务执行完毕
        if (mode < 0 || a.result == null)
            a.cleanStack();//任务出栈
        else
            a.postComplete();
    }
    if (result != null && stack != null) {
        if (mode < 0)
            return this;
        else
            postComplete();
    }
    return null;
}
```
##### ③supplyAsync源码
```java
static <U> CompletableFuture<U> asyncSupplyStage(Executor e,
                                                 Supplier<U> f) {
    if (f == null) throw new NullPointerException();
    CompletableFuture<U> d = new CompletableFuture<U>();
    e.execute(new AsyncSupply<U>(d, f));
    return d;
}
```
```java
static final class AsyncSupply<T> extends ForkJoinTask<Void>
    implements Runnable, AsynchronousCompletionTask {
        CompletableFuture<T> dep;//
        Supplier<T> fn;//执行逻辑
        AsyncSupply(CompletableFuture<T> dep, Supplier<T> fn) {
            this.dep = dep; this.fn = fn;
        }

        public final Void getRawResult() { return null; }
        public final void setRawResult(Void v) {}
        public final boolean exec() { run(); return true; }

        public void run() {
            CompletableFuture<T> d; Supplier<T> f;
            if ((d = dep) != null && (f = fn) != null) {
                dep = null; fn = null;
                //result为任务执行完后的结果，为null表示未完成结果
                if (d.result == null) {
                    try {
                        d.completeValue(f.get());//等待任务结束并设置结果
                    } catch (Throwable ex) {
                        d.completeThrowable(ex);
                    }
                }
                //任务执行完成，执行所有依赖改任务的所有任务
                d.postComplete();
            }
        }
    }
```
```java
final void postComplete() {
    CompletableFuture<?> f = this; 
    Completion h;
    while ((h = f.stack) != null ||
           (f != this && (h = (f = this).stack) != null)) {
        CompletableFuture<?> d; 
        Completion t;//保存的是依靠当前CompletableFuture的任务
        if (f.casStack(h, t = h.next)) {//获取栈中下一个Completion
            if (t != null) {
                //当前的CompletableFuture不是this的，将所有Completion加入当前栈中
                if (f != this) {
                    pushStack(h);
                    continue;
                }
                h.next = null;    // 为当前CompletableFuture，解除联系
            }
            f = (d = h.tryFire(NESTED)) == null ? this : d;
        }
    }
}
```
每个CompletableFuture持有一个Completion栈stack, 每个Completion持有一个CompletableFuture， 如此递归循环下去，是层次很深的树形结构，所以想办法将其变成链表结构。
![](https://cdn.nlark.com/yuque/0/2023/webp/29496365/1677058693628-12e94f36-1114-40b6-9864-1fe0b9ff1b35.webp#averageHue=%23f6ebdc&clientId=udc49f82a-3194-4&from=paste&id=u46e4d02d&originHeight=923&originWidth=1775&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=u15af37ce-ea8e-4b6e-a061-db981afb536&title=)
首先取出头结点，下图中灰色Completion结点，它会返回一个CompletableFuture, 同样也拥有一个stack，策略是遍历这个CompletableFuture的stack的每个结点，依次压入到当前CompletableFuture的stack中，关系如下箭头所示，灰色结点指的是处理过的结点。
![](https://cdn.nlark.com/yuque/0/2023/webp/29496365/1677058706103-db065756-9b0e-43b9-acd4-05afa156fc69.webp#averageHue=%23f6ecde&clientId=udc49f82a-3194-4&from=paste&id=u7c089b54&originHeight=933&originWidth=1775&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=ue810852b-f463-4699-aae7-c38c376c2ca&title=)
第一个Completion结点返回的CompletableFuture, 将拥有的stack里面的所有结点都压入了当前CompletableFuture的stack里面
![](https://cdn.nlark.com/yuque/0/2023/webp/29496365/1677058717485-4eabee00-7b40-417b-9950-774107d7f9d1.webp#averageHue=%23f5ede2&clientId=udc49f82a-3194-4&from=paste&id=uaef38460&originHeight=950&originWidth=1775&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=ud3b50550-cb0e-4d9b-a849-d08269145b1&title=)
后续的Completion结点返回的CompletableFuture, 将拥有的stack里面的所有结点都压入了当前CompletableFuture的stack里面，重新构成了一个链表结构，后续也按照前面的逻辑操作，如此反复，便会遍历完所有的CompletableFuture, 这些CompletableFuture(叶子结点)的stack为空，也是结束条件。
![](https://cdn.nlark.com/yuque/0/2023/webp/29496365/1677058730044-52d6f0ed-8896-4a49-86dc-51d8c17aa13e.webp#averageHue=%23f1efed&clientId=udc49f82a-3194-4&from=paste&id=uad13c6ba&originHeight=950&originWidth=1718&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=u2bfe8877-080b-4587-b1c3-1ca2543e36a&title=)
