kiwi-hello
==========

Hello World for Kiwi Move; get raw data in with your device ID and password!

Step 1. Set up your wi-fi hotspot

Set the SSID of your wi-fi network to be kiwimoveID, where ID is your Kiwi Device ID
Set the security on your wi-fi network to Open
The easiest way to do this is to set up a portable wi-fi hotspot on your mobile phone
Note: This setup process will change in the next software upgrade which will allow you to connect your Kiwi to a secure network of your choice using the Kiwi mobile app.

Step 2. Plug the battery into the Kiwi

Step 3. Log-in to the Kiwi Test Panel

You can use this test panel to view, record, save and analyze streaming sensor data
We are working on additional features that will make it easy for you to train classification algorithms
To confirm that your Kiwi is setup and working correctly:
Check that the light on your Kiwi is blinking, and
Check that the live graphs in the Kiwi Test Panel are streaming sensor data (accelerometer, gyroscope)

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