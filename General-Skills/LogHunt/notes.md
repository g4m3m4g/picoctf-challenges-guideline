## Challenge: Log Hunt

**Author:** Yahaya Meddy  
**Category:** General Skills

### Core Concept

This challenge demonstrates how **Log Analysis and Information Disclosure** work in a real-world scenario. Developers sometimes log variables or sensitive data chunks for debugging and forget to turn them off. When a server leaks data this way, an analyst (or an attacker) just needs to find the unique "fingerprint" or keyword in the log structure to filter out the noise and reconstruct the original data.

### Toolbox

- **cat:** To output the raw content of the log file.
- **grep:** To filter the text and isolate lines containing the specific keyword.
- **Piping (`|`):** To stream the log contents directly into the search filter.

### Methodology

1.  **Spotting the Pattern:** You used `cat` to read the log and noticed a specific, structured format: `[1990-08-09 10:00:10] INFO FLAGPART: picoCTF{...`.
2.  **Identifying the Key Anchor:** Instead of guessing randomly, you picked up on the developer's custom prefix: `FLAGPART`. This is the perfect anchor because it's unique to the data you actually want.
3.  **Targeted Filtering:** You refined your approach by running `cat server.log | grep FLAGPART`. This instantly stripped away all the standard `INFO`, `WARN`, or connection logs, leaving you with just the flag fragments.
4.  **Reconstruction:** With only the relevant `FLAGPART` lines visible on your screen, you lined up the fragments in order and merged them to get the complete flag.

### My Insight

--