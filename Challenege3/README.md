# 🔓 JWT Authentication Bypass → System Compromise

**Category:** Web / Authentication  
**Impact:** Admin access → Sensitive log disclosure → Credential & key exposure  
**Vulnerability:** Improper JWT validation (`alg: none`)

---
### initial mistake
i opend the debian server machine and it asked for password and idk neither user or pass so i gone to GRUB removed the 

### qo quiet to rw init=bin/bash

then i gone in and saw the intern profile.. then i changed its pssword but still didnt had the root permission 

so then i change that to 
#### rw  mount -o reount
which gave me as a root and i read the file easy way in ryt!!!!

then i tried to go find the web vul.. after getting in i spent days trying to loggin as intern ssh but the fact ioos i forgot that i changed the password so i wasted too many days
 ;( ;(
so i made anothe copy of the .ova for the ctf purpose and proceeded


## 📌 Overview

This challenge involved a web application that relied on **JWT-based authentication** to protect administrative API endpoints. Although the token appeared to be signed and secure, the backend failed to properly validate the JWT signature.

By abusing the classic **`alg: none` JWT vulnerability**, it was possible to forge an admin token, gain unauthorized access to protected endpoints, and pivot further into the system.

---

## 🔍 Step 1: Admin Endpoint Enumeration

While enumerating the application, the following endpoint was discovered:

/api/admin/logs
/api/admin/orders


Direct access resulted in:
- `403 Forbidden`
- `406 Method Not Allowed` when incorrect HTTP verbs were used

An `OPTIONS` request revealed allowed methods:

```http
Allow: GET, HEAD, OPTIONS
```
then when i logged in it created me a token and then i googled then got to know about the jwt token n stuffs and deodding the token i got 
header:
{
  "alg": "HS250",
  "typ": "JWT"
}


payload:
{
  "userId": 6,
  "admin": false,
  "iat": <timestamp>,
  "exp": <timestamp>
}
 .signature

 i Tried changing the admin as true and changint the cookie but it seems signaturre is validating

 Step 3: Initial Misinterpretation

Initially, effort was spent attempting to:
Crack or brute-force the JWT secret
Decrypt the signature:
Assume proper HS256 verification was enforced.This turned out to be unnecessary and misleading

step 4:
refferred some yt vids and tried to change the alg to non and uploaded with the signature boom crtacked.
and in the logs downloaded the file and which had all the login creditials for fth(file transfer)

step 5:
i connecte throught fth and downloaded a zip file and upon unzipping it i got a alot of the info abt the ssh crediials 

i logged in as intern and but no sudo permission to view secret recepie,,
i read the ssh initialization and got to know that DENYUSER deploy

### info so i cant loggin as root as ssh was blocking denyuser deploy

i switched to backup still no use and i tried to switch to 

### su - and gave the intern pass boom cracked

FLAG : gdg(5utd@_ld3_13_4_5tndwich)

