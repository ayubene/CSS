### 层叠性
由于CSS(Cascading Style Sheets)叫做层叠样式表，即一层一层覆盖，最下面的一层会覆盖前一层，因此如果给一个标签设置了两个相同的样式，写在最下面的会生效
```html
<style>
    p{
        color:red;
        color:blue;
    }
</style>
<p>这是一个p标签</p>
```
![层叠性代码结果](images/00-01.png)