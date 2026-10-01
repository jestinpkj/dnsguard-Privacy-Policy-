# Privacy Policy for DNSGuard

**Last Updated:** October 2, 2026  
**Effective Date:** October 2, 2026  

Welcome to **DNSGuard** ("we," "our," or "us"). We are committed to protecting your privacy and ensuring your personal data remains completely confidential. This Privacy Policy explains our practices regarding the information handled through the **DNSGuard** Android application (the "App", package name `com.dnsguard.app`).

**Summary:**  
DNSGuard is designed from the ground up as a zero-knowledge, privacy-first application. **We do not collect, store, sell, or share any personal information, browsing history, or DNS queries.** All DNS traffic encryption and cache management occur locally on your device or directly between your device and trusted upstream DNS resolvers using DNS-over-HTTPS (DoH).

---

## 1. Information We Do NOT Collect

We believe that your personal data belongs solely to you. Specifically:
- **No Personal Identifiable Information (PII):** We do not collect names, email addresses, phone numbers, postal addresses, or user identifiers.
- **No Account Registration:** You do not need to register an account, log in, or provide any credentials to use the App.
- **No Browsing History or Query Logs:** We do not record, log, or maintain records of domain names, websites visited, search queries, or network destinations.
- **No Persistent Tracking or Device Identifiers:** We do not collect Android Advertising IDs (AAID), IMEI numbers, MAC addresses, or persistent device fingerprints.
- **No Third-Party Analytics or Advertising SDKs:** DNSGuard does not include advertising networks (e.g., Google AdMob), tracking scripts, or analytics SDKs (e.g., Google Analytics, Firebase Analytics, Meta SDK).

---

## 2. Information Handled Locally on Your Device

To provide high-performance DNS encryption and real-time network performance monitoring, DNSGuard processes certain data strictly within temporary, volatile device memory (RAM):

- **DNS Queries:** When DNSGuard is enabled, local DNS lookups (port 53) are routed through the App's local native engine (`rust-dns-core`) to be encapsulated into encrypted DNS-over-HTTPS requests. These queries are never written to disk or sent to any server controlled by us.
- **In-Memory Cache:** DNSGuard maintains an in-memory, short-lived (60-second TTL) Least Recently Used (LRU) cache of DNS records locally to improve query response times and reduce network overhead. This cache is wiped when the app closes or the service stops.
- **Real-Time Operational Metrics:** The app calculates live counters (such as total query count, cache hit count, bytes transferred, and average latency in milliseconds) exclusively to display statistics on your active dashboard. These metrics are stored in volatile RAM and are not saved permanently or transmitted anywhere.

---

## 3. Android `VpnService` Disclosure (Google Play Compliance)

DNSGuard utilizes Android’s `VpnService` API in accordance with Google Play's Developer Program Policies:

- **Split-Tunnel Architecture:** DNSGuard operates exclusively as a **DNS-Only Split-Tunnel VPN**. It configures virtual routing specifically and only for the local virtual DNS resolver IP address (`10.255.0.2/32` and `fd00::2/128`).
- **No Traffic Interception:** All other non-DNS network traffic (web browsing, streaming media, downloads, messaging, and app data) completely bypasses the VPN tunnel and travels through your regular network interfaces.
- **Purpose:** The `VpnService` is used strictly to capture unencrypted local UDP/TCP DNS packets on your device and translate them into secure, encrypted DNS-over-HTTPS (DoH) requests.
- **No Remote Intermediary Server:** We do not route your traffic through any VPN server, proxy, or server infrastructure owned or operated by DNSGuard. DNS queries are transmitted directly to the configured upstream DNS-over-HTTPS provider.

---

## 4. Upstream DNS Resolvers (Third-Party Services)

When resolving domain names, encrypted DNS queries (using DNS-over-HTTPS / DoH) are routed directly from your device to high-reputation, privacy-conscious public DNS providers. The App supports:

1. **Cloudflare DNS** (`cloudflare-dns.com` / `1.1.1.1`, `1.0.0.1`)  
   [Cloudflare Privacy Policy](https://www.cloudflare.com/privacypolicy/)
2. **Google Public DNS** (`dns.google` / `8.8.8.8`, `8.8.4.4`)  
   [Google Privacy Policy](https://policies.google.com/privacy)
3. **Quad9** (`dns.quad9.net` / `9.9.9.9`, `149.112.112.112`)  
   [Quad9 Privacy Policy](https://www.quad9.net/privacy/policy/)
4. **Local System DNS:** If encrypted upstream connectivity is completely unreachable, the app may temporarily use your network's default DNS provider as an emergency fallback to preserve your device's network connectivity.

*Note: Queries sent to upstream providers are governed by their respective privacy policies. We encourage you to review their practices.*

---

## 5. Android Permissions Explained

DNSGuard requests only permissions that are strictly necessary to deliver its core DNS protection functionality:

| Permission | Purpose |
| :--- | :--- |
| `android.permission.BIND_VPN_SERVICE` | Required to create the local split-tunnel loopback interface that captures local DNS requests. |
| `android.permission.INTERNET` | Required to send encrypted DNS-over-HTTPS (DoH) queries to upstream resolvers. |
| `android.permission.ACCESS_NETWORK_STATE` & `CHANGE_NETWORK_STATE` | Used to detect transitions between networks (e.g., Wi-Fi to Cellular) to ensure seamless socket reconnection. |
| `android.permission.FOREGROUND_SERVICE` & `FOREGROUND_SERVICE_SYSTEM_EXEMPTED` | Ensures the DNS protection service remains active in the background without being prematurely terminated by the OS. |
| `android.permission.POST_NOTIFICATIONS` | Used to display the mandatory foreground service notification showing current DNS status and toggle controls. |
| `android.permission.RECEIVE_BOOT_COMPLETED` | Allows DNSGuard to automatically restore DNS protection when your device reboots (if enabled in settings). |

---

## 6. Data Security

The security of your DNS communication is our primary objective:
- All DNS queries forwarded upstream utilize industry-standard Transport Layer Security (TLS 1.2 / TLS 1.3) with standard root certificate verification via `rustls` and Mozilla's root certificate bundle (`webpki-roots`).
- Encrypted DNS-over-HTTPS protects your lookups against ISP inspection, eavesdropping, man-in-the-middle (MitM) attacks, and DNS spoofing/hijacking.

---

## 7. Children's Privacy (COPPA Compliance)

DNSGuard is not directed at children under the age of 13 (or under 16 in the European Economic Area). Because DNSGuard does not collect, retain, or process any personal information from any user, we do not knowingly collect personal data from children.

---

## 8. User Rights (GDPR & CCPA/CPRA Compliance)

Depending on your jurisdiction (such as under the General Data Protection Regulation (GDPR) in the EU/EEA, or the California Consumer Privacy Act (CCPA/CPRA) in the United States), individuals possess legal rights concerning their personal information:
- The right to access, rectify, or delete personal data.
- The right to opt-out of data collection or sales.
- The right to data portability.

**Because DNSGuard collects zero personal information and maintains no user identifiers or remote databases, we hold no personal data to disclose, modify, or delete.**

---

## 9. Changes to This Privacy Policy

We may update this Privacy Policy periodically to reflect updates in app functionality, operational practices, or legal requirements. Any modifications will be posted within this document alongside an updated "Last Updated" date. We recommend checking this policy periodically.

---

## 10. Contact Us

If you have any questions, concerns, or inquiries regarding this Privacy Policy or DNSGuard's security practices, please contact us:

- **Developer / Organization:** DNSGuard Project Team
- **Contact Email:** [soon001soon@gmail.com](mailto:soon001soon@gmail.com)
- **Package Name:** `com.dnsguard.app`
