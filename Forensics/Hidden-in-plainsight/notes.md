## Hidden in plainsight

**Author:** Yahaya Meddy  
**Category:** Forensics / Steganography

### Core Concept

This challenge is a perfect introduction to **Steganography**—the art of hiding a message or file _inside_ another file so that it doesn't attract attention. Unlike basic metadata challenges, this one uses **password-protected steganography**, meaning the hidden payload is encrypted and can only be extracted if you find the "secret key" hidden elsewhere in the file.

### Toolbox

- **Metadata Viewer (ExifTool):** To find the initial hidden password.
- **Base64 Decoder:** To translate the password from the metadata.
- **Steghide:** A classic command-line tool used to hide or extract data from image and audio files.

### Methodology

1.  **Initial Reconnaissance:** You started by checking the image's metadata. This is a solid first step because developers often hide keys or clues in the "Comment" or "Description" fields.
2.  **Secret Key Retrieval:** You found a Base64-encoded string in the metadata comments. After decoding it, you realized it was the password needed for the next layer.
3.  **Extraction:** You used the `steghide` tool to pull out the hidden payload. The command usually looks like this:
    `steghide extract -sf image.jpg`
4.  **Authentication:** When prompted, you entered the password you found in step 2.
5.  **Final Reveal:** Once the password was accepted, `steghide` extracted a hidden file (likely a `.txt` file) containing the flag.

### My Insight

Steganography is like a digital Russian nesting doll. A common "best practice" in CTFs is to always check metadata first, then look for hidden files with tools like `binwalk` or `steghide`. If you're on a system where you can't install `steghide`, there are online versions like **StegOnline**, but knowing the command line is much faster for a pro!
