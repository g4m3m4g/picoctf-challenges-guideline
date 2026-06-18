## Challenge Name

Time Machine

## Author

Jeffery John

## Category

General Skills

---

## Core Concept

This challenge introduces basic version control forensics using Git. The goal is to retrieve sensitive data or flags that are no longer visible in the current working directory but remain preserved within the project's repository history. It highlights how metadata and past revisions can leak information if a repository is distributed without being properly cleaned.

## Toolbox

- **wget:** To download the challenge archive.
- **unzip:** To extract the files from the zipped package.
- **Linux Command Line Utilities:** `cd` to navigate directories and `cat` to read file contents.
- **Git:** To inspect the repository's commit logs and history.

---

## Methodology

- **Environment Setup:** Download the `challenge.zip` file using `wget` and extract its contents using the `unzip` command.
- **Initial Inspection:** Navigate into the extracted folder and read the contents of `message.txt` using `cat`. The file contains a hint: "This is what I was working on, but I'd need to look at my commit history to know why..."
- **Repository Exploration:** Recognize that the directory is an active Git repository. Run the `git log` command to view the commit history.
- **Flag Retrieval:** Inspect the commit messages and changes listed in the log to locate and extract the flag.

---

## Insight

Deleting a file or modifying its contents in your current workspace does not erase it from a Git repository's memory. The entire purpose of version control is to track every change ever made. When deploying code or sharing projects publicly, developers must ensure that sensitive information—like API keys, passwords, or flags—is never committed in the first place, as anyone with access to the `.git` folder can easily roll back the clock to expose it.
