###Eson简单日历控件
用于web的简单日历控件，支持单选，多选，自定义控件数量，自定义星期显示，自定义工作日的第一天，自定义日期格式，表单自动绑定。
不依赖于任何前端框架。
基于09年以前一个叫UANV或ESONCalendar的日历控件制作，代码已大部分重写。
<a href="http://www.thinkasp.cn/" target="_blank">http://www.thinkasp.cn/</a>

####单选
#####参数
```js
Eson('calendar', {
	//初始日期，默认为当前日期
	date : new Date(),
	//一周的第一天，默认为星期日。可选。
	first_week_day : 0,
	//星期的显示文本，weeks : ['Sun', 'Mon', 'Tues', 'Wed', 'Thur', 'Fri', 'Sat']。可选。
	weeks : "日一二三四五六", 
	//日期选择事件，this引用为选择的日期对象，参数分别为年、月、日。
	//如果不定义，并且绑定的文本框，则直接将值赋值给文本框。
	onselect : function(y,m,d){
		get("result").innerHTML = y + "-" + m + "-" + d;
	},
	//日期格式，未定义onselect时有效。可选yyyy/MM/M/dd/d/H/HH/h/hh/mm/m/ss/s组合。
	format : ""
});
```
#####绑定到DIV容器#####
```html
<p id="result"></p>
<div id="calendar"></div>
```
```js
Eson('calendar', {
	first_week_day : 1,
	weeks : "一二三四五六日",
	onselect : function(y,m,d){
		get("result").innerHTML = y + "-" + m + "-" + d;
	}
});
```
#####绑定文本框（文本框获得焦点时弹出）#####
```html
<input id="inputtext" type="text" value="2009-9-3" />
```
```js
Eson('inputtext', {
	onselect : function(y,m,d){
		set_val("inputtext", y + "-" + m + "-" + d);
	}
});
//或
Eson('inputtext');
```
#####绑定任一元素#####
```html
<input id="inputtext2" type="text" value="" readonly="readonly" />
<a id="selectdate" style="cursor: pointer; color: red;">选择日期</a>
```
```js
Eson('selectdate', {
	date : "2012-3-24",
	onselect : function(y,m,d){
		set_val("inputtext2", y + "-" + m + "-" + d);
	}
});
```
####多选####
#####同月单控件#####
```html
<input id="inputtext_m" type="text" size="50" value="2009-9-3,2009-9-5,2009-9-23" />
```
```js
Eson('inputtext_m', {
	multi_select : true
});
```
#####不同月多控件#####
```html
<input id="inputtext_n" type="text" size="50" value="2009-9-3,2009-10-5,2011-9-23" />
```
```js
Eson('inputtext_n', {
	multi_select : true
});
```
#####不同月强制单控件#####
```html
<input id="inputtext_j" type="text" size="50" value="2009-9-3,2009-10-5,2011-9-23" />
```
```js
Eson('inputtext_j', {
	multi_select : true,
	multi : false
});
```
#####不同月多控件，限制最多控件个数#####
```html
<input id="inputtext_i" type="text" size="50" value="2009-9-3,2009-10-5,2011-9-23,2011-9-24,2011-10-24" />
```
```js
Eson('inputtext_i', {
	multi_select : true,
	max_count : 3
});
```