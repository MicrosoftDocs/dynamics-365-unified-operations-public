---
# required metadata

title: Create org modeling hierarchies for B2B organizations
description: This topic describes how to create organizational modeling hierarchies for business-to-business (B2B) organizations.
author: josaw1
ms.date: 01/20/2021
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
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

# Create org modeling hierarchies for B2B organizations

[!include [banner](../../includes/banner.md)]

This topic describes how to create organizational modeling hierarchies for business-to-business (B2B) organizations in Microsoft Dynamics 365 Commerce.

In Commerce headquarters, business partner organizations are represented by customer and customer hierarchy entities. The business partner organization and its users are represented as customers, and customer hierarchies are used to associate those customers with each other.

When a business partner request to join a B2B e-commerce site is approved, the following actions are performed:

- Two new customer records are created in the system: a **Type Organization** customer record for the business partner organization and a **Type Person** customer record for the requestor (that is, the business partner user who submitted the request).
- A new customer hierarchy record is created under **Customer \> Customer hierarchy**. This record has the following header properties:

    - **Customer hierarchy ID** – A unique ID for the customer hierarchy. This ID uses the number sequence that is defined in Commerce shared parameters in Commerce headquarters.
    - **Name** – The organization name of the business partner, as specified in the onboarding request.
    - **Purpose** – This property is set to the predefined value **B2B organization**.
    - **Organization** – The customer ID of the business partner.

Here are the details of the customer hierarchy record:

- The customer record of the requestor is associated with the customer hierarchy.
- The administrator role is associated with the requestor.

When the administrator adds more users are to the business partner organization on a B2B site, a new customer record for each user is created in Commerce headquarters. This customer record is also added to the relevant customer hierarchy record for the business partner and has the role of a "user."

> [!NOTE]
> In most cases, the corresponding property values of all customer records in a hierarchy should match. For example, because all business partner users should get similar prices for products, their price group and associated configurations should match. However, the system doesn't enforce this consistency. Therefore, the relevant Commerce headquarters users are responsible for ensuring that the property values and configurations match for all customers in a given hierarchy.

Commerce headquarters users can look at the property values for all customer records in the hierarchy in a side-by-side view. Select the relevant customer record properties by selecting the tab names on the drop-down menu. Users can directly view and edit the property values from this view. Alternatively, if you want to apply all the values from the administrator customer record to all the user customer records, select **Override** in the customer hierarchy details.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Manage business partner users on B2B e-commerce sites](manage-b2b-users.md)

[Configure the customer account payment method for B2B e-commerce sites](payment-method.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
