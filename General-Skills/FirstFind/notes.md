## Challenge: First Find

**Author:** LT 'syreal' Jones

**Category:** General Skills

### Core Concept

This challenge introduces basic **File System Navigation and Searching**. While you can manually click through nested folders on a graphical interface like Windows, it becomes incredibly tedious if there are dozens of empty or hidden directories. Learning how to leverage command-line utilities to scan through directories instantly is a fundamental skill for both developers and security professionals.

### Toolbox

- **unzip:** To extract the contents of the downloaded archive.
- **ls -a:** The "list" command with the "all" flag, which reveals hidden files and directories (those starting with a dot `.`).
- **find (Optional Pro-Tip):** A powerful built-in Linux command used to walk a file hierarchy and locate specific files by name instantly.

### Methodology

1. **Extraction:** You started by unzipping the downloaded archive to reveal a structure of nested directories.
2. **Manual Navigation vs. Terminal Power:** If doing this via a Windows GUI, a user would have to click folder after folder to locate the payload. On Linux, you utilized the terminal to look deeper.
3. **Revealing Hidden Files:** You noted the importance of the `ls -a` command. In Linux, any file or folder starting with a dot (e.g., `.hidden_folder`) is treated as a hidden asset and will not show up with a standard `ls`. Using the `-a` flag ensures absolutely nothing is ignored.
4. **Retrieval:** Once you navigated to the correct directory and listed all assets, you located `uber-secret.txt` and read it to claim the flag.

---

### My Insight

`ls -a` is spot on—hidden directories are a favorite hiding spot for configuration files, SSH keys, and occasional CTF flags!

However, if a challenge creator decides to bury a file inside 100 nested folders, clicking or `cd`-ing through them manually will take forever. Since the challenge description explicitly gave you the filename (`uber-secret.txt`), you can skip the navigation entirely by letting the Linux **`find`** tool do the hunting for you:

```bash
find . -name "uber-secret.txt"

```

- `.` tells the tool to start searching from your current directory.
- `-name "uber-secret.txt"` tells it exactly what filename to look for.

Running this single command will instantly scan every single subfolder (including hidden ones) and print out the exact path to the file (e.g., `./folder1/folder2/hidden/uber-secret.txt`). From there, you can just `cat` that path and grab your flag in under three seconds!
