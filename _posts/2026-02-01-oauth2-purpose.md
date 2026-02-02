---
layout: post
title: "The Purpose of OAuth2: Why Do We Use Tokens?"
date: 2026-02-01
description: "Understanding the core philosophy of OAuth2: Securely delegating data access without sharing passwords."
---

# The Purpose and Philosophy of OAuth2

Many people think of OAuth 2.0 simply as a tool for "Social Login." However, the true purpose of this protocol is **Delegation**: allowing a third-party application to access your data securely **without you ever having to share your password.**

These challenges become even more pronounced in modern environments like **Microservices Architecture (MSA)** or when integrating various external cloud resources.

---

## 1. Before OAuth2: The "Password Sharing" Dilemma

Before OAuth2, if a third-party app wanted to access your data (e.g., your Google Calendar), you had to **give that app your actual ID and Password.** This approach created three critical security flaws:

1. **Security Vulnerabilities:** If an app stores or exchanges your password in plain text, the risk of a total credential leak increases exponentially.
2. **Excessive Permissions:** Providing a password gives the app unlimited access to everything (emails, payments, settings, etc.). This makes it impossible to implement **Access Control Lists (ACL)** or granular authorization.
3. **Difficulty in Revocation:** You cannot revoke access for just one specific app. To stop an app from accessing your data, you would have to change your main password, which breaks every other service you use.



---

## 2. Three Core Objectives of OAuth2

### 🔒 Password Privacy
Users only enter their passwords into 'Trusted Services' (e.g., Google, Azure, GitHub). Instead of a password, the requesting application receives an **'Access Token'**—a dedicated credential with a limited lifespan.

### 🛡️ Granular Authorization (Scope)
OAuth2 operates on the principle of **'Least Privilege.'**
- "This app can only **Read** my contacts, but it cannot **Delete** them."
- Through `Scope` settings, you can control exactly what functions an application can perform.

### ⚡ Standardized Delegation
If every service communicated using its own proprietary method, development costs would be astronomical. OAuth2 defines a **standardized framework (RFC 6749)**, ensuring that any platform can exchange authorization securely using the same mechanism.

---

## 3. A Simple Analogy: The Hotel Key Card System

The mechanics of OAuth2 are very similar to staying at a hotel.

* **ID/Password:** This is the **Master Key** held by the hotel owner that opens every room. You never give this to a guest.
* **Authentication:** This is the process of checking your ID at the front desk. While OAuth2 focuses on *Authorization*, **OIDC (OpenID Connect)** adds this identity layer on top of OAuth2.
* **Access Token:** This is the **Key Card** issued by the front desk.
    * The card only opens **specific rooms (Scopes)**.
    * The card **Expires** automatically after your checkout time.
    * If lost, you can deactivate the card without changing the hotel's master locks. (Even if a guest keeps the physical card, it becomes useless once invalidated in the system.)



---

> **Summary**
> OAuth2 is a technology about the **'Transfer of Trust.'** By allowing users to maintain direct control over **Authorization**, it creates a more secure and convenient web ecosystem.
