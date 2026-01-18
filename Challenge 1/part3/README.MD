# GDG CTF – QR Zipbomb Challenge Write-up

## 🏁 Challenge Overview
The challenge provided a `.rar` archive containing **~3000 QR code images**.  
Each QR code decoded to text, but most were **decoys** like:

- "Not this one"
- "Nothing useful here"
- "Just a decoy"

The goal was to extract the **final flag** hidden within these QR codes.

---

## 🔍 Initial Approach
- Wrote a Python script to scan all QR images and decode the text.
- Attempted to find **unique QR outputs**, assuming the flag would appear only once.

###  First Failure
- Many outputs appeared unique, but they were all decoys.
- Reason: decoy messages included a changing suffix `(scan #XXXX)`, making identical messages seem different.

---

## 🛠️ Fix & Improved Approach
- Normalized decoded text by **removing `(scan #XXXX)`** from each message.
- Grouped messages by their **logical content** and counted occurrences.
- Focused on messages that appeared **only once** or very few times.

---

## 🎯 Breakthrough
- After normalization, only **one logically unique message** remained:
the message was base64 encoded decoding it i got the part 3 of the flag

Flag: gg1ol}
