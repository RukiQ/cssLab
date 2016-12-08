## css-demo（html和body）5/24/2016 2:12:54 PM 

### 1.背景色

当不设置html的时候，html的属性不生效，浏览器会捕获body的颜色作为浏览器背景颜色，如果html生效了，则会捕获html的颜色作为浏览器背景颜色。

<span style="color:#ac4a4a">[例1：不设置 `html`]</span>

	body {
		background-color: #069;
		margin: 50px;
		border: 30px solid #093;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex1-new.png?raw=true">

<span style="color:#ac4a4a">[例2：设置 `html`]</span>

	html {	// 设置 html 样式
		background: #999;
		margin: 50px;
		border: 30px solid #053;
	}
	
	body {
		background-color: #069;
		margin: 50px;
		border: 30px solid #093;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex2.png?raw=true">

### 2.margin

<span style="color:#ac4a4a">[例3：去掉前面例子中设置的 `margin`]</span>

	html {
		background: #999;
		border: 30px solid #053;
	}
	
	body {
		background-color: #069;
		border: 30px solid #093;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex3-1.png?raw=true">

##### `html` 与 `浏览器` 之间：默认没有 `margin`

##### `html` 与 `body` 之间：默认有 `margin`

<span style="color:#ac4a4a">[例4：设置 `body { margin: 0; }` ——> 会使 `html` 与 `body` 之间的 `margin` 消失]</span>

	html {
		background: #999;
		border: 30px solid #053;
	}
	
	body {
		background-color: #069;
		border: 30px solid #093;
		margin: 0;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex3-2.png?raw=true">

### 3.宽和高

> [张鑫旭-鑫空间-鑫生活：对html与body的一些研究与理解](http://www.zhangxinxu.com/wordpress/2009/09/%E5%AF%B9html%E4%B8%8Ebody%E7%9A%84%E4%B8%80%E4%BA%9B%E7%A0%94%E7%A9%B6%E4%B8%8E%E7%90%86%E8%A7%A3/)：
> 
> 要想高度百分比起作用，一般来说，要满足两个条件：
> 
> - 其一，父标签有高度可寻，就是向上遍历父标签要找到一个定值高度（body，html另外讨论），如果中途有个height为auto或是没有设置height属性，则高度百分比不起作用；
> 
> - 其二，标签本身的属性，如果inline属性的标签，如果没有浮动，zoom，或是绝对定位之类属性是不支持百分比高度的，block或inline-block属性可以说是高度百分比起作用的前提条件之一吧。
>
> 默认状态下，body不是高度100%显示的
>

`html` 和 `body` 的<span style="color:red">默认高度</span>都为0；<span style="color:red">默认宽度</span>遵照 `div` 元素，自动撑满整个容器。


> 如果不设置 `html` 和 `body` 的 `box-sizing: border-box`，边框的存在会让浏览器产生滚动条（如果 `width` 和 `height` 都设置了 100% 的话，横竖都会产生滚动条）

<span style="color:#ac4a4a">[例5：同时设置 `html` 和 `body` 宽和高为100%]</span>

	html {
		background: #999;
		border: 30px solid #053;
		// box-sizing: border-box;
		width: 100%;
		height: 100%;
	}
	
	body {
		background-color: #069;
		border: 30px solid #093;
		// box-sizing: border-box;
		width: 100%;
		height: 100%;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex4.png?raw=true">

- 只设置 `body` 的高为100%，不起作用，因为父元素高度为0；
- 横向（竖向）滚动条的产生：`html` 和 `body` 都等于浏览器宽度（高度），但是边框又使盒模型更大了，一方面 `html` 会挤出去，`body` 的向右（向下）偏移又会增加一定的距离。

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex5.png?raw=true">

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex5-h.png?raw=true">

	html {
		background: #999;
		border: 30px solid #053;
		// box-sizing: border-box;
		width: 100%;
		height: 100%;
	}
	
	body {
		background-color: #069;
		border: 30px solid #093;
		// box-sizing: border-box;
		width: 100%;
		height: 100%;
	}

<img width="600" height="450" src="https://github.com/RukiQ/css-demo/blob/master/demo6/img/ex6.png?raw=true">

如果 `html` 不设置边框，则浏览器滚动条的产生是由 `body` 与 `html` 之间的 `margin` 造成的。同样，设置 `body { margin: 0; }` ——> 会使浏览器滚动条消失
