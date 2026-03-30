---
title: Configure receipt emails to use custom layouts and templates
description: Learn how to configure receipt emails so that they use custom layouts and templates in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-02-16
ms.search.form: RetailParameters, SysEmailTable
ms.custom: 
  - bap-template
---

# Configure receipt emails to use custom layouts and templates

[!include [banner](includes/banner.md)]

This article describes how to configure receipt emails to use custom layouts and templates in Microsoft Dynamics 365 Commerce. You can also send receipt emails that use unique receipt formats, and configure the emailing of receipts on a receipt-by-receipt basis.

You can email most receipt formats from a point of sale (POS) terminal, both during checkout and from the journal. Before the Commerce version 10.0.18 release, the sales receipt format (receipt format 1) was used for all receipts that were emailed.

You can disable the emailing of receipts for individual receipts. Additionally, you can modify the option that prompts cashiers to ask customers whether they want to receive a receipt by email for individual receipts.

To enable additional email receipt formats, add them and map them to a template in the receipt profile. Reference the receipt profile from the functionality profile that is associated with the retail store that the receipt emails are sent from.

## Email receipt formats

The following table shows the receipt formats that you can email as of the Commerce version 10.0.18 release.

| Receipt format | Receipt type                                  |
| -------------- | --------------------------------------------- |
| 1              | Sales receipt                                 |
| 3              | Customer credit card receipt                |
| 5              | Customer credit card receipt for returns    |
| 8              | Customer account receipt                      |
| 10             | Customer account return receipt               |
| 14             | Product sale                                  |
| 15             | Credit memo                                   |
| 18             | Sales order receipt                           |
| 21             | Quotation receipt                             |
| 23             | Pick up receipt                               |
| 33             | Gift receipt                                  |
| 40             | Gift card inquiry (gift card balance inquiry) |

## Set up receipt emails

To set up receipt emails so that they use other receipt formats, first turn on the **Email any receipt type and customize emailed receipts** feature in the **Feature management** workspace in Commerce headquarters (**Workspaces \> Feature management**).

> [!IMPORTANT]
> Before you can turn on the **Email any receipt type and customize emailed receipts** feature, turn on the **Email receipts from the Journal** feature.

When you turn on the **Email any receipt type and customize emailed receipts** feature, it enables the following functionality:

- The ability to email the receipt formats that are listed in the [Email receipt formats](#email-receipt-formats) section earlier in this article.
- The ability to customize the template that delivers the receipt emails for specific receipt types.
- The ability to configure whether specific receipt types are emailed from the POS, and whether cashiers are prompted to ask customers whether they want to receive a receipt by email.
- A fix for a formatting issue that required that implementers remove line breaks from the HTML for receipt emails.
- POS support for emailing of gift receipts.

> [!NOTE]
> - After you turn on the **Email any receipt type and customize emailed receipts** feature, map a receipt email template from the **Organization email templates** page to a receipt type in your Commerce email notification profile. If job **1110** (Global configuration) runs before you complete this step, receipt emails stop working.
> - By default, every receipt format is configured so that receipts are never emailed, and cashiers are never prompted. To enable emailing of receipt formats, change the value of their **Email behavior** field from **Do not email** to **Prompt user** or **Always email**.
> - If you implemented any extensions to email code, test the functionality after you turn on the **Email any receipt type and customize emailed receipts** feature.

### Configure a receipt profile

A receipt profile defines the receipt types and the associated receipt formats that a specific store or set of stores uses. You can define separate profiles for printed and emailed receipts on a store-by-store basis.

The functionality profile that you associate with a store includes a **Receipt profile ID** field. This field specifies the receipt profile that defines the receipts that the store can email.

To add receipt types to a receipt profile that you use to email receipts, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles**.
1. Select **Add** to create a new, empty row.
1. In the **Receipt type** field, select the receipt type.
1. In the **Receipt format** field, select a receipt format that defines the layout of the selected receipt type. For more information about how to create receipt formats, see [Set up and design receipt formats](receipt-templates-printing.md).
1. Select an email template that should be used as the container template for receipt emails. All the templates that you create on the **Organization email templates** page are available for selection. If you previously configured receipt emails, you have a template named **emailrecpt**. You can use this template. For information about how to specify a custom container template on a receipt-by-receipt basis, see [Create receipt email templates](#create-receipt-email-templates).

> [!NOTE]
> Even if a receipt type can't be emailed, Commerce headquarters doesn't prevent you from adding it to a receipt profile. For a list of the receipt formats that can be emailed, see the [Email receipt formats](#email-receipt-formats) section earlier in this article.

### Create receipt email templates

Every receipt format that you can email can be associated with its own container template. The container template defines the header and footer that surrounds the formatted receipt. It also provides a placeholder for the receipt ID. This placeholder enables a QR code or bar code that represents the receipt ID to be inserted into receipt emails.

Create and upload email templates on the **Organization email templates** page in Commerce headquarters (**Retail and Commerce \> Headquarters setup \> Organization email templates**). For more information, see [Create an email template](email-templates-transactions.md#create-an-email-template). For specific instructions for creating receipt email templates, see [Create a template for emailed receipts](email-templates-transactions.md#create-a-template-for-emailed-receipts).

### Configure the receipt email behavior in the POS

This section describes the settings that enable emailing of receipts in Commerce headquarters.

#### Commerce parameters

On the **Commerce parameters** page (**Retail and Commerce > Commerce setup > Parameters > Commerce parameters**), on the **Posting** tab, on the **Email receipt** FastTab, in the **Receipt option** field, select one of the following values:

- **Standard receipt** – Enable receipts to be printed for all customers.
- **Email** – Enable receipts to be emailed for all customers.
- **Both** – Enable receipts to be both printed and emailed for all customers.

#### Customer profile

On the **Customer profile** page (**Retail and Commerce > Customers > Customer**), in the **Retail** section, in the **Receipt option** field, select one of the following values:

- **Standard receipt** – Enable receipts to be printed for this customer.
- **Email** – Enable receipts to be emailed for this customer.
- **Both** – Enable receipts to be both printed and emailed for this customer.

#### Receipt format

On the **Receipt format** page (**Retail and Commerce > Channel setup > POS setup > POS > Receipt formats**), the **Email behavior** field defines whether cashiers are prompted about receipt emails at the POS. Values that you select in this field for individual receipt formats override values that are selected in the **Receipt option** field on the **Commerce parameters** and **Customer profile** pages.

- **Do not email** – Never send email receipts or prompt cashiers. This value overrides the **Email** and **Both** values on the **Commerce parameters** and **Customer profile** pages.
- **Always email** – Always send emailed receipts, without prompting cashiers.
- **Prompt user** – Prompt cashiers to ask customers whether they want to receive a receipt by email and, if they do, what email address the receipt should be sent to.

> [!NOTE]
> - The gift card inquiry receipt format isn't configured by using Commerce parameters or customer profiles. To enable the gift card inquiry receipt format, set the **Email behavior** field to **Prompt user** or **Always email**. To disable the gift card inquiry receipt format, set the **Email behavior** field to **Do not email**. 
> - By default, if a receipt format can't be emailed, its **Email behavior** field is set to **Do not email**, and the value can't be changed.
> - If a receipt format can be emailed, it can always be emailed from the journal, regardless of the settings on the **Commerce parameters**, **Customer profile**, and **Receipt format** pages.

## Additional resources

[Send email receipts from Store Commerce](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions.md)

[Set up an email notification profile](email-notification-profiles.md)

[Set up and design receipt formats](receipt-templates-printing.md)
