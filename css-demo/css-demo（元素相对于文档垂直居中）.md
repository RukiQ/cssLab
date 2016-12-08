## css-demo（元素相对于文档居中） 5/11/2016 3:09:05 PM 

	<body>
		<div class="content"></div>
	</body>

> **实现一**：margin + 相对定位（relative)

	// html 和 body 的高度默认为0，因此要先设置为100%，并且清除默认样式（margin:0; padding:0）
	html, body {
		width: 100%;	
		height: 100%;
		margin: 0;
		padding: 0;
	}

	.content {
		width: 200px;
		height: 200px;
		background: #0f0;
		
		margin: 0 auto;	// 水平居中
		position: relative;	// 相对于自身静态位置进行定位
		top: 50%;	// 向下偏移 body 高度的50%
		transform: translateY(-50%); // 向上偏移自身高度的 50%
	}

> **实现二**：不使用 margin，只用相对定位（relative)

	// html 和 body 的高度默认为0，因此要先设置为100%，并且清除默认样式（margin:0; padding:0）
	html, body {
		width: 100%;	
		height: 100%;
		margin: 0;
		padding: 0;
	}

	.content {
		width: 200px;
		height: 200px;
		background: #0f0;
		
		position: relative;	// 相对于自身静态位置进行定位
		top: 50%;	// 向下偏移 body 高度的50%
		left: 50%;	// 向左偏移 body 宽度的50%
		transform: translate(-50%, -50%); // 向上/左偏移自身高度/宽度的 50%
	}

> **注意**，实现二中的 transform 不能分开写，类似于下面这样，这样后写的 transform 会覆盖先写的，将导致只能实现一处偏移。

	top: 50%;
	left: 50%;
	transform: translateX(-50%);
	transform: translateY(-50%);



### 实现

![demo-6](https://github.com/RukiQ/css-demo/blob/master/img/demo6-new.png?raw=true)