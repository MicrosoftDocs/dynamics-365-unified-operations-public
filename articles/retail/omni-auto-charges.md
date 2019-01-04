---
# required metadata

title: Omni-Channel Advanced Auto Charges
description: This topic describes capabilities for managing additional order charges for Retail channel orders using Advanced Auto Charges features.
author: hhaines
manager: AnnBe
ms.date: 1/4/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: , 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16231
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Omni-Channel Advanced Auto Charges

[!include [banner](includes/banner.md)]

This topic will provide information on configuration and deployment of the Advanced Auto Charges feature.

By enabling the Advanced Auto Charges features in Dynamics 365 for Commerce, orders created in any supported Retail channel (POS, Call Center and Online), will be able to take advantage of the [Auto-Charges](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/configure-call-center-delivery#define-charges-for-delivery-services) configurations defined in the backoffice application for both header and line level related charges.  

In previous releases, the [auto-charges](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/configure-call-center-delivery#define-charges-for-delivery-services) configurations were only accessible by orders created in Ecommerce and Call Center channels.  With this feature change, POS created orders will now be able to leverage these same auto-charges configurations, which will allow for additional misc charges to systematically be added to these sales transactions.

Before the release of the Advanced Auto Charges feature, a POS user was only prompted to manually enter a shipping fee during the creation of a "ship all" or "ship selected" POS transaction.   While this feature utilized the misc charges capabilities of the application in respect to how the charges were written to the order, it did not provide a systematic calculation and relied on the users input to determine the value of the charges.  These charges were also only able to be added as a single "shipping" related charges code and could not easily be edited or changed in the POS once created. With the new Advanced Auto Charges feature, POS users will now be able to have systematic calculations for any defined misc charges code based on auto-charges setup tables.  In addition, users will have the ability to add or edit an unlimited amount of additional charges/fees to any POS sales transaction at the header or line level (cash and carry or customer order).

## Enabling Advanced Auto Charges

From the Retail Parameters form **Retail>Headquarters setup>Parameters>Retail parameters** navigate to the **Customer orders** tab.  In the **Charges** fasttab, locate the **Use Advanced Auto-charges** toggle and set to **Yes**.

Please note that when Advanced auto-charges are enabled, users will no longer be prompted to manually enter a shipping charge at the POS terminal when creating a Ship-all or Ship-selected customer order.   Users will instead have the ability to add or maintain header or line level charges manually through newly added POS operations that should be added to your POS layouts. By turning on this feature, POS order charges may also be systematically calculated if a corresponding auto-charges table that matches the criterion of the order being created in POS are found.

Before enabling this feature, ensure you have tested and trained your employees as this will change the business process flow of how shipping or other charges are calculated and added to POS sales orders. Ensure you understand the impact of the process flow to POS transaction creation before you enable this feature.  For Call Center and Ecommerce orders, the impact of enabling Advanced Auto Charges is minimal in the first release of this feature. Call Center and Ecommerce applications will continue to have the same behavior they have had historically related to the auto-charges tables to calculate additional order fees.   Call Center channel users will continue to have the ability to manually edit any system calculated auto-charges at the header or line level or manually add additional misc charges at the header or line level.

## Additional POS Operations

In order for Advanced Auto-charges to work properly in your POS application environment, new POS operations have been added.  These operations must be added to your POS screen layouts and deployed to the POS devices as you roll out this feature.  If these operations are not added, users will not be able to manage or maintain misc charges on the POS transactions and would have no way of adjusting or changing the charges values that are systematically calculated based on auto-charges configurations.  At minimum we would suggest deploying the **Manage Charges** operation to your POS layout.

The new operations are:

- **Manage charges** - use this operation to allow POS users to view and edit misc charges for the POS transaction that were either added manually or systematically through auto-charges calculations.
- **Add header charges** - use this operation to give the user the ability to manually add a header level misc charge to any POS sales transaction (and select the charges code to be used).
- **Add line charges** - use this operation to give the user the ability to manually add a line level misc charge to any POS sales transaction line (and select the charges code to be used).
- **Recalculate charges** - use this operation to perform a full re-calculation of the charges for the sales transaction.  Any previously user-overwritten auto-charges will be recalculated based on the current cart configuration.  

As with all POS operations, security configurations can be done to require manager approval in order to execute the operation.

## Use Case Examples
The remainder of this documentation will cover some sample use cases to better understand the configuration and usage of auto-charges and misc. charges within the context of Retail channel orders.   Note that these examples will illustrate the behavior of the application when the **Use advanced auto-charges** parameter has been enabled.

### Auto-charges header charges example
#### Use case scenario description:  

_A retailer wishes to automatically add charges for freight when transactions are created in any Retail channel that require a shipment of products to the customer.  The retailer offers 2 methods of delivery: Ground and Air.   If a customer chooses Ground delivery and the order value is less than $100, the retailer wishes to charge the customer a freight charge of $10.  If the order is over $100 in value and the customer chooses ground shipping, the customer will not be charged any additional freight fees.   If the customer chooses the Air method of delivery, all orders, regardless of their total value will be charged a freight fee of $20.00._

#### Setup and Configuration

#### Sales processing in POS


#### Sales processing in call center


#### Sales processing through Ecommerce connector



### Auto-charges line charges example
#### Use case scenario description:
_A retailer wishes to add an additional charge to the customer for setup fees whenever the customer purchases a particular model of computer.  This particular computer requires additional non-optional setup actions that the retailer will perform for the customer.  The retailer has informed customers that there will be an additional fee for this setup.  The retailer prefers to manage the charges related to this fee seperately from the product sales price for finanical reporting purposes.   A setup fee of $19.99 will be charged to the customer whenver this particular computer is purchased in any retail channel._

#### Setup and Configuration

#### Sales processing in POS


#### Sales processing in call center


#### Sales processing through Ecommerce connector

### Manual header charges example
  #### Use case scenario description:
_A retailer is making an exception to normal processes and is offering to provide a special home delivery of products to a particular customer.  The retailer and the customer have agreed that the customer will pay an additional $25 handling fee for this service.  The order taker needs to add this additional fee to the transaction.  Because the fee is a blanket fee and not related to any single product on the order, a header charge will be utilized._

#### Setup and Configuration

#### Sales processing in POS


#### Sales processing in call center


#### Sales processing through Ecommerce connector

### Manual line charges example
 #### Use case scenario description:
_A customer has requested that 2 of the 5 items on their sales order be gift-wrapped. The retailer offers this optional service for a fee of $2.00 per item.  The order taker will need to add these fees to the specific items that need to be gift-wrapped._

#### Setup and Configuration

#### Sales processing in POS


#### Sales processing in call center


#### Sales processing through Ecommerce connector

## Additional Features
### Editing charges on a POS sales transaction

### Editing charges on a Call Center sales transaction

### Editing charges on an Ecommerce transaction

### Refunding charges on a POS return transaction

### Refunding charges on a Return Order transaction in HQ

