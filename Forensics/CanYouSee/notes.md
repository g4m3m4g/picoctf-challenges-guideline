## CanYouSee

**Author:** Mubarak Mikail  
**Category:** Forensics

### Core Concept

This challenge is another lesson in **Metadata Hunting**, but it focuses on a less common field: the **AttributionURL**. In digital forensics, you can't just look at the "Author" or "Comment" fields; you have to scan every single attribute. Developers or CTF creators often hide strings in obscure metadata tags that tools like standard file properties won't show you.

### Toolbox

- **ExifTool / Metadata Viewer:** To dump all possible metadata fields from the image.
- **Base64 Decoder:** To translate the string found in the URL field.

### Methodology

1.  **Full Metadata Dump:** You ran a deep scan of the image's metadata. Instead of just looking for text, you looked for unusual or long strings in every available field.
2.  **Targeting AttributionURL:** You spotted a suspicious string in the `AttributionURL` field. While this field is normally meant for crediting the source of an image, here it contained a scrambled alphanumeric string.
3.  **Decoding:** You recognized the pattern (likely Base64 again) and decoded it to reveal the flag.

### My Insight

This is why you should always use `exiftool -a -u` on Linux. The `-a` flag allows duplicate tags to be shown, and `-u` shows unknown tags. Sometimes a flag is hidden in a "custom" tag that most online viewers might ignore.
