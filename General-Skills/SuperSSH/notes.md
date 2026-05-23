## Challenge: Super SSH

**Author:** Jeffery John  
**Category:** General Skills

### Core Concept

This challenge introduces you to **SSH (Secure Shell)**, which is pretty much the industry standard for logging into and managing remote Linux servers securely. It encrypts all the traffic between your machine and the server, so no one can sniff your password or commands over the network. In CTFs, this is the most common way you'll interact with a live "target" environment.

### Toolbox

- **Terminal / Command Prompt:** Your built-in command-line interface.
- **SSH Client:** Built into Linux and macOS terminals, and available via PowerShell or tools like PuTTY on Windows.

### Methodology

1.  **Parsing the Credentials:** You looked at the connection details provided by the challenge instance, which usually look like this: `ssh -p <PORT> <USERNAME>@<HOST>` along with a password.
2.  **Establishing the Connection:** You opened your terminal and ran the exact command provided.
3.  **Handling the Fingerprint:** If it was your first time connecting, the terminal asked you to verify the host authenticity. You typed `yes` to save the server's fingerprint.
4.  **Authentication:** You entered the given password. (Remember, Linux hides the password as you type it—no asterisks, just invisible text).
5.  **Instant Capture:** Since this was a beginner challenge designed just to test your connection skills, the server was scripted to print the flag to your screen immediately upon a successful login.

### My Insight

--
