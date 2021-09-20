# Sessions and cookies

Since We know that HTTP is a stateless protocol it does not saves sessions and cookies or literally any data about the client. 

Sessions and cookies are the ways to make HTTP state full.   

Cookies is a way of storing state that is only client side.

Sessions are generally stored on server side. But sometimes they are stored on client side. Storing sessions on client side makes the interaction really. This is what rails provides by default. But this has a disadvantage that is lack of storage.