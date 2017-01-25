Now we can run both scripts. In a terminal, from the path/to/the/ folder, run the sender:


```bash
$ ./send.js
```

then, run the receiver:

```bash
$ ./receive.js
```
The receiver will print the message it gets from the sender via RabbitMQ. The receiver will keep running, waiting for messages (Use Ctrl-C to stop it), so try running the sender from another terminal.

If you want to check on the queue, try using

```bash
$ rabbitmqctl list_queues
```

Hello World!