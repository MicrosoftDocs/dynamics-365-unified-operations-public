---
title: Supplier Communications Agent overview (production ready preview)
description: The Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management helps purchasers be more productive by using AI to automate many of these communications so they can focus on more value-adding tasks
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

Purchasing personnel spend a large part of their day on manual tasks related to communicating with vendors, following up with vendors, and maintaining changes related to purchase orders. Often, these tasks are manual, repetitive, and low-complexity, which procurement personnel would be eager to automate so they could save time for more complex and meaningful tasks. Automating these tasks can also help companies save on procurement costs in general.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Communication between procurement departments and vendors is commonly unstructured and via email, even for companies using electronic data interchange (EDI) implementations and even when working with recurrent vendors.

The Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management helps purchasers be more productive by automating many of these communications so they can focus on more value-adding tasks.

## Follow up on purchase orders

The agent can automatically compose emails that remind vendors to confirm a purchase order or ask why a delivery is late. This saves the time otherwise needed to find the orders that require attention and then author specific emails for them. The agent can either send the emails automatically, right away, or generate draft for human review before sending. Learn more in [Follow up on purchase orders using the Supplier Communications Agent](supplier-com-agent-follow-up.md)

## Speed up purchase order communications

The agent helps purchasers speed up communications with vendors by allowing Copilot to read emails from some or all vendors.

The Supplier Communications Agent understands what each email is about (such as purchase order confirmation, purchase order change request, or other intent) and which purchase order numbers it applies to. Then the agent matches information extracted from the email to the fields in the system, indicating if there are any changes. This way, the purchaser can just review this information and update the fields in the system as needed rather than manually opening the purchase order and doing all the work, thereby saving time that can be used on other more value-adding tasks.

Learn more in [Review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md)

## Cost

Using the agent incurs charges related to utilizing Microsoft Copilot Studio messages.

For information about the billing rates and management for Microsoft Copilot Studio, go to [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).

## Related information

- [Responsible AI for Supplier Communications Agent](../faq-supplier-communications-agent.md)