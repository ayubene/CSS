**学习时间：2022.11.12**
## CSS特性
### 继承性
* 子女元素默认继承父母元素的相关属性
* 只有文字相关的属性会被继承，其他属性均不被继承
* 当子女元素有自己的浏览器默认属性时，如a标签，h系列标签，不会继承
* 可以使用浏览器调试工具来判断样式是否能被继承

### 层叠性
* 后面的样式会覆盖前面的
* 只有优先级相同的选择器才有层叠的效果

### 优先级
#### 基本测试
* 优先级高的选择器样式会覆盖优先级低的样式
* 优先级从低到高：
  + 继承<通配符选择器<标签选择器<类选择器< id选择器<行内样式<!important
* 选择器包含的范围越广，优先级越低
* !important不能提高继承的优先级
* !important很少使用
```html
<!-- 02-优先级-基本测试.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>优先级基本测试</title>
    <style>
        /* 继承 */
        body{
            color: red;
        }
        /* 通配符选择器 */
        *{
            color: orange;
        }
        /* 标签选择器 */
        div{
            color: yellow;
        }
        /* 类选择器 */
        .class{
            color: green;
        }
        /* id选择器 */
        #id{
            color: skyblue;
        }
        /* 给通配符选择器加上!important */
        *{
            color: orange !important;
        }
    </style>
</head>
<body>
    <!-- 行内样式 "color: blue" -->
    <div class="class" id="id" style="color: blue">这是一个div标签</div>
</body>
</html>
```
![02-优先级-基本测试.html在浏览器的显示效果](images/07-01.png)

#### 权重计算
* 用于多个复合选择器之间进行优先级比较
* 格式：
  + (行内样式个数，id选择器个数，类选择器个数，标签选择器个数)
  + 从第一位数字开始比较，数字越大优先级越高。如果第一位数字相等，则比较第二位，数字越大优先级越高。如果第二位也相等，则比较第三位，以此类推。
  + 如果所有数字都相同，则根据层叠性来判断
  + !important只要不在继承，永远优先级最高，但要谨慎使用
* 关于继承
  + 继承永远是最低的
  + 如何判断继承：看选择器是否能直接选中内容
  + 继承也分高低，内容离得最近的那个选择器最高
```html
<!-- 03-优先级-权重叠加计算.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>优先级-权重叠加计算</title>
    <style>
        /* 权值（行内，id，类，标签） */
        /* 0,1,1,0 */
        .parent #two{
            color: red;
        }
        /* 0,0,1,1 */
        div .child{
            color: orange;
        }
        /* 0,2,0,0 */
        #one #two{
            color: green;
        }
        /* 0,0,0,2 */
        div p{
            color: purple
        }
    </style>
</head>
<body>
    <div class="parent" id="one">
        <p class="child" id="two" >这是一个p标签</p>
    </div>
</body>
</html>
```
![03-优先级-权重叠加计算.html在浏览器的显示效果](images/07-02.png)


![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]
![在浏览器的显示效果]