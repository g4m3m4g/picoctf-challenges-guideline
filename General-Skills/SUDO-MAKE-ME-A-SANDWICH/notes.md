## SUDO MAKE ME A SANDWICH

**Author:** Darkraicg492  
**Category:** General Skills / Privilege Escalation

### Core Concept

This challenge is a classic lesson in **Linux Privilege Escalation**. It revolves around misconfigured **sudo permissions** (found in the `sudoers` file). Even if you aren't allowed to run common commands like `cat` as root, being allowed to run a powerful tool—like a text editor—with root privileges can be exploited to "break out" into a root shell.

### Toolbox

- **SSH:** To access the remote challenge environment.
- **sudo -l:** The most important command for checking your current user's sudo privileges.
- **Emacs:** A highly extensible text editor that allows running shell commands internally.

### Methodology

1.  **Access & Identification:** You SSH'd into the server and found `flag.txt`. A quick `ls -l` showed the file is owned by root and is only readable by root.
2.  **Permission Testing:** You tried `sudo cat flag.txt`, but the system blocked it, explicitly stating that `ctf-player` isn't allowed to run `cat` as root.
3.  **Privilege Enumeration:** You ran `sudo -l` to see what you _are_ allowed to do. You discovered that you can run `/bin/emacs` with sudo privileges without needing a root password.
4.  **Exploitation (The Breakout):** You launched the editor using `sudo emacs`. Once inside, you used a built-in feature to escape the editor's constraints:
    - Hit `Alt + X` (or `M-x` in Emacs terminology).
    - Typed `shell` and hit Enter.
5.  **Victory:** Because Emacs was running as root, the shell it spawned also had root privileges. From there, you simply ran `cat flag.txt` to get the flag.

### My Insight

This is a perfect example of why the **Principle of Least Privilege** is so important. Giving a user sudo access to a text editor (like Emacs, Vim, or Nano) is essentially the same as giving them full root access, because almost every editor has a way to execute system commands or open a shell. If you ever find a sudo permission for a binary you don't recognize, check **GTFOBins**—it's a legendary site that lists exactly how to exploit different Linux binaries to get a shell!
