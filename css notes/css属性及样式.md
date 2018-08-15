### 文本间隔
 -  word-spacing 属性可以改变字（单词）之间的标准间隔。其默认值 normal 与设置值为 0 是一样的。
     ```
      p { word-spacing:30px; }
     ```
### 列表样式（ul）
 - 对list-style-type属性的常见属性值的描述
      + none：不使用项目符号
      + disc：实心圆
      + circle：空心圆
      + square：实心方块
      + demical：阿拉伯数字 
      + lower-alpha：小写英文字母 
      + upper-alpha：大写英文字母 
      + lower-roman：小写罗马数字 
      + upper-roman：大写罗马数字
 - 对list-style-position属性的常见属性值的描述
     + inside	列表项目标记放置在文本以内，且环绕文本根据标记对齐。
     + outside	默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不根据标记对齐。
     + inherit	规定应该从父元素继承 list-style-position 属性的值。
#### 伪元素
  - 获取第一个字符：实现首字下沉
    ```
         p::first-letter{
                color: red;
                font-size: 30px;
                float: left;
            }
    ```
  - 获取第一行内容:如果设置了::first-letter,那么无法同时设置它的样式
    ```
        p::first-line{
            text-decoration: underline;
        }
    ```
  - 设置当前选中内容的样式
    ```
        p::selection{
            background-color: pink;
            color: red;
            /*font-size: 30px;它只能设置显示的样式，而不能设置内容大小*/
        }
    ```
#### 阴影
  - 文本阴影
     ```
         <!-- text-shadow:offsetX offsetY blur color-->
         text-shadow: -2px -2px 5px red;
    ```
  - 边框阴影
    ```
        <!-- box-shadow:h v blur spread color inset
        h:水平方向的偏移值
        v:垂直方向的偏移值
        blur:模糊--可选，默认0
        spread:阴影的尺寸，扩展和收缩阴影的大小--可选 默认0
        color:颜色--可选，默认黑色
        inset:内阴影--可选,默认是外阴影-->
        box-shadow: 3px 3px 3px #ccc inset,-3px -3px 3px #ccc inset;     
    ```
#### 边框图片(border-image-source)的用法
   - border-image-source:url("../images/border1.jpg")
   - 可以指定边框图片的路径,默认只是填充到容器的四个角点
   - 边框图片的宽度。如果没有设置这个属性，那么宽度默认就是元素的原始的边框宽度
#### 多列布局(column-count)
   - 设置多列布局
     ```
       1.设置列数
       column-count: 3;
       2.添加列间隙样式,与边框样式的添加一样
       column-rule: dashed 3px red;
       3.设置列间隙大小
       column-gap: 50px;
       4.设置列宽
       原则：取大优先
       1.如果人为设置宽度更大，则取更大的值，但是会填充整个屏幕，意味最终的宽度可能也会大于设置的宽度--填充满整个屏幕
       2.如果人为设置宽度更小，使用默认计算的宽度
       column-width: 200px;       
      ```



