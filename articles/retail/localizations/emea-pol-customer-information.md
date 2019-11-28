---
# required metadata

title: Customer information management for Poland
description: This topic describes how to handle customer information in Retail POS for Poland.
author:
manager:
ms.date: 11/11/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailParameters
audience: Application User
# ms.devlang:
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Poland
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2019-11-11
ms.dyn365.ops.version: 10.0.9

---
# Customer information management for Poland

[!include [banner](../includes/banner.md)]

## Introduction

This topic describes how you can handle customer information, such as the customer's NIP, in Retail point of sale (POS) for Poland.

You can specify the customer's NIP when you create or edit a customer master record in POS. You can also specify the NIP for a sales transaction by copying it from the transaction customer or entering it manually. The customer information can then be printed on both regular and fiscal receipts, and can be used for the invoicing purposes.

> [!NOTE]
> This functionality is available in version 10.0.9 and later of the Retail apps.

## Setup

You must complete the following configuration to use this functionality:

- Add the "Add customer information" operation to screen layouts.
- Activate the inquiry for customer information.
- Set up receipt formats.
- Configure retail channel components.

### Add the "Add customer information" operation to screen layouts

The "Add customer information" operation can be used to add customer information, such as the NIP, to a sales transaction. This information can be copied from the customer that is specified for the transaction, or it can be manually entered.

On the **Button grids** page, select the button grid where the operation should appear, and open the Button grid designer. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

### Activate the inquiry for customer information

If the customer information isn't specified for a sales transaction, an inquiry for that information can be triggered automatically after the transaction is finalized. This approach is an alternative to the "Add customer information" operation.

To activate the inquiry for customer information, set the **Enable inquiry of customer information in sales transactions** option to **Yes** in the **Tax parameters** section on the **Functions** FastTab of the **POS functionality profiles** page.

### Set up receipt formats

You can configure receipt formats so that the customer's fiscal code is printed on receipts.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, on the **POS** tab, add the following records for the labels of the custom fields for receipt formats. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the following table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

| Language ID | Text ID | Text                |
|-------------|---------|---------------------|
| en-US       | 900001  | Vat number          |

On the **Custom fields** page, add the following records for the custom fields for receipt formats. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                           | Type    | Caption text ID |
|--------------------------------|---------|-----------------|
| FISCALCUSTOMER\_VATNUMBER\_PL  | Receipt | 900001          |

In the Receipt format designer, add the custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Configure retail channel components

To make the functionality that is specific to Poland available, you must configure extensions for retail channel components. For more information, see the [Deployment guidelines](#deployment-guidelines) section later in this topic.

## Example scenarios

The following examples show how to work with customer information in POS for Poland.

### Scenario 1: Make a sale to an anonymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's NIP, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's NIP.

### Scenario 2: Make a sale to a new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **New**.
1. Specify the new customer's attributes. In the **VAT number** field, enter the customer's NIP.
1. Save the customer record, and add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. In the **Enter customer information** dialog box, select **Yes**, and then select **Copy from transaction customer**.
1. Verify the customer's NIP, and then select **OK**.
1. Verify that the printed receipt contains the customer's NIP.

> [!NOTE]
> If you have to specify a different customer for the transaction, you must clear the customer information and then copy it again after the new customer is added.

### Scenario 3: Change the customer information for a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Select **Add customer information**, and then select **Copy from transaction customer**.
1. Verify the customer's fiscal code, and then select **OK**.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Add customer information**, and then select **Enter Manually**.
1. Specify the customer's fiscal code, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's NIP.

## Deployment guidelines

This section provides deployment guidance for enabling customer information management in the localization of Dynamics 365 Retail for Poland.
