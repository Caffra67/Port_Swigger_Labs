# 2FA simple bypass

The first thing I did was look at the user, and I noticed a URL containing a user parameter, which means there is a possibility of an IDOR vulnerability.

```
https://0a4000ac0351e1c6829bd03e000e0099.web-security-academy.net/my-account?id=wiener
```

<img width="1170" height="688" alt="image" src="https://github.com/user-attachments/assets/cb995443-e8a8-4835-8716-b6bc5f14080e" />

After logging in as Carlos, when the website prompted me for 2FA, I changed the ID to Carlos's ID, and in that way I was able to bypass the 2FA.

```
https://0a4000ac0351e1c6829bd03e000e0099.web-security-academy.net/my-account?id=carlos
```

<img width="1114" height="481" alt="image" src="https://github.com/user-attachments/assets/3f585ff3-bacb-4594-995a-d76102028591" />

Not every vulnerability is complicated. 
