kiwi-hello
==========

Hello World for Kiwi Move; get raw data in with your device ID and password!

You can use this test panel to view, record, save and analyze streaming sensor data
We are working on additional features that will make it easy for you to train classification algorithms
To confirm that your Kiwi is setup and working correctly:
Check that the light on your Kiwi is blinking, and
Check that the live graphs in the Kiwi Test Panel are streaming sensor data (accelerometer, gyroscope)

```javascript
//script src="http://build.kiwiwearables.com:8080/socket.js/socket.io.js"
				
var socket = io.connect('http://build.kiwiwearables.com:8080')

socket.on('connect', function() {
	socket.emit('listen', {device_id: 'your device ID', password: 'your password'});
});

socket.on('listen_response', function(data) {
	
	var kiwi_data = JSON.parse(data.message);
		console.log(kiwi_data);   // Kiwi sensor data is a JSON object
	
		var packet_type = kiwi_data.packet_type;  

		// Capture accelerometer and gyroscope data, or tap motion events
		// 00 = raw sensor data 
		// 03 = motion events
	
	var acceleration_x = kiwi_data.ax;
			var acceleration_y = kiwi_data.ay;
			var acceleration_z = kiwi_data.az;
});  
```
