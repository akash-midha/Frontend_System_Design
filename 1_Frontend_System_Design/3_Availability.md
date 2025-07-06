# Availability

**Availability** is the ability of a system to remain operational and accessible when needed. High Availability (HA) ensures minimal downtime, even during hardware or software failures, making the system reliable and user-friendly.

---

## 🌐 Offline Availability (Service Workers)

Offline availability allows web or mobile apps to function without internet access — critical for Progressive Web Apps (PWAs) or apps in low-connectivity environments.

### 🔧 Enabled by **Service Workers**:
- **Caching**: Store static assets (HTML, CSS, JS, images) locally for offline access.
- **Request Interception**: Serve cached responses when offline.
- **Background Sync**: Queue user actions and sync them with the server once back online.

### ✅ Why It Matters:
- **Seamless UX** even without internet.
- **Improved reliability** in poor network areas.
- **Faster performance** through cached content.

---

## 🧰 Supporting Technologies for Offline Mode

- **IndexedDB**: A client-side database for storing structured data offline.
- **LocalStorage / SessionStorage**: Basic key-value storage for small data (e.g., preferences).
- **Background Sync API**: Defers important actions until the device reconnects.

---

## ⚖️ Availability During High Traffic (Load Balancing)

**Load balancing** distributes incoming traffic across multiple servers to:
- **Prevent overload**
- **Ensure uptime**
- **Maintain performance under heavy usage**

### 🔄 Common Strategies:
- **Round-Robin**
- **Least Connections**
- **IP Hashing**

Load balancers can be software-based (e.g., NGINX, HAProxy) or hardware appliances.

---

## ✅ Summary

High availability is achieved by combining **offline support** (via service workers, IndexedDB, etc.) with **load balancing** during high traffic. Together, they ensure that applications remain responsive, reliable, and accessible — both in low-connectivity scenarios and during server load spikes.
