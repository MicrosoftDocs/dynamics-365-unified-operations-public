---
title: Responsible AI for Supplier Communications Agent (production ready preview)
description: This FAQ provides answers to frequently asked questions about the AI technology that is used in Supplier Communications Agent with Microsoft Copilot in Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 04/25/2025
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-Copilot
---

# Responsible AI for Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This FAQ provides answers to frequently asked questions about the AI technology that is used in the *Supplier Communications Agent* with Microsoft Copilot in Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

## What is the Supplier Communications Agent?

The *Supplier Communications Agent* provides a set of two capabilities that help purchasers in their daily work communicating with vendors. The two capabilities are:

- Send follow-up emails to vendors on purchase orders
- Speed up updates in purchase orders based on incoming vendor emails

### Send follow-up emails to vendors on purchase orders overview

Following up on purchase orders sent to vendors when the vendors haven't confirmed yet or when delivery is late can be a tedious task. It can take significant time to find the right orders in the system and then author a specific email for each of the orders.

To streamline this process, the system helps you to:

- Create a query to find the purchase orders to follow up on. Configuration is user specific.
- Configure the email creation process for each group of purchase orders (result of the query). By default, the system provides two queries (follow up on unconfirmed purchase orders and follow up on late deliveries). Queries are unique for each user, so you can create and adjust them to best match your own business needs.
- Review and possibly modify drafted emails, copy them to your email client, and/or send them. Data used to compose the email comes from the purchase order lines and/or related tables.

### Speed up updates in purchase orders based on incoming vendor emails overview

This capability helps speed up communications vendors about purchase orders. It allows Copilot to read emails from all or certain specified vendors.

The Supplier Communications Agent understands what each email is about (such as purchase order confirmation, purchase order change request, or other intent) and which purchase order numbers it applies to. Then Copilot matches information extracted from the email to the fields in the system, indicating if there are any changes. This way, the purchaser can just review this information and update the fields in the system as needed rather than manually opening the purchase order and doing all the work, thereby saving time that can be used on other more value-adding tasks.

## What are the capabilities of Supplier Communications Agent?

### Send follow-up emails to vendors on purchase orders capability

The *Send follow-up emails to vendors on purchase orders* capability uses Copilot to generate natural-language email texts and subjects. It uses information from purchase orders that are found based on user-defined queries. Additionally, user-defined settings such as language tone, length, and urgency are used to adjust the resulting text. Copilot uses the *gpt-4o* generative AI model to generate the natural-language content.

### Speed up updates in purchase orders based on incoming vendor emails capability

The *Speed up updates in purchase orders based on incoming vendor emails* capability must be set up to allow access to the user's email and indicate whether it should analyze emails from all vendors or only from certain vendor email addresses. A vendor email address must be stored in each relevant vendor record so Copilot can recognize them.

The capability must also be set to control how often the system analyzes emails.

When Copilot reads an email, it classifies it by intent using the following categories:

- *Purchase order confirmation* – Copilot detected that the purpose of the vendor email is to confirm one or more purchase orders (all the purchase orders mentioned in the email)
- *Requested changes* – Copilot detected that the vendor email contains at least one requested change to a purchase order (for example, the vendor can't deliver the full quantity requested or can't meet the requested delivery date).
- *Rejection* – Copilot detected that the vendor can't deliver the purchase order as a whole.
- *Other* – Copilot couldn't identify any of the previous intents.

For the first two intent categories, the system identifies which purchase orders the email relates to and matches the information in the email to information in the system.

For messages where the vendor requests a change, the system indicates the current information plus the new information in the purchase order, making it easier to understand the changes.

A review page lists the classified emails identified and classified and summarizes the information contained in each message. From there, you can choose to apply the changes directly to the purchase order stored in the system.

## What is the intended use of the Supplier Communications Agent?

The *Supplier Communications Agent* has the following intended uses:

- The *Send follow-up emails to vendors on purchase orders* capability streamlines the process of following up on purchase orders. By default, it identifies orders that are delayed or unconfirmed. Purchasers are presented with a draft message that they can be review and optionally modify, copy to email client, and/or send.
- The *Speed up updates in purchase orders based on incoming vendor emails* capability saves purchasers time by automatically reading emails, extracting the information, mapping it to the system.

## How were was the Supplier Communications Agent evaluated? What metrics are used to measure performance?

The *Supplier Communications Agent* underwent substantial testing with demo data examples before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of the Supplier Communications Agent? How can users minimize the impact of these limitations?

The *Send follow-up emails to vendors on purchase orders* capability uses Copilot to generate email based on the information retrieved by queries specified by the user. You can choose which fields to include in the email text, which is limited to the data coming from purchase orders, purchase order lines, and related information (such as vendor records). Primary contacts linked to the emails and vendors are used to identify the recipient's name and company. User data is used to identify the sender's name and company.  
  
The system doesn't send emails automatically (unless specifically configured to do so) and it's your responsibility to review and send each email.

The generated content should never be used without manual review or supervision.

To set the system to send emails automatically, an admin must turn on a specific feature in feature management (*Supplier Communications Agent – automatically send emails*). You should only use this capability after testing and reviewing drafted emails for a long time.

The *Speed up updates in purchase orders based on incoming vendor emails* capability is only intended for vendor collaboration (for classifying emails related to purchase orders). That is why it's mandatory on setup to specify which vendor email addresses (all or specific) the system can read.

## What operational factors and settings allow for effective and responsible use of the Supplier Communications Agent?

When you use the feature, follow these recommendations:

- Make sure that your company has enough control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- When using the *Send follow-up emails to vendors on purchase orders* capability, always review each email and subject before you make any use or decisions based on the information that is provided.
- When using the *Speed up updates in purchase orders based on incoming vendor emails* capability, always review each email, intent extraction, and data before you make any use or decisions based on the information that is provided.

## Related information

- [Supplier Communications Agent overview (production ready preview)](procurement/supplier-com-agent-overview.md)