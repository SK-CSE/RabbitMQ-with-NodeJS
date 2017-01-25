One of the advantages of using a Task Queue is the ability to easily parallelise work. If we are building up a backlog of work, we can just add more workers and that way, scale easily.

First, let's try to run two worker.js scripts at the same time. They will both get messages from the queue, but how exactly? Let's see.

You need three consoles open. Two will run the worker.js script. These consoles will be our two consumers - C1 and C2.

```bash
shell1$ ./worker.js
 [*] Waiting for messages. To exit press CTRL+C
```


```bash
shell2$ ./worker.js
 [*] Waiting for messages. To exit press CTRL+C
```

In the third one we'll publish new tasks. Once you've started the consumers you can publish a few messages:

```bash
shell3$ ./new_task.js First message.
```

```bash
shell3$ ./new_task.js Second message..
```

```bash
shell3$ ./new_task.js Third message...
```

```bash
shell3$ ./new_task.js Fourth message....
```

```bash
shell3$ ./new_task.js Fifth message.....
```

Let's see what is delivered to our workers:

```bash
shell1$ ./worker.js
 [*] Waiting for messages. To exit press CTRL+C
 [x] Received 'First message.'
 [x] Received 'Third message...'
 [x] Received 'Fifth message.....'
```
```bash
shell2$ ./worker.js
 [*] Waiting for messages. To exit press CTRL+C
 [x] Received 'Second message..'
 [x] Received 'Fourth message....'
```
By default, RabbitMQ will send each message to the next consumer, in sequence. On average every consumer will get the same number of messages. This way of distributing messages is called round-robin. Try this out with three or more workers.