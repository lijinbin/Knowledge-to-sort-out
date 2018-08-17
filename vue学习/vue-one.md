## jquery

### jQuery对象和DOM对象互转问题
   - DOM对象转jQuery对象,只需要把DOM对象放在$(dom对象)
   - jQuery对象转DOM对象两种方式
     + $(btnObj).get(0);---->DOM对象
     + $(btnObj)[0];----->DOM对象
### jQuery常见的几种方法
   - .html()方法,设置标签中间显示其他标签及内容,类似于innerHTML
   - .text()方法,设置标签中间显示的文本内容,类似于innerText
   - .val()方法.设置input标签中value的值,类似于value
   - .css()方法,.设置元素的样式,类似于style
### jQuery奇偶选择器
  - even 选择器选取带有偶数索引号的每个元素
  - odd 选择器选取带有奇数索引号的每个元素
  ```
    $("#uu>li:even").css("backgroundColor","yellow");//偶数的li
    $("#uu>li:odd").css("backgroundColor","red");//奇数的li
   ```

