# Multi-endpoint race conditions

First thing to do is to catch 3 request 

- POST /cart | productId=2
- POST /cart/checkout
- POST /cart | productId=1

After that create group with productId=1, checkout, productId=1

<img width="470" height="809" alt="image" src="https://github.com/user-attachments/assets/3979745d-f4c0-418f-92f6-c5331008f353" />

And send it sometimes it take more then 1 try
