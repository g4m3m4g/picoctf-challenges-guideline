# 🚩 My picoCTF Journey: Personal Methodology & Guidelines

Welcome! This repository is a collection of my personal notes, thought processes, and technical methodologies developed while navigating the [picoCTF](https://picoctf.org/) challenges.

> **Note:** This is an educational resource documenting my personal growth in Cybersecurity. It is **not** a collection of answers, but a map of how to think.

---

## 🧠 Philosophy & Ethics

To maintain the integrity of the picoCTF competition and follow Carnegie Mellon University's (CMU) Terms of Service, this repository adheres to the following rules:

1.  **No Flags Provided:** I will **never** post a direct flag. The goal is to learn the "How," not just the "Result."
2.  **Focus on Methodology:** I document the logical steps, the tools used, and the underlying security concepts (e.g., RSA padding, SQL injection patterns, or Buffer Overflows).
3.  **Experience-Based:** These guidelines are written from my own perspective and experience—mistakes included!
4.  **No Spoilers:** I aim to provide "hints" and "concepts" rather than "overly-revealing" walkthroughs that take away the learning moment.

---

## 📂 Repository Structure

The challenges are organized by the official picoCTF categories. Each folder contains a conceptual breakdown of the problems I have encountered.

| Category | Description |
| :--- | :--- |
| [**General Skills**](./General-Skills) | Linux command line, encodings (Base64, Hex), and basic CTF hygiene. |
| [**Web Exploitation**](./Web-Exploitation) | Analyzing HTTP headers, Cookies, SQLi, XSS, and Robot files. |
| [**Cryptography**](./Cryptography) | Modern and Classic ciphers, RSA attacks, and hashing algorithms. |
| [**Forensics**](./Forensics) | Network analysis (pcap), steganography, and file structure analysis. |
| [**Reverse Engineering**](./Reverse-Engineering) | Static and dynamic analysis of binaries, Assembly, and Ghidra workflows. |
| [**Binary Exploitation**](./Binary-Exploitation) | Memory corruption, stack smashing, and pwntools implementation. |

---

## 🛠 My Toolkit

Through my journey, these have become my most-used tools. My guidelines often refer to them:
*   **Analysis:** `CyberChef`, `Strings`, `Grep`, `ExifTool`
*   **Web:** `Burp Suite`, `Curl`, `EditThisCookie`

---

## 📖 How to Use These Guidelines

If you are using this repo to help your own learning:
1.  **The 10-Minutes Rule:** Try the challenge on your own for at least 10 minutes before looking for a hint.
2.  **Identify the Gap:** Look at the **"Core Concept"** section in my notes. Do you understand the theory? If not, research the theory first.
3.  **Follow the Logic:** Read the **"Methodology"** section to see how I approached the problem. Try to replicate the logic, not just the commands.
4.  **Reflect:** Once you find the flag, think about how you could have found it faster.

---

## ⚖️ Disclaimer & Compliance

*   **Terms of Service:** This project is intended for personal educational use and is fully compliant with the picoCTF ToS. I do not claim ownership of any picoCTF content.
*   **Non-Commercial:** This repository is, and will always be, free and non-commercial.
*   **Copyright:** All challenge descriptions and files are the property of **Carnegie Mellon University**.

---

## 🤝 Contact & Feedback

Cybersecurity is a collaborative field. If you find a more efficient way to approach a challenge or notice a technical error in my notes, feel free to open a **Pull Request** or an **Issue**. Let's learn together!

**Happy Hacking!** 💻