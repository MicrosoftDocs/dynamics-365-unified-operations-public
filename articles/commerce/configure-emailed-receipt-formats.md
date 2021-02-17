---
# required metadata

title: Configure emailed receipts to use custom layouts and templates
description: It is now possible to send emailed receipts using unique receipt formats, and to configure emailing of receipts on a per-receipt basis. 
author: stuharg
manager: 
ms.date: 02/16/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce

# optional metadata

ms.search.form: RetailParameters, SysEmailTable,
# ROBOTS: 
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid:
ms.search.region: global
ms.search.industry: 
ms.author: jashanno
ms.search.validFrom: 2021-02-16
ms.dyn365.ops.version: 

---

# Configure emailed receipts

You can configure emailed receipts to use custom layouts and templates
description: It is also possible to send emailed receipts using unique receipt formats, and to configure emailing of receipts on a per-receipt basis. 

## Overview

Most receipt formats can be emailed from a point of sale terminal (POS), both during checkout and from the journal. Prior to release 10.0.18, the receipt format for receipt format 1 (sales receipt) was used for all emailed receipts. Individual receipts can also be disabled from being emailed, and the option to prompt the cashier to ask if the customer would like an emailed receipt can also be modified on a per-receipt basis.

To enable emailing of additional receipt formats, they need to be added and mapped to a template in the receipt profile that is referenced from the functionality profile associated with the retail store from which the email is sent.

The following receipt formats can be emailed

 

| Receipt | Receipt Type                                   |
| ------- | ---------------------------------------------- |
| 1       | Sales  Receipt                                 |
| 8       | Customer account  receipt                      |
| 10      | Customer account  return receipt               |
| 14      | Product sale                                   |
| 15      | Credit Memo                                    |
| 18      | Sales Order  Receipt                           |
| 21      | Quotation  Receipt                             |
| 23      | Pick up  Receipt                               |
| 33      | Gift Receipt                                   |
| 40      | Gift Card  Inquiry (gift card balance inquiry) |

 

# Set up emailed receipts

## Prerequisite

To set up emailing for receipt formats, the feature named **Email any receipt type and customize emailed receipts** in Headquarters (**Workspaces** > **Feature management**) to enable the full functionality of emailed receipts. This feature switch enables the following capabilities:

1. Ability to email the receipt formats listed above
2. Ability to customize the template that delivers the emailed receipt for specific receipt types
3. Ability to configure whether specific receipt types are emailed from point of sale (POS), and whether cashiers get prompted to ask customers if they want an emailed receipt.
4. Fix for a formatting issue in emailed receipts that required implementers to remove line breaks from the HTML
5. Support in POS for emailing a gift receipt

 

NOTES: 

- In order to enable this feature switch, the **Email receipts from the Journal** feature switch must first be enabled.
- After enabling the **Email any receipt type and customize emailed receipts** feature switch, you must map an emailed receipt template from **Organization email templates** to a receipt type in your **Commerce email notification profile**. If job 1110 (Global configuration) is run prior to doing this, emailed receipts will stop working.
- By default, all receipt formats will be set to **Do not email**. Set the receipt formats you wish to email to **Prompt user** or **always email** to enable them for emailing.     
- If you have implemented any extensions to email code, that functionality should be tested after the feature switch is enabled. 

 

## Configure the receipt profile

A receipt profile defines the receipt types and their associated receipt formats that will be used for a particular store or set of stores. Separate profiles can be defined for printed and emailed receipts on a store-by-store basis. 

The receipt profile that specifies the receipts that can be emailed for a particular store is the one that is specified in the **Receipt profile ID** field within the functionality profile associated with that store. 

To add receipt types to a receipt profile that will be used for emailing receipts, do the following:

1. Click **+ Add** to create a new, empty row
2. Select the receipt type from the receipt type dropdown
3. Select a receipt format that defines the layout of this receipt type. To learn more about creating receipt formats, see the [Set up and design receipt formats](receipt-templates-printing.md) help topic.
4. Select an email template that will serve as the container template for this emailed receipt. The list of email templates that appear in the dropdown are the templates that are created in Organization email templates. NOTE: If you have previously configured emailed receipts, you will have a template named emailRecpt which may be used. If you wish to specify a custom container template on a per-receipt basis, see the Create emailed receipt templates section below for more information. 

 

NOTE: 

Headquarters does not prevent you from adding receipt types to the receipt profile that cannot be emailed. See the table above for a list of receipt formats that can be emailed.



## Create emailed receipt templates

All receipt formats that are emailable can be associated with their own "container" template. The container template defines the header and footer that surrounds the formatted receipt. The container template also provides a placeholder for the receipt ID so that a barcode or QR code representing the receipt ID can be inserted into the emailed receipt. 

Email templates are established and uploaded in Organization email templates. See the [Create an email template](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions#create-an-email-template) section of the [Creating email templates for transactional events](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions) help topic, and the [Create a template for emailed receipts](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions#create-a-template-for-emailed-receipts) section for specific instructions on creating emailed receipt templates. 

 

## Configure emailed receipt behavior in POS

Receipts are enabled for emailing through the following settings in Dynamics 365 Commerce headquarters

**Commerce parameters** (Retail and commerce > Commerce setup > Parameters > Commerce parameters)  

The Receipt option field within the Email receipt section in the Posting tab provides the following options:

- **Standard receipt** - Receipts are enabled for printing for all customers
- **Email** - Receipts are enabled for email for all customers
- **Both** - Receipts are enabled for both printing and email for all customers

 

**Customer profile** (Retail and commerce > Customers > [customer])

The receipt option field within the Retail section provides the following options:

- **Standard receipt** - Receipts are enabled for printing for this customer
- **Email** - Receipts are enabled for email for this customer
- **Both** - Receipts are enabled for printing and email for this customer

 

**Receipt format** (Retail & Commerce > Channel setup > POS setup > POS > Receipt formats)

The choices in the Email behavior dropdown define whether cashiers are prompted to send an emailed receipt in point of sale (POS). These settings, which are defined for each receipt format, override the email settings in commerce parameters and customer profile.

- **Do not email** - no email is sent and the cashier is not prompted. This setting overrides the **Email** and **Both** options in Commerce parameters and the customer's profile
- **Always email** - always send an emailed receipt, do not prompt the cashier
- **Prompt user** - prompt the cashier to ask if the customer wants an emailed receipt, and what email address to send it to.

 

NOTES:

- The Email behavior dropdown for receipt formats that cannot be emailed will be set to **Do not email** and cannot be changed.
- All emailable receipts can be emailed from the Journal regardless of how emailed receipts are configured in Commerce parameters, the customer profile or the receipt format. 

 

 

## Additional resources

[Send email receipts from Modern POS (MPOS)](https://docs.microsoft.com/en-us/dynamics365/commerce/email-receipts)

[Create email templates for transactional events](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions)

[Set up an email notification profile](https://docs.microsoft.com/en-us/dynamics365/commerce/email-notification-profiles)

[Set up and design receipt formats](https://docs.microsoft.com/en-us/dynamics365/commerce/receipt-templates-printing)



