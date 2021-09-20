# HTTP , TCP and OSI Model

### HTTP

Hyper Text Transfer Protocol is an application layer protocol for transmitting hypermedia documents such html. It follows a classical client-server model ([refer to this](https://en.wikipedia.org/wiki/Client%E2%80%93server_model)). Http is a stateless protocol meaning server does not keeps any state about the client 

More :

- [MDN DOCS](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- [This Video is really good](https://www.youtube.com/watch?v=SzSXHv8RKdM)

Client can also provide headers to server. The major ones are :

- GET : get the data from server
- POST : post the data on the server
- PUT : update the data on server ( id is generally provided )
- DELETE : Delete the data on sever ( id is generally provided)

The server also responds with various code and to the client. Some are :

- 200 : everything was fine
- 403 : bad request
- 500 : server is f***ed

( tcp and osi notes )