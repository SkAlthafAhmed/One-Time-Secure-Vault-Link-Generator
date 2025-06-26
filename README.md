# 🔐 One-Time Secure Vault Link Generator

A backend project that allows users to upload a secret (text), get a one-time-use link, and self-destructs the secret after the first access.

No database. No frontend. Just pure secure backend logic using Node.js, Express, and UUID.

---

## 🧠 How It Works – Step-by-Step

### 🪜 Step 1: Client sends a POST request to `/vault`
- A JSON body containing a `"secret"` is sent to the server.
- Example:
  `{ "secret": "My password is 1234" }`

---

### 🪜 Step 2: Server generates a unique link
- The server uses the `uuid` package to create a unique ID.
- It stores the secret in an in-memory object like this:
  `vault[uuid] = "My password is 1234"`
- It responds with the unique one-time link:
  `/vault/uuid-here`

---

### 🪜 Step 3: User accesses the one-time link
- When the link is visited using GET `/vault/:id`, the server checks if the secret exists.
- If it exists:
  - The secret is returned.
  - It is immediately deleted from memory.
- If it doesn't exist (already accessed or wrong ID), the server returns an error message.

---

## 🧰 Tech Stack

- Node.js
- Express.js
- UUID (for unique link generation)
- Replit (for development & hosting)

---

## 📁 File Structure
one-time-secure-vault-link-generator/
├── index.js # Main server logic
├── package.json # Project dependencies
├── README.md # Documentation (this file)


---

## 💼 Project Summary

This project simulates real-world behavior of password vaults like 1Password or Bitwarden. Secrets are securely shared with self-destructing links using in-memory logic — no database required.

---

## 🧪 Testing Flow (Inside Replit)

1. Open Webview > Inspect > Console
2. Run POST request using `fetch()` to `/vault`
3. Copy the returned link
4. Run GET request using `fetch()` to retrieve the secret
5. Try GET again — you’ll see the "not found" error

---

## 📝 Resume Description

**One-Time Vault Link Generator** – Secure backend project that generates self-destructing links for confidential data sharing. Built using Node.js, Express, and UUID. No database. Deployed and tested fully on Replit. Inspired by real-world password manager tools.

---

## ✨ Built by

**Shaik Althaf Ahmed**
