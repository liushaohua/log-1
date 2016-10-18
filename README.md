## 流量日志自动化采集说明

### 1. 在页面加入`script`外链
```html
<script src="http://www.misued.com/log.js"></script>
```
将以下JS代码复制到您所需分析页面中的 `<head>` 和 `</head>` 标签之间即可。安装成功后，除 localhost 和 IP 地址外，所有网址下的行为数据都将会被收集

### 2.标签自动采集规范实例

#### 2.1 点击事件
```html
<body>
   <span dc="{tag:'reset',fm:'beha','key1':'key1','key2':'key2'}">重置</span>
</body>
```

#### 2.2 输入框光标文本采集
```html
<body>
   <input dc="{tag:'input2',fm:'blur'}"/>
</body>


需要为需要统计埋点的`dom`元素上增加`dc`属性(JSON)
- `tag`为模块的名称(必选)，字符长度最好限制在10个字符内
- `fm`为统计类型（必须），`beha|href|blur`,`beha`为交互点击，`href`为跳转点击，`blur`为输入框光标离开
- `key1|key2`为`自定义属性`(格式为`key:value`可选,数量不限)

### 注意事项
- 尽量不要阻止冒泡，如果需要请`手动发送日志`
```javascript
document.getElementById('clickDom').onclick = function (ev) {
   alert(3);
   window.__MisLog(this);
   ev.stopPropagation();
}
```
