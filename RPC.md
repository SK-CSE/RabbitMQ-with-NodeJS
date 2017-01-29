We can start the server:

```bash
$ ./rpc_server.js
 [x] Awaiting RPC requests
```
To request a fibonacci number run the client:

```bash
$ ./rpc_client.js 30
 [x] Requesting fib(30)
```
The design presented here is not the only possible implementation of a RPC service, but it has some important advantages:

If the RPC server is too slow, you can scale up by just running another one. Try running a second rpc_server.js in a new console.
On the client side, the RPC requires sending and receiving only one message. As a result the RPC client needs only one network round trip for a single RPC request.