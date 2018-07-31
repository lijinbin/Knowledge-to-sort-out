##点击input时value变换


### 点击input时value清空，当input失去焦点时value返回初始值

```
  <input id="txt" type="text" name="" placeholder="" value="Enter keyword to search products">
```

```
 $(function(){
    var text=document.getElementById("text").value;
    var input=document.getElementById("text");
    var flag=true;
    input.onfocus = function () {
        if (this.value ===text&& flag==true) {
            this.value = "";
        }
    };
    input.onblur = function () {
        if (this.value === "") {
            this.value =text;
        }else{
            flag=false;
        }
    };
})
```
