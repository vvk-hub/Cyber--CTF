# 🥧 Apple Pie — CTF Writeup

## 📌 Challenge Overview

- **Challenge Name:** Apple Pie  
- **Category:** Reverse Engineering  
- **Difficulty:** Easy–Medium  
- **Goal:** Extract the hidden flag from the binary  


This challenge initially looks like it may contain a **format string vulnerability**, but that turns out to be a **deliberate misdirection**. The real flag is revealed through **XOR deobfuscation**.

---

## 🔍 Initial Recon & Misdirection
used ghidra..

During static analysis, they got the input and directly printing it so , i was misdirected as if it were a formatiing vulnerability and trying to acces the stack address using the local_10
 i tried using the gbd (gnu debugger) to stop at main and proceed but wasted
---

### finally
then i was just trying to see where it points and then i found the nothing imp function and which had printf of you ofund the hidden treasure n stuff and i cld see it was some roation charcter stuff so i copied and ran the code
 THE MISDIRECTION TOOK ME ALONG TIME TO REALIZE THATS NOT THE WAY ;(
```c
printf("\nYou found the hidden treasure: %s\n", local_26);

---
Flag : gdg{P1E_3xpl01t3d_lol}
