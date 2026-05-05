## interencdec
**Author:** NGIRIMANA Schadrack  
**Category:** Cryptography

### Core Concept
This challenge is all about **Nested Encoding and Encryption**. It teaches you that data is often wrapped in multiple layers (like an onion), and you have to peel them back one by one. You'll encounter **Base64**—a binary-to-text encoding scheme easily identified by its alphanumeric characters and `==` padding—and the **Caesar Cipher**, a basic substitution shift.

### Toolbox
*   **Text Editor (Notepad/VS Code):** To open the initial mystery file.
*   **Base64decode.org:** A quick online tool to reverse the encoding.
*   **Cryptii.com:** A versatile site for handling various ciphers, including Caesar.

### Methodology
1.  **File Inspection:** You downloaded the extensionless file and opened it in a text editor. Spotting the `==` at the end was the key—that's a dead giveaway for Base64 padding.
2.  **Layer 1 (Base64):** You decoded the first string, but instead of the flag, it spat out *another* Base64 string.
3.  **Layer 2 (Base64):** You repeated the decoding process for the second string. This time, you got something that looked like a flag but was still gibberish (e.g., `wpbnPGS{...}`).
4.  **Layer 3 (Caesar Cipher):** You recognized the structure of the flag format. By comparing the scrambled prefix to the known `picoCTF` prefix, you could determine the shift value (rotation).
5.  **Final Decryption:** You plugged the scrambled flag into a Caesar decoder and shifted the letters until it transformed into the readable `picoCTF{...}` flag.

### My Insight
Multi-step challenges like this are super common. The trick is to keep a cool head and look for the "signature" of each layer. 
*   Ends in `=`? Try Base64. 
*   Looks like a flag but the letters are wrong? Try Caesar/ROT. 
*   Starts with `0x`? Try Hex. 
Always use the known flag format (`picoCTF`) as your "North Star" to calculate shift distances quickly!