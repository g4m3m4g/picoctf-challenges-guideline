## Riddle Registry

**Author:** Prince Niyonshuti N.  
**Category:** Forensics

### Core Concept

This challenge is a classic lesson in **Metadata Forensics**. In the world of files, there is the data you see (the content) and the data _about_ the data (the metadata). Metadata includes things like the author, creation date, software used, and GPS coordinates. Hackers and investigators always check the "hidden" properties of a file because sensitive info—like a flag or a username—is often tucked away where the average user never looks.

### Toolbox

- **Metadata2Go:** A handy web-based tool to view all hidden attributes of a file.
- **Base64 Decoder:** To translate the encoded string found in the metadata.
- **ExifTool (Alternative):** A powerful command-line tool for reading and writing meta information.

### Methodology

1.  **Thinking Outside the Content:** You realized the "garbled nonsense" inside the PDF was a distraction. Following the hint, you shifted your focus from the document's pages to its internal properties.
2.  **Metadata Extraction:** You uploaded the file to an online metadata viewer to see the hidden fields associated with the PDF.
3.  **Pattern Spotting:** While scanning the results, you checked the **"Author"** field. Instead of a name, it contained a suspicious string of alphanumeric characters ending in `==`.
4.  **Decoding the Treasure:** Recognizing the Base64 signature, you decoded the string from the Author field, which revealed the actual flag.

### My Insight

Metadata is a goldmine in real-world investigations. Whether it's a "Confidential" PDF that still has the original author's name or a photo that accidentally includes the GPS location of a secret facility, metadata leaks happen all the time. Pro tip: If you're on a Linux terminal, just typing `exiftool <filename>` is the fastest way to check this without leaving your shell!
