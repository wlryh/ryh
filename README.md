# ryh
HTML+CSS
1、水平垂直居中 链接：https://www.w3cplus.com/css/vertically-center-content-with-css
内容垂直居中 链接：https://www.cnblogs.com/moqiutao/p/4807792.html

不定宽高div垂直水平居中：
（1）3，2
  父：
     display:table-cell;
     text-align:center;
     vertical:middle;
  div:
     display:inner-block;
     vertical:middle;
（2）1,4
   父：
      position:relative;
   div:
      transform:translate(-50%,-50%);
      position:absolute;
      top:50%;
      left:50%;
   

2、css 绘制圆形 扇形：http://blog.csdn.net/fankof29/article/details/51712541



js
1、null和undefined
null:null是一个只有一个值的特殊类型。表示一个空对象引用。
undefined:是一个没有设置值的变量
undefined 和 null 的区别:值相等，但是类型不相等，
                         typeof undefined             // undefined
                         typeof null                  // object
                         null === undefined           // false
                         null == undefined            // true
