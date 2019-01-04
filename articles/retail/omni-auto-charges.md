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

In order for Advanced Auto-charges to work properly in your POS application environment, 3 new POS operations have been added.  These operations must be added to your POS screen layouts and deployed to the POS devices as you roll out this feature.  If these operations are not added, users will not be able to manage or maintain misc charges on the POS transactions and would have no way of adjusting or changing the charges values that are systematically calculated based on auto-charges configurations.  At minimum we would suggest deploying the **Manage Charges** operation to your POS layout.

The 3 new operations are:
**Manage Auto-charges**
**Add Header Charges**
**Add Line Charges**

As with all POS operations, security configurations can be done to require manager approval in order to execute the operation.

## POS auto-charges header charges example


## POS auto-charges line charges example

## POS manual header charges example

## POS manual line charges example

## Editing charges on a POS transaction


## Refunding charges on a POS transaction

