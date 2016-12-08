## css-demo 5/5/2016 17:30:12 PM

### demo1：文字水平垂直居中

![demo1](https://github.com/RukiQ/css-demo/blob/master/img/demo1.png?raw=true)

	<div class="demo1">
		标题1111
	</div>

>**方案一**：普通布局
	
	.demo1 {
		text-align: center;	//水平居中
		line-height: $height; //垂直居中
	}

> **方案二**：`flex` 布局

	.demo1 {
		display: flex;
		display: -webkit-flex;
		justify-content: center; //水平居中
		align-items: center; //垂直居中
	}

> **方案三**：`box` 布局（2009年语法，`flex` 的前身）

	.demo1 {
		display: box;
		display: -webkit-box;
		-webkit-box-pack:center; //水平居中
		-webkit-box-align:center; //垂直居中
	}


### demo2：带图片和文字的布局

##### (1) 图片+文字+居中

![demo2-1](https://github.com/RukiQ/css-demo/blob/master/img/demo2-1.png?raw=true)

> **方案一**：`img` + 文字

	<div class="demo2-1">
		<img src="" alt="logo">标题1111
	</div>

> 普通布局

	.demo2-1 {
		// 文字可用demo1中的方案一布局;
		line-height: $px;
		text-align: center;

		img {
			width: $px;	// 设置图片宽和高
			height: $px;
			position:relative;
			top: $px;	// 相对于父元素，text-align: center 只会把文字居中，图片还是置顶
			right: $px;	// 相对于文字靠左偏移（其实relative是相对于自身本来的位置进行定位）
		}
	}

> **方案二**：`span` + 文字

	<div class="demo2-2">
		<span></span>标题2222
	</div>

> `flex` 布局

> *`align-items` 会把图片也垂直居中，而 `line-height` 只会把文字居中

	.demo2-2 {
		// 文字可用demo1中的方案二布局;
		display: flex;	
		display: -webkit-flex;
		justify-content: center;
		align-items: center;

		span {
			display: inline-block;	// 使span为块级元素，才可以设置宽和高
			width: $px;
			height: $px;
			background: url();
			background-size: 100% 100%; // 图片填充整个span，同 background-size: cover;
			margin-right: 5px;     // 距右边文字距离
		}
	}
	

> **方案三**：文字包含在 `span` 中

	<div class="demo2-3">
		<span>标题3333</span>
	</div>

> 普通布局

	.demo2-3 {
		// 文字可用demo1中的方案一布局;
		line-height: $px;
		text-align: center;

		span {
			display: inline-block;	// 设置为块级元素
			background: url() no-repeat; // no-repeat: 图片全部填充
			background-size: 30px 30px; // 设置背景图片的大小
			background-position: center left; // 第一个参数垂直布局，第二个参数水平布局
			padding-left: 35px;	// 距最左边距离，而非距图片距离
		}
	}


##### (2) 左右箭头+文字

![demo2-2](https://github.com/RukiQ/css-demo/blob/master/img/demo2-2.png?raw=true)

> **方案**：

	<div class="demo2-4">
		标题3333
	</div>

> 箭头可以用 `::after` 和 `::before` 伪类实现

> 相对于父元素绝对定位
	
	.demo2-4 {
		// 文字可用demo1中的方案一布局;
		text-align: center;
		line-height: $px;
		
		position: relative;	// 定位父元素
		
		&:after {
			content: "";	// 内容为空
			display: inline-block;	// 设置为块级元素，从而设定宽和高
			width: $px;
			height: $px;
			border-right: 1px solid #00f;
			border-bottom: 1px solid #00f;
			transform: rotate(-45deg);

			position: absolute;	// 相对父元素绝对定位
			top: $px;
			right: $px;
		}
	}


	 

