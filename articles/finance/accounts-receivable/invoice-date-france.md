---
title: Validate invoice dates for French regulation 
description: Learn about the French invoicing regulation in Dynamics 365 Finance. 
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 04/24/2026
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:  CustomerInvoiceWorkspace
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1040678e-ffcb-47fb-a1bc-626db8046504
---

# Validate invoice dates for French regulation

To comply with French invoicing regulations, Dynamics 365 Finance introduces a new validation to ensure that the invoice date isn't earlier than the delivery (confirmed receipt) date. This validation
is enforced when you post the invoice and prevents non-compliant invoices from being generated.

## Key features

• The system validates the invoice date against the delivery or confirmed receipt date for each sales line.
• The system blocks invoice posting if any sales line has a delivery date that's later than the invoice date.
• The system displays a clear and actionable validation error message to the user.

### Configuration

You control the invoice validation through the **Accounts receivable parameters** page.

To configure invoice validation, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Sales setup** tab, enable the parameter.
1. Set the **Allow invoice posting only if invoice date is after confirmed receipt date** parameter to **Yes**.

When you enable this parameter:

- The invoice date must be greater than or equal to the confirmed receipt (delivery) date.
- The system blocks invoice posting if any sales line violates this condition, ensuring strict compliance.
- The system displays an error message to guide users in correcting the issue.

>[!NOTE]
> The validation applies only to French legal entities.

You can post invoices only when the date condition is satisfied for all relevant sales lines. If the condition isn't met, the system prevents posting to ensure regulatory compliance.

### Scenarios

The invoice date validation applies to the following invoicing situations:

- Single-line and multi-line sales order invoicing
- Sales orders with delivery and site split enabled. The validation is applied per split line.
- Invoices summarized by packing slip
- Invoices summarized by invoice account across multiple sales orders
- Batch invoicing
- Proforma invoicing

>[!NOTE]
> For invoice account–level summarizations, the invoice date of the first sales line is used for validation across all related sales lines.
