## css-demo（左边固定，右边自适应） 5/11/2016 3:09:05 PM 

### demo3：
	
	<body>
		<div class="sidebar"></div>
		<div class="main"></div>
	</body>

css:

	// html 和 body 的高度默认为0，因此要先设置为100%，并且清除默认样式（margin:0; padding:0）
	html,body {
		width: 100%;
		height: 100%;
		margin: 0;
		padding: 0;
	}

	.sidebar {
		width: 200px;
		height: 100%;	// 撑满整个页面高度
		background: orange;
		float: left;	// 左边浮动
	}

	.main {
		background: green;
		height: 100%;	// 撑满整个页面高度
		margin-left: 200px;	//距左边距200px
	}

> 如果浮动非替换元素，则要<span style="background:yellow">指明一个明确的宽度</span>；否则，它们会尽可能地窄。

> **注释**：假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。

### 实现效果：

![demo-7](https://github.com/RukiQ/css-demo/blob/master/img/demo7.png?raw=true)