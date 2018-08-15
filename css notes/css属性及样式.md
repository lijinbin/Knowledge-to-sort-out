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
#### 伸缩布局
   - 弹性盒子由弹性容器(Flex container)和弹性子元素(Flex item)组成。弹性容器通过设置 display 属性的值为 flex 或 inline-flex将其定义为弹性容器。
     ```
       1.flex-direction   属性指定了弹性子元素在父容器中的位置
         row：横向从左到右排列（左对齐），默认的排列方式。
         row-reverse：反转横向排列（右对齐，从后往前排，最后一项排在最前面。
         column：纵向排列。
         column-reverse：反转纵向排列，从后往前排，最后一项排在最上面。
         
       2.justify-content  内容对齐属性应用在弹性容器上，把弹性项沿着弹性容器的主轴线对齐
          flex-start:让子元素从父容器的起始位置开始排列
          flex-end:让子元素从父容器的结束位置开始排列
          center:让子元素从父容器的中间位置开始排列
          space-between:左右对齐父容器的开始和结束，中间平均分页，产生相同的间距
          space-around:将多余的空间平均的分页在每一个子元素的两边
          
       3.flex-wrap:控制子元素是否换行显示，默认不换行
          nowrap:不换行则收缩
          wrap:换行
          wrap-reverse:翻转，原来是从上到下，翻转后就是从下到上来排列
          
       4.align-items 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式
         flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
         flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
         center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
         baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
         stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。
         
       5.align-content  用于修改 flex-wrap 属性的行为。类似于 align-items, 但它不是设置弹性子元素的对齐，而是设置各个行的对齐
         stretch - 默认。
         flex-start - 各行向弹性盒容器的起始位置堆叠。
         flex-end - 各行向弹性盒容器的结束位置堆叠。
         center -各行向弹性盒容器的中间位置堆叠。
         space-between -各行在弹性盒容器中平均分布。
         space-around - 各行在弹性盒容器中平均分布，两端保留子元素与子元素之间间距大小的一半。
      ```


