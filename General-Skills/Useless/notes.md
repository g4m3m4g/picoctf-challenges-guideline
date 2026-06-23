## Challenge Name

useless

## Author

Loic Shema

## Category

General Skills

---

## Core Concept

This challenge highlights the importance of thorough system reconnaissance and utilizing built-in Unix documentation systems. Rather than embedding the flag inside the execution logic of the script itself, the author hidden it within the system's manual pages (man pages). It teaches players to look beyond just the raw source code and check the accompanying system metadata and documentation.

## Toolbox

- **SSH Client:** To connect to the remote challenge server.
- **Linux Command Line Utilities:** `ls` to list files and `cat` to view script contents.
- **Man System:** `man` to view the reference manuals interface.

---

## Methodology

- **Remote Access:** Establish an active terminal session to the target server using the provided SSH credentials.
- **Initial Reconnaissance:** Run `ls` in the user's home directory to inspect the available files. Identify an executable shell script named `useless`.
- **Execution Attempt:** Run the script using `./useless`. The program outputs a simple text message: `"Read the code first"`.
- **Source Code Review:** Use `cat useless` to dump the script contents and inspect its internal logic. The code appears to be a basic wrapper script handling conditional statements for standard arithmetic operations (addition, subtraction, multiplication, and division).
- **Identifying the Hint:** Notice that the catch-all `else` block at the very bottom of the execution tree prints a different clue: `"Read the manual"`.
- **Flag Retrieval:** Recognize that "manual" refers to the built-in Linux manual layout. Execute the `man useless` command to open the documentation page for the script, where the hidden flag is documented.

---

## Insight

Software documentation can often hold forgotten secrets, old configurations, or overlooked blocks of information. When performing a security audit or a penetration test, reading manual pages, help files (`--help`), and localized deployment guides is a crucial part of information gathering. Developers frequently bundle notes or historical details into these documentation files, making them prime targets for uncovering subtle configuration leaks.
