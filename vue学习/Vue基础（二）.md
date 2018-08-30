### Vue基础（二） 

#### 过滤器
概念：Vue.js 允许你自定义过滤器，**可被用作一些常见的文本格式化**。过滤器可以用在两个地方：**mustache 插值和 v-bind 表达式**。过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符指示；
+ 全局过滤器 可以多次使用
```
  <div id="app">
     <p>{{msg| msgcontent}}</p>
  </div>
  <script type="text/javascript">
     Vue.filter("msgcontent",function(){
       return 123
     })
     var vm=new Vue({
       el:"#app",
       data:{
         msg:"hello world"
       }
     })
  </script>
```
+ 过滤器 可以传递参数
```
 <div id="app">
     <p>{{msg| msgcontent("疯狂")}}</p>
  </div>
  <script type="text/javascript">
     Vue.filter("msgcontent",function(msg,arg){
       return msg.replace(/l/g,arg)
     })
     var vm=new Vue({
       el:"#app",
       data:{
         msg:"hello world"
       }
     })
  </script>
```
+ 私有过滤器
```
filters: { // 私有局部过滤器，只能在 当前 VM 对象所控制的 View 区域进行使用
    语句块
  }
```
+ **注意：当有局部和全局两个名称相同的过滤器时候，会以就近原则进行调用，即：局部过滤器优先于全局过滤器被调用 **
#### 键盘修饰符以及自定义键盘修饰符

+  1.x中自定义键盘修饰符【了解即可】
```
Vue.directive('on').keyCodes.f2 = 113;
```
+  [2.x中自定义键盘修饰符](https://cn.vuejs.org/v2/guide/events.html#键值修饰符)

1.通过`Vue.config.keyCodes.名称 = 按键值`来自定义案件修饰符的别名：
```
Vue.config.keyCodes.f2 = 113;
```
2.使用自定义的按键修饰符：
```
<input type="text" v-model="name" @keyup.f2="add">
```
#### [自定义指令](https://cn.vuejs.org/v2/guide/custom-directive.html)
+  自定义全局指令
```
    // 自定义全局指令 v-focus，为绑定的元素自动获取焦点：
    <input type="text" v-model="searchName" v-focus>
    
    Vue.directive('focus', {
      bind: function (el) { // 每当指令绑定到元素上的时候，会立即执行这个 bind 函数，只执行一次
        // el.focus()
      },
      inserted: function (el) {// inserted 表示元素 插入到DOM中的时候，会执行 inserted 函数
        el.focus()
      },
      updated: function (el) {// 当VNode更新的时候，会执行 updated， 可能会触发多次

      }

    });
```
+ 自定义局部指令
```
  // v-color 和 v-font-weight，为绑定的元素设置指定的字体颜色 和 字体粗细：

  <div><input type="text" v-color="'blue'"></div>
  
  var vm=new Vue({
        el:'#app',
        data:{},
        directives: {
           color: { // 为元素设置指定的字体颜色
             bind(el, binding) {
               el.style.color = binding.value;
             }
           },
         'font-weight': function (el, binding2) { 



           // 自定义指令的简写形式，等同于定义了 bind 和 update 两个钩子函数
          el.style.fontWeight = binding2.value;
        }

      }
   })
```
####  [vue-resource 实现 get, post, jsonp请求](https://github.com/pagekit/vue-resource)
 除了 vue-resource 之外，还可以使用 `axios` 的第三方包实现实现数据的请求
 + 发送get请求：
 ```
  getInfo() {
        //  当发起get请求之后， 通过 .then 来设置成功的回调函数
         this.$http.get('https://locally.uieee.com/slides').then(function (result) {
            console.log(result.body)
         })
       }
 ```
 + 发送post请求：
 ```
  postInfo() {
  var url = 'http://127.0.0.1:8899/api/post';
  // post 方法接收三个参数：
  // 参数1： 要请求的URL地址
  // 参数2： 要发送的数据对象
  // 参数3： 指定post提交的编码类型为 application/x-www-form-urlencoded
  this.$http.post(url, { name: 'zs' }, { emulateJSON: true }).then(res => {
    console.log(res.body);
  });
}
 ```
 + 发送JSONP请求获取数据：
 ```
  jsonpInfo() { // JSONP形式从服务器获取数据
	  var url = 'https://api.douban.com/v2/movie/in_theaters';
	  this.$http.jsonp(url).then(res => {
	    console.log(res.body);
	  });
	}
 ```
 +  如果我们通过全局配置了，请求的数据接口 根域名，则 ，在每次单独发起 http 请求的时候，请求的 url 路径，应该以相对路径开头，前面不能带 /  ，否则 不会启用根路径做拼接；
   ```
    Vue.http.options.root = 'http://vue.studyit.io/';
   ```
 + 全局启用 post中的emulateJSON 选项
 ```
  Vue.http.options.emulateJSON = true;
 ```
####  [Vue中的动画](https://cn.vuejs.org/v2/guide/transitions.html)
为什么要有动画：动画能够提高用户的体验，帮助用户更好的理解页面中的功能；
+ 使用过渡类名实现过渡
```
1. HTML结构：
<div id="app">
    <input type="button" value="toggle" name=""  @click="flag=!flag">
    <!-- 使用 transition 将需要过渡的元素包裹起来 -->
    <transition name="fade">//这里的name属性可以自定义 写样式时替代v-前缀 即是fade-enter
      <h3 v-show="flag">hello world</h3>
    </transition>
  </div>
2. VM 实例：
// 创建 Vue 实例，得到 ViewModel
var vm = new Vue({
  el: '#app',
  data: {
    flag: false
  },
  methods: {}
});
3. 定义两组类样式：
  /* 定义进入和离开时候的过渡状态 */
    .v-enter-active,
    .v-leave-active {
      transition: all 0.2s ease;
    }

    /* 定义进入过渡的开始状态 和 离开过渡的结束状态 */
    .v-enter,
    .v-leave-to {
      opacity: 0;
      transform: translateX(100px);
    }
```
+ [使用第三方 CSS 动画库](https://cn.vuejs.org/v2/guide/transitions.html#自定义过渡类名)
```
 1. 导入动画类库：
 <link rel="stylesheet" href="./lib/animate.css">
 2. 定义 transition 及属性：
 <transition enter-active-class="bounceIn" leave-active-class="bounceOut"  :duration="{enter:200,leave:1000}">        
   <h3 v-if="flag" class="animated">hello world</h3>
</transition>
```