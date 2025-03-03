---
title: Entra ID - User Identity Types
description: Basics of the three types of user identities in Entra ID.
date: 2025-03-03 07:40:00 -0300
tags:
  - entra id
  - authentication
  - IAM
  - account security
  - active directory
  - ad
  - microsoft
---

## Introduction

Microsoft Entra ID (formerly Azure Active Directory) offers various **user** identity types to manage access and authentication in cloud environments. 

This post explores the three primary user identity types in Microsoft Entra ID: **Cloud Identity**, **Synchronized Identity**, and **Guest Identity**, highlighting their characteristics, use cases, pros, and cons.

## **1. Cloud Identity**

### **Definition:**

- A cloud identity is created and managed directly within Microsoft Entra ID (formerly Azure AD) without the need for any on-premises infrastructure.

### **Characteristics:**

- **Creation:** Identities are manually created in Microsoft Entra or through automated provisioning from cloud applications.
- **Management:** All identity management is done in the cloud.
- **Authentication:** Handled directly by Microsoft Entra, leveraging Azure AD authentication methods like MFA, SSO, and Conditional Access.
- **Use Case:** Ideal for organizations that are entirely cloud-based or have no on-premises Active Directory.

### **Pros:**

- Simple setup and management.
- No dependency on on-premises infrastructure.
- Full use of Microsoft Entra cloud-native features.

### **Cons:**

- Limited integration with on-premises resources.
- Not ideal if hybrid scenarios or legacy applications require on-premises authentication.


## **2. Synchronized Identity**

### **Definition:**

- Synchronized identity involves connecting on-premises Active Directory (AD) with Microsoft Entra ID using tools like Azure AD Connect. 

### **Characteristics:**

- **Synchronization:** User accounts, groups, and optionally passwords are synchronized from on-premises AD to Microsoft Entra.
- **Authentication:** Can be cloud-based (password hash synchronization or pass-through authentication) or remain on-premises (federated authentication).
- **Management:** User identities are managed on-premises, with changes synced to the cloud.
- **Use Case:** Perfect for hybrid organizations needing both cloud and on-premises resource access.

### **Pros:**

- Seamless user experience for accessing both on-premises and cloud resources.
- Centralized identity management.
- Supports advanced hybrid scenarios, including legacy app integration.

### **Cons:**
- Requires on-premises infrastructure and management.
- More complex setup and maintenance, particularly with federated authentication.

## **3. Guest Identity**

### **Definition:**

- A guest identity is an external user (e.g., partners, vendors, or customers) who is invited to collaborate within your organization’s Microsoft Entra environment using their existing credentials.

### **Characteristics:**

- **Authentication:** Guests sign in using their own identity provider (e.g., Microsoft account, Gmail, or another Entra ID tenant).
- **Management:** Invited and managed through B2B (Business-to-Business) collaboration features.
- **Permissions:** Controlled through access policies, roles, and Conditional Access within Microsoft Entra.
- **Use Case:** Ideal for enabling secure external collaboration in Microsoft 365, Teams, and other cloud applications.

### **Pros:**

- No need to create and manage separate accounts for external users.
- Simplifies collaboration while maintaining security and compliance.
- Guest access can be tightly controlled through governance policies.

### **Cons:**

- Limited access compared to full internal identities.
- Potential security risks if not managed properly.

## **Summary: When to Use Each Identity Type**

| Feature                    | **Cloud Identity**               | **Synchronized Identity**         | **Guest Identity**                  |
|----------------------------|----------------------------------|----------------------------------|------------------------------------|
| **User Management**        | Cloud-only                       | On-premises, synced to cloud      | External users, managed in cloud    |
| **Authentication Source**  | Microsoft Entra                   | On-premises or cloud              | External identity provider          |
| **Best Use Case**          | Cloud-native organizations       | Hybrid environments               | External collaboration              |
| **Setup Complexity**       | Low                              | High                             | Moderate                           |
| **Infrastructure Required**| None                             | On-premises AD                    | None                               |
| **External User Support**  | Limited                          | Limited                          | Robust                             |

## **Best Practices**

1. **Cloud Identity:**
   - Use for small businesses or cloud-native startups with no legacy systems.
   - Leverage Conditional Access and MFA for enhanced security.

2. **Synchronized Identity:**
   - Ideal for hybrid scenarios and organizations transitioning to the cloud.
   - Regularly monitor Azure AD Connect for sync health.
   - Use password hash sync or pass-through authentication for simplified management.

3. **Guest Identity:**
   - Set up access reviews and policies to prevent over-permissioning.
   - Monitor guest activities through Microsoft Entra audit logs.
   - Implement governance policies to manage guest lifecycle.

## **Conclusion**

Understanding the different user identity types in Microsoft Entra ID is crucial for designing a secure and efficient identity management strategy. By choosing the right identity type based on your organization's needs, you can ensure seamless access to resources while maintaining robust security controls.
