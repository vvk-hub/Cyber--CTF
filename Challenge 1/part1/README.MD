# 🧩 CTF Write‑Up — Git History Secret Recovery

## Challenge Overview
In this challenge, we were given access to a **py program** where a sensitive value (flag/secret) had supposedly been **removed**.

At first glance, the repository appeared clean — no secrets visible in the latest commit.

---

## Initial Observation
The python program had a line base64 encoded which was not printed so on printing it
it gave  clude "no flag here ,  check for hidden directory"
then i foundd the .git file  
 and another file had the logs for git where secrets where removed

After inspecting the repository:

- No flag in the current files
- Commit history was publicly accessible
- No history rewriting (`git filter-branch` / `git rebase`) detected

---
## Investigation: Commit History
 inspecting the **commit history** using Git

📸 **Commit history view**  
![Commit History](images/git_commit_history.png)

One commit message stood out:
- Mentioned cleanup / removal
- Suggested something existed earlier

---
GitHub shows:
- Lines **removed** in red
- Lines **added** in green

using:
git log --online 
git show 53ad829:config.txt
it gave a base64 encoded on decoding got the flag
---

## Result
🎯 **Secret successfully recovered from Git history**

FLAG part1 : gdg{sw1ss_API_KEY=dont_redeem_it_

This confirmed:
- The challenge relied on **version control awareness**
- The removal was intentional but incomplete

---

## Security Lesson
🚨 **Never commit secrets — even temporarily**

---

