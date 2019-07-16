一个比赛项目的前端展示页面，实现图片轮播的简单效果。

**技术Tips**

1. HTML + CSS + JS
2. jQuery、AJAX、JSON、PHP



**功能概述**

设计网页结构，CSS样式，以及逻辑功能, 实现按钮点击触发图片自动轮播效果。jQuery实现图片轮播功能底层逻辑，使用AJAX实现与服务器交换数据，异步更新部分网页内容。使用PHP实现伪后台获取更新数据。



**项目收获**

了解熟悉了AJAX技术的工作原理和基本构建流程：

```html
<script >
	//1.建立xmlHttpRequest对象
	//2.使用OPEN方法与服务器建立连接此步注意设置http的请求方式（post/get）
	//3.设置回调函数，在回调函数中针对不同的响应状态进行处理
	//4.向服务器端发送数据， 如果是POST方式就不为空

	// 可以简写为 var xmlHttp = new XMLHttpRequest();
	if(window.XMLHttpRequest) {
		// 建立xmlHttpRequest对象
		var xmlHttp = new XMLHttpRequest();
		if(xmlHttp.overrideMimeType) {
			xmlHttp.overrideMimeType("text/xml");
		}
	   }
    else if(window.ActiveXobject) {
		var activeName = ["MSXML2.XMLHTTP", "Microsoft.XMLHTTP"];
		for(var i = 0; i < activeName.length; i++) {
			try {
			  xmlHttp = new ActiveXobject(activeName[i]);
			  break;
			 } catch(e) {}
			}
	   }
	   if(!xmlHttp) {
		alert("创建xmlhttprequest对象失败");
	   }
	else {}
		
	// 如果是POST方式，注意设置请求头信息, GET方式可以不设置
	// xmlHttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded")
	xmlHttp.open("get","getData.php?name="+ name,true)
		
	// 设置回调函数
	xmlHttp.onreadystatechange= callback;
	function callback(){
	if(xmlHttp.readyState == 4 && xmlHttp.status == 200){      
		//判断交互是否成功获取服务器返回的数据 
		var responseText =xmlHttp.responseText;
		document.getElementById("info").innerHTML = responseText;
	   }
	}
	//向服务器端发送数据
	xmlHttp.send(null);
</script>
```

