### js库

- iScroll.js 一个可以实现客户端原生滚动效果的类库。
-  Moment.js--js日期处理类库
-  Modernizr     用于检测用户浏览器的html5和css3特性
-  Covering-Bad
-  Viewer.js 是一款强大的图片查看器
-  sliphover演示9种不同的图片动画遮罩效果
-  jquery.hoverdir
-  http://www.codeforge.cn/
-  性能优化
  https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651554511&idx=2&sn=cfe3ca6038917e4dbcddcd90baf65914&chksm=8025550eb752dc18bb269d894c53814dc5256010e524bbc4d6970c7ea7de82254f9e07d7e19f&mpshare=1&scene=23&srcid=07042l5li18oIJ1xddevKJrj#rd
-  http://fgm.cc/learn/  原生JavaScript学习

-  https://www.mipengine.org/doc/00-mip-101.html  移动网页加速器
- h5编辑器
  + https://xiumi.us
  + https://www.ih5.cn
  + http://www.e7wei.com/

1.正则表达式的作用？
正则表达式主要是针对字符串进行操作，可以简化对字符串的复杂操作，其主要功能有匹配、切割、替换、获取。
2.js运行机制
单线程机制：同一时间只能做一件事，当有多个任务时，只能按照一个顺序一个完成了再执行下一个
任务队列：同步与异步 关注的是消息通知机制
          阻塞和非阻塞 注的是程序在等待调用结果（消息，返回值）时的状态
3.什么是跨域？
跨域，指的是浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对JavaScript施加的安全限制。
解决办法：1、JSONP
          2、nginx反向代理
          3、PHP端修改header
          4、通过 window.name 实现跨域
4.Json对象转换为json字符串
  for循环
  JSON.stringify(userinfo);

  json字符串转换为Json对象
  使用Ajax 的转换对象  $.parseJSON(workJsonString);//使用Ajax
  JSON.parse(workJsonString)
  使用eval()对象
