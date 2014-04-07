kiwi-hello
==========

Hello World for Kiwi Move; get raw data in with your device ID and password!

You can use this test panel to view, record, save and analyze streaming sensor data.

To confirm that your Kiwi is setup and working correctly:

Check that the light on your Kiwi is blinking green, and check that the live graphs in the Kiwi Test Panel are streaming sensor data (accelerometer, gyroscope, magnetometer).

	script src="http://build.kiwiwearables.com:8080/socket.js/socket.io.js"
					
	var socket = io.connect('http://build.kiwiwearables.com:8080')
	
	socket.on('connect', function() {
		socket.emit('listen', {device_id: 'your device ID', password: 'your password'});
	});
	//e.g. socket.emit('listen', {device_id: '42', password: '123'});
	
	socket.on('listen_response', function(data) {
		
		var kiwi_data = JSON.parse(data.message);
		//console.log(kiwi_data);   // Kiwi sensor data is a JSON object
			
		var packet_type = kiwi_data.packet_type;  
		
		// Capture accelerometer, gyroscope and magnetometer data
			
		var acceleration_x = kiwi_data.ax;
		var acceleration_y = kiwi_data.ay;
		var acceleration_z = kiwi_data.az;
		var gyroscope_x = kiwi_data.gx;
		var gyroscope_y = kiwi_data.gy;
		var gyroscope_z = kiwi_data.gz;
		var magnetometer_x = kiwi_data.mx;
		var magnetometer_y = kiwi_data.my;
		var magnetometer_z = kiwi_data.mz;
			
	});
