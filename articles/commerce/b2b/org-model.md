---
# required metadata

title: Create org modeling heirarchies for B2B organizations
description: This topic describes how to create organizational modeling heirarchies for B2B organizations.
author: josaw1
manager: AnnBe
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Create org modeling heirarchies for B2B organizations

[!include [banner](../../includes/banner.md)

This topic describes how to create organizational modeling heirarchies for B2B organizations.

Business partner organizations are represented through customer & customer hierarchy entities in Dynamics 365 Commerce headquarters. The business partner organization and its users are represented as customers and these customers are associated with each other using customer hierarchies.

When a business partner request is approved, the following flowing actions are performed:

- Two new customer records are created in the system: a **Type Organization** customer record for the business partner organization and a **Type Person** customer record for the requestor.
- A new customer hierarchy record is created under **Customer \> Customer hierarchy** with the following header properties:
    - **Customer hierarchy ID** – A unique ID for the customer hierarchy that uses the number sequence defined in Commerce headquarters shared parameters.
    - **Name** – The organization name of the business partner, as specified in the onboarding request.
    - **Purpose** – This property is set to a predefined value of "B2B organization."
    - **Organization** – The business partner customer ID.

The details of the customer hierarchy record are as follows:
- The customer record of the requestor is associated with the customer hierarchy.
- The role of administrator is associated with the requestor.

When additional users are added to the business partner organization by the administrator on the B2B site, a new customer record for each user is also created in headquarters and the new customer record is also added to the relevant business partner customer hierarchy record with the role of a "user."

> [!NOTE]
> In most cases, the respective property values of all customer records in the hierarchy should match. For example, all the users of the business partner should get similar prices for products and so their price group and associated configurations should be the same. However, the system does not enforce these consistencies so it is up to the relevant headquarters users to ensure that the field values and configurations for all customers in the hierarchy are the same.

Headquarters users can see field values for all customer records in the hierarchy in a side-by-side view. To do this, choose to the relevant fields of the customer tab by selecting the tab name from the drop-down list. Users can directly view and edit the property values directly from this view. Alternatively, if you want to apply all the values from the administrator customer record to all the user customer records, select **Override** on the customer hierarchy details page.

<!-- link to create partner user topic at top of this topic-->

