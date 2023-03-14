#### 一、逻辑运算符
1、逻辑与（&）、短路与（&&）区别：
&：第一个条件为false，还需要判断第二个条件；
&&：第一个条件为false，不需要执行第二个条件。
2、逻辑或（|），短路或（||）区别：
|：第一个条件为true，需要判断第二个条件；
||：第一个条件为true，不需要判断第二个条件

#### 二、位运算
1、原码、反码、补码：
（1）最高位为符号位，0正数，1负数；
（2）正数原码，反码、补码一样；
（3）负数反码=他的符号位不变，其他位取反；
（4）负数的补码=他的反码+1，负数的反码=负数的补码-1；
（5）0的反码、补码都是0；
（6）java没有1无符号数，java的数都是有符号的；
（7）计算机运行以补码运算；
（8）看运算结果要看原码。
2、运算符：
（1）按位与&：两位全为1，结果为1，否则为0；
（2）按位或|：两个一个为1，结果为1，否则为0；
（3）按位异或^：两位一个为0，一个为1，结果为1，否则为0；
（4）按位取反~:0->1,1->0；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662792681892-ba6fa430-70ef-493f-bfa4-c0d8035db687.png#averageHue=%23fbfaf9&clientId=uae3ba29e-c793-4&from=paste&height=389&id=ucd49eb70&name=image.png&originHeight=583&originWidth=1020&originalType=binary&ratio=1&rotation=0&showTitle=false&size=73425&status=done&style=none&taskId=u0f52b781-ddc4-4ac2-bccb-bc71f184c90&title=&width=680)
（5）>> 算术右移：低位溢出，符号位不变，并用符号位补溢出高位；
（6）算术左移<<：符号位不变，低位补0；
（7）无符号右移>>>：低位溢出，高位补0。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662793331085-c6bc1385-b9ff-40fa-8d66-d86a9050558d.png#averageHue=%23faf9f7&clientId=uae3ba29e-c793-4&from=paste&height=191&id=u9ccae6eb&name=image.png&originHeight=286&originWidth=936&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39646&status=done&style=none&taskId=u824b5d65-9ae3-4783-bf4c-17782938daf&title=&width=624)


#### 三、数组
1、数组赋值方式为引用传递，赋的值是地址，赋值方式为引用赋值
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662794012250-30941224-7d8d-4228-9726-0117fb4979e2.png#averageHue=%23fcfbfb&clientId=uae3ba29e-c793-4&from=paste&height=167&id=ubcf9eec0&name=image.png&originHeight=251&originWidth=737&originalType=binary&ratio=1&rotation=0&showTitle=false&size=24129&status=done&style=none&taskId=uc5962ace-f662-4d3e-b06c-1933e99818b&title=&width=491.3333333333333)
2、值传递(拷贝)与引用传递区别
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1669801075757-bbad246c-173d-4ed1-b8ec-fd590132a27d.jpeg)

#### 四、类与对象
1、对象内存布局
String类型是引用类型，存在常量池，基本类型可以直接存放堆内
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1662799602788-89c61eae-8746-4668-90f1-6385e89d27c4.jpeg)
2、类与对象内存分配机制
（1）先加载Person类信息，只会加载一次；
（2）在堆中欧分配空间，进行默认初始化；
（3）把地址赋给person，person就指向对象；
（4）指定初始化
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662799872852-626bf632-619c-47d3-8028-4acfab92f299.png#averageHue=%23fbfaf7&clientId=ub3b0cff6-ea45-4&from=paste&height=91&id=ue5c87ccb&name=image.png&originHeight=137&originWidth=790&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14540&status=done&style=none&taskId=u6cb53a16-2eef-44ac-be47-b31095377b4&title=&width=526.6666666666666)
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1662800022920-828b017e-0e44-498a-bea2-7fbc375d113b.jpeg)
3、对象创建流程分析（面试题）
（1）加载Person类信息，只会加载一次；
（2）在堆中分配空间（地址）；
（3）进行对象初始化（先默认初始化，然后显示初始化，最后构造器初始化）;
（4）对象在堆中地址返回给person，person对象引用，真正对象在堆中;
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1662877997555-d0b82696-66ed-4ef4-8603-92901d7951f8.jpeg)
4、this本质
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1662990288983-dc0df21f-3f80-4f50-b6d7-7ceebd143e83.jpeg)
5、方法调用流程
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1671272093856-9d8fe9df-1f0f-4878-b224-ecb69ad2e1fb.jpeg)
6、参数引用
```java
class Person{
    String name;
    int age;
}

public static void main(String[] args){
    Person p=new Person();
    person.age=12;
    person.name="name";
    update(p);
    System.out.println(p.age);//输出12
    update2(p);
    System.out.println(p.age);//输出12
}

public void update(Person p){
    p=null;
}

public void update2(Person p){
    p=new Person();
	p.age=44;
}
```
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1671275716184-df974019-cc52-43b8-a5f7-97034bcea489.jpeg)
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1671275717337-95ed783b-7846-4400-8739-db4df236858d.jpeg)

#### 五、继承
1、继承细节
（1）子类必须调用父类的构造器，完成父类初始化；
（2）创建子类对象时，不管使用子类哪个构造器，默认会调用父类构造器；
（3）父类未提供无参构造器，必须在子类构造器中指定使用父类哪个构造器；
（4）super（）在使用时，必须放在构造器第一行；
（5）Java所有类都是Object的子类；
2、本质
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662895156799-4c8c07a3-c234-4468-be50-7cfa8fcb0d8a.png#averageHue=%23fdfcfb&clientId=uf1fb69c9-a2ed-4&from=paste&height=254&id=u2eeafdf9&name=image.png&originHeight=527&originWidth=971&originalType=binary&ratio=1&rotation=0&showTitle=false&size=55240&status=done&style=none&taskId=u694d78a0-281e-4685-820e-2547c877ad5&title=&width=467.3333740234375)
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1662896034213-2b9e1cd2-dcb7-4254-993f-d52f90b2df29.jpeg)

#### 六、多态
1、对象多态
（1）一个对象的编译类型和运行类型可以不一致；
（2）编译类型在定义时对象时就确定了，不可以改变；
（3）运行类型是可以变化的；
（4）编译类型看定义时=号左边，运行类型看=号右边；
2、动态绑定机制
（1）当调用对象方法时，该方法会和该对象的内存地址和运行类型绑定；
（2）当调用对象属性时，没有动态绑定机制，哪里声明，哪里调用；

#### 七、Object类
1、==与equals对比
（1）==一个比较运算符，判段基本类型，判断值是否相等，判断引用类型，判断地址是否相等，即是否为同一对象；
（2）equals只能判断引用类型，默认判断地址是否相等，Integer和String重写该方法，用于判断内容是否相等；
String中的equals原码
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1662971732695-fa7da520-f110-4541-aa27-15e6586716e0.png#averageHue=%23fdfdfd&clientId=ueb8cad37-9984-4&from=paste&height=485&id=ude37cdb4&name=image.png&originHeight=727&originWidth=933&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75598&status=done&style=none&taskId=u5a2fbb07-31dc-4f2b-b49f-a83e9925a20&title=&width=622)
2、hashCode（）方法
（1）提高具有hash结构的容器的效率；
（2）如果指向同一个对象，hash值一样；
（3）hash值根据地址计算，但不能将hash值等价于地址
3、finalize方法（几乎不会运用）
（1）对象被回收，系统会调用finalize方法；
（2）销毁对象前，会先调用finalize方法

#### 八、main方法和代码块
1、main特点：
（1）main方法有java虚拟机调用，权限必须为public；
（2）调用main方法不必创建对象，所以必须为static；
（3）字符串数组参数：java执行程序时传入的参数
（4）静态方法main可以访问本类中的静态成员；
2、代码块
（1）静态代码块只会在类加载时加载，只会执行一次；
（2）普通代码块是在创建对象时调用，每创建一次调用一次；
（3）多个静态代码块，优先级一样，按顺序执行；
（4）调用顺序：静态代码块->普通代码块->构造器；
（5）创建一个子类对象（继承关系），顺序如下:
①父类静态代码块和静态属性；
②子类静态代码块和静态属性；
③父类普通代码块和普通属性初始化；
④父类构造方法；
⑤子类普通代码块和普通属性初始化；
⑥子类构造方法
（6）静态代码块只能调用静态成员，普通代码块可以调用任意成员。

#### 九、单例设计模式
1、采取一定方法保证整个软件系统中，对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法。如Runtime就是单例模式
2、饿汉式：
（1）构造器私有化，防止用户new对象；
（2）类的内部创建对象；
（3）向外暴露一个静态公共方法
可能造成创建了对象没有使用，导致资源浪费，不存在线程安全
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663081176471-91390f83-ce9f-4939-965e-4b361d1c0b97.png#averageHue=%23fbfbf9&clientId=u7388020b-28c3-4&from=paste&height=516&id=ua4cfbe82&name=image.png&originHeight=774&originWidth=1086&originalType=binary&ratio=1&rotation=0&showTitle=false&size=123959&status=done&style=none&taskId=u815db590-6415-46e5-ad1c-ef4aba12204&title=&width=724)
3、懒汉式
（1）构造器私有化，防止用户new对象；
（2）类的内部创建对象；
（3）向外暴露一个静态公共方法
只有调用公共方法才会创建对象，不会造成资源浪费，存在线程安全
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663082061103-734b4c5b-a09d-40c7-a1af-7f1f124884e4.png#averageHue=%23fdfdfc&clientId=u7388020b-28c3-4&from=paste&height=530&id=uf624ba85&name=image.png&originHeight=795&originWidth=1138&originalType=binary&ratio=1&rotation=0&showTitle=false&size=112901&status=done&style=none&taskId=ua341fcde-3b90-43e8-ad3c-af7783dc02b&title=&width=758.6666666666666)

#### 十、模板设计模式
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663155816605-f9c793bf-367d-42d3-aed5-19886a1b8846.png#averageHue=%23fcfbf9&clientId=u7388020b-28c3-4&from=paste&height=230&id=u20c93f46&name=image.png&originHeight=345&originWidth=1007&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53029&status=done&style=none&taskId=u33ee8722-3d1f-4fc1-842b-a42fe9ff82b&title=&width=671.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663155839897-43f05e74-8279-44b6-806a-35c9f071a88c.png#averageHue=%23fdfdfd&clientId=u7388020b-28c3-4&from=paste&height=419&id=u0397ff49&name=image.png&originHeight=629&originWidth=997&originalType=binary&ratio=1&rotation=0&showTitle=false&size=46864&status=done&style=none&taskId=uc36894c6-ee46-4ec7-b1b0-51cfc8b1419&title=&width=664.6666666666666)

#### 十一、内部类
1、局部内部类：定义在外部类的局部位置，并且有类名，如：方法中
（1）可以访问外部类所有成员，包含私有；
（2）不能使用访问修饰符，可以使用final修饰；
（3）作用域仅仅在定义他的方法中；
（4）外部类在方法中可以创建局部内部类对象，然后调用方法；
（5）外部类与局部类重名，遵循就近原则，如果访问外部类成员，可以使用（外部类.this.成员）
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663165451711-c9bd0f45-fa13-44c8-bbe4-388e01a37641.png#averageHue=%23fdfbfb&clientId=u7388020b-28c3-4&from=paste&height=457&id=u4b16b430&name=image.png&originHeight=685&originWidth=1089&originalType=binary&ratio=1&rotation=0&showTitle=false&size=56242&status=done&style=none&taskId=u41eeb0cb-a291-470e-987f-dcaf9f3ade9&title=&width=726)
2、匿名内部类（重点）
（1）定义在外部类的局部位置，没有类名，同时还是一个对象，本质为类；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663167012435-0720b77a-ac84-4068-8fc7-97f4aff2250d.png#averageHue=%23fdfdfd&clientId=u7388020b-28c3-4&from=paste&height=521&id=u13a4ef38&name=image.png&originHeight=782&originWidth=1136&originalType=binary&ratio=1&rotation=0&showTitle=false&size=85441&status=done&style=none&taskId=ued1fe976-cf13-4a34-8797-5cd58f6068b&title=&width=757.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663167636116-1e20f637-3ab1-4d67-98da-27f5318eb99e.png#averageHue=%23fdfdfc&clientId=u7388020b-28c3-4&from=paste&height=393&id=uea764c1a&name=image.png&originHeight=589&originWidth=1100&originalType=binary&ratio=1&rotation=0&showTitle=false&size=74073&status=done&style=none&taskId=ue6fff68a-0d4e-41ea-b49b-c47f7e29785&title=&width=733.3333333333334)
（2）匿名内部类本身也是返回类对象；
（3）匿名内部类可以访问外部类的所有成员变量，包括私有；
（4）作用域仅仅只是在方法或代码块中；
（5）外部类与局部类重名，遵循就近原则，如果访问外部类成员，可以使用（外部类.this.成员）

#### 十二、异常
1、Exption异常：
（1）运行异常：程序运行时发生的异常；
（2）编译异常：编程时，编译器检查出的异常。
2、异常体系图：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663254384839-68187658-b7ed-467d-b924-bab57504ccdc.png#averageHue=%23fcfcfc&clientId=u7388020b-28c3-4&from=paste&height=446&id=uad103189&name=image.png&originHeight=669&originWidth=1807&originalType=binary&ratio=1&rotation=0&showTitle=false&size=40219&status=done&style=none&taskId=u6ce3495f-c7ce-4ba6-b483-fd150a06fb4&title=&width=1204.6666666666667)
3、异常处理机制
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663313734912-e955de0e-4c73-4ca7-88e3-aa7daf5a9572.jpeg)

#### 十三、String
1、String体系图
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663336739000-ed76a3ee-ce66-49b0-888f-67ecc59dfd9b.png#averageHue=%23fdf7f6&clientId=ua23f3c97-6d0b-4&from=paste&height=240&id=uadf2bc3e&name=image.png&originHeight=360&originWidth=1117&originalType=binary&ratio=1&rotation=0&showTitle=false&size=29011&status=done&style=none&taskId=ubf58239f-96b4-4039-99e2-3284af98ebf&title=&width=744.6666666666666)
2、用于存放字符串内容，赋值后不能修改（value地址不能修改），value不能指向新的地址
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663337193714-8702a2ec-3f95-477b-a98a-87fe2f8d7e31.png#averageHue=%23fcfaf5&clientId=ua23f3c97-6d0b-4&from=paste&height=55&id=uc6c68bc0&name=image.png&originHeight=82&originWidth=962&originalType=binary&ratio=1&rotation=0&showTitle=false&size=7452&status=done&style=none&taskId=u9a24c341-1f1c-40d4-aac8-4efb2d2609c&title=&width=641.3333333333334)
3、String的内存布局
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1663391507899-9791b217-5488-424e-ad75-7436a2fc471a.png#averageHue=%23fcfaf5&clientId=ua23f3c97-6d0b-4&from=paste&height=61&id=u0f15bf9c&name=image.png&originHeight=91&originWidth=720&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10139&status=done&style=none&taskId=u8da909ac-1ea9-40d8-9c0d-84308593f8f&title=&width=480)
（1）第一种直接在常量池中找，若未找到，就创建；
（2）第二种方式，先在堆中开辟一个空间，value去常量池寻找，未找到则创建，找到则指向该常量地址；
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1663393445952-6bd947f5-59ce-44cb-8d13-1eaa75d2ea54.jpeg)
4、StringBuffer与String
（1）StringBuffer存放在堆中，里面值可以更改，不用每次更新地址，效率高，线程安全；
```java
    public synchronized StringBuffer append(Object obj) {
        toStringCache = null;
        super.append(String.valueOf(obj));
        return this;
    }
```
（2）String存放字符串常量，里面值不能更改，每次更新String类，实际就是更改地址，效率低
5、StringBuilder
（1）不是线程安全；
（2）在普通拼接字符串常量时，试用+；
（3）对于for循环拼接字符串，使用stringBuilder最快；；
（4）对于有并发安全的字符串拼接，采用stringBuffer

---

#### 十四、包装类
##### 1、Integer
（1）值的范围在-128——127之间，直接返回缓存池中的数据值，多次获取均为同一个对象；编译器会**在缓冲池范围内的基本类型**自动装箱过程调用 valueOf() 方法，因此多个 Integer 实例使用自动装箱来创建并且值相同，那么就会引用相同的对象。
```java
Integer m=1;
Integer n=1;
System.out.println(m==n);//true
```
（2）值的范围不在-128——127之间，会new Integer（），返回对象不同；
```java
Integer m=139;
Integer n=139;
System.out.println(m==n);//false
Integer a=12;
Integer b=new Integer(12);
a==b;//false
```
```java
	public static Integer valueOf(int i) {
        //范围在-128——127
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);//超出范围
    }
```

