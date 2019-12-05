# 集合

### Java集合框架中有哪些类？都有什么特点？

![Java &#x96C6;&#x5408;&#x6846;&#x67B6;&#x7C7B;&#x56FE;](../.gitbook/assets/2243690-9cd9c896e0d512ed.gif)

### 集合、数组、泛型的关系，并比较

数组是由相同类型的若干项数据组成的一个数据集合,数组是引用类型。数组创建后在内存里面占用连续的内存地址，数组一旦被创建，就不能更改数组的长度。

集合是包含多个对象的简单对象，所包含的对象称为元素。Collection 接口是一组允许重复的对象。

Set 接口继承 Collection，无序但不允许重复。

List 接口继承 Collection，有序但允许重复，并引入位置下标。

Map 接口既不继承 Set 也不继承 Collection，是键值对。

###  ArrayList  和 LinkList 的区别？

ArrayList 内部使用数组的形式实现了存储，实现了RandomAccess接口，利用数组的下面进行元素的访问，因此对元素的随机访问速度非常快。

因为是数组，所以ArrayList在初始化的时候，有初始大小10，插入新元素的时候，会判断是否需要扩容，扩容的步长是0.5倍原容量，扩容方式是利用数组的复制，因此有一定的开销；

另外，ArrayList在进行元素插入的时候，需要移动插入位置之后的所有元素，位置越靠前，需要位移的元素越多，开销越大，相反，插入位置越靠后的话，开销就越小了，如果在最后面进行插入，那就不需要进行位移。  

LinkedList 内部使用双向链表的结构实现存储，LinkedList有一个内部类作为存放元素的单元，里面有三个属性，用来存放元素本身以及前后2个单元的引用，另外LinkedList内部还有一个header属性，用来标识起始位置，LinkedList的第一个单元和最后一个单元都会指向header，因此形成了一个双向的链表结构。

LinkedList是采用双向链表实现的。所以它也具有链表的特点，每一个元素（结点）的地址不连续，通过引用找到当前结点的上一个结点和下一个结点，即插入和删除效率较高，只需要常数时间，而get和set则较为低效。  
  
当插入和删除操作较频繁时，使用 LinkedList 性能更好；当随机访问比较频繁时，使用 ArrayList 更好。

另外，LinkedList 还实现了 `Deque`接口，可以用来作为队列使用。

### ArrayList和Vector的区别？

### HashSet和TreeSet的区别？

### HashMap和HashTable的区别？
