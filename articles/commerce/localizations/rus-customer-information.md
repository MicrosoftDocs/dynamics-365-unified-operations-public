---
# required metadata

title: Customer information management for Russia
description: This topic describes how to handle customer information in POS for Russia.
author: EvgenyPopovMBS
ms.date: 09/02/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailParameters
audience: Application User
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Russia
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2021-8-2
ms.dyn365.ops.version: 10.0.21

---
# Customer information management for Russia

[!include [banner](../includes/banner.md)]

## Introduction

This topic describes how you can handle customer information, such as the customer's phone number or email address, in the Commerce point of sale (POS) for Russia.

You can specify the customer information, such as the phone number and email address, when you create or edit a customer master record in POS. You can also specify it for a sales transaction by copying it from the transaction customer or entering it manually. The information can then be included in the fiscal receipt. See [Fiscal printer integration sample for Russia](rus-fpi-sample.md) for more information on generating and printing fiscal receipts.

> [!NOTE]
> The customer information is included in the fiscal receipt that is sent to the fiscal printer, but it is not printed in the sample fiscal receipt. You need to customize the sample in order to print the customer informaation in the fiscal receipt.

## Example scenarios

The following example scenarios show how to work with customer information in POS for Russia.

### Scenario 1: Make a sale to an anonymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Choose whether a phone number or an email address is to be specified.
1. Enter the customer information, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. The fiscal receipt that is sent to the fiscal printer includes the customer information.

### Scenario 2: Make a sale to a new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **New**.
1. Specify the new customer's attributes including:

  - Primary and/or receipt email.
  - Primary phone.

1. Save the customer record and add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Because the inquiry for customer information has been activated, but customer information hasn't been added to the transaction, the **Enter customer information** dialog box is opened. Select **Yes**, and then select **Copy from transaction customer**.
1. Choose whether the phone number or the email address is to be copied to the customer information.
1. Verify the customer information, and then select **OK**.
1. The fiscal receipt that is sent to the fiscal printer includes the customer information.

> [!NOTE]
> If you need to specify a different customer for the transaction, you must clear the customer information and then copy it again after the new customer is added.

### Scenario 3: Change the customer information for a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Select **Add customer information**, and then select **Copy from transaction customer**.
1. Choose whether the phone number or the email address is to be copied to the customer information.
1. Verify the customer information, and then select **OK**.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Add customer information**, and then select **Enter manually**.
1. Choose whether a phone number or an email address is to be specified.
1. Enter the customer information, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. The fiscal receipt that is sent to the fiscal printer includes the customer information.

## Setup

You must complete the following configuration to use this functionality:

- Add the **Add customer information** operation to screen layouts.
- Activate the inquiry for customer information.
- Configure channel components.

### Add the Add customer information operation to screen layouts

The **Add customer information** operation can be used to add customer information, such as the phone number or email address, to a sales transaction. This information can be copied from the customer that is specified for the transaction, or it can be manually entered.

On the **Button grids** page, select the button grid where the operation should appear, and open the Button grid designer. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

### Activate the inquiry for customer information

If the customer information isn't specified for a sales transaction, an inquiry for that information can be triggered automatically after the transaction is finalized. This approach is an alternative to the **Add customer information** operation.

To activate the inquiry for customer information, set the **Enable inquiry of customer information in sales transactions** option to **Yes** in the **Tax parameters** section on the **Functions** FastTab of the **POS functionality profiles** page.

### Configure channel components

To make the functionality that is specific to Russia available, you must configure extensions for commerce channel components.
