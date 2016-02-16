Object sync protocol specification (Draft)
=======
Object sync protocol is designed to synchronize two objects remotely. 
Those are the basic principles of OSP:
- Bidirectional.
- Asynchronous.
- Lightweight, sending the minimum bytes possible.
- Good performance when encoding and decoding a request.
- The format used to send data must be regular [JSON](https://en.wikipedia.org/wiki/JSON).

In this documentation we will use the term **user** as **sender** and **server** as **receptor**. But don't forget OSP is bidirectional, so user can be a receptor and server can be sender.

### Structure of request
```js
[<request_id>, <action>, <params...>]
```
1. **`<request_id>`** Always an integer greater than 0 that represent the ID of each request. request_id is unique by the user, which means a server can receive exactly the same request multiple times with the same request_id from different users. A sender (client/send) can not send two requests with the same request_id.
2. **`<action>`** Type of the action (connect, sync, call, set...). Always an integer greater than -1. See below for the action types.
3. **`<params...>`** Multiples parameters can be passed on every request. The parameters are defined for the type of action described bellow.





### Structure of response

