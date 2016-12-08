## css-demo-checkbox 5/14/2016 9:31:13 AM 

![cb1](https://github.com/RukiQ/css-demo/blob/master/img/cb1.png?raw=true)

	<div class="wrap">
		<label>性别：</label>

		<div class="cb-wrap">	<!-- 整体为一个checkbox，用div包裹 -->
			<input type="radio" name="sex1" value="男"></input>   <!-- 需要隐藏，置于最上层 -->
			<span class="cb-icon"></span>	<!-- 加伪元素，模拟checkbox样式 -->
			<span class="cb-label">男</span>		<!-- 当选中时，字体颜色也得改变 -->
		</div>

		<div class="cb-wrap">
			<input type="radio" name="sex1" value="女"></input>
			<span class="cb-icon"></span>
			<span class="cb-label">女</span>
		</div>

	</div>

**css实现：**

	.wrap {
		label {
			display: inline-block;
			width: 50px;
			text-align: right;
			margin-right: 15px;
		}
	}
	
	.cb-wrap {
		display: inline-block;	// 将div元素设置成行内元素，不然尽管设置的宽度较小，还是会占据一行
	
		width: 50px;
		height: 30px;
		margin-right: 15px;
		line-height: 30px;

		position: relative;	// 设置定位
	
		input {
			opacity: 0;	// 设置透明度为0
			width: 100%; // 设置宽度为一个checkbox（.cb-wrap）的宽度
			height: 100%;
			z-index: 2;	// 置于最上层
			position: absolute;	// 相对于.cb-wrap定位
			top: 0;
			left: 0;
		}
	
		// 用伪类:checked，实现checkbox选中状态时改变其它元素样式
		input:checked + span {	// 用“相邻兄弟选择器”，改变模拟checkbox的颜色
			background: red;
		}
	
		input:checked ~ .cb-label {	// 用“同级元素通用选择器”，改变字体的颜色
			color: red;
		}
	
		.cb-icon {	// 实现模拟checkbox
			display: inline-block;	// span设宽，必须得设置成块级元素！
			width: 16px;
			height: 16px;
			border: 1px solid #ddd;
			border-radius: 8px;
			position: relative;	// 相对于自身原来的位置定位，使其与字体对齐
			top: 3px;
	
			&:after {	// 伪元素实现对勾（√）部分
				content: "";
				display: inline-block;
				width: 9px;
				height: 6px;
				border-left: 1px solid #fff;
				border-bottom: 1px solid #fff;
				transform: rotate(-45deg);
				position: absolute;
				top: 3px;
				right: 3px;
			}
		}
	}

---

![cb2](https://github.com/RukiQ/css-demo/blob/master/img/cb2.png?raw=true)

###### （示例2相对实例1较为简单，不需要用为元素实现模拟的checkbox，也少了一个`span`元素，区别在于`cb-icon`的实现不同）

	<div class="wrap">
		<label>性别：</label>

		<div class="cb-wrap">
			<input type="radio" name="sex2" value="男"></input>
			<span class="cb-icon">男</span>
		</div>

		<div class="cb-wrap">
			<input type="radio" name="sex2" value="女"></input>
			<span class="cb-icon">女</span>
		</div>

	</div>

**css实现：**

	.cb-wrap {
		display: inline-block;
	
		width: 50px;
		height: 30px;
		margin-right: 15px;
		line-height: 30px;
		position: relative;
	
		input {
			opacity: 0;
			width: 100%;
			height: 100%;
			z-index: 2;
			position: absolute;
			top: 0;
			left: 0;
		}
	
		input:checked + span {
			background: orange;
			color: #fff;
		}
	
		.cb-icon {
			display: inline-block;
			width: 50px;
			height: 25px;
			border: 1px solid #ddd;
			text-align: center;
			line-height: 25px;
		}
	}

<br>