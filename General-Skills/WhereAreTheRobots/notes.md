## Challenge: where are the robots

**Author:** zaratec / Danny

**Category:** Web Exploitation

### Core Concept

This challenge introduces the **`robots.txt`** file, which is a fundamental component of web infrastructure and Open Source Intelligence (OSINT). The `robots.txt` file is a plain text file placed in the root directory of a website to give instructions to automated web crawlers and search engine bots (like Googlebot). It dictates which parts of the site the bots are allowed or not allowed to index using directives like `Allow` and `Disallow`.

A common security misconception is using `robots.txt` to hide sensitive directories. Because this file must be publicly readable so bots can find it, attackers frequently check it first to discover hidden pages or admin panels that the developers were hoping to keep private.

### Toolbox

- **Web Browser:** To navigate the website and view the target files directly.
- **URL Manipulation:** Manually editing the web address path in the browser bar.

### Methodology

1. **Clue Analysis:** You looked at the challenge title and the main page header: _"Where are the robots?"_ This was a clear wordplay hint pointing directly toward the standard `robots.txt` path.
2. **Inspecting the Directory:** You appended `/robots.txt` to the end of the challenge instance URL.
3. **Parsing the Directives:** The server displayed the raw text configuration:

```text
User-agent: *
Disallow: /cc6b1.html

```

- `User-agent: *` means these rules apply to all automated bots.
- `Disallow: /cc6b1.html` explicitly tells search engines _not_ to look at or index that specific HTML page.

4. **Exploitation:** Knowing that the disallowed path is a hidden page, you bypassed the bot restrictions by manually typing `/cc6b1.html` into your browser.
5. **Capture:** Navigating to the hidden page revealed the flag.

---

### My Insight

Checking `robots.txt` is one of the very first manual steps an auditor or attacker takes during the reconnaissance phase of a web application assessment.

In real-world pentesting, developers often make the mistake of putting paths like `/admin`, `/backup`, or `/staging` inside `robots.txt` to prevent them from showing up on Google search results. Ironically, this provides a map of high-value targets for malicious actors.

If you want to automate this check during larger web assessments, you can use security tools like **Nikto**, **Dirsearch**, or **Gobuster**. These tools automatically scan for `robots.txt` and parse out any disallowed entries instantly so you don't have to check them by hand!
