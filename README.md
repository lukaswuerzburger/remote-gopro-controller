# remote-gopro-controller

This is a project to build a software that triggers GoPro features from another machine using a Raspberry Pi as the controller in the middle. Since the GoPro API is only available via Wifi the Raspberry Pi needs to handle Ethernet and Wifi at the same time (Check out [Development Environment](#development-environment)).

### First Goal

The first goal is to take photos from the GoPro triggered by a computer in the same network. 

### Second Goal

Second goal would be to open up ports to make it accessible from the internet, so that you can use your phone or another computer that aren't in the same network.

### Development Environment

Hardware setup:
* Router (Fritz!Box 7430)
* Raspberry Pi 3 B
* GoPro Hero 4

<img src="https://raw.githubusercontent.com/lukaswuerzburger/remote-gopro-controller/master/readme-resources/development-environment.jpg" alt="Development Environment" title="Development Environment">

#### How Things are connected

The Router provides the connection to the local network via Ethernet. The GoPro is hosting a Wifi and runs a server to provide actions and data. The Raspberry Pi connects to the Wifi of the GoPro and to the Ethernet of the Router. The Raspberry Pi also hosts a web server to expose the API from the GoPro

The difficulties are now to use Ethernet and Wifi at the same time for different purposes.

### Example Scenario

1. A random computer A in the network requests a photo using the API running on the Raspberry Pi (Raspberry Pi is connected over Ethernet to the rest of the network).
2. The Raspberry Pi receives the request and sends another request to the GoPro API, running on the GoPro itself (Raspberry Pi uses Wifi to connect to the GoPro).
3. The GoPro receives the request from the Raspberry Pi, captures a picture and returns it in response.
4. The Raspberry Pi receives the response and responds to the initial request of the computer A with the picture of the GoPro.

