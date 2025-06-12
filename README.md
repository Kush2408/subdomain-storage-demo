# Subdomain Storage Demo Project

A fully practical project demonstrating how `localStorage`, `sessionStorage`, and `Cookies` behave across domains and subdomains.

---

## 📖 Purpose

This project helps to:

- Understand how browser storage works with subdomains.
- Learn how cookies can be shared across subdomains.
- Demonstrate common interview questions on storage, subdomain isolation, and authentication patterns (SSO).
- Simulate real-world multi-app architecture using subdomains.

---

## 🌐 Subdomains Overview

The following subdomains are simulated for this demo:

| Subdomain | Purpose |
|-----------|---------|
| `local.example.com` | Demonstrates `localStorage` |
| `session.example.com` | Demonstrates `sessionStorage` |
| `cookie.example.com` | Demonstrates `Cookies` |
| `local2.example.com` | Additional subdomain for localStorage isolation |
| `session2.example.com` | Additional subdomain for sessionStorage isolation |

> ⚠ **Note:** These subdomains are simulated locally via the `hosts` file.

---

## ⚙️ Subdomain Setup (hosts file)

Modify your `/etc/hosts` file:

### Windows:

1. Open Notepad as Administrator.
2. Open file: `C:\Windows\System32\drivers\etc\hosts`
3. Add these lines at the bottom:

```txt
127.0.0.1 local.example.com
127.0.0.1 local2.example.com
127.0.0.1 session.example.com
127.0.0.1 session2.example.com
127.0.0.1 cookie.example.com


| App Folder           | Subdomain                  | Storage Type     |
| -------------------- | -------------------------- | ---------------- |
| `localstorage-app`   | `local.example.com:3000`   | `localStorage`   |
| `sessionstorage-app` | `session.example.com:3001` | `sessionStorage` |
| `cookies-app`        | `cookie.example.com:3002`  | `Cookies`        |


1️⃣ Clone the repository
git clone https://github.com/YOUR-USERNAME/subdomain-storage-demo.git
cd subdomain-storage-demo


2️⃣ Install dependencies
Run the following for each app:
cd localstorage-app && npm install
cd ../sessionstorage-app && npm install
cd ../cookies-app && npm install

3️⃣ Run each app (in separate terminal windows)
cd localstorage-app && npm start  # runs on port 3000
cd ../sessionstorage-app && npm start  # runs on port 3001
cd ../cookies-app && npm start  # runs on port 3002


4️⃣ Access the apps
| Subdomain      | URL                               |
| -------------- | --------------------------------- |
| localStorage   | `http://local.example.com:3000`   |
| sessionStorage | `http://session.example.com:3001` |
| cookies        | `http://cookie.example.com:3002`  |


🔬 Storage Behavior Summary
| Subdomain              | localStorage | sessionStorage | Cookies (`domain=.example.com`) |
| ---------------------- | ------------ | -------------- | ------------------------------- |
| `example.com`          | Separate     | Separate       | ✅ Shared                        |
| `local.example.com`    | Separate     | Separate       | ✅ Shared                        |
| `session.example.com`  | Separate     | Separate       | ✅ Shared                        |
| `cookie.example.com`   | Separate     | Separate       | ✅ Shared                        |
| `local2.example.com`   | Separate     | Separate       | ✅ Shared                        |
| `session2.example.com` | Separate     | Separate       | ✅ Shared                        |


💡 Storage Deep Explanation
| Storage Type       | Scope                                     | Lifespan                         | Shared Between Subdomains? | Use Case                   |
| ------------------ | ----------------------------------------- | -------------------------------- | -------------------------- | -------------------------- |
| **localStorage**   | Origin (protocol+domain+port)             | Persistent                       | ❌ No                       | User preferences, settings |
| **sessionStorage** | Origin + Browser Tab                      | Until tab close                  | ❌ No                       | Per-tab form data, wizards |
| **Cookies**        | Domain (can be shared via `.example.com`) | Expire by `max-age` or `expires` | ✅ Yes                      | Authentication, SSO, CSRF  |
