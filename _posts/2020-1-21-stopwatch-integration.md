---
title: Stopwatch Integration
tags: [site]
---

## Stopwatch Integration

Simple stopwatch Integration. Located at right of the article :)

<!--more-->

### Includes

- Hide/Unhide the timer
- Start the timer
- Stop the timer
- Reset the timer
- Embed in article.html

### Files associated

- /_include/aside/stopwatch.html
- /_layout/page.html
- /_sass/stopwatch.css
- /assets/css/main.scss

### stopwatch.html

```html
<div class="stopwatch-wrapper">
	<div>Read Timer</div>
	<input type="radio" name="controls" id="start">
	<input type="radio" name="controls" id="stop">
	<input type="radio" name="controls" id="reset">
	<input type="checkbox" name="controls" id="hide">
	<div class="stopwatch">
		<div class="cell">
			<span class="num ten ten_hour">0 1 2 3 4 5 6 7 8 9</span>
		</div>
		<div class="cell">
			<span class="num ten hour">0 1 2 3 4 5 6 7 8 9</span>
		</div>
		<div class="cell">
			<span class="num">:</span>
		</div>
		<div class="cell">
			<span class="num sex ten_minu">0 1 2 3 4 5</span>
		</div>
		<div class="cell">
			<span class="num ten minu">0 1 2 3 4 5 6 7 8 9</span>
		</div>
		<div class="cell">
			<span class="num">:</span>
		</div>
		<div class="cell">
			<span class="num sex ten_sec">0 1 2 3 4 5</span>
		</div>
		<div class="cell">
			<span class="num ten sec">0 1 2 3 4 5 6 7 8 9</span>
		</div>
	</div>
	<div class="control">
		<label for="hide" class="fa fa-times"></label>
		<label for="start" class="fa fa-play"></label>
		<label for="stop" class="fa fa-pause"></label>
		<label for="reset" class="fa fa-stop"></label>
	</div>
</div>
```

### page.html

line 190:

`include aside/stopwatch.html`

### stopwatch.css

```css
.stopwatch-wrapper{
  padding-left: 48px;
}
.stopwatch-wrapper input[type="radio"]{
  display:none;}
.stopwatch-wrapper input[type="checkbox"]{
	display:none;
}
.stopwatch .cell{
	width: 10px;
	height: 20px;
	text-align: center;
	overflow: hidden;
	display: inline-block;
}
.stopwatch .cell .num {
	line-height: 20px;
	color: #444;
	display: block;
	-webkit-animation-play-state: paused;
	animation-play-state: paused;
}
.control {
  text-align: left;
}
.control label {
	display: inline-block;
	cursor: pointer;
}


.ten{
	-webkit-animation-name: ten;
	animation-name: ten;
	-webkit-animation-timing-function: steps(10);
	animation-timing-function: steps(10);
	-webkit-animation-iteration-count: infinite;
	animation-iteration-count: infinite;
}
@-webkit-keyframes ten {
	0%{margin-top: 0;}
	100%{margin-top: -200px;}
}
@keyframes ten {
	0%{margin-top: 0;}
	100%{margin-top: -200px;}
}
.sex{
	-webkit-animation-name: sex;
	animation-name: sex;
	-webkit-animation-timing-function: steps(6);
	animation-timing-function: steps(6);
	-webkit-animation-iteration-count: infinite;
	animation-iteration-count: infinite;
}
@-webkit-keyframes sex {
	0%{margin-top: 0;}
	100%{margin-top: -120px;}
}
@keyframes sex {
	0%{margin-top: 0;}
	100%{margin-top: -120px;}
}

.mill {
	-webkit-animation-duration: 0.01s;
	animation-duration: 0.01s;
}
.ten_mill {
	-webkit-animation-duration: 0.1s;
	animation-duration: 0.1s;
}
.hund_mill {
	-webkit-animation-duration: 1s;
	animation-duration: 1s;
}
.sec {
	-webkit-animation-duration: 10s;
	animation-duration: 10s;
}
.ten_sec {
	-webkit-animation-duration: 60s;
	animation-duration: 60s;
}
.minu {
	-webkit-animation-duration: 600s;
	animation-duration: 600s;
}
.ten_minu {
	-webkit-animation-duration: 3600s;
	animation-duration: 3600s;
}
.hour {
	-webkit-animation-duration: 36000s;
	animation-duration: 36000s;
}
.ten_hour {
	-webkit-animation-duration: 360000;
	animation-duration: 360000;
}

	#start:checked~.stopwatch .num{
	-webkit-animation-play-state: running;
	animation-play-state: running;
}
	#stop:checked~.stopwatch .num{
	-webkit-animation-play-state: paused;
	animation-play-state: paused;
}
	#reset:checked~.stopwatch .num{
	-webkit-animatione: none;
	-webkit-animation: none;
	        animation: none;
}
	#hide:checked~.stopwatch .num{
	visibility: hidden;
}
```

### main.scss

line 74: `"stopwatch"`
