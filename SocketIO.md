Socket.IO is a Javascript library, which enables real-time bidirectional event-based communication.
It occupies Websockets for the purpose upon TCP connections.

SocketIO is all about:

      1. Listening to an event
      2. Emit an event
One listens to an event and when another one emits it, the listener handle the event by doing particular tasks related.

Read the original documentation: https://socket.io/docs

Refer our GitHub project: https://github.com/meetrix/Socket-Server

SocketIO can be used in Android applications by adding its dependecy.
(can be found in https://socket.io/blog/native-socket-io-and-android/)

Here, the usage of SocketIO with Node.js server is focused.

##### 1. Configure a Client
This is basically achieved in a Web page

            var socket = io();
            
##### 2. Configure a listener
A listener in server-side for 'connection' event i.e. to get notified when a client is connected.

            io.on('connection', 
                ... //things to do
            });
            
##### 3. Emit an Event
            socket.emit('event-name', 
                ... //things to do
            });     
            
##### 4. listen to an Event            
            socket.on('event-name', 
                ... //things to do
            });
            
##### 5. Group/room Concept 
This concept enables to join several users to a single connection and obtain updates of all.

            socket.join('room-name'); //to join the room named with 'room-name'
            socket.leave('room-name'); //to leave the room
            
Obtain and distribute updates within the room:

            io.sockets.in('room-name').emit('function', 'data1', 'data2');
