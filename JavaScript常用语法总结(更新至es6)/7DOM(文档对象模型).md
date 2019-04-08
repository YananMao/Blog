# DOM(文档对象模型)

获取一个html页面中body中的node：

```
<body>
	<div class="maomao">
		<p>hiahia</p>
		hiaha
	</div>
	<script type="text/javascript" src="test.js"></script>
</body>
```

```
let map = [];
function dfs(elem) {
	if(elem) {
		map.push({
			nodeType: elem.nodeType,
			nodeName: elem.nodeName,
			nodeValue: elem.nodeValue,
			childNodes: elem.childNodes,
			parentNode: elem.parentNode,
			previousSibling: elem.previousSibling,
			nextSibling: elem.nextSibling,
			
		})
	}
	for(let i=0,len=elem.childNodes.length;i<len;i++) {
		dfs(elem.childNodes[i])
	}
}
dfs(document.body);
console.log(map);
```

![7.0](https://github.com/YananMao/JavaScript-Grammars/blob/master/pictures/7.0.png)