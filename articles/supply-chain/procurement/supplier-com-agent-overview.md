---
title: Supplier Communications Agent overview (production ready preview)
description: Learn about the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management. This agent uses AI to automate communications with vendors, so that purchasers can focus on tasks that add more value.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Supplier Communications Agent overview (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Purchasing personnel spend a large part of their day on manual tasks that are related to communicating with vendors, following up with them, and maintaining changes that are related to purchase orders. Often, these tasks have low complexity, but they are manual and repetitive. Therefore, procurement personnel are eager to automate them. They can then spend the time that they save on more complex and meaningful tasks. Automation of these tasks can also help companies save on procurement costs in general.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Communication between procurement departments and vendors is often unstructured and conducted via email, even for companies that implement electronic data interchange (EDI) and companies that work with recurrent vendors.

The Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management uses AI to automate many communications with vendors. Therefore, purchasers can focus on tasks that add more value and can be more productive.

## Follow up on purchase orders

The Supplier Communications Agent can automatically generate emails that remind vendors to confirm a purchase order or ask why a delivery is late. Therefore, purchasers don't have to spend time finding the orders that require attention and then writing emails for them. The agent can automatically send the emails right away, or it can save them as drafts that require human review before they can be sent.

Learn more in [Follow up on purchase orders using the Supplier Communications Agent](supplier-com-agent-follow-up.md).

## Speed up purchase order communications

The Supplier Communications Agent helps purchasers speed up communications with vendors by enabling Copilot to read emails from some or all vendors.

The agent can determine what each email is about (for example, whether it's a purchase order confirmation or a purchase order change request) and which purchase order numbers it applies to. The agent then matches information that it extracts from the email to fields in the system and indicates any changes. In this way, purchasers can review just that information and update the fields in the system as required. They don't have to manually open the purchase order and do all the work. They can then spend the time that they save on other tasks that add more value.

Learn more in [Review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md).

## Cost

Use of the Supplier Communications Agent incurs charges that are related to using Microsoft Copilot Studio messages.

Learn about the billing rates and management for Copilot Studio in [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).

## Related information

- [Responsible AI for the Supplier Communications Agent](../faq-supplier-communications-agent.md)
