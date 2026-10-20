---
tags:
  - ccna/concept
course_days:
  - 4
---

# Concept: Cisco Password Types

> [!abstract] In one line  
> In the config, a number appears before a stored password. That **type number** tells you how the password is protected: **0 = plain text, 7 = weak scramble, 5 = MD5 hash** (newer IOS also uses 8 and 9).

## What the Config Shows

```
enable password CCNA                          ← plain text (type 0), anyone can read it
enable password 7 08026F6028                  ← type 7, after service password-encryption
enable secret 5 $1$mERr$Y1CkLMcTYWwkF1Ccndtl1. ← type 5, MD5 hash
```

## The Types

|Type|How it's protected|Reversible?|Comes from|
|---|---|---|---|
|**0**|Not at all (clear text)|— it's readable|`enable password` alone|
|**7**|Cisco's own simple scramble|✅ **Yes, in seconds** (free online crackers)|`service password-encryption`|
|**5**|**MD5 hash**|❌ No (only guessable by brute force)|`enable secret`|
|8 / 9|SHA-256 / scrypt hash (stronger)|❌ No|`enable secret` on newer IOS|

> [!info]- Scramble vs hash: what's the difference? (click)  
> **Type 7 (encryption)** is like a lock whose key everyone knows: it can be turned straight back into `CCNA`.  
> **Type 5 (hashing)** is like a fingerprint: you can check whether a password *matches*, but you can't rebuild the password from the fingerprint. When you type the password, the router hashes your input and compares the two fingerprints.

## Exam Points

- Use **`enable secret`**, not `enable password`.
- If both are set, **`enable secret` wins**. The `enable password` is ignored.
- `service password-encryption` turns plain passwords into **type 7** and **never affects `enable secret`**, which is always hashed.
- `no service password-encryption` does **not** decrypt existing passwords. It only leaves *future* ones in plain text.
- Type 7 is **weak**: treat it as "hidden from a glance", not secure.

## Self-Test

1. You see `enable password 7 08026F6028`. Is it safe?
2. Which number means an MD5 hash?
3. Does `service password-encryption` change how `enable secret` is stored?

> [!success]- Answers  
> 1. No. Type 7 can be reversed in seconds.  
> 2. **5**.  
> 3. No. The enable secret is always hashed, whatever that setting is.

## Related

- [Day 04 - Intro to the CLI](../01%20-%20Course%20Days/Day%2004%20-%20Intro%20to%20the%20CLI.md)
