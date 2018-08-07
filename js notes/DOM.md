## DOM

### 内部文本属性
 - innerHTML  获取内部的html
 - innerText     获取和设置标签中的内容，设置的内容会被当作普通文本（有兼容性问题，旧版ff不支持）
 - textContent  获取和设置标签中的内容，设置的内容会被当作普通文本（有兼容性问题，旧版ff不支持）
### 自定义属性
  - 操作标签属性
  ```
   <div id="box" a="1" class="cls"></div> 
   console.log(box.getAttribute("a"));//可以获取没有规定的属性
   console.log(box.getAttribute("id"));//也可以获取有规定的属性
   //设置 任何标签中的属性都可以设置
   box.setAttribute("b", "2");//可以设置没有规定的属性
   box.setAttribute("b","2")
  box.setAttribute("class", "cls");//可以设置有规定的属性
  //移除 任何标签中的属性都可以移除
  box.removeAttribute("a");
  box.removeAttribute("b")
  box.removeAttribute("class");
  ```
### 节点
 ```
  childNodes 	//子节点 
  children		//子元素 虽然不是早期DOM标准中的方法，但是所有浏览器都支持
  nextSibling //下一个兄弟节点
  nextElementSibling //下一个兄弟元素 有兼容性问题
  previousSibling//上一个兄弟节点
  previousElementSibling //上一个兄弟元素 有兼容性问题
  firstChild //第一个节点
  firstElementChild //第一个子元素 有兼容性问题
  lastChild //最后一个子节点
  lastElementChild //最后一个子元素 有兼容性问题
  parentNode //父节点 （一定是元素节点，所以无需处理）
  ```
###  动态创建元素
- 克隆节点
要克隆的节点.cloneNode(布尔值);//一般情况下传true
- 在父元素中的最后追加子元素
father.appendChild(要追加的节点对象);
- 在父元素中的某个子元素前面插入子元素
father.insertBefore(要插入的节点对象,插到这个节点对象的前面);
- 从父元素中移除子元素
father.removeChild(要移除的子节点对象);
- 创建节点
 createElement（）