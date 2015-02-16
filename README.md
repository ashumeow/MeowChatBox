<b>MeowChatBox</b> is a WebRTC one-to-one chat application. <br>
It is currently 100% working in Firefox, but it's partially working in Chrome and it never works in IE. <br>
<br>
<b>Running the application:- </b><br>
In a Firefox browser, run <code>chat.html</code> <br>
<code>chat.css</code> is mainly for stylesheet. <br>
<code>chat.js</code> is the script that runs the application. <br>
<code>process.php</code> is the background process that runs behind the script <code>chat.js</code>. <br>
<br>
<b>Explanation</b> <br>
1. <code>chat.js</code> <br>
(a) For sending the message
```js
msg=document.getElementById("msg").value;
chatZone.innerHTML+='<div class="chatmsg"><b>'+name+'</b>: '+msg+'<br/></div>';
oldata='<div class="chatmsg"><b>'+name+'</b>: '+msg+'<br/></div>';          
this.ajaxSent();
```
(b) Sending message to server
```js
xhr=new XMLHttpRequest();
```
```js
xhr.open('GET','process.php?msg='+msg+'&name='+name,false);
```
(c) SSE initialization (initializing the <code>process.php</code>)
```js
sevr = new EventSource('process.php');
```
(d) Creating a new object
```js
var chat= new ChatEngine();
```
<br>
2. <code>process.php</code>
```php
  echo "data: $msg" . PHP_EOL;
  ob_flush();
  flush();
```
