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
### 事件目标
 - 获取事件目标
 ```
  事件目标:触发事件的元素
  var target = event.target || event.srcElement;
  ```
  
### 事件监听
  - 绑定事件监听 
   ```
    1，方式：addEventListener
       a，参数：
       第一个参数：绑定事件的类型（不带“on”），是一个字符串
       第二个参数：事件的处理程序（函数体，可以写一个函数的名称）
       第三个参数：是否使用捕获，true为使用捕获，false为不使用捕获
       使用捕获：当前事件在捕获阶段执行
       不使用捕获：当前事件在冒泡阶段执行
       b，使用方式：
       btn2.addEventListener("click", function () {
            alert("第一个人的代码");
        }, false);
        c，特点：
        可以多次绑定事件，并且不会覆盖
    2，方式：attachEvent
    a，参数：
    第一个参数：绑定事件的类型（带“on”），是一个字符串
    第二个参数：事件处理程序
    3，兼容addEventListener和attachEvent
    //封装 兼容所有浏览器的添加事件的函数
    //element要绑定事件的元素对象 eventName是字符串而且不加on listener事件处理函数
    function addEvent(element, eventName, listener) {
        if (element.addEventListener) {
            element.addEventListener(eventName, listener, false);
        } else if (element.attachEvent) {
            element.attachEvent("on" + eventName, listener);
        } else {
            element["on" + eventName] = listener;
        }
    }
   ```
  - 删除事件监听
   ```
    1，方式：removeEventListener
     a，参数：
     第一个参数：要移除的事件类型（不带“on”）
     第二个参数：要移除的事件处理程序
     第三个参数：是否使用捕获（与解绑事件保持一致）
     b，每次只能删除一个事件处理程序，并且第二个参数是绑定时事件处理函数的引用
    2，方式：detachEvent
    a，参数：
     第一个参数：要解绑的事件类型
     第二个参数：要删除的事件处理程序的引用
     注意：绑定的事件如果想要移除，传入的事件处理程序必须是一个函数体的引用，
     这样移除事件的时候removeEventListener/detachEvent才能找到事件处理程序，并且移除这个操作。
     3，兼容removeEventListener和detchEvent
    //封装 兼容所有浏览器的移除事件的函数
      function removeEvent(element, eventName, listener) {
          if (element.removeEventListener) {
              element.removeEventListener(eventName, listener, false);
          } else if (element.detachEvent) {
              element.detachEvent("on" + eventName, listener);
          } else {
              element["on" + eventName] = null;
          }
      }
   ```
   - 事件阶段
     如果一个元素触发了某个事件，浏览器会执行以下过程：
     捕获阶段 —— 目标阶段 —— 冒泡阶段
