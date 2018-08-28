### Vue基础（一） 

#### MVC 和 MVVM 的区别
+ MVC 是后端的分层开发概念；
+ MVVM是前端视图层的概念，主要关注于 视图层分离，也就是说：MVVM把前端的视图层，分为了 三部分 Model, View , VM ViewModel
#### 如何定义一个基本的Vue代码结构
```
  <!-- 将来 new 的Vue实例，会控制这个 元素中的所有内容 -->
  <!-- Vue 实例所控制的这个元素区域，就是我们的 V  -->
  <div id="app">
    <p>{{ msg }}</p>
  </div>

  <script>
    // 2. 创建一个Vue的实例
    // 当我们导入包之后，在浏览器的内存中，就多了一个 Vue 构造函数
    //  注意：我们 new 出来的这个 vm 对象，就是我们 MVVM中的 VM调度者
    var vm = new Vue({
      el: '#app',  // 表示，当前我们 new 的这个 Vue 实例，要控制页面上的哪个区域
      // 这里的 data 就是 MVVM中的 M，专门用来保存 每个页面的数据的
      data: { // data 属性中，存放的是 el 中要用到的数据
        msg: '欢迎学习Vue' // 通过 Vue 提供的指令，很方便的就能把数据渲染到页面上，程序员不再手动操作DOM元素了【前端的Vue之类的框架，不提倡我们去手动操作DOM元素了】
      }
    })
  </script>
```
#### Vue指令
+  v-cloak  能够解决 插值表达式闪烁的问题(用`v-cloak`时需要css定义`display: none;`)
```
  <style>
    [v-cloak] {
       display: none;
    }
  </style>
  <div id="app">
    <p v-cloak>++++++++ {{ msg }} ----------</p>
 </div>
 <script>
    var vm = new Vue({
      el: '#app',
      data: {
        msg: '123',
      }
    })
  </script>
```
+  v-text    默认 v-text 是没有闪烁问题的
+  v-html
+  v-bind (三种用法)
     1. 直接使用指令`v-bind`
     2. 使用简化指令`:`
     3. 在绑定的时候，拼接绑定内容：`:title="btnTitle + ', 这是追加的内容'"`
+  v-on     Vue提供的事件绑定机制   缩写是 `@`
#### 事件修饰符：
+ .stop       阻止冒泡
+ .prevent    阻止默认事件
+ .capture    添加事件侦听器时使用事件捕获模式
+ .self       只当事件在该元素本身（比如不是子元素）触发时触发回调
+ .once       事件只触发一次
####  v-model  只能应用于表单元素
```
 <div id="app">
    <h4>{{ msg }}</h4>
    <!-- v-bind 只能实现数据的单向绑定，无法实现数据的双向绑定  -->
    <!-- <input type="text" v-bind:value="msg" style="width:100%;"> -->
    <!-- 使用  v-model 指令，可以实现 表单元素和 Model 中数据的双向数据绑定 -->
    <input type="text" style="width:100%;" v-model="msg">
  </div>
  <script>
    var vm = new Vue({
      el: '#app',
      data: {
        msg: '大家都是好学生，爱敲代码，爱学习，爱思考，简直是完美，没瑕疵！'
      },
      methods: {
      }
    });
  </script>
```
#### 绑定样式两种方式 
+ v-bind:class 
+ v-bind:style  
#### Vue指令之`v-for`和`key`属性
+ 迭代数组
```
<ul>
  <li v-for="(item, i) in list">索引：{{i}} --- 姓名：{{item.name}} --- 年龄：{{item.age}}</li>
</ul>
```
+  迭代对象中的属性
```
	<!-- 循环遍历对象身上的属性 -->
    <div v-for="(val, key, i) in userInfo">{{val}} --- {{key}} --- {{i}}</div>
```
+ 迭代数字
```
<p v-for="i in 10">这是第 {{i}} 个P标签</p>
```
#### Vue指令之`v-if`和`v-show`
+ v-if 的特点：每次都会重新删除或创建元素，有较高的切换性能消耗
+ v-show 的特点： 每次不会重新进行DOM的删除和创建操作，只是切换了元素的 display:none 样式，有较高的初始渲染消耗