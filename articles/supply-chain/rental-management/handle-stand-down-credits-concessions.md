---
title: Handle stand-down credits and concessions (preview)
description: Learn how to apply stand-down credits for weather, venue closures, or other downtime, and manage customer concessions on rental contracts.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Handle stand-down credits and concessions (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Stand-down credits are concessions that reduce a customer's rental charges for periods when they can't use the fleet item. Common reasons include weather, venue closures, holidays, and fleet item breakdowns that are the rental company's responsibility.

## Understand stand-down types

Rental management supports two types of stand-down credits:

- **Full-day stand-down** – Credits the customer for one or more complete rental days.
- **Partial stand-down** – Credits the customer for a portion of a day, registered with the **Register partial day** option. For example, if a delay stops work for part of a shift, only that portion is credited.

The stand-down amount isn't always a flat daily-rate credit. It depends on the rental template settings and on whether you register a partial day.

## Apply a stand-down credit

To apply a stand-down credit to a rental contract, follow these steps:

1. Open the rental contract.
1. Select **Contract stand-down** on the Action Pane. The command is available while the contract is *Active*. To register a stand-down for a single line, select the line, and then select **Register stand-down**.
1. In the stand-down form, select the relevant main lines on the **Rental contract items** tab. Attachments on a selected line get their own stand-down records.
1. Set the **From date** and **To date** for the stand-down period. The number of stand-down days is read-only. The system derives it from the two dates, so you can't type a day count of your own. When the rental template uses **Calendar-based invoicing** or **Use calendar for stand-down**, the system counts only the days that are open in the template calendar. Otherwise, it counts every day from **From date** to **To date**.
1. For a partial stand-down (hourly), select **Register partial day** and enter the number of hours that the fleet item was unused in **Hours**, which is editable only when you register a partial day. The system prorates the credit against the hours allowed on the rate, and recalculates **Days** and **To date** from the hours that you enter.
1. Select a **Reason code** that explains why you apply the stand-down (for example, *Weather*, *Fleet item breakdown*, or *Customer request*).
1. Select **OK** to create the stand-down record. **From date** can't be earlier than the earliest invoice period that can still be credited. If overtime is already approved for the period, you're asked to confirm, because the approved overtime doesn't change.

The system calculates the stand-down amount for each line from the billing rate and the derived days or the hours that you entered. When you register from a line, the dialog shows it in **Stand-down amount**. If the **Prorate stand-down** option is enabled on the rental template, the calculation uses the prorated active rental rate rather than the base rate.

The stand-down credit appears on the next invoice, or on the final invoice when you close the contract.

## View stand-down history

To review all stand-down credits applied to a contract, open the contract, and then select **Contract stand-down history**. To review the stand-down credits for a single line, select the line, and then select **View stand-down**. This view shows the following information:

- The date range and number of days (or hours) of each stand-down
- The reason code
- The calculated credit amount
- The stand-down status

Each stand-down record progresses through the following statuses:

| Status | Description |
|---|---|
| *Created* | The stand-down is entered but isn't included on an invoice schedule. |
| *Invoice schedule* | The stand-down credit is added to an invoice schedule. |
| *Invoiced* | The invoice for the stand-down is posted. |
| *Credit scheduled* | A credit note is scheduled to apply the stand-down credit. |

Use this history to track concession patterns and identify customers or job sites that frequently request stand-downs. When you open it from a contract or a line, you can delete stand-downs that are still *Created*, which also removes their credit. Select **Select all created** to select them all.

To review stand-downs across all contracts, go to **Rental management (Preview)** > **Inquiries and reports** > **Stand-down history**.

When the rental template uses **Calendar-based invoicing**, the line details on the contract also have a **Calendar-based invoicing** tab. It lists each invoicing period of the line with its stand-down days, stand-down hours, and stand-down amount, so you can see which period a stand-down is credited in.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
- [Set up rental templates](set-up-rental-templates.md)
