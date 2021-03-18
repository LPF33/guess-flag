# Socket.io (Encounter)

## Cheatsheet (server-side)

### sending to the client:

-   socket.emit('message', 'hello stranger!');

### sending to all clients except sender: (broadcast)

-   socket.broadcast.emit('broadcast', 'hello friends!');

### sending to all connected clients:

-   io.emit('an event sent to all connected clients');
-   io.sockets.emit('an event sent to all connected clients');

### sending to a specific socketId (private message):

-   io.to(socketId).emit('message', 'for your eyes only');
-   socket.broadcast.to(socketId).emit('message', 'for your eyes only');

### Send to all sockets except for a specific one:

-   io.sockets.sockets.get(socketId).broadcast.emit("message", "we exclude one socket");

## Rooms

### join to subscribe the socket to a given channel:

-   socket.join('some room');

### sending to all clients in 'game' room except sender:

-   socket.to('game').emit('message', "let's play a game");
-   socket.broadcast.to('game').emit('message', "let's play a game");

### sending to all clients in 'game1' and/or in 'game2' room, except sender:

-   socket.to('game1').to('game2').emit('nice game', "let's play a game");

### sending to all clients in 'game' room, including sender:

-   io.to('some room').emit('some event'):
-   io.in('game').emit('big-announcement', 'the game will start soon');

### leave to unsubscribe the socket to a given channel:

-   socket.leave('some room');

## Note: The following events are reserved and should not be used as event names by your application:

-   connect
-   connect_error
-   disconnect
-   disconnecting
-   newListener
-   removeListener

## Some useful stuff:

### Disconnect the socket:

-   socket.disconnect();

### Event, when the socket disconnects (e.g. closes the browser):

-   socket.on("disconnect", () => {
    io.emit('The socket with the id \${socket.id} left us!');
    });

More on:
https://socket.io/docs/v3
