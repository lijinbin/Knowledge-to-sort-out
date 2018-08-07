## jquery

### jQuery对象和DOM对象互转问题
   + DOM对象转jQuery对象,只需要把DOM对象放在$(dom对象)
   + jQuery对象转DOM对象两种方式
     - $(btnObj).get(0);---->DOM对象
     - $(btnObj)[0];----->DOM对象
### jQuery常见的几种方法
   + .html()方法,设置标签中间显示其他标签及内容,类似于innerHTML
   +   .text()方法,设置标签中间显示的文本内容,类似于innerText
   +   .val()方法.设置input标签中value的值,类似于value
   +  .css()方法,.设置元素的样式,类似于style
### jQuery奇偶选择器
  + even 选择器选取带有偶数索引号的每个元素
  + odd 选择器选取带有奇数索引号的每个元素
  ```
    $("#uu>li:even").css("backgroundColor","yellow");//偶数的li
    $("#uu>li:odd").css("backgroundColor","red");//奇数的li
   ```
### jQuery索引选择器
  + eq(4)获取索引4的元素
  + gt(4)索引大于4的所有元素
  + lt(4)索引小于4的所有的元素
  ```
    $("#uu>li:eq(4)").css("backgroundColor","red");
    $("#uu>li:gt(4)").css("backgroundColor","red");
    $("#uu>li:lt(4)").css("backgroundColor","red");
   ```
### 获取兄弟元素的几个方法
```
  $(function () {
    $("#uu>li").mouseenter(function () {
        //.next();获取的是当前元素的下一个兄弟元素
        $(this).next().css("backgroundColor","green");
        //.nextAll();获取的是当前元素的后面的所有的兄弟元素
        $(this).nextAll().css("backgroundColor","green");
        //.prev();获取的是当前元素的前一个兄弟元素
        $(this).prev().css("backgroundColor","green");
        //.prevAll();获取的是当前元素的前面的所有的兄弟元素
        $(this).prevAll().css("backgroundColor","green");
        //.siblings();获取的是当前元素的所有的兄弟元素(自己除外)
        $(this).siblings().css("backgroundColor","green");
    });
}); 
```
###  jquery中attr和prop的区别
  + 对于HTML元素本身就带有的固有属性，在处理时，使用prop方法。
    - attr();可以写两个参数:1参数；属性,2属性值
    - attr();只写了一个参数,获取该元素的这个属性的值
  + 对于HTML元素我们自己自定义的DOM属性，在处理时，使用attr方法。
