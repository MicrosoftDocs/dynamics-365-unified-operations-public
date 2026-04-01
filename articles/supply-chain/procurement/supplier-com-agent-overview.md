---
title: Supplier Communications Agent overview (production ready preview)
description: Learn about the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management. This agent uses AI to automate communications with vendors, so that purchasers can focus on tasks that add more value.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 02/26/2026
ms.custom: 
  - bap-template
---

# Supplier Communications Agent overview (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Purchasing personnel spend a large part of their day on manual tasks that are related to communicating with vendors, following up with them, and maintaining changes that are related to purchase orders. Often, these tasks have low complexity, but they're manual and repetitive. Therefore, procurement personnel are eager to automate them. They can then spend the time that they save on more complex and meaningful tasks. Automating these tasks can also help companies save on procurement costs.

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

Specifically, the agent helps with the following scenarios:

- **Increase or decrease order quantity** – The agent detects a supplier's request to increase or decrease the ordered quantity by reading the email body and any attachments (PDF). It summarizes the requested change, identifies the impacted purchase order and purchase order line, and flags it for approval when needed.
- **Cancel quantity or line** – The agent recognizes that the supplier is asking to cancel (for one line or multiple lines) and matches the message to the correct purchase order and lines. It provides a short summary of what is being reduced.
- **Price increase or decrease** – The agent detects a requested unit price increase or decrease (including supporting rationale if provided) by reading the supplier's email and any attached documentation. It summarizes the old versus new price (where available) and flags it as a commercial change requiring buyer decision or approval.
- **Cancel balance** – When a supplier indicates they won't fulfill the remaining (open) balance of a purchase order, the agent detects this intent and identifies the affected purchase orders and lines. It summarizes what portion is being canceled (if stated) and flags it as an exception that typically needs buyer intervention (alternate sourcing, renegotiation, and so on).
- **Updating confirmed delivery date** – If the supplier confirms or revises the order confirmation date, the agent extracts the date change from the email or attachment and links it to the correct purchase order. It summarizes what changed (previous versus updated date if present) and surfaces it so the buyer can quickly validate and accept.
- **Updating confirmed shipping date (ETA based on ETD)** – When the supplier provides only an estimated time of departure (ETD) or ship date (not an *into warehouse* date), the agent detects which date is provided and indicates the estimated time of arrival (ETA) date. The agent can learn to infer or derive the receiving ETA using agreed transit-time assumptions.
- **Match unit of measure** – If the supplier uses a different unit representation (for example, *packs* versus *each*), the agent identifies the unit mismatch and still extracts the intent of the change. The agent can learn or standardize unit patterns over time and presents a clear summary for the buyer rather than failing the match.
- **Follow up for not confirmed purchase order** – For purchase orders that remain unconfirmed after a defined threshold (such as seven days), the agent identifies the gap and prompts follow-up with the vendor.
- **Follow up on delayed purchase order** – For purchase orders that are delayed beyond a defined threshold, the agent identifies the gap and prompts follow-up with the vendor.

The agent doesn't currently support the following scenarios:

- **Splitting a line into multiple deliveries** – When a supplier proposes splitting delivery (for example, *ship 30 now, 70 later*), the agent should extract the proposed delivery breakdown from the email or attachment and summarize it. It should clearly call out new delivery dates and quantities, associate them to the correct purchase order lines, and split them into multiple deliveries. This scenario isn't yet supported.
- **Changing site for delivery receipt for specific line** – If the supplier requests shipping to a different site or warehouse for a particular line, the agent should extract the new delivery location from the message or attachment and match it to the purchase order line. It should summarize the requested site change and highlight it as a logistics-impacting update requiring review before acceptance. This scenario isn't yet supported.
- **Changing vendor for a specific line** – When a supplier asks to ship from a different operating entity (same supplier, different state or account), the agent should detect that the request implies a vendor account change for processing. It should summarize the reason and proposed vendor ID (if provided) and flag it as an exception scenario for procurement to validate and approve. This scenario isn't yet supported.
- **Changing vendor for the purchase order** – When a supplier asks to ship from a different operating entity (same supplier, different state or account) for the entire purchase order, the agent should detect that the request implies a vendor account change for processing. It should summarize the reason and proposed vendor ID (if provided) and flag it as an exception scenario for procurement to validate and approve. This scenario isn't yet supported.

## Cost

The Supplier Communications Agent incurs charges based on the number of Microsoft Copilot Studio credits you use when running it. The agent has a fixed cost per run and a variable cost that depends on the resources it consumes.

- For the *follow up on purchase orders* feature, the fixed cost applies each time the agent runs. The variable cost depends on the number of emails the agent writes.
- For the *review and apply purchase order changes* feature, the fixed cost applies each time the agent runs. The variable cost depends on the number of emails the agent reads and the number of attachments those emails have.

Learn about the billing rates and management for Copilot Studio in [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).

## Related information

- [Responsible AI FAQ for the Supplier Communications Agent](../faq-supplier-communications-agent.md)
