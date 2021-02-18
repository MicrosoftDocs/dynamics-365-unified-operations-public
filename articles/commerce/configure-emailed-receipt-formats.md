---
# required metadata

title: Configure receipt emails to use custom layouts and templates
description: This topic describes how to configure receipt emails to use custom layouts and templates in Dynamics 365 Commerce. 
author: bicyclingfool
manager: 
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce

# optional metadata

ms.search.form: RetailParameters, SysEmailTable,
# ROBOTS: 
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid:
ms.search.region: global
ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2021-02-16
ms.dyn365.ops.version: 

---

# Configure receipt emails to use custom layouts and templates

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to configure receipt emails to use custom layouts and templates in Dynamics 365 Commerce.

In Commerce, you can configure receipt emails to use custom layouts and templates. It is also possible to send receipt emails that use unique receipt formats, and to configure the emailing of receipts on a per-receipt basis. 

Most receipt formats can be emailed from a point of sale (POS) terminal, both during checkout and from the journal. Prior to the Commerce version 10.0.18 release, the sales receipt format (format 1) was used for all emailed receipts. 

Individual receipts can also be disabled from being emailed, and the option to prompt the cashier to ask if the customer would like an emailed receipt can also be modified on a per-receipt basis.

To enable additional email receipt formats, the formats must be added and mapped to a template in the receipt profile that is referenced from the functionality profile associated with the retail store from which the email is sent.

## Email receipt formats

The following email receipt formats can be emailed.

| Receipt format | Receipt type                                   |
| ------- | ---------------------------------------------- |
| 1       | Sales receipt                                 |
| 8       | Customer account receipt                      |
| 10      | Customer account return receipt               |
| 14      | Product sale                                   |
| 15      | Credit memo                                    |
| 18      | Sales order receipt                           |
| 21      | Quotation receipt                             |
| 23      | Pick up receipt                               |
| 33      | Gift receipt                                   |
| 40      | Gift card inquiry (gift card balance inquiry) |

 
## Set up receipt emails

To set up receipt emails to use additional receipt formats, the **Email any receipt type and customize emailed receipts** feature must be enabled in Commerce headquarters at **Workspaces \> Feature management**. In order to enable this feature, the **Email receipts from the Journal** feature must first be enabled.

Enabling the **Email any receipt type and customize emailed receipts** feature activates the following capabilities:

- The ability to email the receipt formats listed above.
- The ability to customize the template that delivers the emailed receipt for specific receipt types.
- The ability to configure whether specific receipt types are emailed from the point of sale (POS), and whether cashiers get prompted to ask customers if they want an emailed receipt.
- A formatting issue fix for an issue that required implementers to remove line breaks from emailed receipt HTML.
- Support in POS for emailing gift receipts.

> [!NOTE]
> After enabling the **Email any receipt type and customize emailed receipts** feature switch, you must map an emailed receipt template from **Organization email templates** to a receipt type in your **Commerce email notification profile**. If job 1110 (global configuration) is run prior to doing this, emailed receipts will stop working.
> All receipt formats are set by default to **Do not email**. To enable receipt formats for emailing, you must set them to **Prompt user** or **Always email**.     
> If you have implemented any extensions to email code, that functionality should be tested after the **Email any receipt type and customize emailed receipts** feature is enabled. 

### Configure the receipt profile

A receipt profile defines the receipt types and associated receipt formats that will be used for a particular store or set of stores. Separate profiles can be defined for printed and emailed receipts on a store-by-store basis. 

The receipt profile that specifies which receipts can be emailed for a particular store is specified in the **Receipt profile ID** field within the functionality profile associated with that store. 

To add receipt types to a receipt profile that will be used for emailing receipts, follow these steps.

1. Select **+ Add** to create a new, empty row.
1. On the **Receipt type** drop-down menu, select the receipt type.
1. Select a receipt format that defines the layout of this receipt type. For more information about creating receipt formats, see [Set up and design receipt formats](receipt-templates-printing.md).
1. Select an email template that will serve as the container template for the emailed receipt. The list of email templates that appear in the drop-down menu are the templates that are created in organization email templates. If you have previously configured emailed receipts, you will have a template named **emailRecpt** which may be used. For information on how to specify a custom container template on a per-receipt basis, see [Create emailed receipt templates](#create-emailed-receipt-templates) below. 

> [!NOTE]
> Commerce headquarters does not prevent you from adding receipt types that cannot be emailed to a receipt profile. Refer to the [Email receipt formats](#email-receipt-formats) table above for a list of receipt formats that can be emailed.

### Create emailed receipt templates

All receipt formats that are emailable can be associated with their own "container" template. The container template defines the header and footer that surrounds the formatted receipt. The container template also provides a placeholder for the receipt ID so that a barcode or QR code representing the receipt ID can be inserted into the emailed receipt. 

Email templates are established and uploaded in Organization email templates. For more information, see [Create an email template](email-templates-transactions.md#create-an-email-template). For specific instructions for creating emailed receipt templates, see [Create a template for emailed receipts](email-templates-transactions.md#create-a-template-for-emailed-receipts). 

### Configure emailed receipt behavior in POS

Receipts are enabled for emailing using the following settings in Commerce headquarters.

#### Commerce parameters (Retail and commerce \> Commerce setup \> Parameters \> Commerce parameters)  

The Receipt option field within the Email receipt section in the Posting tab provides the following options:

- **Standard receipt** - Receipts are enabled for printing for all customers.
- **Email** - Receipts are enabled for email for all customers.
- **Both** - Receipts are enabled for both printing and email for all customers.

#### Customer profile (Retail and commerce \> Customers \> Customer)

The receipt option field within the Retail section provides the following options:

- **Standard receipt** - Receipts are enabled for printing for this customer.
- **Email** - Receipts are enabled for email for this customer.
- **Both** - Receipts are enabled for printing and email for this customer.

#### Receipt format (Retail and commerce \> Channel setup \> POS setup \> POS \> Receipt formats)

The choices in the Email behavior dropdown define whether cashiers are prompted to send an emailed receipt in point of sale (POS). These settings, which are defined for each receipt format, override the email settings in commerce parameters and customer profile.

- **Do not email** - No email is sent and the cashier is not prompted. This setting overrides the **Email** and **Both** options in Commerce parameters and the customer's profile.
- **Always email** - Always send an emailed receipt, do not prompt the cashier.
- **Prompt user** - Prompt the cashier to ask if the customer wants an emailed receipt, and what email address to send it to.

> [!NOTE]
> The **Email behavior** drop-down menu option for receipt formats that cannot be emailed will be set to **Do not email** and cannot be changed.
> All emailable receipts can be emailed from the journal regardless of how emailed receipts are configured in Commerce parameters, the customer profile, or the receipt format. 

## Additional resources

[Send email receipts from Modern POS (MPOS)](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions.md)

[Set up an email notification profile](email-notification-profiles.md)

[Set up and design receipt formats](receipt-templates-printing.md)



