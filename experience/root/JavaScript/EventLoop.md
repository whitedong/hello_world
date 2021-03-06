# 事件循环Event Loop

> 资料来源[MDN(并发模型与事件循环)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/EventLoop)    
> 推荐视频：[https://www.youtube.com/watch?v=8aGhZQkoFbQ](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

``事件循环``负责执行代码，收集和处理事件以及执行队列中的子任务，实现异步的机制。

```html
  Event Loop
                                              ┌──────────────────────────────────────────────┐ 
                                              │  Web APIS                                    │ 
    ┌───────────────────────────────┐         │ ┌───────────────────────┐  ┌───────────────┐ │ 
    │  JavaScript Engine            │         │ │ Task                  │  │ MicroTask     │ │
    │ ┌──────────────┐ ┌──────────┐ │         │ │ ┌───────────────────┐ │  │ ┌───────────┐ │ │
    │ │  Call Stack  │ │  Heap    │ │         │ │ │  DOM(document)    | |  │ │  Promise  │ │ │
    │ │              │ │ ┌──────┐ │ │         │ | └───────────────────┘ | ┌| └───────────┘ │ │ 
    │ │              │ │ │Object│ │ │         │ | ┌───────────────────┐ | |└───────────────┘ │
    │ │              │ │ └──────┘ │ │         │ | |  ajax             | | |                   │ 
    │ │              │ │          │ │         │ | |  (XMLhttpRequest) | | |                   │ 
    │ │              │ │          │ │         │ | └───────────────────┘ | |                   │
    │ │              │ │          │ │ — — — —>│ │ ┌───────────────────┐ │ |                   │ 
    │ │ ┌──────────┐ │ │          │ │         │ │ | setTimeout        | │ |                   │ 
  ┌────>│ Function │ │ │          │ │         │┌│ └───────────────────┘ │ |                   │
  │ │ │ └──────────┘ │ │          │ │         ││└───────────────────────┘ |                   │
  │ │ └──────────────┘ └──────────┘ │         └│──────────────────────────|───────────────────┘  
  │ └───────────────────────────────┘          │                          | 
  │                                            │                          | 
  │                                            ↓                          ↓
  │ ─────────────────────────────────────────────────────         ─────────────────────────────────────────────────────
  │   CallBack Queue                                                 MicroQueue
  │   ┌───────────┐ ┌──────────┐ ┌──────────┐                         ┌────────────────┐
  └───┤  onClick  │ │  onLoad  │ |  onDone  |                         |  Promise.then  |
      └───────────┘ └──────────┘ └──────────┘                         └────────────────┘
    ──────────────────────────────────────────────────────        ──────────────────────────────────────────────────────
    
```

**栈Stack**
- 是一个``先入后出``的数据结构
- 函数调用时候生成一个若干帧组成的栈，每次调用函数都会生成一个新的栈帧，
- JavaScript是单线程编程语言，只有一个执行栈

**堆Heap**
- 用于存放对象的区域
- 是用来表示一大块内存区域的计算机术语

**队列Queue**
- 一种``先进先出``的数据结构
- ``JavaScript运行时(runtime)``包含一个待处理消息队列, 每个消息都关联一个处理该消息的回调函数(callback)函数

**Task**

**MicroTask**



