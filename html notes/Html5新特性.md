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
