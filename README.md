# Fortify your data security with MS Purview - Regional
Data Security with MS Purview Regional Workshops

This repository contains a series of labs focused on configuring security, compliance, and data protection in a Microsoft Purview  portal. These labs simulate real-world scenarios to help organizations (here using the fictional **Contoso Ltd.**) implement Microsoft Purview features and services to enhance their data security and compliance strategy.

---

## Table of Contents

1. [Lab 1: Managing Compliance Roles and Office 365 Message Encryption](#lab-1-managing-compliance-roles-and-office-365-message-encryption)
2. [Lab 2: Managing Sensitive Information Types](#lab-2-managing-sensitive-information-types)
3. [Lab 3: Working with Sensitivity Labels](#lab-3-working-with-sensitivity-labels)
4. [Lab 4: Creating and Managing DLP Policies](#lab-4-creating-and-managing-dlp-policies)
5. [Lab 5: Configuring Insider Risk Management Prerequisites](#lab-5-configuring-insider-risk-management-prerequisites)
6. [Lab 6: Configuring Insider Risk Management](#lab-6-configuring-insider-risk-management)
7. [Lab 7: Configuring Communication Compliance](#lab-7-configuring-communication-compliance)
8. [Lab 8: Configuring Information Barriers](#lab-8-configuring-information-barriers)
9. [Optional Labs]

---

## Lab 1: Managing Compliance Roles and Office 365 Message Encryption

In this lab, you will create users and assign them roles, teams, and groups in the Office 365 admin center. You'll also activate trial licenses for compliance assessments and configure Office 365 Message Encryption (OME) for external recipients.

- **Exercise 1:** Activating trial licenses for security with Microsoft Purview.
- **Exercise 2:** Modifying default and creating custom OME templates for secure message encryption.

---

## Lab 2: Managing Sensitive Information Types

Here, you’ll create custom sensitive information types and use EDM-based classification for identifying and protecting personal data in emails and documents.

- **Exercise 1:** Creating custom sensitive information types using PowerShell.
- **Exercise 2:** Creating EDM-based classification information types.
- **Exercise 3:** Uploading EDM data sources.
- **Exercise 4:** Creating a keyword dictionary.
- **Exercise 5:** Testing custom sensitive information types.

---

## Lab 3: Working with Sensitivity Labels

You'll create and publish sensitivity labels to categorize and protect documents and emails, especially those related to HR in your organization.

- **Exercise 1:** Enabling support for sensitivity labels in Microsoft 365.
- **Exercise 2:** Creating sensitivity labels for internal and HR use.
- **Exercise 3:** Publishing sensitivity labels.
- **Exercise 4:** Applying sensitivity labels in Word and Outlook.
- **Exercise 5:** Configuring auto-labeling for GDPR-related information.

---

## Lab 4: Creating and Managing DLP Policies

In this lab, you will configure Data Loss Prevention (DLP) policies to protect sensitive data, such as credit card information and employee IDs.

- **Exercise 1:** Creating and modifying DLP policies using Microsoft Purview and PowerShell.
- **Exercise 2:** Managing DLP policies and adjusting priority.
- **Exercise 3:** Enabling file monitoring and creating file policies for OneDrive and SharePoint Online.
- **Exercise 4:** Creating a DLP policy for Power Platform.

---

## Lab 5: Configuring Insider Risk Management Prerequisites

This lab focuses on preparing the infrastructure for Insider Risk Management. You’ll configure Azure devices, onboard them in Azure AD and Intune, and install MDM agents for monitoring and alerts.

---

## Lab 6: Configuring Insider Risk Management

In this lab, you’ll configure Insider Risk Management policies using the sensitive information types and DLP policies created in previous labs. You will learn how to mitigate risks from data theft or leaks and risky browser usage.

---

## Lab 7: Configuring Communication Compliance

In this lab, you will configure communication compliance policies to detect and review sensitive information being communicated through emails within the organization.

- **Exercise 1:** Enabling permissions for communication compliance.
- **Exercise 2:** Setting up groups for communication review.
- **Exercise 3:** Creating and editing communication compliance policies.
- **Exercise 4:** Creating notice templates and configuring user anonymization.
- **Exercise 5:** Testing communication compliance policies.

---

## Lab 8: Configuring Information Barriers

You will configure Information Barriers (IB) to restrict communication between departments as per Contoso's industry regulations.

- **Exercise 1:** Prevent Sales from communicating with Research.
- **Exercise 2:** Prevent Research from communicating with Sales.
- **Exercise 3:** Configure restrictions for Manufacturing to communicate only with HR and Marketing.

---

## Optional Labs

- **Optional Lab A:** Data Governance in Microsoft Purview using Data Catalogue.
- **Optional Lab B:** Exploring the capabilities of Adaptive Protection.
- **Optional Lab C:** Managing Trainable Classifiers.

In these optional labs, you will explore advanced features of Microsoft Purview and learn how to implement data governance and trainable classifiers.

---

## Prerequisites

Before starting these labs, ensure you have:

- Microsoft 365 E5 Trial licenses activated.
- Active Azure Subscription
- PowerShell.
