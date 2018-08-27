### Es6特性

####  兼容性
 -  http://kangax.github.io/compat-table/es6/
 -  http://kangax.github.io/compat-table/es5/
 -  ES6(ES2015)——在IE10+、Chrome、FireFox、移动端、NodeJS上是正常识别的
 -  如果在IE9及以下的浏览器上需要编译、转换
	+ 在线转换
	+ 提前编译（babel==browser.js）
	```
	 <script src="browser.js"></script>
	 <script type="text/babel">
	```
#### 变量/赋值
 - var     可以重复定义、不能限制修改、没有块级作用域
 - let     不能重复定义、变量、块级作用域
 - const   不能重复定义、常量、块级作用域
#### 函数
 - 箭头函数
   ```
   function (参数,参数){
       函数体
    }
    (参数,参数)=>{
      函数体
    }
     1.如果有且仅有1个参数，()可以省
     2.如果函数体只有一句话，而且是return，{}可以省
   ```
 - 函数的参数
  + 参数扩展/数组展开
     ```
	1.收集参数
	   function show(a, b, ...args){}
	   *Rest Parameter必须是最后一个
	2.展开数组
	   ...arr    =>    1,2,3
	  *展开后的效果，跟直接把数组的内容写在这儿一样
     ```
  + 默认参数
     ``` 
         $('#div1').animate({width: '200px'});
         $('#div1').animate({width: '200px'}, 1000);//'1000可写可不写，不写按默认执行，写的话按这个执行
      ```
####  解构赋值
 - 1.左右两边结构必须一样
 - 2.右边必须是个东西
 - 3.声明和赋值不能分开(必须在一句话里完成)
   + let [a,b,c]=[12,5,8];
   + let {a,b,c}={a: 12, b: 5, c: 8};
#### 数组
  -  map     映射：一个对一个
     ```
        let arr=[12,5,8];
        let result=arr.map(item=>item*2);
        alert(result);//24,10,16
     ```
  -  reduce  汇总：一堆->一个
     ```
	 let arr=[12,43,56,32];
         let result=arr.reduce(function(tmp,item,index){
           return tmp+item;//143
          })
         alert(result);
      ```
  -  filter   过滤
      ```
	 let arr=[12,5,8,99,27,36,75,11];
         let result=arr.filter(item=>item%3==0);
         alert(result);//12,99,27,36,75
      ```
  -  forEach 遍历
      ```
       let arr=[12,5,8,9];
       arr.forEach((item,index)=>{
         alert(index+': '+item); //0:12 1:5 2:8 3:9
        });
      ```  
####  字符串
  -  多了两个新方法
   + startsWith
     ```
       let str="https://www.baidu.com/";
	    if(str.startsWith("https://")){
	       alert("加密地址")
	    }else if(str.startsWith("http://")){
	       alert("普通地址")
	    }else{
	      alert("其他")
	    }
      ```
   + endsWith
     ```
       let str="1.txt";
	 if(str.endsWith("txt")){
	   alert("文本")
	 }else if(str.endsWith("jpg")){
	    alert("图片")
	 }else{
	   alert("其他")
	 }
      ```
  - 字符串模板 字符串拼接 
    + 直接把东西塞到字符串里面  $(东西)
    + 可以折行
####  面向对象
  - class关键字、构造器和类分开了
  - class里面直接加方法
     ```
      class Test{
		    constructor(){
		      this.xxx=
		    }
		    方法1(){
		
		    }
		    方法2(){
		
		    }
	   }
	
	  class Cls2 extends Cls1{
	    constructor(){
	      super();
	    }
	  }
	  
     ```
####  json
   - JSON对象
	+  JSON.stringify
	   JSON.stringify({a:12,b:5})  =>  '{"a":12,"b":5}'
    + JSON.parse
      JSON.parse('{"a":12,"b":5}')=>  {a:12,b:5}
   -  简写
         名字跟值(key和value)一样的      留一个就行
         方法                           : function一块删
         show: function (){...}
         show(){...}
####  Promise 封装异步操作(用同步一样的方式，来书写异步代码)
   -  Promise.all
      ```
      Promise.all([$.ajax(), $.ajax()]).then(results=>{
		  //对了
		}, err=>{
		  //错了
		});
      ```
   -  Promise.race    竞速
#### generator
  - 在有逻辑的情况下用generator异步操作相比promise更方便一点
	 ```
	     //带逻辑-generator
		runner(function *(){
		  let userData=yield $.ajax({url: 'getUserData', dataType: 'json'});

		  if(userData.type=='VIP'){
		    let items=yield $.ajax({url: 'getVIPItems', dataType: 'json'});
		  }else{
		    let items=yield $.ajax({url: 'getItems', dataType: 'json'});
		  }

		  //生成、...
		});
	 ```
