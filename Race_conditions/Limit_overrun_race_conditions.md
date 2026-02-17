# Limit overrun race conditions

To do race condition we need to send request at once, with that we can use **Repeater** 

At first add product to cart

<img width="550" height="685" alt="image" src="https://github.com/user-attachments/assets/10dbba1b-f437-4c48-a386-325d24aca8ee" />

Apply coupon and catch it with intruder and send it to Repeater 

<img width="504" height="270" alt="image" src="https://github.com/user-attachments/assets/04edcdb4-9ee7-4842-91db-fdc08a44cd49" />

At Reapeter create group and duplicate request 

https://github.com/user-attachments/assets/12f424cf-5dbd-44da-8414-1d3e628701d7

Set Send group in patallel and send it 

<img width="386" height="138" alt="image" src="https://github.com/user-attachments/assets/9a021deb-4d65-424e-8dcd-0a374ebc8fe7" />

And like that we apply coupon several times

<img width="356" height="234" alt="image" src="https://github.com/user-attachments/assets/da79060c-2f7f-48a1-9958-878339efba51" />
