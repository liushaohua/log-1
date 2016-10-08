## 日志采集部署-beta版本

### 1. 在页面head顶端加入全局函数
```javascript
<script>
var _maq = _maq || [];
_maq.push(['_setAccount', '网站标识']);
</script>
```
_setAccount 为站点标识名称，例如：_maq.push(['_setAccount', 'big_data']);

### 2. 在页面head埋点`全局函数`后加入`script`外链
```html
<script src="http://www.misued.com/log.js"></script>
```

### 3.为模块增加埋点
```html
<body>
   <span class="OP_LOG_BTN blue_btn" data-click="{fm:'beha',tag:'submit'}">提交</span>
   <span class="OP_LOG_BTN" data-click="{fm:'beha',tag:'reset'}">重置</span>
</body>
```
需要为需要统计埋点的`dom`元素上增加`OP_LOG_BTN`的`class`名称，以及`data-click`属性，其中`fm`为统计类型，`beha`为交互点击，`tag`为模块的名称，字符长度最好限制在10个字符内。

### 注意事项
- 不要覆盖元素的点击事件,选用追加事件的形式为元素增加事件
```javascript
//反例：
var oDiv = document.getElementById('div1');
oDiv.onclick = function () {
  alert(1);
}

//正例：
var oDiv = $('div1');
oDiv.click(function () {
   alert(1);
});
```
