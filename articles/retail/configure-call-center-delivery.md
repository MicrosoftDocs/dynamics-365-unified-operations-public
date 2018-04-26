---
# required metadata

title: Configure call center delivery modes and charges
description: This topic describes how to set up modes of delivery and charges for a call center order in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 04/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailMCRChannelDetailPage, MCROrderParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Configure call center delivery modes and charges 

[!INCLUDE [banner](includes/banner.md)]

When placing a sales order in Dynamics 365 for Retail, if the user is tied to a call center channel, the sales orders they create will utilize logic and rules for delivery mode validation and charges.

When creating a sales order, a delivery mode can be configured on the sales order header and the sales order lines. The mode of delivery selected on the header will default to all sales lines, although it is possible to override the mode of delivery on any individual sales line as needed.   It is also possible to define a mode of delivery on the customer record, which can be defaulted into the order header when orders are created for that customer.

Dynamics 365 for Retail has capabilities to allow users to limit which delivery modes can be utilized by a channel, which delivery modes can be used for a product, and which delivery modes are valid for certain shipping destinations.  Charges can also be defined to add additional fees to a customer’s order based on the delivery mode(s) selected for a sales order in relation to the total order value.

## Define modes of delivery
Before configuring which modes of delivery can be used for call center orders and the associated rules and charges, the modes of delivery must first be defined. Navigate to **Sales and marketing > Setup > Distribution > Modes of delivery**.  Click the New action button to create a new mode of delivery, or select an existing method from the list and click the Edit action button to make changes.

You may choose any alphanumeric combination to define the data for the Mode of delivery field based on your business needs.  The Description field can be used to provide additional context.  The Charges group is optional and will be further defined later in this document.  The Expedite setting is optional and will be further defined later in this document.

From the Retail channels section, add any Retail channel that should be allowed to select and use this delivery mode when creating sales transactions in that channel.

In the Products section, you can define which product and/or product categories to include or exclude from being able to use this mode of delivery.  For example, if you have a product that cannot ship by Air due to hazmat restrictions, ensure that this product or product category is excluded from all Air transportation methods.  

In the Addresses section, you can define which countries/regions or states can be included or excluded from using this delivery method.  For example, orders shipping to Hawaii or Alaska are not eligible for Ground delivery.   In this scenario, these states would be excluded from any method of delivery that is associated to a ground delivery service but would be included in any Air delivery services defined.


