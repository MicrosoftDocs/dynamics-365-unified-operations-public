---
# required metadata

title: Unlinked refunds
description: This topic describes how unlinked refunds work in Dynamics 365 Commerce
author: Brian Shook
manager: Brendan Sullivan
ms.date: 08/20/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: BrianShook
ms.search.validFrom: 
ms.dyn365.ops.version: 


---

# Unlinked refunds in Dynamics 365 Commerce with Adyen Connector
The Dynamics 365 Commerce Adyen Connector supports the ability to process refunds against a different payment method than was used for the original transaction. Where it is recommended to use [Linked Refunds](linked-refunds.md) to process a refund against the originating payment method provided, there are scenarios where a different method is required. An example may be that the original card utilized for payment is now expired, lost, or cancelled by the user. This article reviews the ability to process the refund against a new payment method in POS or Call Center.

## Prerequisites
[Payment Method Setup](https://docs.microsoft.com/en-us/dynamics365/commerce/payment-methods)

[Omni-channel payments setup](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments)

### Additional Setup
Customers who aren't using the out-of-box implementation of the Adyen Connector must set up the connector that supports tokenization of credit cards. All the scenarios that are described in this topic can be implemented by using the standard Payments software development kit (SDK) that is provided with Commerce. [The Dynamics 365 Payment Connector for Adyen](adyen-connector.md) provides an out-of-box implementation of every scenario that is described here.

## Refund Supported Scenarios
Dynamics 365 Commerce supports refunds of a transaction that was previously approved and confirmed. Refunds can be either a full refund or a partial refund of the transaction. Refunds cannot exceed the full amount of the original authorization which occurred. Unlinked refunds are only supported in POS and Call Center.

## Enable unlinked refunds functionality
To turn on the linked refunds functionality, go to **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters**. On the Omni-channel payments tab, set the **Use omni-channel payments** option to **Yes**.

## Supported Payment Method Variants
The following Payment Method Variants support unlinked refunds out of the box:
- Cards
- Wallet

## Processing an unlinked refund in POS
When a customer brings in an item for return and provides a receipt within the allowed period for returns, as the cashier processes the payment for the return the **Return Payment** dialogue will include an option to **Choose a payment method**. Here the option to choose a supported payment method for refunds (Ca

## Processing an unlinked refund in Call Center
When processing an unlinked refund in Call Center against an order, a Call Center employee choosing a differing payment method than the originating method will be prompted to get an Admin Override in order to process the different payment method for the refund.

### Setting up Admin Override Pin for Call Center
In **HQ**, search for **Override Permissions** in the search bar (Retail and Commerce > Channel setup > Call center setup). Select the Role for which you are allowing the unlinked refund processing permissions, and under the **Returns** fast tab, set **Allow alternate payment** to **Yes**.

> [!Note]
> Not all Cards support Unlinked Refunds. Please confirm with Adyen documentation if the payment methods you plan to configure support unlinked refunds.
