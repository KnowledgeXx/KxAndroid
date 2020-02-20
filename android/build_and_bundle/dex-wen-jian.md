# dex 文件



{% embed url="https://tech.youzan.com/qian-tan-android-dexwen-jian/" %}

### 与 class 文件相比优势？

去除了类与类之间的重复信息，比如每个类的class文件中都有一个常量池，而dex会去除冗余，区域复用并整合，整个工程中的同类型数据存储在一个数据区域，这样dex文件较小；

一个文件记录了所有类的信息，而不是像class文件一个文件记录一个类的信息，减少了类加载时的io次数。

### 结构

主要分为三块区域：

* 文件头：记录了dex文件信息及所有字段大致的分布
* 索引：分别记录了字符串、类型、方法原型、域、方法的索引，**这部分指定了dex文件中所有不同类型数据存储的位置**，数据最终存储于“数据区”
* 数据区：此块可分成普通数据区和链接数据区，后者听起来较为陌生，总所周知Android中常有一些动态链接库so的引用，而链接数据区就是对这个的指向。

混淆和压缩可以减少dex中记录的字符串长度，从而减少dex文件大小

[Android Dex VS Class：实例图解剖析两种格式文件结构、优劣](https://blog.csdn.net/ITermeng/article/details/79218060)

[浅谈 Android Dex 文件](https://tech.youzan.com/qian-tan-android-dexwen-jian/)
