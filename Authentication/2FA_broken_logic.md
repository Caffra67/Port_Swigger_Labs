# 2FA broken logic

At first login with credencial you get and catch request
- GET /login2 send it to repeater
- POST /login2 send it to intruder

After that send in repeater GET /login2 with changed Cookie to carlos

<img width="766" height="492" alt="image" src="https://github.com/user-attachments/assets/815806c6-8f4e-4f55-a76e-529ad571c8d3" />

Later change in POST /login2 change cookie verify=carlos
And set payload type to Brute forcer and character set to 0123456789

<img width="1883" height="649" alt="image" src="https://github.com/user-attachments/assets/98c59c9d-b228-44a8-9519-a6504280c934" />

After brute force you will found mfa code and session cookie 

<img width="1091" height="519" alt="image" src="https://github.com/user-attachments/assets/f873124d-dcfb-42cc-909c-6e74e82361c8" />

Go to the website using the established session, and you will be logged in automatically

<img width="766" height="413" alt="image" src="https://github.com/user-attachments/assets/2d83ddcc-4be3-4e45-a5bd-92a5f873d630" />
