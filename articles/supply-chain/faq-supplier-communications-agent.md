---
title: Responsible AI for the Supplier Communications Agent (production ready preview)
description: Get answers to frequently asked questions about the AI technology that is used in the Supplier Communications Agent with Copilot in Microsoft Dynamics 365 Supply Chain Management. This FAQ includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 04/25/2025
ms.update-cycle: 180-days
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-Copilot
---

# Responsible AI for the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This FAQ provides answers to frequently asked questions about the AI technology that is used in the Supplier Communications Agent that is available with Copilot in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

## What is the Supplier Communications Agent?

The Supplier Communications Agent provides two capabilities that help purchasers communicate with vendors as part of their daily work:

- *Send follow-up emails to vendors on purchase orders*
- *Speed up updates in purchase orders based on incoming vendor emails*

### Send follow-up emails to vendors on purchase orders overview

It can be tedious to follow up on purchase orders that are sent to vendors if the vendors haven't yet confirmed or delivery is late. It can take significant time to find the correct orders in the system and then write a specific email for each order.

To streamline this process, the system helps you to perform the following actions:

- Create a query to find the purchase orders to follow up on. Configuration is user specific.
- Configure the email generation process for each group of purchase orders that the query finds. The system provides two default queries. One is used to follow up on unconfirmed purchase orders, and the other is used to follow up on late deliveries. Queries are unique for each user. Therefore, you can create and adjust them toy meet your specific business needs.
- Review and modify drafted emails, copy them to your email client, and/or send them. The data that is used to generate the emails comes from the purchase order lines and/or related tables.

### Speed up updates in purchase orders based on incoming vendor emails overview

This capability helps speed up communications with vendors about purchase orders. It enables Copilot to read emails from all or specific vendors.

The Supplier Communications Agent can determine what each email is about (for example, whether it's a purchase order confirmation or a purchase order change request) and which purchase order numbers it applies to. Copilot then matches the information that it extracts from the email to fields in the system and indicates whether there are any changes. Therefore, the purchaser can review just the information that Copilot provides and update the fields in the system as required. They don't have to manually open the purchase order and do all the work themselves. They can then spend the time that they save on other tasks that add more value.

## What are the capabilities of the Supplier Communications Agent?

### Send follow-up emails to vendors on purchase orders capability

The *Send follow-up emails to vendors on purchase orders* capability uses Copilot to generate natural language email texts and subjects, based on information from purchase orders that are found through user-specified queries. User-defined settings such as language tone, length, and urgency are used to adjust the resulting text. Copilot uses the gpt-4o generative AI model to generate the natural language content.

### Speed up updates in purchase orders based on incoming vendor emails capability

The *Speed up updates in purchase orders based on incoming vendor emails* capability must be set up to access the user's email and analyze emails from either all vendors or only specific vendor email addresses. A vendor email address must be stored in each relevant vendor record. Otherwise, Copilot can't recognize it.

The frequency of the email analysis must also be set up.

Copilot classifies each vendor email that it reads into one of the following categories, based on the intent that it detects:

- *Purchase order confirmation* – Copilot detected that the purpose of the email is to confirm one or more purchase orders (all the purchase orders that are mentioned in the email).
- *Requested changes* – Copilot detected that the email contains at least one requested change to a purchase order. For example, the vendor can't deliver the full quantity that was requested, or they can't meet the requested delivery date.
- *Rejection* – Copilot detected that the vendor can't deliver the purchase order as a whole.
- *Other* – Copilot could not identify any of the previous intents.

For the first two categories, the system identifies which purchase orders the email is related to and matches the information in the email to information in the system.

For messages where the vendor requested a change, the system indicates the current information plus the new information in the purchase order. Therefore, the changes are easier to understand.

A review page lists the emails that were identified and classified, and summarizes the information in each message. From this page, you can apply the changes directly to the purchase order that is stored in the system.

## What is the intended use of the Supplier Communications Agent?

The Supplier Communications Agent has the following intended uses:

- The *Send follow-up emails to vendors on purchase orders* capability streamlines the process of following up on purchase orders. By default, it identifies orders that are delayed or unconfirmed. It presents a draft message to purchasers, who can review and modify it, copy it to their email client, and/or send it.
- The *Speed up updates in purchase orders based on incoming vendor emails* capability saves purchasers time by automatically reading emails, extracting information from it, mapping that information to information in the system.

## How was the Supplier Communications Agent evaluated? What metrics are used to measure performance?

The Supplier Communications Agent underwent substantial testing with demo data examples before it was released.

Microsoft relies on users to report inappropriate generated content. If you encounter inappropriate content, report it to Microsoft by using the following feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of the Supplier Communications Agent? How can users minimize the impact of these limitations?

The *Send follow-up emails to vendors on purchase orders* capability uses Copilot to generate email based on information that is retrieved through user-specified queries. You can select which fields to include in the email text. The information in the email is limited to data that comes from purchase orders, purchase order lines, and related information (such as vendor records). Primary contacts that are linked to emails and vendors are used to identify the recipient's name and company. User data is used to identify the sender's name and company.

The generated content should never be used without manual review or supervision.

The system doesn't send emails automatically, unless it's explicitly configured to do so. You're responsible for reviewing and sending each email. 

To configure the system to send emails automatically, an admin must turn on the *Supplier Communications Agent – automatically send emails* feature in Feature management. You should use this capability only after you test and review drafted emails over a long period.

The *Speed up updates in purchase orders based on incoming vendor emails* capability is intended only for vendor collaboration (classification of emails that are related to purchase orders). Therefore, during setup, you must specify which vendors email addresses (either all or only specific ones) the system can read emails from.

## What operational factors and settings allow for effective and responsible use of the Supplier Communications Agent?

When you use the feature, follow these recommendations:

- Make sure that your company has enough control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- When you use the *Send follow-up emails to vendors on purchase orders* capability, always review each email and subject before you use the information that is provided or make decisions based on it.
- When you use the *Speed up updates in purchase orders based on incoming vendor emails* capability, always review each email, intent extraction, and data before you use the information that is provided or make decisions based on it.

## Related information

- [Supplier Communications Agent overview](procurement/supplier-com-agent-overview.md)
