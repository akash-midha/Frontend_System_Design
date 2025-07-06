# Databases and Caching

Caching improves performance by storing frequently accessed or expensive data in temporary storage for faster retrieval.

## Cache

Cache refers to a storage system used to temporarily store data that is frequently accessed or computationally expensive to fetch. 

Caching helps improve performance by reducing the time it takes to retrieve this data.


---

## 🚀 Types of Caching

| Type             | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| **Web Caching**      | Stores web pages, images, or resources in browser cache.                   |
| **Database Caching** | Caches frequent query results in memory to avoid repeated DB hits.         |
| **Memory Caching**   | Uses RAM (e.g., Redis, Memcached) to store temporary, fast-access data.    |
| **HTTP Caching**     | Stores HTTP responses via headers like `Cache-Control`, `ETag`, etc.       |
| **Apollo Caching**   | Apollo Client caches GraphQL responses locally to prevent redundant fetches.|
| **State Management** | Redux, Zustand, or Context store UI state and cached data in memory.       |

---

## 📦 Client-Side Storage Options


### Cookies

Cookies are small pieces of text stored in the browser and automatically sent to the server with every HTTP request.

#### 🔹 Key Features:
- **Used for**: Authentication, session tracking, personalization, analytics.
- **Auto-sent with HTTP requests**: Ideal for maintaining user login state.
- **Security Options**:
  - `HttpOnly`: Prevents JavaScript access for added security.
  - `Secure`: Sends cookie only over HTTPS.
  - `SameSite`: Controls cross-site request behavior.
- **Size Limit**: ~4 KB per cookie.
- **Expiration**: Can be set using `expires` or `max-age`.

#### ✅ Best For:
- Login sessions
- Server-side session management
- Secure, small-scale storage

---

### 🗃️ LocalStorage

LocalStorage provides persistent storage in the browser using a key-value system.

#### 🔹 Key Features:
- **Used for**: UI state, dark mode, user preferences, cached API data.
- **Persistence**: Survives browser restarts and stays until explicitly cleared.
- **Capacity**: ~5–10 MB per origin.
- **Not sent with HTTP requests**
- **Synchronous API**: `localStorage.getItem()`, `setItem()`

#### ✅ Best For:
- Long-term, non-sensitive data
- Preferences and settings
- Client-side caching

---

### 📄 SessionStorage

SessionStorage is similar to localStorage, but the data only lasts for the duration of the page session (i.e., until the tab is closed).

#### 🔹 Key Features:
- **Used for**: Temporary data like form drafts, navigation state, or modal visibility.
- **Lifespan**: Cleared automatically when the tab or browser is closed.
- **Capacity**: ~5–10 MB.
- **Not sent with HTTP requests**
- **Synchronous API**: `sessionStorage.getItem()`, `setItem()`

#### ✅ Best For:
- Temporary session-specific state
- Tab-specific interactions
- One-time UI flags

---

### 📊 Summary Table

| Feature             | 🍪 Cookies           | 🗃️ LocalStorage       | 📄 SessionStorage     |
|---------------------|----------------------|------------------------|------------------------|
| Lifespan            | Customizable         | Until cleared          | Until tab is closed    |
| Capacity            | ~4 KB                | ~5–10 MB               | ~5–10 MB               |
| Sent with HTTP      | ✅ Yes               | ❌ No                  | ❌ No                  |
| JavaScript Access   | ✅ (unless HttpOnly) | ✅                     | ✅                     |
| Use Cases           | Auth, sessions       | Preferences, cache     | Temp tab/session data  |
| Accessible By       | Client & Server      | Client only            | Client only            |
| Security Options    | HttpOnly, Secure     | ❌ No built-in         | ❌ No built-in         |

---

## ⚠️ Security Tips
- Avoid storing sensitive information (e.g., passwords, tokens) in localStorage/sessionStorage as they are accessible via JavaScript.
- Use `HttpOnly` and `Secure` flags for cookies storing auth tokens.
- Prefer short-lived tokens + refresh strategies for authentication.



| Feature           | 🍪 Cookies                | 🗃️ Local Storage           | 📄 Session Storage        |
|-------------------|---------------------------|-----------------------------|---------------------------|
| Lifespan          | Defined by expiry/session | Until manually cleared      | Until tab is closed       |
| Size Limit        | ~4 KB                     | ~5–10 MB                    | ~5–10 MB                  |
| Accessible via JS | ✅                        | ✅                          | ✅                        |
| Sent with HTTP    | ✅ (automatically)         | ❌                          | ❌                        |
| Use Cases         | Auth, session, tracking   | Preferences, cached data    | Temp session data         |

> ⚠️ All are origin-specific (`example.com ≠ sub.example.com`). Cookies can be made `HttpOnly` for security. Avoid storing sensitive data in local/sessionStorage.

---

## 🧰 Advanced Storage

### ✅ **IndexedDB**
- Asynchronous, transactional client-side database.
- Stores large structured data.
- Ideal for offline apps, caching, and complex queries.

---

## 💡 Real-World Analogy

Caching is like keeping **tissues or water on your desk** — frequently used, easily accessible, and avoids repeated trips to the source (server or database).

---

## ✅ Summary

- **Caching** enhances performance across web, DB, memory, and state layers.
- Use **browser storage** (localStorage, sessionStorage, cookies) for client-side persistence.
- Use **IndexedDB** for complex, structured offline storage.
- Choose the right caching/storage method based on data size, lifespan, sensitivity, and access needs.
