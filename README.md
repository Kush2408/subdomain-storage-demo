# Subdomain Storage Demo

A complete practical demonstration of how `localStorage`, `sessionStorage` and `Cookies` behave across subdomains.

---

## ⚙️ Project Structure

| App | Folder | Subdomain |
|-----|--------|-----------|
| LocalStorage | `localstorage-app` | `local.example.com:3000` |
| SessionStorage | `sessionstorage-app` | `session.example.com:3001` |
| Cookies | `cookies-app` | `cookie.example.com:3002` |

---

## 🏗 Subdomains Mapping (in /etc/hosts)

```bash
127.0.0.1 local.example.com
127.0.0.1 local2.example.com
127.0.0.1 session.example.com
127.0.0.1 session2.example.com
127.0.0.1 cookie.example.com


