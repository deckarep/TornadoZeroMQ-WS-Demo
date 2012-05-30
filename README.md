TornadoZeroMQ-WS-Demo
=====================

Demonstrates using Tornado Web Sockets with data published from a ZeroMQ process.

The intended goal is to implement a pub/sub system whereas a publisher exists in your system that will broadcast messages to a list
of connected websocket clients.  The message could be anything such as a notification, or a lat/lon pair and as the messages are
generated in real-time, a tornado based web socket server is acting as a subscriber listening for the messages.  It will then loop
through the connected websocket clients and broadcast the message to each user.

zmq_soccer_pub.py - this file represents the pub origin messages.  In this example, this is simply random data produced in a loop of soccer
events.  This script was originally provided by: Nicholas Piel (http://nichol.as/zeromq-an-introduction)

basic-websocket.py - this file is the tornado socket server.  It hooks into the pyzmq polling mechanism that is designed to work with tornado's own
IO loop.  When data is received, it will loop through all websocket client connections and broadcast the zmq subscriber message along to all clients.

basic-websocket.html - this file is just the client's html file that is initially loaded in the browser.  This file doesn't do much except
for get the ws connection started.

Dependancies:
* TornadoWeb - http://www.tornadoweb.org
* pyzmq - https://github.com/zeromq/pyzmq
* vanilla python 2.7+ - http://www.python.org

Also, this only works on browsers that support WebSockets.  Like a fairly new version of Chrome!

WARNING: This example shows a working prototype. The code is bad and needs to be refactored and simplified.  I'm still working on it!!!
