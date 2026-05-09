## Scan Surprise

**Author:** Jeffery John  
**Category:** Forensics

### Core Concept

This challenge plays with the idea of **Data Representation**. Instead of hiding a flag in code or metadata, the information is encoded into a visual format designed for machines to read: a **QR Code** (Quick Response Code). It’s a reminder that "Forensics" isn't always about deep binary analysis; sometimes it’s just about knowing how to translate a visual pattern back into text.

### Toolbox

- **QR Scanner:** Any smartphone camera or an online tool like [QRCode Decoder Online](https://scanqr.org/).

### Methodology

1.  **Unzipping:** You downloaded the `challenge.zip` file and extracted it to find a single image file
2.  **Visual Confirmation:** Upon opening the image, you saw a standard QR code.
3.  **Decoding:** You didn't need to overthink it—you just scanned the code. The encoded data inside was the flag in its standard `picoCTF{...}` format.

### My Insight

QR codes are basically just high-density versions of barcodes. They use a specific pattern of squares to represent bits of data, including "finder patterns" (the big squares in the corners) that help the scanner orient itself. In more advanced CTFs, you might find a QR code that is broken or inverted, requiring you to fix it in an image editor before it will scan. For this one, though, a simple point-and-click did the trick!
