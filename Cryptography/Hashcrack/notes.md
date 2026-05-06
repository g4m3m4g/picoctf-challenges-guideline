## hashcrack

**Author:** Nana Ama Atombo-Sackey  
**Category:** Cryptography / Password Cracking

### Core Concept

This challenge highlights the dangers of using **weak cryptographic hashes**. Unlike encryption, hashing is a one-way function meant to be irreversible. However, if a weak algorithm is used (like MD5 or SHA1), attackers can use "rainbow tables" or brute-force tools to find the original plaintext. This task specifically tests your ability to identify hash types and handle "Nested Hashing," where a value is hashed multiple times.

### Toolbox

- **Netcat (nc):** To connect to the breached server.
- **hashid / hash-identifier:** Command-line tools that analyze a string's format to guess which hashing algorithm was used.
- **CrackStation / HashKiller:** Online databases that instantly look up pre-computed hashes.

### Methodology

1.  **Initial Connection:** You used `nc` to access the server and received a hash string representing a "weakly hashed password."
2.  **Identification:** You used `hashid` to figure out what you were looking at (e.g., MD5, SHA-256). Knowing the type is 90% of the battle because it tells you which tool or website to use for cracking.
3.  **Layered Decryption (The Onion Approach):** You discovered that cracking one hash didn't give you the flag—it gave you _another_ hash.
4.  **Iteration:** You repeated the process:
    - **Level 1:** Identify hash -> Crack it -> Get Level 2 Hash.
    - **Level 2:** Identify hash -> Crack it -> Get Level 3 Hash.
    - **Level 3:** Identify hash -> Crack it -> Final Secret/Flag.
5.  **Completion:** After three rounds of identifying and cracking, the final plaintext revealed the secret flag.

### My Insight

In the real world, we prevent this by using "Salting" (adding random data to the password before hashing) and "Key Stretching" (using algorithms like Argon2 or bcrypt that are intentionally slow). If you ever run into a hash that isn't in an online database, you'd have to switch to heavy hitters like **John the Ripper** or **Hashcat** to brute-force it using your GPU!
