# 🔐 GoodPass

## Live Demo: [https://saintberat.github.io/goodpass/](https://saintberat.github.io/goodpass/)

A lightweight, privacy-first web application that analyzes password strength in real time and checks for known data breaches without ever exposing your credentials.

Everything runs entirely in your browser — your password never leaves your device (breach checks use k-anonymity so raw passwords are never transmitted).

---

## 🔍 How It Works

### ⚙️ Core Logic

As you type your password:
- Character composition is analyzed in real time
- Information entropy is calculated
- Estimated brute-force cracking time is computed
- Strength tier is determined
- UI & meter update dynamically

---

### 🔐 Entropy Calculation

Password strength is evaluated via **information entropy (bits)**:

- **Character Pool ($N$):** Checks for lowercase ($26$), uppercase ($26$), numbers ($10$), and symbols ($32$).
- **Formula:** 
  $$\text{Entropy} = L \times \log_2(N)$$
  *(where $L$ is length and $N$ is pool size)*

Higher entropy means an exponentially larger search space for brute-force attacks.

---

### ⏱️ Cracking Time Estimation

- Assumes an attacker capable of **$10\text{ GH/s}$** ($10^{10}$ hashes per second)
- Computes time based on $2^{\text{Entropy}} / 10^{10}$ seconds
- Formatted into human-readable units (seconds, minutes, hours, days, months, years, or centuries)

---

### 📊 Strength Levels

Categorized into 5 distinct levels based on entropy thresholds:

- **Critical** ($< 28\text{ bits}$)
- **Weak** ($28 - 35\text{ bits}$)
- **Medium** ($36 - 59\text{ bits}$)
- **Strong** ($60 - 79\text{ bits}$)
- **Excellent** ($\ge 80\text{ bits}$)

The progress bar color and width adapt immediately to match the level.

---

### ✅ Rule Checklist

Evaluates the password against industry-standard criteria:
- At least 8 characters
- Uppercase letters (`A–Z`)
- Lowercase letters (`a–z`)
- Numbers (`0–9`)
- Special characters / symbols
- No consecutive repeated characters (e.g., `aaa`)

---

### 👁️ Visibility Toggle

- Toggle between masked (`password`) and plain text (`text`) mode
- Fully client-side with accessibility support

---

### 🧨 Breach Detection via k-Anonymity

Checks whether the password has appeared in compromised credential databases (Have I Been Pwned API):

1. Computes the **SHA-1** hash of the password locally in the browser using the Web Crypto API.
2. Sends **only the first 5 characters** of the hash prefix to the API.
3. The API returns matching hash suffixes and breach counts.
4. The browser searches for the remaining 35 characters locally.

> **Your password is never sent to any server in whole form.**

---

### 🌐 Language Support

GoodPass includes built-in **English** and **Turkish** language options with instant switching and local preference storage.

---

### 📄 License

MIT License. Free to use, fork, and contribute!

<!-- sync-activity: 2026-10-25T17:00:36Z (af1068ad) -->
