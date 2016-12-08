## css-demo 5/6/2016 10:51:06 AM 

### demo3：

	<div class="demo3">
		<div class="col-1"></div>
		<div class="col-2"></div>
	</div>


##### 3-1. 两栏等宽布局（三栏等宽同理）

![demo3-1](https://github.com/RukiQ/css-demo/blob/master/img/demo3-1.png?raw=true)
![demo3-2](https://github.com/RukiQ/css-demo/blob/master/img/demo3-2.png?raw=true)

>**方案一**： `float` 布局

	.col-1, .col-2 {
		width: 50%;	// 各占一半，尺寸相同
		float: left; // 都脱离文档流
	}

 *要想中间留有空隙，可以给两栏分别加上左右边框，但：`box-sizing:border-box;`

![demo3-3](https://github.com/RukiQ/css-demo/blob/master/img/demo3-3.png?raw=true)
	
> **方案二**：`inline-block`（不推荐）

> *元素间有换行符间隙问题，解决方法：`font-size:0;`

> 参考：[去除inline-block元素间间距的N种方法](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

	.demo3 {
		font-size: 0;	// font-size 使水平方向重叠，line-height 使垂直方向重叠
		.col-1, .col-2 {
			display: inline-block;
			width: 50%;
		}
	}

> **方案三**：`flex` 布局

> 中间通过边框留空隙也不会挤下去

	.demo3 {
		display: felx;
		display: -webkit-flex;
		.col-1, .col-2 {
			flex: 1;
			-webkit-flex: 1;
			width: 50%;
		}
	}
	
##### 3-2. 两栏布局，左边固定，右边自适应

![demo3-4](https://github.com/RukiQ/css-demo/blob/master/img/demo3-4.png?raw=true)

> **方案一**：`float` 布局

	.demo3 {
		.col-1 {
			width: 150px;
			float: left;	// 脱离文档流
		}
		.col-2 {
			// 不需要设置 margin-left, float会形成包围文字效果，虽然col-2的左边部分被col-1覆盖
		}
	}

![demo3-4(1)](https://github.com/RukiQ/css-demo/blob/master/img/demo3-4(1).png?raw=true)

如果设置 `margin-left: 170px;` 则 col-2 会向右偏移:

![demo3-4-add](https://github.com/RukiQ/css-demo/blob/master/img/demo3-4-add.png?raw=true)

给 col-2 添加 `overflow: hidden;`，则不需要设置 `margin-left`，自动偏右：

![demo3-4(2)](https://github.com/RukiQ/css-demo/blob/master/img/demo3-4(2).png?raw=true)

> **方案二**： `position: absolute;` 左边元素相对于父元素绝对定位

> *`float` 和 `position:absolute;` 都脱离文档流

![demo3-5](https://github.com/RukiQ/css-demo/blob/master/img/demo3-5.png?raw=true)

	.demo3 {
		position: relative;	// 定位父元素

		.col-1 {
			width: 150px;
			position: absolute;	// 脱离文档流
		}
		.col-2 {
			margin-left: 150px;	// absolute不会形成文字环绕效果，因此col-2会向上浮,
								// 左边部分（包括文字）会隐藏在col-1下面，需要设置 margin-left
		}
	}

若 col-2 不设置 `margin-left`:

![demo3-5(1)](https://github.com/RukiQ/css-demo/blob/master/img/demo3-5(1).png?raw=true)

设置 `margin-left` 后：

![demo3-5(2)](https://github.com/RukiQ/css-demo/blob/master/img/demo3-5(2).png?raw=true)

注意：这种情况下，对 col-2 使用 `overflow: hidden` 不起作用，只能通过偏移量来进行定位

> **方案三**： `flex` 布局

	.demo3 {
		display: flex;
		display: -webkit-flex;

		.col-1 {
			width: 150px;
		}
		.col-2 {
			flex: 1;	// flex:1; 自动撑满剩余宽度
			-webkit-flex: 1;
		}
	}

### demo4：综合

##### 4-1. 左边多行文字（宽度自适应），右边图标（固定宽度）

![demo4-1](https://github.com/RukiQ/css-demo/blob/master/img/demo4-1.png?raw=true)

	<div class="demo4-1">
		<div class="col-left">
			<h1>大标题</h1>
			<h2>小标题</h2>
		</div>
		<div class="col-right"></div>
	</div>

> **实现**（移动端，`flex` 布局）：

	.demo4-1 {
		display: flex;
		display: -webkit-flex;

		.col-left {	// 宽度自适应
			flex: 1;
			-webkit-flex: 1;
		}
		.col-right {
			width: 100px;	// 设定宽度 
			position: relative;	// 定位父元素

			&:after {
				position: absolute;	// 相对于父元素绝对定位
				content: "";
				display: inline-block;
				width: 50px;
				height: 50px;
				border-right: 2px solid #0f0;
				border-bottom: 2px solid #0f0;
				transform: rotate(-45deg);
				top: 40px;
				right: 40px;
			}
		}
	}


##### 4-2. 左边图片（宽度固定），中间多行文字（宽度自适应），右边图标（宽度固定）

![demo4-2](https://github.com/RukiQ/css-demo/blob/master/img/demo4-2.png?raw=true)

	<div class="demo4-2">
		<div class="col-left">
			
		</div>
		<div class="col-middle">
			<h1>大标题</h1>
			<h2>小标题</h2>
		</div>
		<div class="col-right">
			
		</div>
	</div>

> **实现**（移动端，`flex` 布局）：

	.demo4-2 {
		display: flex;
		display: -webkit-flex;

		.col-left {
			width: 200px;	// 设定宽度
			background: url(../img/logo.png) no-repeat;
			background-size: 100px 100px;
			background-position: center center;	// 定位图片位置
		}
		.col-middle {
			flex: 1;
			-webkit-flex: 1;
		}
		.col-right {
			width: 100px;	// 设定宽度 
			position: relative;	// 定位父元素

			&:after {
				position: absolute;	// 相对于父元素绝对定位
				content: "";
				display: inline-block;
				width: 50px;
				height: 50px;
				border-right: 2px solid #0f0;
				border-bottom: 2px solid #0f0;
				transform: rotate(-45deg);
				top: 40px;
				right: 40px;
			}
		}
	}

### demo5：父元素包含子元素，子元素垂直居中布局

![demo4-3](https://github.com/RukiQ/css-demo/blob/master/img/demo4-3.png?raw=true)

	<div class="demo5">
		<div class="child">A</div>
	</div>

##### 5-1. 子元素 A 宽高已知，相对于父元素水平垂直居中

> **方案一**：`position: absolute` 布局

> *基于自身高度/宽度偏移的缺点：若宽度/高度改变，则偏移会改变，不会持续保持居中
	 
	.demo5 {
		width: $px;
		height: $px;

		position: relative;	// 定位父元素

		.child {
			width: 400px;
			height: 50px;

			position: absolute;	// 相对于父元素定位
	    	top: 50%;	// 使用百分比定位
	   		left: 50%;	// 使用百分比定位
	    	margin-top: -25px;	 // 向上偏移自身高度的一半
	    	margin-left: -250px;	 // 向左偏移自身宽度的一半
		}
	}

##### 5-2. 子元素 A 宽高未知，相对于父元素水平垂直居中

> **方案二**：`position: absolute` 布局

	.demo5 {
		width: $px;
		height: $px;

		position: relative;	// 定位父元素

		.child {
			width: $px;
			height: $px;

			position: absolute;	// 相对于父元素定位
			margin: auto;	// 上下左右margin都自适应
			top: 0;
			bottom: 0;
			left: 0;
			right: 0;
		}
	}

> **方案三**：`position: absolute` + `CSS3` 布局

	.demo5 {
		width: $px;
		height: $px;

		position: relative;	// 定位父元素

		.child {
			width: $px;
			height: $px;

			position: absolute;	// 相对于父元素定位
			top: 50%;	// 使用百分比定位
			left: 50%;	// 使用百分比定位
			transform: translate(-50%, -50%);	// 向X轴/Y轴偏移自身宽度/高度的一半
			-webkit-transform: translate(-50%, -50%);
		}
	}

> **方案四**：`position: relative` + `CSS3` 布局

	.demo5 {
		width: $px;
		height: $px;

		.child {
			width: $px;
			height: $px;

			position: relative;	// 相对于父元素定位
			top: 50%;	// 使用百分比定位
			left: 50%;	// 使用百分比定位
			transform: translate(-50%, -50%);	// 向X轴/Y轴偏移自身宽度/高度的一半
			-webkit-transform: translate(-50%, -50%);
		}
