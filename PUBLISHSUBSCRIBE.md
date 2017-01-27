If you want to save logs to a file, just open a console and type:

```bash
$ ./receive_logs.js > logs_from_rabbit.log
```
If you wish to see the logs on your screen, spawn a new terminal and run:
```bash
$ ./receive_logs.js
```
And of course, to emit logs type:
```bash
$ ./emit_log.js
```
Using rabbitmqctl list_bindings you can verify that the code actually creates bindings and queues as we want. With two receive_logs.js programs running you should see something like:

```bash
$ sudo rabbitmqctl list_bindings
Listing bindings ...
logs    exchange        amq.gen-JzTY20BRgKO-HjmUJj0wLg  queue           []
logs    exchange        amq.gen-vso0PVvyiRIL2WoV3i48Yg  queue           []
...done.
```
The interpretation of the result is straightforward: data from exchange logs goes to two queues with server-assigned names. And that's exactly what we intended.

