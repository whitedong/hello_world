# MVVM

**MVVM**

``MVVM`` -> Model-View-ViewModel，``Model``代表数据模型，``View``代表视图模型，数据会绑定到``ViewModel``并自动更新数据渲染页面，视图变化会通知``ViewModel``更新数据。

```html
  ┌───────┐    ┌───────────┐    ┌──────┐
  | Model ├───>| ViewModel ├───>| View |
  |       |<───┤           |<───┤      |             
  └───────┘    └───────────┘    └──────┘ 
```

**响应式原理**

``Vue.js``通过**数据劫持**和**发布订阅模式**来实现响应式数据。
- 数据劫持    
  通过``Object.defineProperty()``或``Proxy``来劫持对象的访问器``setter``和``getter``,在属性值变化时可以获取变化，进行操作。
  
  区别：
  
  ``Object.defineProperty()``只劫持对象属性，所以需要遍历对象的每个属性。
  
  ``Proxy``直接代理对象，不需要遍历操作。
  
  
- 发布订阅     
  在属性变动时发布消息给订阅者，触发相应的监听回调

```javascript
  // Vue 实现语法
  var vm = new Vue({
    el: '#example',
    data: {
      a:1
    }
  })
```

**简单实现**

```javascript
  var Vue = function(options){
    console.log(arguments)
  }
```
