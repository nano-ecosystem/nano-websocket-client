# nano-websocket-client
nano javascript WebSocket client SDK

## API

### Connect to server

```javascript
nano.init(params, callback);
```

Examples

```javascript
nano.init({
    host: host,
    port: port,
	user: {},
	handshakeCallback : function(){}
}, function() {
	console.log('success');
});
```

### Send request to server with callback

```javascript
nano.request(route, msg, callback);
```

Examples

```javascript
nano.request(route, {
	rid: rid
}, function(data) {
	console.log(dta);	
});
```

### Send request to server without callback

```javascript
nano.notify(route, params);
```

### Receive message from server

```javascript
nano.on(route, callback); 
```

Examples

```javascript
nano.on('onChat', function(data) {
	addMessage(data.from, data.target, data.msg);
	$("#chatHistory").show();
});
```

### Disconnect from server

```javascript
nano.disconnect();
```

## Usage

```html
<!DOCTYPE html/>
<html>
<head>
	<title>nano WebSocket Test Page</title>
</head>
<body>
<script src="./protocol.js"></script>
<script src="./nano-websocket-client.js"></script>
<script type="text/javascript">

var nano = window.nano

nano.init({host: "127.0.0.1", port: 3250, log: true}, function(){
	nano.request("gate.Handler.Login", {"name":"chrislonng", "age":10000}, function(data){
		console.log(data);
	});

	nano.request("gate.Handler.Signup", {"name":"Signup chrislonng", "age":10000}, function(data){
		console.log(data);
	});

	nano.on("notify", function(data){
		console.log(data);
	});
});

</script>
</body>
</html>
```



## License

[MIT License](./LICENSE)