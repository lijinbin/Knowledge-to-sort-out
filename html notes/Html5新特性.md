#### data-*自定义属性
  - 规范：
    + 1.data-开头
    + 2.data-后必须至少有一个字符，多个单词使用-连接
  - 建议：
    + 1.名称应该都使用小写--不要包含任何的大写字符
    + 2.名称中不要有任何的特殊符号
    + 3.名称不要副作用纯数字
    ```
      <div data-name="itcast">中国</div>
      <p data-school-name="st">中国人民</p>
     <script>
            window.onload= function () {
               var div=document.querySelector("div");
               var p=document.querySelector("p");
               var value1= div.dataset.name;
               //var value1=div.dataset["name"];
               var value2= p.dataset.schoolName;
               //var value2= p.dataset["schoolName"];
                console.log(value1);//itast
                console.log(value2);//st
            }
        </script>
    ```
 #### 网络接口
  - ononline:当网络连接的时候触发
    ```
      window.addEventListener("online",function(){
        alert("网络连通了...");
      });
    ```
  - onoffline:当网络断开的时候触发
    ```
      window.addEventListener("offline",function(){
        alert("网络断开了...");
      })
    ```
  #### 全屏接口
   - 1.requestFullScreen():开启全屏显示:不同浏览器需要添加不同的前缀,chrome:webkit   firefox:moz   ie:ms   opera:o
   - 2.cancelFullScreen():退出全屏显示:也添加前缀，在不同的浏览器下.退出全屏只能使用document来实现
   - 3.fullScreenElement:是否是全屏状态，也只能使用document进行判断
    
