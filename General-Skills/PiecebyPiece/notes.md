## Challenge: Piece by Piece

**Author:** Yahaya Meddy  
**Category:** General Skills

### Core Concept

This challenge is a great lesson in **File Reconstruction and Handling** in Linux. In security, you'll often run into situations where a large payload, a memory dump, or an exfiltrated file has been split into smaller fragments to bypass network limits or security filters. Knowing how to stitch these pieces back together into a functional archive is a foundational command-line skill.

### Toolbox

- **cat:** Short for "concatenate," this tool reads sequential data and can be used to merge multiple files into one.
- **unzip:** A standard utility used to decompress and extract files from `.zip` archives.

### Methodology

1.  **File Concatenation:** You looked at your home directory and saw multiple file parts. Instead of dealing with them individually, you used `cat part1 part2 part3 ... > combined.zip` (or used a wildcard like `cat part* > combined.zip`) to merge them back into a single, cohesive ZIP file.
2.  **Reading Instructions:** You checked `instruction.txt` to grab the password needed to unlock the archive.
3.  **Extraction:** With the complete archive and the password ready, you ran `unzip combined.zip`, entered the password when prompted, and extracted the hidden contents.
4.  **Retrieval:** The extraction process dropped `flag.txt` into your directory, which you read to find the flag.

### My Insight

The `cat` command is incredibly powerful because in Linux, "everything is a file." Whether it's a text file or a binary zip file, `cat` doesn't care—it just glues the raw bytes together in the order you specify. A great real-world companion to this is the `split` command, which does the exact opposite. If you ever need to exfiltrate a massive database backup over a slow connection, you'd use `split` to break it up, and then use `cat` just like you did here to put it back together on your own machine!
