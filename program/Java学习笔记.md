# Java学习笔记

## 工作中存在的知识点学习

### list,set,map

#### list

> 元素有序放入，可重复

List主要有ArrayList、LinkedList与Vector

- **ArrayList**:是一个可改变大小的数组.当更多的元素加入到ArrayList中时,其大小将会动态地增长.内部的元素可以直接通过get与set方法进行访问.
- **LinkedList**：在添加和删除元素时具有比ArrayList更好的性能.但在get与set方面弱于ArrayList
- **Vector**：Vector 和ArrayList类似,但属于强同步类。如果你的程序本身是线程安全的(thread-safe,没有在多个线程之间共享同一个集合/对象),那么使用ArrayList是更好的选择

#### set

> 元素无放入顺序，元素不可重复