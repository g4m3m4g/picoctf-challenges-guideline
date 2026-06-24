## Challenge Name

Timeline 0

## Author

LT 'syreal' Jones

## Category

Forensics

---

## Core Concept

This challenge involves digital forensics on a disk image, specifically focusing on timeline analysis and detecting "timestomping"—a technique where attackers or users intentionally alter file timestamps to hide activity. When timestomping is performed poorly, it often creates anomalies like extremely old or unrealistic dates. By generating a MAC (Modified, Accessed, Created) timeline using The Sleuth Kit, these chronological anomalies can be easily spotted to locate hidden or altered files.

## Toolbox

- **gunzip:** To decompress the downloaded disk image file.
- **The Sleuth Kit (fls, mactime):** Tools used to extract metadata and generate a human-readable chronological timeline from a filesystem image.
- **Spreadsheet Software (Excel or similar):** To open, sort, and analyze the resulting CSV timeline.
- **icat:** A Sleuth Kit utility used to output the contents of a file specified by its inode/metadata number.
- **Base64 Utility:** To decode the extracted ciphertext into plaintext.

---

## Methodology

- **Decompression:** Extract the raw disk image from the downloaded archive using the `gunzip` command.
- **Generating the Body File:** Use the `fls` tool from The Sleuth Kit to recursively parse the directory structure of the disk image and output a timeline body file format with a specified root directory mount path:
  `fls -m / -r partition4.img > body.txt`
- **Building the Timeline:** Convert the raw body data into a human-readable, comma-separated timeline using `mactime`, configuring it to output in a standard database format:
  `mactime -b body.txt -d > timeline.csv`
- **Anomalous Analysis:** Open `timeline.csv` inside spreadsheet software and sort by the timestamp column. Look specifically for outliers based on the challenge hint regarding sloppy timestomping yielding very old timestamps.
- **Identifying the Target:** Locate a highly suspicious file entry dated back to `Wed Jan 02 1985 00:00:00`. Note down the specific metadata (inode) number associated with this record.
- **Extracting Content:** Use the `icat` utility to extract the raw data blocks corresponding to that specific inode number directly out of the disk image:
  `icat partition4.img [meta_number]`
- **Flag Retrieval:** The output returns a Base64-encoded string. Pass this string through a Base64 decoder to reveal the final flag wrapped in the required format.

---

## Insight

Timestamps are highly valuable artifacts in digital forensics, but they can be easily manipulated by user-space tools. However, anti-forensics techniques like timestomping often leave glaring logical artifacts—such as clear dates pointing to the beginning of Unix epoch time, or mismatched metadata structures—because changing every layer of time tracking uniformly across a file system is difficult. Consolidating metadata into an organized timeline allows investigators to establish a clear order of events and easily flag entries that break logical temporal patterns.
