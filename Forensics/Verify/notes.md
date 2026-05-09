## Verify

**Author:** Jeffery John  
**Category:** Forensics

### Core Concept

This challenge focuses on **Integrity Verification**. In security, hashes (like SHA-256) act as digital fingerprints. Since even a tiny change in a file results in a completely different hash, they are used to ensure a file hasn't been tampered with or to find a specific "needle in a haystack." Here, you're tasked with finding the one "legitimate" flag file out of a massive directory of fakes.

### Toolbox

- **SSH:** To log into the challenge server.
- **sha256sum:** A utility that calculates the SHA-256 hash of files.
- **grep:** A command-line tool for searching plain-text data for lines that match a specific pattern.
- **Piping (`|`):** To pass the output of the hashing command directly into the search command.

### Methodology

1.  **Preparation:** You started by reading `checksum.txt` to get the "official" hash provided by the author. This is the fingerprint of the real flag.
2.  **Mass Hashing:** Since the `files/` folder was packed with too many files to check manually, you used a wildcard: `sha256sum files/*`. This tells the system to calculate the hash for every single file in that directory.
3.  **The Shortcut:** Instead of scrolling through a giant list, you piped the output to `grep`. By running `sha256sum files/* | grep <your_checksum>`, you filtered the results to show only the line where the hash matched.
4.  **Identification:** The command returned the specific filename associated with that unique hash.
5.  **Decryption:** With the correct filename in hand, you ran the provided script: `./decrypt.sh files/<correct_file>`. The script verified the file one last time and spat out the flag.

### My Insight

Using `grep` with `sha256sum` is a pro move. In real-world forensics or incident response, you might have thousands of system files and a list of "Known Bad" hashes (malware). You'd use this exact same technique to quickly scan a hard drive to see if any malicious files are hiding in there. Automating the search saves your eyes from the "visual noise" of 99% fake data!
