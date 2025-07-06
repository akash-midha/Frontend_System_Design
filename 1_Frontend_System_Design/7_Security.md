# Frontend Application Security

Frontend security is about protecting the app and user data from attacks, misuse, and unauthorized access. 

Key areas include secure authentication, safe content delivery, and protection from common exploits.

---

## 🛡️ Key Security Concepts

### ✅ Authentication vs Authorization
- **Authentication**: Verifying who the user is (e.g., login with username/password).
- **Authorization**: Checking what the user is allowed to do (e.g., access to admin panel).

---

### 🚫 DDoS (Distributed Denial of Service)
- An attack where multiple systems flood a server with requests to **crash or slow it down**.
- Frontend can't prevent it directly, but can use tools like **CDNs and rate limiting** at the backend.

---

### 🧱 CSP (Content Security Policy)
- A browser feature that **prevents XSS attacks** by controlling which resources (scripts, styles, images) the browser is allowed to load.
- Set via HTTP header: `Content-Security-Policy`.

---

### 🌐 CORS (Cross-Origin Resource Sharing)
- A browser mechanism that **controls API access across different domains**.
- Helps prevent malicious domains from accessing sensitive data via JavaScript.
- Configured via response headers like `Access-Control-Allow-Origin`.

---

### 🔓 Man-in-the-Middle (MITM)
- An attacker intercepts communication between user and server (e.g., stealing tokens).
- Prevented using **HTTPS**, **secure cookies**, and **SSL certificates**.

---

## ✅ Summary

| Term             | Description                                                              |
|------------------|---------------------------------------------------------------------------|
| Authentication   | Confirms user identity                                                    |
| Authorization    | Grants access based on roles/permissions                                  |
| DDoS             | Overwhelms server with traffic to crash or slow it                        |
| CSP              | Prevents XSS by restricting what resources can be loaded                  |
| CORS             | Restricts cross-domain API access                                         |
| MITM             | Intercepts data between user & server; mitigated by HTTPS & secure tokens |

