**学习时间：2022.11.30**
[toc]
## CSS定位装饰
### 定位
#### 定位的基本介绍
* 网页常见布局方式
  + 标准流
  + 浮动
  + 定位：让元素可以在网页的任意位置，一般用于盒子之间的层叠情况
#### 定位的基本方式
* 属性名：position
  + 设置定位方式
    |定位方式|属性值|
    |----|----|
    |静态定位|static|
    |相对定位|relative|
    |绝对定位|absolute|
    |固定定位|fixed|
  + 设置偏移值
    |方向|属性名|属性值|含义|
    |----|----|----|----|
    |水平|left|数字px|距离左边的距离|
    |水平|right|数字px|距离右边的距离|
    |垂直|top|数字px|距离上边的距离|
    |垂直|bottom|数字px|距离下边的距离|
  + 注意事项：如果left,right,top,bottom都有，则left和bottom生效
##### static
* The element is positioned according to the normal flow of the document. The top, right, bottom, left, and z-index properties have no effect. This is the default value.
```html
<!-- 01-静态定位.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>静态定位</title>
    <style>
        div{
            position: static;
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <div>用于实现静态定位</div>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
</body>
</html>
````
##### relative
* 参照自己原来的位置进行改变
* 仍然占有原来的位置
* 仍然具有原标签显示模式的特点
```html
<!-- 02-相对定位.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>相对定位</title>
    <style>
        div{
            /* position: static; */
            position: relative;
            left: 100px;
            top: 200px;
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <div>用于实现相对定位</div>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
</body>
</html>
```
##### absolute
* 脱标，不占位
* 可以改变原标签显示模式，改为行内块模式
* 子女绝父母相：一般情况下，子女标签使用绝对定位，父母标签使用相对定位
* 实现方式：就近找已经定位的父母级(不能是静态定位)
  + 存在这样的父母级，根据该父母级进行定位
  + 不存在这样的父母级，根据浏览器窗口进行定位
```html
<!-- 03-绝对定位.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>绝对定位</title>
    <style>
        .parent{
            position: relative;
            width: 400px;
            height: 400px;
            background-color: green;
        }
        .child{
            /* position: static; */
            position: absolute;
            left: 100px;
            top: 200px;
            width: 200px;
            height: 200px;
            background-color: pink;
        }

    </style>
</head>
<body>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <div class="parent"><div class="child">用于实现绝对定位</div></div>
    
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
</body>
</html>
```
* 绝对定位的盒子不能使用margin进行居中
* 应该使用以下方法
  + 居中方法1
    ```html
    <!-- 04-绝对定位的居中 -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>绝对定位的居中</title>
    </head>
    <style>
        div{
            position: absolute;
            /* 居中方法1 */
            left: 50%;
            margin-left: -150px;
            top: 50%;
            margin-top: -150px;
            width: 300px;
            height: 300px;
            background-color: pink;
        }
    </style>
    <body>
        <div>这是一个绝对定位的盒子，需要上下左右居中</div>
    </body>
    </html>
    ```
  + 居中方法2：使用transform(translate(-50%.-50%))，这里50%指盒子自身长度，宽度的50%
    ```html
    <!-- 04-绝对定位的居中 -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>绝对定位的居中</title>
    </head>
    <style>
        div{
            position: absolute;
            /* 居中方法2 */
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            width: 500px;
            height: 300px;
            background-color: pink;
        }
    </style>
    <body>
        <div>这是一个绝对定位的盒子，需要上下左右居中</div>
    </body>
    </html>
    ```
##### fixed
* 脱标，不占位置
* 只相对于浏览器窗口移动
* 具有行内块特点，必须设置宽高
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>固定定位</title>
    <style>
        div{
            position: fixed;
            top: 40px;
            left: 50px;
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <div>用于实现固定定位</div>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
    <p>测试定位测试定位测试定位测试定位测试定位测试定位测试定位测试定位</p>
</body>
</html>
```
#### 不同元素之间的层级关系
* 不同布局方式元素的层级关系
  + 标准流<浮动<定位
* 不同定位之间的层级关系
  + 相对，绝对，固定默认层级相同
  + HTML中写在下面的标签层级更高，居于上方：后来者居上
  + 可以使用 z-index:数字 对层级关系进行改变，该值默认为0
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>层级关系</title>
    <style>
        div{
            width: 200px;
            height: 200px;
        }
        .one{
            position: relative;
            background-color: pink;
            top: 40px;
            left: 30px;

            z-index: 30;
        }
        .two{
            position: absolute;
            background-color: green;
            top: 80px;
            left: 30px;
        }
    </style>
</head>
<body>
    <div class="one">
        写在前面的定位标签
    </div>
    <div class="two">
        写在后面的定位标签
    </div>
</body>
</html>
```
### 装饰
#### 垂直对齐
* 属性名：vertical-align
* 属性值
  + baseline 默认，基线对齐
  + top 顶部对齐
  + middle 中部对齐
  + bottom 底部对齐
* **浏览器遇到行内块，均按照文字处理**，即基线对齐。但若行内块标签是图片、输入框、按钮等，基线对齐的方式就会使得页面不整齐。这个时候有2种解决方法
  + 将对应标签改为块标签
  + 但凡处理行内块之间，行内块和文字之间的关系，在其中一个的选择器中加上vertical-align就可以实现
```html
<!-- 07-垂直居中 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>垂直居中</title>
    <style>
        .box{
            width: 400px;
            height: 400px;
            background-color: pink;
            line-height: 400px;
            text-align: center;
        }
        img{
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="box">
        
        <img src="../markdown笔记/images/10-03.jpg" alt="">
    </div>
    <p>这是一段文字，父母标签加上line-height后就可以垂直居中。但上面的图片除了line-height以外，还需要给img标签加上vertical-align才能使得图片垂直居中。同样，使用text-align可以使得文字和图片水平居中。原因在于浏览器解析行内块一律当作文字处理</p>
</body>
</html>
```
#### 光标类型
* 用于设置鼠标光标在元素上显示的样式
* 属性名：cursor
* 属性值
  + default 默认值，通常是箭头
  + pointer 小手形状，提示用户可以点击
  + text 工字形，提示用户可以复制，一般是在文字处
  + move 十字型，提示用户可以移动
```html
<!-- 08-光标类型.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>光标类型</title>
    <style>
        div{
            width: 300px;
            height: 300px;
            background-color: pink;

            /* cursor: pointer;
            cursor: text; */
            cursor: move;
        }
    </style>
</head>
<body>
    <div></div>
</body>
</html>
```
#### 边框圆角
* 书写方式：border-radius：数字px/百分比
* 最多可以写4个数字
```html
<!-- 09-边框圆角.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>边框圆角</title>
    <style>
        .box{
            width: 300px;
            height: 300px;
            background-color: pink;

            border-radius: 20px 30px 40px;
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
</html>
```
* 常用的圆角边框
  + 圆形，用于头像的显示等
  + 胶囊形
```html
<!-- 10-边框圆角-应用.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>边框圆角-应用</title>
    <style>
        .one{
            width: 200px;
            height: 200px;
            background-color: pink;

            border-radius: 50%;
        }
        .two{
            width: 300px;
            height: 120px;
            background-color: green;

            border-radius: 60px;
        }
    </style>
</head>
<body>
    <div class="one"></div>
    <div class="two"></div>
</body>
</html>
```
#### overflow溢出部分显示效果
* 用于控制溢出部分的显示
* 属性名：overflow
* 属性值
  + visible 默认值，溢出部分可见
  + hidden 隐藏溢出部分
  + scroll 无论是否溢出都显示滚动条
  + auto 只有溢出时才显示滚动条
```html
<!-- 11-溢出.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>溢出</title>
    <style>
        div{
            width: 300px;
            height: 400px;
            overflow: hidden;
            /* overflow: scroll;
            overflow: auto; */
        }
    </style>
</head>
<body>
    <div>
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
        这是一个div标签，用于测试溢出属性
    </div>
</body>
</html>
```
#### 元素本身隐藏
* 元素隐藏有两种方式
  + visibility：hidden 占位隐藏，隐藏后仍然在占用原来位置
  + display：none 不占位隐藏，使用场景较多
```html
<!-- 12-元素本身隐藏.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>元素本身隐藏</title>
    <style>
        div{
            width: 200px;
            height: 200px;
        }
        .one{
            background-color: pink;
            /* visibility: hidden; */
            display: none;
        }
        .two{
            background-color: green;
        }
    </style>
</head>
<body>
    <div class="one"></div>
    <div class="two"></div>
</body>
</html>
```