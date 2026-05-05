## Mod 26

**Author:** Pandu  
**Category:** Cryptography

### Core Concept

This one is all about the basics of classical substitution ciphers. Specifically, it introduces **ROT13** (Rotate by 13 places). It’s a special case of the Caesar Cipher where the alphabet is shifted by 13 positions. Since the Latin alphabet has 26 letters, shifting by 13 is unique because applying the same shift twice brings you right back to the original letter—making it its own inverse.

### Toolbox

- **ROT13.com:** A quick web-based tool for shifting text.
- **Command Line (Optional):** You can also do this in Linux with the `tr` command: `tr 'A-Za-z' 'N-ZA-Mn-za-m'`.

### Methodology

1.  **Identification:** The challenge description literally gives you the hint: "do you know what ROT13 is?". The flag format usually starts with `cvpbPGS`, which is `picoCTF` shifted by 13.
2.  **Transformation:** You took the scrambled string from `values.txt`, threw it into an online ROT13 converter, and the readable flag popped right out.
3.  **Broadening Scope:** While this was a simple 13-place shift, you recognized that this belongs to the "ROT" family, where the shift value ($n$ in $Mod(26)$) can be anything from 1 to 25.

### My Insight

ROT13 is essentially the "spoiler tag" of the internet; it's not meant for real security, just to hide text from accidental reading. In CTFs, whenever you see a string that looks like a flag but the letters are all "wrong," a ROT shift or Caesar cipher should be the very first thing you check. It’s the simplest form of encryption you'll ever run into.
