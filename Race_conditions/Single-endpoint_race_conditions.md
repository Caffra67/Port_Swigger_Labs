# Single-endpoint race conditions

At first get request POST /my-account/change-email you will get it while trying to change email

<img width="1551" height="714" alt="image" src="https://github.com/user-attachments/assets/f75f65bb-789d-4691-860d-6bb267894e99" />

Send it to repeater and:
- change one request it carlos email and other with random email
- send group (parallel)

<img width="757" height="594" alt="image" src="https://github.com/user-attachments/assets/3e3297b9-5729-42e1-a8ca-047abf2ab878" />

And like that you can change email to carlos, after that you can finish lab deleteing carlos.

<img width="1186" height="245" alt="image" src="https://github.com/user-attachments/assets/5155edbc-ae70-4931-b261-72ae712cbe0d" />
