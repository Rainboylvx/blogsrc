---
title : STL 第一讲:vector 向量容器

---






### 概讲

STL 可以说是 **数据结构** + **算法** 的结合,其中STL为了实现**数据结构**,采用了一种**容器**的思想:
把数据(包括基本类型和类对象)放到容器里,而**算法** 通过**迭代器**操作容器来实现各种预期结果.

容器种类:

 - 顺序容器
  - vector 向量
  - deque 双端队列
  - list 链表
 - 关联容器
  - set 集合
  - multiset 多重集合
  - map 映射
  - multimap 多重映射
  
 - 容器适配器
  - stack 栈
  - queue 队列
  - priority 优先队列/堆
  
 - 迭代器种类
  - input（输入）迭代器
  - output（输出）迭代器
  - forward（向前）迭代器 
  - bidirectional(双向)迭代器
  - random access(随机存取)迭代器
  
  > [注意]:
  每个容器都有它的特点,也就是有它适用的情况,这个我会在讲解每个容器的开头讲解
  迭代器种类有五种,我会在讲解一定的STL容器后讲解.
  我会在最后讲解算法有关,并总结NOIP常用的算法.
 
 
### vector 向量容器

#### 基本概念和特征

 - vector 是一种`动态数组模型`,代替数组
 - 在vector 容器后面添加/删除数据都非常快
 - 采用数据结构:连续线性空间
 - 采用随机存取迭代器,支持下标读取
 
 > [注意]:
 vector可以理解为动态数组,所谓动态增加大小，并不是在原空间之后接续新空间（因为无法保证之后尚有可供配置的空间），而是每次**再分配**原大小两倍的内存空间.
 同时,也可以理解到:凡是能引起vector内存重新分配的行为都有可能导致迭代器失效.
 
 
#### vector 操作大全

| 初始化      |    作用| 
| :-------- | :--------|                                                                         |
|vector<T> c;            | 定义一个空的vector容器                                                |
|vector<T> c1(c);        | 用容器c 初始化 c1                                                     |
|vector<T> c2(n);        | 定义一个容器C2,有n个值,默认的值和T的类型有关系,如果是类,由构造函数决定|
|vector<T> c3(n,e);      | 定义容器c3,有n个值,初值是e                                            |
|vector<T> c4(begin,end);| 由迭代器[begin,end) 指向的范围内的值来初始化, 可以是数组的指针        |
|c.~vector<T>()          | 销毁容器c,释放空间                                                    |
| **基本操作**                 |                                               |
| c.size();            | 容器c的大小                                        |
| c.empty();           | 容器c是否为空                                      |
| c.push_back(i)       | 在容器后部加入一个元素                             |
| c.pop_back()         | 删除最后一个元素,不会返回元素的引用                |
| c[]                  | 用下标来操作元素,不进行越界检查                    |
| c.at(id)             | 返回下标id的引用,进行越界检查                      |
| c.front()            | 返回第一个元素的引用                               |
| c.back()             | 返回最后一个元素的引用                             |
| c.max_size()         | 返回容器的最大数据容量                             |
| **添加数据**             |                                                    |
| c.inser(pos,e)       | 在pos位置插入e的拷贝,返回新数据的位置              |
| c.inser(pos,n,e)     | 在pos位置插入n个e,无返回值                         |
| c.inser(pos,end,end) | 在pos位置插入[begin,end)的里的值,无返回值          |
| **删除操作**             |                                                    |
| c.erase(pos)         | 删除pos位置的数据,返回下一个数据的位置             |
| c.erase(begin,end)   | 删除[begin,end)之决的数据,返回下一个数据的位置     |  
| **迭代器**               |                                                    |
| c.begin()            | 指向第一个元素的迭代器                             |
| c.end()              | 指向最后一个元素后面一个位置的迭代器               |
| c.rebegin()          | 指向反向的第一个数据                               |
| c.rend()             | 指向反向的最后一个数据的后面                       |
| **其它操作**             |                                                    |
| c.swap(c2)           | c ,c2交换                                          |
| swap(c,c2)           | c,c2交换                                           |
| c.reserve()          | 保留适当的容量                                     |
| >,>=,<,<=,==         | 逻辑运算                                           |
| c =  c2              | 赋值运算                                           |
| **特殊的操作**           |                                                    |
| capacity             | 获取容器需要分配更多存储空间之前能夠存储的元素数量 |
| reserve              | 应该预留多少个元素的存储空间                       |

 > [记住]: 可以使用数组来完成初始化,应该所有的STL容器都可以使用数组来完成初始化(存疑)
 
 
 
### vector代码联系


#### 代码1

```
/* 说明：
 *  vector本质：
 *          快速后端操作(存入/读取)的连读空间的数据结构
 * */

#include <cstdio>
#include <iostream>
#include <vector>

using namespace std;

int main(int argc,char **argv)
{
    vector<int> v1;
    vector<int> v2(10);
    vector<int> v3(10,1);

    //输出大小
    cout<<v1.size()<<endl;
    cout<<v2.size()<<endl;
    cout<<v3.size()<<endl;
    return 0;
}
```



#### 代码2

```
#include  <iostream>
#include  <
```

### cojs 明明随机数




### 总结 

单单看vector,不如果在数组在NOIP中更直观,更好用,但是vector可以做为面STL学习的基石,
真正好用的是list,stack,queue,priority_queue,map和set,
最重要是算法
 