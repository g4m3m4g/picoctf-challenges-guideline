## Challenge: endianness

**Author:** Nana Ama Atombo-Sackey

**Category:** General Skills

### Core Concept

This challenge focuses on **Endianness**, which describes the order in which bytes of multi-byte data are stored in computer memory.

- **Big-Endian:** Stores the most significant byte (the "big end") at the lowest memory address. This matches how humans naturally read numbers from left to right.
- **Little-Endian:** Stores the least significant byte (the "little end") at the lowest memory address. This is the standard native format for x86 and x64 Intel/AMD processors.

### Toolbox

- **Netcat (nc):** To interact with the challenge server.
- **ASCII to Hex Table / Converter:** To translate the random 5-letter word into its raw byte values.

### Code Walkthrough & Logic

You broke down the source code perfectly! Here is a summary of how the server handles the game mechanics under the hood:

- **`find_little_endian`:** Reverses the string order. It loops backward from the last character to the first, printing each character's ASCII value as a 2-digit uppercase Hex string (`%02X`).
- **`find_big_endian`:** Keeps the standard string order. It loops forward from the first character to the last, printing each ASCII value directly to Hex.
- **`main` (The Game Loop):** The server spawns a random 5-letter word. It forces you through two gated verification checks using `scanf()` and `strncmp()`. You cannot guess or pass to the Big-Endian gate without solving the Little-Endian gate first. Passing both prompts the server to read `flag.txt` and display your reward.

---

### Step-by-Step Solving Execution

When you run the `nc` command, the server will hand you a randomized 5-letter word. Let's trace an execution example using the word **`picoS`**:

#### 1. Translate the Characters to Hex

First, look up the hexadecimal value of each character on an ASCII chart:

- `p` = `70`
- `i` = `69`
- `c` = `63`
- `o` = `6F`
- `S` = `53`

#### 2. Format for Little-Endian (Round 1)

Take the hex representations and reverse their sequence, starting from the **last character to the first**:

- _Sequence:_ `S` -> `o` -> `c` -> `i` -> `p`
- _Your Input:_ **`536F636970`**

#### 3. Format for Big-Endian (Round 2)

Take the hex representations and arrange them in their **normal, standard reading order** from left to right:

- _Sequence:_ `p` -> `i` -> `c` -> `o` -> `S`
- _Your Input:_ **`7069636F53`**

Once you submit the second string accurately, the server triggers its success block and drops the flag.

### My Insight

-
