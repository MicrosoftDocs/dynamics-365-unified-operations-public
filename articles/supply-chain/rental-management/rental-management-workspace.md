---
title: Use the Rental management workspace (preview)
description: Learn how to use the Rental management workspace to monitor contracts, track fleet items, and manage daily rental operations.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: RentalManagementWorkspace
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Use the Rental management workspace (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Rental management workspace** is the central dashboard for rental coordinators and managers. It provides a real-time view of all active rental operations, making it easy to monitor contract statuses, follow up on outstanding items, and quickly navigate to specific contracts. To open it, go to **Rental management (Preview)** > **Workspaces** > **Rental management workspace (Preview)**.

## Overview of the workspace

Below the action buttons, the workspace has the following sections:

- **Summary** – Status tiles.
- **Lists** – Tabbed lists.
- **Related information** – Links to fleet item, rental contract, rental quotation, fleet item movement, and fleet management pages.

Rental management provides a second workspace on the same menu, the **Fleet item movement action items workspace (Preview)**, for the follow-up work that shipping and receiving raise. Learn more in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).

As on other workspaces and pages in Supply Chain Management, you can personalize the layout to fit how you work—for example, by hiding, moving, or renaming elements, and by exporting and sharing your personalizations with other users. Learn more in [Personalize the user experience](../../fin-ops-core/dev-itpro/get-started/personalize-user-experience.md).

### Action buttons

The top of the workspace provides quick-access buttons for common tasks:

- **Create contract** – Opens the contract creation dialog to start a new rental contract.
- **Create quotation** – Opens the quotation creation dialog to start a new rental quotation.
- **Create fleet item movement** – Creates a new fleet item movement for shipping or receiving fleet items.
- **Rental cart** – Opens the rental cart dialog to guide you through creating a quotation or contract.

### Status tiles

The workspace tiles provide at-a-glance counts for the most important categories of rental activity. Select any tile to open the corresponding list of contracts or items.

**Contract tiles:**

- **My active contracts** – *Active* contracts for which you're the **Sales taker**.
- **Contracts on hold** – Contracts in *On hold* status, for any reason.
- **Called off, not returned contracts** – Contracts with lines in *Call-offs* status that have an inbound fleet item movement still to be processed. Follow up on these to arrange pickup or confirm customer drop-off. Call-offs without an inbound fleet item movement aren't counted.
- **Called off, not invoiced contracts** – Contracts with a line in *Call-offs* or *Best rate calculation* status. Rental coordinators work through these before the end of each day.
- **Contracts due to return** – *Active* contracts whose **Estimated return date and time** has passed. Use these to follow up with customers and determine whether they need to extend their rental.
- **Contracts due to ship** – *Created* or *Active* contracts that have started and that have an outbound fleet item movement still to be shipped.
- **Created contracts** – Contracts in *Created* status.

**Quotation tiles:**

- **Sent quotations** – Quotations in *Sent* status.
- **Expiring quotations** – Quotations whose expiration date falls within **Expiration time in days** on the **Rental parameters** page.

**Other tiles:**

- **SMU invoicing overtime approval** – Opens the **Overtime approvals** page, where you review, approve, cancel, or delete the service meter unit (SMU) overtime approvals for rental contract lines.
- **Rental purchase option** – Fleet items that have an active rental purchase option.

### Tabs

The workspace includes the following tabs:

- **Contract lines** – The default view showing contract lines across active rental operations. Use this tab to filter and find specific contracts.
- **My sent quotations** – Track quotations that you sent to customers.
- **Scheduled fleet item movements** – View fleet item movements in *To be shipped* or *To be picked* status.
- **Swap - pending pickup/delivery** – Track fleet item swaps where one fleet item is exchanged and a pickup or delivery is still pending.
- **Rental rates** – Quick access to rental rate cards, including customer-specific rates.

## Filter and find contracts

The **Contract lines** tab displays contract lines for active rental operations. This tab is especially useful when you're on the phone with a customer and need to quickly locate their contract.

To filter and find a specific contract, use the filter fields to search by one or more of the following criteria:

- Customer name
- Fleet item number
- Serial number
- Rental document ID

Select a contract line to drill directly into the corresponding rental contract. This gives you immediate access without searching through the customer record and their rental history. You can also act on the selected line from the tab with **Swap fleet item**, **Call-offs**, **Register stand-down**, and **Contract closing**.

## View rental rates

The **Rental rates** tab provides quick access to your rate cards. The system organizes rental rates by rental class, which groups similar fleet items across different manufacturers (for example, all 19-foot scissor lifts share the same rental class regardless of brand).

To view a customer's rates, enter the **Customer account**, and select an **Application**, **Shift**, or **Location** to apply that price factor. The list shows the **Daily rate**, **Weekly rate**, **Monthly rate**, **Monthly calendar rate**, and **Overtime rate** for each rental class. Select a rental class, and then select **Floor rate** to see the lowest daily, weekly, and monthly rates that you can give the customer without exceeding the rate override limits for the class.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
