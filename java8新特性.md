### 1、lambda表达式
#### （1）函数式接口：
①如果一个接口只有一个抽象方法，那么该接口是函数式接口；
②如果在接口上声明FunctionalInterface 注解，那么编译器就会按照函数式接口定义要求该接口；
③如果某个接口只有一个抽象方法，但我们并没有给该接口声明FunctionalInterface注解，那么编译器依旧会将该接口看作是函数式接口；
#### （2）function函数
①compose（Function function）先执行内部function后，结果传给外部function；
②andThen（Function function）先执行外部functino后，再执行内部function；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670302763349-648abc29-454a-412e-80cf-2ff9c35435fa.png#averageHue=%232f2c2c&clientId=u3a89b8f0-23a4-4&from=paste&height=176&id=ua3d156a1&name=image.png&originHeight=264&originWidth=1002&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30002&status=done&style=shadow&taskId=u5e00c4aa-7707-4b72-acb1-eae3b6ef7c1&title=&width=668)
#### （3）Predicate函数接口
①两个Predicate条件满足，test返回true
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670385919866-df51288b-ce7a-453f-9c95-1f6f91fb399d.png#averageHue=%232d2c2b&clientId=u38cc6872-ee2b-4&from=paste&height=126&id=ufa52d5a8&name=image.png&originHeight=189&originWidth=1005&originalType=binary&ratio=1&rotation=0&showTitle=false&size=23881&status=done&style=shadow&taskId=u9cbb9cb5-ccb6-4536-8148-a7cc8ae0dba&title=&width=670)
②两个条件其中一个满足，test返回true
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670385933940-e82253a6-5c27-4505-842e-5eca75c762e6.png#averageHue=%232d2c2b&clientId=u38cc6872-ee2b-4&from=paste&height=124&id=u7c0bb5f1&name=image.png&originHeight=182&originWidth=973&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22524&status=done&style=shadow&taskId=u0b91e752-ca59-4490-a91a-7a61af656a8&title=&width=664.6666870117188)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670385990398-e3de15f0-3f9d-4d2a-8d73-3138a4a83c8e.png#averageHue=%232c2c2b&clientId=u38cc6872-ee2b-4&from=paste&height=127&id=u869a0c1c&name=image.png&originHeight=151&originWidth=784&originalType=binary&ratio=1&rotation=0&showTitle=false&size=11826&status=done&style=shadow&taskId=u4020a85c-cc63-40af-89e1-706ce1dba04&title=&width=658.6666870117188)
#### （4）Supplier函数接口
get（）方法，不接受参数，返回一个结果
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670386810226-014db562-a8ca-464c-b77a-cfc971f41133.png#averageHue=%232f2e2d&clientId=u38cc6872-ee2b-4&from=paste&height=125&id=ub4a6b567&name=image.png&originHeight=187&originWidth=978&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38033&status=done&style=shadow&taskId=u01acdfe7-c251-4f4e-87f2-157d359068b&title=&width=652)
#### （5）Optional
通常用于一个方法中，处理一个值（空或非空）的返回结果
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670395830430-009d30a0-1688-416d-9320-24b1cbd6abb7.png#averageHue=%23332c2b&clientId=u38cc6872-ee2b-4&from=paste&height=127&id=u07c2bb09&name=image.png&originHeight=190&originWidth=1145&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32607&status=done&style=shadow&taskId=uce4d4eed-784d-4628-835b-3ee3a94cc56&title=&width=763.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670395967361-d9a5e7a2-644d-4452-8580-e7dcc59ac00a.png#averageHue=%23382e2c&clientId=u38cc6872-ee2b-4&from=paste&height=117&id=uc2ec1bfc&name=image.png&originHeight=176&originWidth=1104&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38156&status=done&style=shadow&taskId=u27d7f823-aa7d-433e-afb3-4750529607f&title=&width=736)

---

### 2、方法引用
（1）方法引用可以看作一个函数指针，不可以传参数；lamdba表达式只有一行代码，且被调用方法存在，才可以使用；
（2）类名：：静态方法名
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670398716774-72d6aef2-a4e3-459a-912f-5fa5dafffa4c.png#averageHue=%232e2d2d&clientId=u38cc6872-ee2b-4&from=paste&height=60&id=uc6076c55&name=image.png&originHeight=86&originWidth=959&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14368&status=done&style=shadow&taskId=ub0526042-f0ac-4054-98e1-f7ca72455ce&title=&width=664.3333740234375)
（3）引用名（对象名）：：实例方法名
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670399377370-25d64c62-115f-45b6-8fc7-ac17d2945fa2.png#averageHue=%232d2d2c&clientId=u38cc6872-ee2b-4&from=paste&height=90&id=u10560141&name=image.png&originHeight=135&originWidth=1032&originalType=binary&ratio=1&rotation=0&showTitle=false&size=17783&status=done&style=shadow&taskId=u0ba07287-8325-4fd5-8aed-f24a5a5ce9e&title=&width=688)
（4）类名：：实例方法名
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670400672333-6c4ea797-fa13-45ce-9a4b-fab32a579e53.png#averageHue=%23362b2a&clientId=u38cc6872-ee2b-4&from=paste&height=55&id=u4dadd3d2&name=image.png&originHeight=83&originWidth=1118&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18876&status=done&style=shadow&taskId=u2de69823-afea-4064-9b92-acb281da23e&title=&width=745.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670400286365-f02fc41f-8e2c-44d6-b6fc-3ef5e7e5f15e.png#averageHue=%232e2d2b&clientId=u38cc6872-ee2b-4&from=paste&height=83&id=u85271489&name=image.png&originHeight=107&originWidth=843&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13290&status=done&style=shadow&taskId=u5eae739e-88cb-474f-91e0-28955efb01f&title=&width=655)
（5）构造方法引用：类名：：new
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670401423891-d7fc1892-c9c7-4c09-a14d-b9d7afce4710.png#averageHue=%232c2c2b&clientId=u38cc6872-ee2b-4&from=paste&height=109&id=u2e9b4c96&name=image.png&originHeight=163&originWidth=1042&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20060&status=done&style=shadow&taskId=u45b53889-0526-4242-a5f0-a98a8005abd&title=&width=694.6666666666666)

---

### 3、Stream流
（1）流由三部分构成：源、零个或多个中间操作、终止操作；一个数据执行完一整条流操作，再进行下一个数据的执行，若前一个操作执行条件满足终止操作，则直接终止操作，不执行后面数据；
（2）map与mapToInt方法区别：mapToInt会避免数据类型自动装箱与拆箱的转换，减少性能消耗；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670475186679-ff1b065b-8b8e-4c16-a0fc-4fc7f8c06b33.png#averageHue=%232f2c2b&clientId=u2e5ec63d-8631-4&from=paste&height=213&id=u19ea0656&name=image.png&originHeight=292&originWidth=791&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22936&status=done&style=shadow&taskId=uce252b08-790b-436b-92cc-5000765d7ac&title=&width=578.3333740234375)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670475249446-08c5534d-104e-4647-8d97-af019e03e06c.png#averageHue=%23342b2a&clientId=u2e5ec63d-8631-4&from=paste&height=189&id=ube64b027&name=image.png&originHeight=284&originWidth=867&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30070&status=done&style=shadow&taskId=ufba7e46e-05c8-436d-a461-9d7fc8f1800&title=&width=578)
（3）重复操作相同的流会报错
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670476640726-6f3c5c08-f8e9-48e1-9503-54231ca5c307.png#averageHue=%232f2d2c&clientId=u2e5ec63d-8631-4&from=paste&height=97&id=u7fbdbf29&name=image.png&originHeight=146&originWidth=1024&originalType=binary&ratio=1&rotation=0&showTitle=false&size=27276&status=done&style=shadow&taskId=u356f1574-2b84-43b4-b5e1-b2955a7e2e7&title=&width=682.6666666666666)
（4）流未遇到终止条件，不会执行中间操作；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670477087734-c9a99806-4350-4473-b1ec-05e640603d11.png#averageHue=%232f2d2c&clientId=u2e5ec63d-8631-4&from=paste&height=150&id=u307cff24&name=image.png&originHeight=225&originWidth=1329&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39765&status=done&style=shadow&taskId=uf3549d9f-c855-474d-b61e-f926fbc0c41&title=&width=886)

---

### 4、Collector源码分析
（1）是一个接口，是一个可变的汇聚操作，将输入元素累积到可变的结果容器中，他会在所有元素处理完毕后，将累积的结果转换为一个最终表示（可选操作），支持串行与并行；
（2）Collectors提供关于Collector的常见汇聚实现，Collectors本身实际是一个工厂；
（3）为确保串行与并行结果等价性，Collector需要满足：同一性和结合性；
①同一性：a（分支部分结果）==combiner.apply(a,supplier.get())：
```java
//a例如list1，supplier.get()创建一个空容器
(List<String> list1,List<String> list2)->{
    list1.addAll(list2);
    return list1;
}
```
②结合性
```java
 A  a1 = supplier.get();
 accumulator.accept(a1, t1);
 accumulator.accept(a1, t2);
 R r1 = finisher.apply(a1);  // result without splitting

 A a2 = supplier.get();
 accumulator.accept(a2, t1);
 A a3 = supplier.get();
 accumulator.accept(a3, t2);
 R r2 = finisher.apply(combiner.apply(a2, a3));  // result with splitting
```
（4）Collector由四个函数组成，这些函数一起工作以将结果累积到可变结果容器中，并可选地对结果执行最终转：
①supplier()：构建一个新的容器；
②accumulator()：将所有新的元素累积到最终结果容器；
③combiner()：将两个结果容器合并为一个结果容器，一般是在并行的情况下使用；
④finisher()：将容器的结果转换为最终结果（可选操作）；
（5）枚举enum Characteristics
①IDENTITY_FINISH：转换类型必须要可以强制转换，否则会抛异常；
②CONCURRENT：多个线程同时操作一个结果容器，combiner方法不需要调用，在Accumulate方法中不能执行额外操作，只能执行累积逻辑；
不使用CONCURRENT：有几个线程，就操作几个结果容器，需要调用combiner方法；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670816776791-2ab95679-885f-4f57-ae90-5bf4a3d5e0e6.png#averageHue=%23352a2a&clientId=u6d8dc90b-6501-4&from=paste&height=373&id=uee24c5a3&name=image.png&originHeight=559&originWidth=1139&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81028&status=done&style=shadow&taskId=ued1df767-17c5-4aa7-b762-0557bb9da2a&title=&width=759.3333333333334)

---

### 5、Collectors源码分析
（1）Collectors静态工厂类，共有两种实现情况：
①通过CollectorImpl来实现；
②通过reducing方法实现，reducing方法又是通过CollectorImpl实现；
（2）groupingby源码分析：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670906239169-dc697698-0eb1-43ce-9005-15a3d8337b9d.png#averageHue=%23352c2b&clientId=u6d8dc90b-6501-4&from=paste&height=155&id=ud73144d8&name=image.png&originHeight=232&originWidth=982&originalType=binary&ratio=1&rotation=0&showTitle=false&size=47386&status=done&style=shadow&taskId=uf8ae4275-6b21-4367-b23e-c80eef07ee7&title=&width=654.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670906671949-df578f53-086a-4103-a64e-4089ca69f442.png#averageHue=%23392c2a&clientId=u6d8dc90b-6501-4&from=paste&height=158&id=ud652d4f9&name=image.png&originHeight=237&originWidth=1162&originalType=binary&ratio=1&rotation=0&showTitle=false&size=55068&status=done&style=shadow&taskId=ue97b5077-c642-40ef-9839-58b2ecf72b7&title=&width=774.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670907067173-39f80afa-94bc-40fe-aa39-103e94c0f9cd.png#averageHue=%23342c2a&clientId=u6d8dc90b-6501-4&from=paste&height=163&id=u398fe355&name=image.png&originHeight=245&originWidth=1195&originalType=binary&ratio=1&rotation=0&showTitle=false&size=66206&status=done&style=shadow&taskId=u8cb83eb2-565b-4986-9128-a53844c6b78&title=&width=796.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670907983121-3b080459-5208-4824-b29d-37079123ae32.png#averageHue=%233b2c2a&clientId=u6d8dc90b-6501-4&from=paste&height=165&id=u9db77b83&name=image.png&originHeight=247&originWidth=1073&originalType=binary&ratio=1&rotation=0&showTitle=false&size=83131&status=done&style=shadow&taskId=u81de3c43-70eb-413f-9187-c17e067d491&title=&width=715.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670909036401-8a6207dd-3eb6-4d82-b2d2-17f9bf96f31d.png#averageHue=%23362c2b&clientId=u6d8dc90b-6501-4&from=paste&height=155&id=u83fdf478&name=image.png&originHeight=233&originWidth=1246&originalType=binary&ratio=1&rotation=0&showTitle=false&size=57500&status=done&style=shadow&taskId=ua5fb2d17-ac66-4473-9fc5-5dd2aa544c0&title=&width=830.6666666666666)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1670909715250-ede96669-a36a-46bf-a5a0-5e37115ba1a4.png#averageHue=%232f2b2a&clientId=u6d8dc90b-6501-4&from=paste&height=251&id=u07f13c2a&name=image.png&originHeight=376&originWidth=1227&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62426&status=done&style=shadow&taskId=uf581af14-92cf-4293-bcda-27262be3dfd&title=&width=818)

---

### 6、stream流源码分析
（1）Spliterator<T>分析：
①遍历元素以及分割元素；
②分割迭代器绑定源后，若再对源进行修改，会抛异常；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1671011356665-acbcc6be-88a6-48d5-b7d1-42a850d7757a.png#averageHue=%23302b2b&clientId=u6d8dc90b-6501-4&from=paste&height=159&id=uf19659fc&name=image.png&originHeight=238&originWidth=1065&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38118&status=done&style=shadow&taskId=ud53da158-c862-4fe5-a99c-e0f977cd179&title=&width=710)
（2）ReferencePipeline类
①表示流的源阶段和中间阶段；
②ReferencePipeline.Head表示流的源阶段；
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1671093413582-42d1068c-afad-4ca2-add9-001c60a3a80c.png#averageHue=%233b2b29&clientId=ud74e7761-9a17-4&from=paste&height=97&id=u5371f59e&name=image.png&originHeight=146&originWidth=908&originalType=binary&ratio=1&rotation=0&showTitle=false&size=31848&status=done&style=shadow&taskId=u99248b37-7528-4a95-8913-551a5278f41&title=&width=605.3333333333334)
（3）流中间操作（map）
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1671176455445-9faa65da-e1a8-4b77-90af-b61016ca8cec.png#averageHue=%232d2c2b&clientId=ud74e7761-9a17-4&from=paste&height=371&id=u8f574dec&name=image.png&originHeight=556&originWidth=1241&originalType=binary&ratio=1&rotation=0&showTitle=false&size=78648&status=done&style=shadow&taskId=u06b89886-bd38-4b54-b7a9-2d3aafb1c68&title=&width=827.3333333333334)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1671174232099-105748ef-c641-48c1-a081-79858b44e4d9.png#averageHue=%232e2b2b&clientId=ud74e7761-9a17-4&from=paste&height=441&id=ue4ce9515&name=image.png&originHeight=661&originWidth=1194&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81198&status=done&style=shadow&taskId=u1e40b805-d0c7-47d6-b185-e72a707e343&title=&width=796)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/29496365/1671174377727-54130779-d34f-42d5-9086-566fa1dfc752.png#averageHue=%23302c2b&clientId=ud74e7761-9a17-4&from=paste&height=378&id=u52dafb35&name=image.png&originHeight=567&originWidth=1240&originalType=binary&ratio=1&rotation=0&showTitle=false&size=123062&status=done&style=shadow&taskId=u97047d75-5f34-47ea-a340-33a325f94a4&title=&width=826.6666666666666)
（4）
![](https://cdn.nlark.com/yuque/0/2022/jpeg/29496365/1671190283168-53672014-69ae-4bd7-b84a-7e9bd04c6016.jpeg)

---

### 
