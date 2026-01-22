## Part 2 — Image Steganography (PNG)

### Challenge Summary
The second part of the challenge provided a PNG image (`heheheha.png`).  
Although it appeared to be a normal image, it contained hidden data using steganography.

---
### initial inspection
it had readdme ffile which said the flag is hidden inside the image.

### Step 1: Metadata Inspection
The image was first analyzed using `exiftool` to check for metadata and embedded hints.
well there was nothing interesting

```bash
exiftool ../assests/heheheha.png
```

### step 2:
I tried using the strigs heheheha.png but nothing interesting.....

### step 3:
Next i searched for some common way for hidding the flag in the image i came to know about a interestig thing that is changing the lsb of a image to store a dataso i used a zsteg and found the flag

```bash
zsteg ../assests/heheheha.png
```
Flag : 10:armykni3_

