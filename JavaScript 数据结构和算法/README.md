# JavaScript 数据结构和算法

最近在补充自己以前落下的知识，算法的知识还是得自己敲一遍算法才行，所以决定写个笔记记录一下自己得学习进度，以便于之后方便复习

## 线性表

**线性表**：就是数据排成像一条线一样的结构。每个线性表上的数据最多只有前和后两个方向。数组、链表、队列、栈 等就是线性表结构。

**非线性表**：数据之间并不是简单的前后关系。二叉树、堆、图 就是非线性表。

### 数组

- **数组是用一组连续的内存空间来存储的**。

  数组支持 **随机访问**，根据下标随机访问的时间复杂度为 O(1)。

- **低效的插入和删除**。

  数组为了保持内存数据的连续性，会导致插入、删除这两个操作比较低效，因为底层通常是要进行大量的数据搬移来保持数据的连续性。
  插入与删除的时间复杂度如下：
  插入：从最好 O(1) ，最坏 O(n) ，平均 O(n)
  删除：从最好 O(1) ，最坏 O(n) ，平均 O(n)

- **数组中常用的操作方法**

  - `push()`：在末尾添加一个或多个元素，==修改原数组==，返回值：数组新的长度。
  - `pop()`：删除数组最后一个元素，无参数，==修改原数组==，返回值：删除元素的值。
  - `unshift()`：向数组的开头添加一个或者多个元素，==修改原数组==，返回值：数组新的长度。
  - `shift()`：删除数组的第一个元素，数组长度减1，无参数，==修改原数组==，返回值：删除元素的值。
  - `reverse()`：颠倒数组中元素的顺序，无参数，==修改原数组==，返回值：新的数组。
  - `sort()`：对数组的元素进行排序，==修改原数组==，返回值：新的数组。
  - `splice()`：数组删除`splice(第几个开始，要删除的个数)`，==修改原数组==，返回值：返回被删除项目的新数组。
  - `toString()`：把数组转换成字符串，逗号分隔每一项，返回值：一个字符串。
  - `join()`：参数为连接符，用于把数组中的所有元素用连接符连接成一个字符串，返回值：一个字符串。
  - `concat()`：连接两个或多个数组，不影响原数组，返回值：一个新的数组。
  - `slice()`：数组截取`slice(begin,end)`，返回值：返回被截取项目的新数组。
  - `indexOf()`：从前往后查找数组元素的索引号，不修改原数组，返回值：数组元素的索引号。
  - `lastIndexOf()`：从后往前查找数组元素的索引号，不修改原数组，返回值：数组元素的索引号。
  - `find()`：用于找出第一个符合条件的数组成员，返回值：数组元素。
  - `findIndex()`：用于找出第一个符合条件的数组成员的位置，返回值：索引号。
  - `includes()`：判断某个数组是否包含给定的值。

### 栈

1. **定义**

   - **先进后出**
   - 新添加的或待删除的元素都保存在栈的末尾，称作`栈顶`，另一端就叫`栈底`。
   - 在栈里，新元素都靠近栈顶，旧元素都接近栈底。
   - 从栈的操作特性来看，是一种 `操作受限`的线性表，只允许在一端插入和删除数据。
   - 不包含任何元素的栈称为`空栈`。

   栈也被用在编程语言的编译器和内存中保存变量、方法调用等，比如函数的调用栈。

2. **实现**

   - `push(element)`：添加一个（或几个）新元素到栈顶。
   - `pop()`：移除栈顶的元素，同时返回被移除的元素。
   - `peek()`：返回栈顶的元素，不对栈做任何修改。
   - `isEmpty()`：如果栈里没有任何元素就返回 true，否则返回 false。
   - `clear()`：移除栈里的所有元素。
   - `size()`：返回栈里的元素个数。

   ```js
   // stack类
   function Stack() {
       this.stack = []
   
       // 添加新元素到栈顶
       this.push = function(element) {
           this.stack.push(element)
       }
   
       // 移除栈顶元素，并返回被移除的元素
       this.pop = function() {
           return this.stack.pop()
       }
   
       // 查看栈顶元素
       this.peek = function() {
           return this.stack[this.stack.length-1]
       }
   
       // 判断是否为空栈
       this.isEmpty = function() {
           return this.stack.length === 0
       }
   
       // 清空栈
       this.clear = function() {
           this.stack = []
       }
   
       // 返回栈的长度
       this.size = function() {
           return this.stack.length
       }
   
       // 打印栈中的元素
       this.print = function() {
           console.log(this.stack.toString())
       }
   
   }
   
   // 创建一个stack实例
   let stack = new Stack()
   console.log(stack.isEmpty())
   stack.push(1)
   stack.push(2)
   console.log(stack.isEmpty())
   console.log(stack.size())
   console.log(stack.pop())
   stack.push([5,8,4,3])
   stack.print()
   ```

### 队列

#### 普通队列

1. **定义**
   - 先进先出
   - 队列在尾部添加新元素，并从顶部移除元素。
   - 最新添加的元素必须排在队列的末尾。
   - 队列只有 入队 `push()` 和出队 `shift()`。
2. **实现**
   - `enqueue(element)`：向队列尾部添加新项。
   - `dequeue()`：移除队列的第一项，并返回被移除的元素。
   - `front()`：返回队列中第一个元素，队列不做任何变动。
   - `isEmpty()`：如果队列中不包含任何元素，返回 true，否则返回 false。
   - `size()`：返回队列包含的元素个数，与数组的 length 属性类似。
   - `print()`：打印队列中的元素。
   - `clear()`：清空整个队列。

```js
function Queue() {
    this.queue = []

    // 向队列尾部添加元素
    this.enqueue = function(element) {
        this.queue.push(element)
    }

    // 移除队列的第一个元素，并返回被移除的元素
    this.dequeue = function() {
        return this.queue.shift()
    }

    // 获取队列的第一个元素
    this.front = function() {
        return this.queue[0]
    }

    // 判断队列是否为空
    this.isEmpty = function() {
        return this.queue.length === 0
    }

    // 清空队列
    this.clear = function() {
        this.queue = []
    }

    // 打印队列中的元素
    this.print = function() {
        console.log(this.queue.toString())
    }

    // 返回队列的长度
    this.size = function() {
        return this.queue.length
    }
}

// 创建一个实例
let queue = new Queue()
console.log(queue.isEmpty())
queue.enqueue(1)
queue.enqueue(2)
queue.enqueue(5)
console.log(queue.size())
console.log(queue.dequeue())
console.log(queue.front())
console.log(queue.print())
queue.clear()
console.log(queue.queue)


```

#### 优先队列

1. **定义**

   优先队列中元素的添加和移除是依赖`优先级`的。

2. **应用**

   - 排队买票，军人、残疾人优先级更高，可以优先买票。

3. **优先队列分为两类**

   - 最小优先队列：把优先级的值最小的元素被放置到队列的最前面。
   - 最大优先队列：把优先级值最大的元素放置在队列的最前面。

4. **实现**

   - 设置优先级，根据优先级正确添加元素，然后和普通队列一样正常移除。
   - 设置优先级，和普通队列一样正常按顺序添加，然后根据优先级移除。

5. **实现最小优先队列**

   ```js
   function MinPriorityQueue() {
       this.queue = []
   
       // 按最小优先级向队列中添加元素
       this.enqueue = function(element, priority) {
           let queueElemet = {
               element: element,
               priority: priority
           }
   
           if(this.queue.length == 0) {
               this.queue.push(queueElemet)
           }
           else {
               let flag = false
               for(let i=0; i<this.queue.length; i++) {
                   if(this.queue[i].priority > priority) {
                       this.queue.splice(i, 0, queueElemet)
                       flag = true
                       break
                   }
               }
               if(!flag) this.queue.push(queueElemet)
           }
       }
   
       // 移除队列的第一个元素，并返回被移除的元素
       this.dequeue = function() {
           return this.queue.shift()
       }
   
       // 获取队列的第一个元素
       this.front = function() {
           return this.queue[0]
       }
   
       // 判断队列是否为空
       this.isEmpty = function() {
           return this.queue.length === 0
       }
   
       // 清空队列
       this.clear = function() {
           this.queue = []
       }
   
       // 返回队列的长度
       this.size = function() {
           return this.queue.length
       }
   
       // 打印元素
       this.print = function() {
           let newArr = []
           for(let i=0; i<this.size(); i++) {
               newArr.push(`${this.queue[i].element}->${this.queue[i].priority}`)
           }
           console.log(newArr.toString())
       }
   }
   
   // 创建最小优先队列minPriorityQueue实例
   var minPriorityQueue = new MinPriorityQueue();
   
   console.log(minPriorityQueue.isEmpty());     // true
   minPriorityQueue.enqueue("John", 1);         // undefined
   minPriorityQueue.enqueue("Jack", 3);         // undefined
   minPriorityQueue.enqueue("Camila", 2);       // undefined
   minPriorityQueue.enqueue("Tom", 3);          // undefined
   minPriorityQueue.print();                    // "John->1,Camila->2,Jack->3,Tom->3"
   console.log(minPriorityQueue.size());        // 4
   console.log(minPriorityQueue.isEmpty());     // false
   console.log(minPriorityQueue.dequeue());                  // {element: "John", priority: 1}                // {element: "Camila", priority: 2}
   minPriorityQueue.print();                    // "Jack->3,Tom->3"
   minPriorityQueue.clear();                    // undefined
   console.log(minPriorityQueue.size());        // 0
   ```

6. **实现最大优先队列**

   ```js
   function MaxPriorityQueue() {
       this.queue = []
   
       // 按最大优先级向队列中添加元素
       this.enqueue = function(element, priority) {
           let queueElemet = {
               element: element,
               priority: priority
           }
   
           if(this.queue.length == 0) {
               this.queue.push(queueElemet)
           }
           else {
               let flag = false
               for(let i=0; i<this.queue.length; i++) {
                   if(this.queue[i].priority < priority) {
                       this.queue.splice(i, 0, queueElemet)
                       flag = true
                       break
                   }
               }
               if(!flag) this.queue.push(queueElemet)
           }
       }
   
       // 移除队列的第一个元素，并返回被移除的元素
       this.dequeue = function() {
           return this.queue.shift()
       }
   
       // 获取队列的第一个元素
       this.front = function() {
           return this.queue[0]
       }
   
       // 判断队列是否为空
       this.isEmpty = function() {
           return this.queue.length === 0
       }
   
       // 清空队列
       this.clear = function() {
           this.queue = []
       }
   
       // 返回队列的长度
       this.size = function() {
           return this.queue.length
       }
   
       // 打印元素  maxPriorityQueue
       this.print = function() {
           let newArr = []
           for(let i=0; i<this.size(); i++) {
               newArr.push(`${this.queue[i].element}->${this.queue[i].priority}`)
           }
           console.log(newArr.toString())
       }
   }
   
   // 创建最大优先队列  maxPriorityQueue实例
   var maxPriorityQueue = new MaxPriorityQueue();
   
   console.log(  maxPriorityQueue.isEmpty());     // true
   maxPriorityQueue.enqueue("John", 1);         // undefined
   maxPriorityQueue.enqueue("Jack", 3);         // undefined
   maxPriorityQueue.enqueue("Camila", 2);       // undefined
   maxPriorityQueue.enqueue("Tom", 3);          // undefined
   maxPriorityQueue.print();                    // "John->1,Camila->2,Jack->3,Tom->3"
   console.log(  maxPriorityQueue.size());        // 4
   console.log(  maxPriorityQueue.isEmpty());     // false
   console.log(  maxPriorityQueue.dequeue());     // {element: "John", priority: 1}                // {element: "Camila", priority: 2}
   maxPriorityQueue.print();                    // "Jack->3,Tom->3"
   maxPriorityQueue.clear();                    // undefined
   console.log(  maxPriorityQueue.size());        // 0
   ```

#### 循环队列

1. **关键**：确定好队空和队满的判定条件。

2. **例子**：

   击鼓传花游戏：在这个游戏中，孩子们围城一个圆圈，击鼓的时候把花尽快的传递给旁边的人。某一时刻击鼓停止，这时花在谁的手里，谁就退出圆圈直到游戏结束。重复这个过程，直到只剩一个孩子（胜者）

3. **实现**

   ```js
   import Queue from "./Queue.js";
   /*
    *@Description：击鼓传花
    *@param: 姓名 一轮的传递个数
    *@return: 胜利者
    *@ClassAuthor: lusy
    *@Date: 2022-08-28 00:14:16
   */
   function hotPotato(nameList, nums) {
       // 新建一个队列
       let queue = new Queue()
       // 将参与者全部放到队列中
       for(let i=0; i<nameList.length; i++) {
           queue.enqueue(nameList[i])
       }
   
       // 当前队列人数大于1时，重复执行击鼓传花游戏，直至只剩下最后一个胜利者
       while(queue.size() > 1) {
           // 设置的每轮游戏中要传递的个数
           for(let i=0; i<nums; i++) {
               queue.enqueue(queue.dequeue())
           }
           // 当传递个数满足（即击鼓停止时），当前花传递到谁手中，谁就退出游戏
           let gameOutPerson = queue.dequeue()
           console.log(`${gameOutPerson} 在击鼓传花中被淘汰！`);
       }
   
       // 返回最后一个胜利者
       return queue.front()
   }
   
   // 测试
   var nameList = ["John", "Jack", "Camila", "Ingrid", "Carl"];
   var winner = hotPotato(nameList, 10);
   console.log(`最后的胜利者是：${winner}`);
   ```


### 链表

1. **定义**
   - 链表存储有序的元素集合，但不同于数组，链表中的元素在内存中并不是连续放置的，它是通过 **指针** 将 **零散的内存块** 串连起来的。
   - 每个元素由一个存储元素本身的 **节点** 和一个指向下一个元素的 **引用**（也称指针或链接）组成。
2. **特点**
   - **链表是通过指针将零散的内存块串连起来的**。==（链表不支持随机访问）==
   - **高效的插入和删除**。

#### 单链表

**实现**

- append(element)：尾部添加元素。
- insert(position, element)：特定位置插入一个新的项。
- removeAt(position)：特定位置移除一项。
- remove(element)：移除一项。
- indexOf(element)：返回元素在链表中的索引。如果链表中没有该元素则返回 -1。
- isEmpty()：如果链表中不包含任何元素，返回 true，如果链表长度大于 0，返回 false。
- size()：返回链表包含的元素个数，与数组的 length 属性类似。
- getHead()：返回链表的第一个元素。
- toString()：由于链表使用了 Node 类，就需要重写继承自 JavaScript 对象默认的 toString() 方法，让其只输出元素的值。
- print()：打印链表的所有元素。

```js
function SinglyLinkedList() {
    function Node(element) {
        this.element = element // 当前节点的元素
        this.next = null // 下一个节点指针
    }

    this.length = 0 // 链表的长度
    this.head = null // 链表的头部节点

    // 向链表尾部添加一个新的节点
    this.append = function(element) {
        // 将要添加的新节点
        let node = new Node(element)
        // 当前所在节点
        let currentNode = this.head

        // 判断链表是否为空链表
        if(this.head == null) {
            // 是，则把当前节点当作头部节点
            this.head = node
        } else {
            // 否，则从this.head开始一直查找到最后一个node
            while(currentNode.next) {
                currentNode = currentNode.next
            }
            // 当前节点的next指针指向新节点
            currentNode.next = node
        }

        // 链表长度+1
        this.length++
        return true
    }

    // 向指定位置插入新节点
    this.insert = function(position, element) {
        // 判断是否越界
        if(position < 0 || position > this.length) {
            return false
        } else {
            let node = new Node(element)
            // 记录当前指针所在的节点
            let currentNode = this.head
            // 记录当前节点的位置
            let index = 0
            // 记录上一个节点
            let previousNode

            // 判断插入的位置是否是头部节点
            if(position == 0) {
                node.next = this.head.next
                this.head = node
            } else {
                while(index < position) {
                    previousNode = currentNode
                    currentNode = currentNode.next
                    index++
                }
                // 把上一个节点的指针指向新节点，新节点的指针指向当前节点
                node.next = currentNode
                previousNode.next = node
            }
            this.length++
            return true
        }
    }

    // 特定位置移除一项
    this.removeAt = function(position) {
        if(this.length == 0 || position < 0 || position > this.length) {
            // 越界
            return false
        } else {
            let currentNode = this.head
            let index = 0
            let previousNode

            if(position == 0) {
                this.head = currentNode.next
            } else {
                while(index < position) {
                    previousNode = currentNode
                    currentNode = currentNode.next
                    index++
                }
                // 将上一个节点的next指针 指向 当前节点的next指针，即删除当前节点
                previousNode.next = currentNode.next
            }
            this.length--
            return true
        }
    }

    // 移除一项元素
    this.remove = function(element) {
        let index = this.indexOf(element)
        this.removeAt(index)
    }

    // 返回元素在链表中的索引
    this.indexOf = function(element) {
        let currentNode = this.head
        let index = 0

        while(currentNode) {
            index++
            if(currentNode.element == element) {
                return index
            }
            currentNode = currentNode.next
        }
        return -1
    }

    // 判空
    this.isEmpty = function() {
        return this.length == 0
    }

    // 返回链表的长度
    this.size = function() {
        return this.length
    }

    // 返回链表的第一个元素
    this.gethead = function() {
        return this.head.element
    }

    // 转换字符串
    this.toString = function() {
        let string = ''
        let currentNode = this.head

        while(currentNode) {
            string+=','+currentNode.element
            currentNode = currentNode.next
        }
        return string.slice(1)
    }

    // 打印
    this.print = function() {
        console.log(this.toString())
    }

    // 获取整个链表
    this.list = function() {
        return this.head
    }
}


// 创建单向链表实例
var singlyLinked = new SinglyLinkedList();
console.log(singlyLinked.removeAt(0)); // false
console.log(singlyLinked.isEmpty()); // true
singlyLinked.append('Tom');
singlyLinked.append('Peter');
singlyLinked.append('Paul');
singlyLinked.print(); // "Tom,Peter,Paul"
singlyLinked.insert(0, 'Susan');
singlyLinked.print(); // "Susan,Tom,Peter,Paul"
singlyLinked.insert(1, 'Jack');
singlyLinked.print(); // "Susan,Jack,Tom,Peter,Paul"
console.log(singlyLinked.gethead()); // "Susan"
console.log(singlyLinked.isEmpty()); // false
console.log(singlyLinked.size()) // 5
console.log(singlyLinked.indexOf('Peter')); // 3
console.log(singlyLinked.indexOf('Cris')); // -1
singlyLinked.remove('Tom');
singlyLinked.removeAt(2);
singlyLinked.print(); // "Susan,Jack,Paul"
singlyLinked.list(); // 具体控制台
```

#### 双向链表

1. **单向链表与双向链表比较**

   - 双向链表需要额外的两个空间来存储后继结点和前驱结点的地址。操作更加灵活。
   - 双向链表提供了两种迭代列表的方法：**从头到尾，或者从尾到头**。
   - 在单向链表中，如果迭代链表时错过了要找的元素，就需要回到链表起点，重新开始迭代。
   - 在双向链表中，可以从任一节点，向前或向后迭代，这是双向链表的一个优点。
   - 所以，双向链表可以支持 O(1) 时间复杂度的情况下找到前驱结点，双向链表在某些情况下的插入、删除等操作比单链表简单、高效。

2. **实现**

   ```js
   // 双向链表
   function DoublyLinkedList() {
       function Node(element) {
           this.element = element
           this.previous = null // 指向前继节点的指针
           this.next = null // 指向后继节点的指针
       }
       // 记录链表的长度
       this.length = 0 
       // 链表的头部节点
       this.head = null
       // 链表的尾部节点
       this.tail = null
   
       // 向链表尾部添加一个新的节点
       this.append = function(element) {
           let node = new Node(element)
           let currentNode = this.tail
           // 判断是否是空链表
           if(!currentNode) {
               // 是，则头尾指针都指向node节点
               this.tail = node
               this.head = node
           } else {
               currentNode.next = node
               node.previous = currentNode
               this.tail = node
           }
           this.length++
           return true
       }
   
       // 向指定位置插入新节点
       this.insert = function(position, element) {
           if(position < 0 || position > this.length) {
               // 越界
               return false
           } else {
               let node = new Node(element)
               let currentNode = this.head
               let index = 0
               let previousNode
   
               if(position == 0) {
                   // 判断是否为空链表
                   if(!currentNode) {
                       this.head = node
                       this.tail = node
                   } else {
                       node.next = currentNode
                       currentNode.previous = node
                       this.head = node
                   }
               } else {
                   if(position == this.length) {
                       this.append(element)
                   } else {
                       while(index < position) {
                           previousNode = currentNode
                           currentNode = currentNode.next
                           index++
                       }
                       node.next = currentNode
                       currentNode.previous = node
                       previousNode.next = node
                       node.previous = previousNode
                   }
   
               }
               this.length++
               return true
           }
   
       }
   
       // 特定位置移除一项
       this.removeAt = function(position) {
           if(this.length == 0 || position < 0 || position >= this.length) {
               // 越界
               return false
           } else {
               let currentNode = this.head
               let index = 0
               let previousNode
   
               if(position == 0) {
                   if(this.length == 1) {
                       this.head = null
                       this.tail = null
                   } else {
                       this.head = currentNode.next
                       this.head.previous = null
                   }
               } else if(position == this.length-1) {
                   if(this.length == 1) {
                       this.head = null
                       this.tail = null
                   } else {
                       this.tail = this.tail.previous
                       this.tail.next = null
                   }
               } else {
                   while(index < position) {
                       previousNode = currentNode
                       currentNode = currentNode.next
                       index++
                   }
                   // 将上一个节点的next指针 指向 当前节点的next指针，将当前节点的next指针的previous 指向 previousNode指针 即删除当前节点
                   previousNode.next = currentNode.next
                   currentNode.next.previous = previousNode
               }
               this.length--
               return true
           }
       }
   
       // 移除一项元素
       this.remove = function(element) {
           let index = this.indexOf(element)
           this.removeAt(index)
       }
   
       // 返回元素在链表中的索引
       this.indexOf = function(element) {
           let currentNode = this.head
           let index = 0
   
           while(currentNode) {
               if(currentNode.element == element) {
                   return index
               }
               currentNode = currentNode.next
               index++
           }
           return -1
       }
   
       // 判空
       this.isEmpty = function() {
           return this.length == 0
       }
   
       // 返回链表的长度
       this.size = function() {
           return this.length
       }
   
       // 返回链表的第一个元素
       this.getHead = function() {
           return this.head.element
       }
   
       // 转换字符串
       this.toString = function() {
           let string = ''
           let currentNode = this.head
   
           while(currentNode) {
               string+=','+currentNode.element
               currentNode = currentNode.next
           }
           return string.slice(1)
       }
   
       // 打印
       this.print = function() {
           console.log(this.toString())
       }
   
       // 获取整个链表
       this.list = function() {
           return this.head
       }
   }
   
   
   // 创建双向链表
   var doublyLinked = new DoublyLinkedList();
   console.log(doublyLinked.isEmpty()); // true
   doublyLinked.append('Tom');
   doublyLinked.append('Peter');
   doublyLinked.append('Paul');
   doublyLinked.print(); // "Tom,Peter,Paul"
   doublyLinked.insert(0, 'Susan');
   doublyLinked.print(); // "Susan,Tom,Peter,Paul"
   doublyLinked.insert(1, 'Jack');
   doublyLinked.print(); // "Susan,Jack,Tom,Peter,Paul"
   console.log(doublyLinked.getHead()); // "Susan"
   console.log(doublyLinked.isEmpty()); // false
   console.log(doublyLinked.indexOf('Peter')); // 3
   console.log(doublyLinked.indexOf('Cris')); // -1
   doublyLinked.remove('Tom');
   doublyLinked.removeAt(2);
   doublyLinked.print(); // "Susan,Jack,Paul"
   console.log(doublyLinked.list()); // 请看控制台输出
   ```

#### 循环链表

1. **定义**

   在单链表的基础上，将尾节点的指针指向头结点，就构成了一个循环链表。环形链表从任意一个节点开始，都可以遍历整个链表。

2. **实现**

   ```js
   // 双向循环
   function CircularLinkedList() {
       function Node(element) {
           this.element = element // 当前节点的元素
           this.next = null // 下一个节点指针
       }
   
       this.length = 0 // 链表的长度
       this.head = null // 链表的头部节点
   
       // 向链表尾部添加一个新的节点
       this.append = function(element) {
           // 将要添加的新节点
           let node = new Node(element)
           // 当前所在节点
           let currentNode
   
           // 判断链表是否为空链表
           if(!this.head) {
               // 是，则把当前节点当作头部节点
               this.head = node
               node.next = this.head
           } else {
               currentNode = this.head
               // 否，则从this.head开始一直查找到最后一个node
               while(currentNode.next !== this.head) {
                   currentNode = currentNode.next
               }
               // 当前节点的next指针指向新节点
               currentNode.next = node
               // 组后一个节点指向头指针
               node.next = this.head
           }
   
           // 链表长度+1
           this.length++
           return true
       }
   
       // 向指定位置插入新节点
       this.insert = function(position, element) {
           // 判断是否越界
           if(position < 0 || position > this.length) {
               return false
           } else {
               let node = new Node(element)
               // 记录当前指针所在的节点
               let currentNode = this.head
               // 记录当前节点的位置
               let index = 0
               // 记录上一个节点
               let previousNode
   
               // 判断插入的位置是否是头部节点
               if(position == 0) {
                   node.next = this.head
                   this.head = node
               } else {
                   while(index < position) {
                       previousNode = currentNode
                       currentNode = currentNode.next
                       index++
                   }
                   // 把上一个节点的指针指向新节点，新节点的指针指向当前节点
                   node.next = currentNode
                   previousNode.next = node
               }
               this.length++
               return true
           }
       }
   
       // 特定位置移除一项
       this.removeAt = function(position) {
           if(this.length == 0 || position < 0 || position >= this.length) {
               // 越界
               return false
           } else {
               let currentNode = this.head
               let index = 0
               let previousNode
   
               if(position == 0) {
                   this.head = currentNode.next
               } else {
                   while(index < position) {
                       previousNode = currentNode
                       currentNode = currentNode.next
                       index++
                   }
                   // 将上一个节点的next指针 指向 当前节点的next指针，即删除当前节点
                   previousNode.next = currentNode.next
               }
               this.length--
               return true
           }
       }
   
       // 移除一项元素
       this.remove = function(element) {
           let index = this.indexOf(element)
           this.removeAt(index)
       }
   
       // 返回元素在链表中的索引
       this.indexOf = function(element) {
           let currentNode = this.head
           let index = 0
   
           while(currentNode && index < this.length) {
               if(currentNode.element == element) {
                   return index
               }
               currentNode = currentNode.next
               index++
           }
           return -1
       }
   
       // 判空
       this.isEmpty = function() {
           return this.length == 0
       }
   
       // 返回链表的长度
       this.size = function() {
           return this.length
       }
   
       // 返回链表的第一个元素
       this.getHead = function() {
           return this.head.element
       }
   
       // 转换字符串
       this.toString = function() {
           let string = ''
           let currentNode = this.head
           let index = 0
   
           while(index < this.length) {
               string+=','+currentNode.element
               currentNode = currentNode.next
               index++
           }
           return string.slice(1)
       }
   
       // 打印
       this.print = function() {
           console.log(this.toString())
       }
   
       // 获取整个链表
       this.list = function() {
           return this.head
       }
   }
   
   
   // 创建单向链表实例
   var circularLinked = new CircularLinkedList();
   console.log(circularLinked.removeAt(0)); // false
   console.log(circularLinked.isEmpty()); // true
   circularLinked.append('Tom');
   circularLinked.append('Peter');
   circularLinked.append('Paul');
   circularLinked.print(); // "Tom,Peter,Paul"
   circularLinked.insert(0, 'Susan');
   circularLinked.print(); // "Susan,Tom,Peter,Paul"
   circularLinked.insert(1, 'Jack');
   circularLinked.print(); // "Susan,Jack,Tom,Peter,Paul"
   console.log(circularLinked.getHead()); // "Susan"
   console.log(circularLinked.isEmpty()); // false
   console.log(circularLinked.indexOf('Peter')); // 3
   console.log(circularLinked.indexOf('Cris')); // -1
   circularLinked.remove('Tom');
   circularLinked.removeAt(2);
   circularLinked.print(); // "Susan,Jack,Paul"
   console.log(circularLinked.list()); // 具体控制台
   ```


## 排序

归并排序、快速排序、希尔排序、堆排序的平均时间复杂度都为`O(nlogn)`

### 冒泡排序

### 插入排序

### 选择排序

### 归并排序

1. **思想**

   排序一个数组，先把数组从中间分成前后两部分，然后对前后两部分分别排序，再将排好序的两部分合并在一起，这样整个数组就都有序了。

   分治思想：将一个大问题分解成许多的小问题来解决。

2. **讨论**

   - 归并算法不是原地排序算法
   - 归并算法是稳定算法
   - 归并算法时间复杂度是`O(nlogn)`

3. **实现**

   ```js
   /**
    * 归并排序：
    *  采用了分治的思想，将一个大问题分解成许多小的子问题来解决。
    *  将数组拆分为左右两个子数组，然后再分别将两个子数组继续进行拆分，最后将排好序的子数组逐一进行合并。
    * 
    */
   
   function mergeSort(arr) {
       let len = arr.length
       if(len < 2) return arr
   
       // 取数组的中间值
       let middle = Math.floor(len/2)
       // 将数组拆分为左右两个子数组
       let left = arr.slice(0, middle)
       let right = arr.slice(middle)
       // 返回排序并合并后的数组
       return merge(mergeSort(left), mergeSort(right))
   }
   
   // 排序算法
   function merge(left, right) {
       let newArr = []
       while(left.length && right.length) {
           if(left[0] <= right[0]) {
               newArr.push(left.shift())
           } else {
               newArr.push(right.shift())
           }
       }
       while(left.length) newArr.push(left.shift())
       while(right.length) newArr.push(right.shift())
   
       return newArr
   }
   
   let arr = [1,5,2,8,3,15,4,2,9,6]
   console.log(mergeSort(arr))
   ```

### 快速排序

1. **思想**

   - 先找一个基准点（一般指数组的中部），然后数组被该基准点分为两部分，依次与基准点数据比较，如果比它小，放左边；比他大，放右边。
   - 左右分别用一个空数组去存储比较后的数据。
   - 最后递归执行上述操作，直到数组长度 <= 1;

2. **优点**

   快速，常用

3. **缺点**

   需要另外两个数组，浪费了内存空间。

4. **实现**

   ```js
   function quickSort(arr) {
       let len = arr.length
       if(len < 2) return arr
   
       // 查找基准数（最中间的数。以此为分界线，小于该数的放左边，大于该数的放右边）
       let middle = Math.floor(len/2)
       let middleData = arr.splice(middle, 1)
   
       let left = []
       let right = []
       for(let i=0; i<arr.length; i++) {
           if(arr[i] <= middleData) {
               left.push(arr[i])
           } else {
               right.push(arr[i])
           }
       }
       // 执行递归操作
       return quickSort(left).concat(middleData, quickSort(right))
   }
   
   let arr = [1,5,2,8,3,15,4,2,9,6]
   console.log(quickSort(arr))
   ```

5. **归并排序和快速排序的区别**

   - 归并排序的处理过程是`自下而上`的，先处理子问题，然后再合并。
   - 快速排序的处理过程是`自上而下`的，先分区，再处理子问题。
   - 归并排序是非原地排序的算法。因为合并数组时仍然需要再次排序。
   - 快速排序是原地排序算法。

### 希尔排序

1. **思想**

   - 先将整个待排序的记录序列分割成为若干子序列。
   - 分别进行直接插入排序。
   - 待整个序列中的记录基本有序时，再对全体记录进行依次直接插入排序。

2. **讨论**

   - 希尔排序是原地排序。
   - 希尔排序不稳定。

3. **实现**

   ```js
   function shellSort(arr) {
       let len = arr.length
    if(len < 2) return arr
   
       // 围绕步长进行循环，第一步步长为数组长度的1/2，最后步长为1
       for(let shellWidth=Math.floor(len/2); shellWidth>=1; shellWidth=Math.floor(shellWidth/2)) {
           // 从步长长度的那组数组开始进行插入排序
           for(let i=shellWidth; i<len; i++) {
               // 同组内元素间进行插入排序
               let j = i-shellWidth // 同组内的元素，从后往前逐一进行比较
               while(j>=0 && arr[j]>arr[i]) {
                   swap(arr, i, j)
                   i = j
                   j = j - shellWidth
               }
   
           }
       }
       
       return arr
   }
   
   // 不增加变量，交换数据
   function swap(arr, i, j) {
       arr[i] = arr[i] + arr[j]
       arr[j] = arr[i] - arr[j]
       arr[i] = arr[i] - arr[j]
       return arr
   }
   
   
   // 测试
   const array = [35, 33, 42, 10, 14, 19, 27, 44];
   console.log('原始array:', array);
   shellSort(array)
   console.log('newArr:', array);
   
   ```
   

### 堆排序

1. **定义**

   - 堆是一个完全二叉树。
   - 堆中每一个节点的值都必须大于等于（或小于等于）其子树中每个节点的值。

2. **思想**

   - 将初始待排序关键字序列 (R1, R2 .... Rn) 构建成大顶堆，此堆为初始的无序区
   - 将堆顶元素 R[1] 与最后一个元素 R[n] 交换，此时得到新的无序区 (R1, R2, ..... Rn-1) 和新的有序区 (Rn) ，且满足 R[1, 2 ... n-1] <= R[n]
   - 由于交换后新的堆顶 R[1] 可能违反堆的性质，因此需要对当前无序区 (R1, R2 ...... Rn-1) 调整为新堆，然后再次将 R[1] 与无序区最后一个元素交换，得到新的无序区 (R1, R2 .... Rn-2) 和新的有序区 (Rn-1, Rn)。不断重复此过程，直到有序区的元素个数为 n - 1，则整个排序过程完成

3. 实现

   ```js
   function heapSort(arr) {
       let len = arr.length
    if(len < 2) return arr
       
       // 初始化大顶堆，从第一个非叶子结点开始
       for(let i=Math.floor(len/2); i>=0; i++) {
           heap(arr, i, len-1)
       }
       // 排序，每一次 for 循环都要找出一个当前的最大值，数组长度-1
       for(let i=Math.floor(len/2); i>0; i++) {
           // 根节点与最后一个节点交换
           swap(arr, 0, i)
           // 从根节点开始调整，并且最后一个结点已经为当前最大值，不需要再参与比较，所以第三个参数为 i，即比较到最后一个结点前一个即可
           heap(arr, 0, i)
   
       }
       return arr
   }
   
   // 交换节点
   function swap(arr, i, j) {
       arr[i] = arr[i] + arr[j]
       arr[j] = arr[i] - arr[j]
       arr[i] = arr[i] - arr[j]
   }
   
   // 使每一个节点i都满足为大顶堆，low表示下界，high表示上界
   function heap(arr, low, high) {
       let i = low
       let j = 2*i+1 // 左子树
       while(j<=high) {
           if(j+1<=high && arr[j+1]>arr[j]) {
               j = j+1
           }
   
           if(arr[i] < arr[j]) {
               swap(arr, i, j)
               // i 更新为被交换的孩子结点的索引
               i = j
               // j 更新为孩子结点的左孩子的索引
               j=j*2+1
           } else {
               break
           }
       }
   
   }
   
   const array = [4, 6, 8, 5, 9, 1, 2, 5, 3, 2];
   console.log('原始array:', array);
   const newArr = heapSort(array);
   console.log('newArr:', newArr);
   ```
   
   