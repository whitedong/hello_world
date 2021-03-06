# 深浅拷贝

## Javascript数据类型

- 基本数据结构

  | 名称 | 定义 |
  | ---- | -- |
  | 栈  | 只允许在一段进行插入或删除操作的线性表，是一种先入后出的数据结构 |
  | 堆 | 基于散列算法的数据结构 |
  | 队列 | 先进先出(FIFO)的数据结构 |

- 数据类型

  根据数据存储位置产生两种类型

  - 基本数据类型

    Number, Boolean, String, Null, Undefined, Symbol

    基本数据类型存储在``栈内存``中。

  - 引用数据类型
    
    Array, Object

    引用数据类型保存在``堆内存``中，然后在``栈内存``中保存一个实际对象的引用。

    ```javascript
      // 变量arr表示在栈内存中存储一个地址来表示对堆内存的引用
      var arr = [];
      
      // 变量copy表示系统为新变量重新在栈内存中分配个地址，实际上都是同一个堆内存的引用。
      // 操作变量copy, 也会引起变量arr改变。
      var copy = arr;
    ```

  - 区别

    1.栈比堆大，栈速度比堆块   
    2.基本数据类型相对稳定，占用内存较少    
    3.引用数据类型大小是动态的    
    4.堆内存是无序存储，可以通过引用直接获取
    
## 浅拷贝

浅拷贝只复制引用，未复制真正的值。

```javascript
  // 使用赋值运算符进行浅拷贝
  var obj = {};
  console.log(obj); // {}
  var cloneObj = obj;
  cloneObj.name = "test";
  console.log(obj); // { name:"test" }
  console.log(cloneObj); // { name:"test" }
```

## 深拷贝

深拷贝不止复制引用，同时也复制对应值。

实现方法：
- ``JSON``对象的``parse``和``stringify``
- 利用递归实现每一层重新创建并赋值

