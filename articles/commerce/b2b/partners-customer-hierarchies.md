---
# required metadata

title: Manage B2B business partners using customer hierarchies
description: This topic covers how to manage business partners using customer hierarchies for Microsoft Dynamics 365 Commerce B2B e-commerce websites.
author: josaw1
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgriffin
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Manage B2B business partners using customer hierarchies

[!include [banner](../../includes/banner.md)]

This topic covers how to manage business partners using customer hierarchies for Microsoft Dynamics 365 Commerce B2B e-commerce websites.

In Commerce headquarters, a *Customer hierarchy* entity is used to represent the business partner organizations who will use your B2B e-commerce site. To get started managing business partners using customer hierarchies, in Commerce headquarters you must first enable the B2B e-commerce capabilities and then define the customer hierarchy number sequence.

## Enable the B2B e-commerce feature in Commerce headquarters

To use the B2B e-commerce capabilities, you must first enable the **"Enable the use of B2B eCommerce capabilities"** feature in Commerce headquarters. 

To enable the **"Enable the use of B2B eCommerce capabilities"** feature, follow these steps.

1. Go to **Workspaces \> Feature management**.
1. Select the **All** tab, and then in the filter box search for "Module: Retail and Commmerce".
1. Find the **Enable the use of B2B eCommerce capabilities**, select it, and then select **Enable now** in the bottom-right corner.

## Define a number sequence for the customer hierarchy

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. You must define a number sequence that will be used to generate the ID for the customer hierarchy. For more information about number sequences, see [Number sequences overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

To define a number sequence for the customer hierarchy in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Number sequences \> Number sequences** and create a number sequence. You can reuse any existing number sequence as well.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters** and add the number sequence created or selected above to the **Customer hierarchy ID** reference as shown in the example image below.

![Assign a number sequence](../media/NumberSequenceCustHierarchy.png)

## How the approval process works

When a business partner requests to join a B2B e-commerce site, the system saves this request as a *prospect*. A headquarters persona such as a retail operations manager can approve or reject partner requests. For more information on managing business partner requests and prospects approval, see [Manage business partner users on B2B e-commerce websites](manage-b2b-users.md).
 
When a prospect is approved, the system creates two new customer records: 

- One customer record of type "Organization" to represent the organization that is requesting to become the business partner. 
- One customer record of type "Person" to represent the person who submitted the request. 

In addition, a new customer hierarchy record is created under **Retail and Commerce \> Customers \> Customer hierarchies**. This customer hierarchy record has the following properties:

- **Customer hierarchy ID** – A unique ID for the customer hierarchy. This ID uses the number sequence that is defined in Commerce shared parameters.
- **Name** – The organization name of the business partner, as specified in the onboarding request. This field is editable.
- **Purpose** – This property is set to the predefined value "B2B organization".
- **Organization** – The customer ID of the business partner organization.

The person who submitted the onboarding request is added under the **Hierarchy** FastTab with the role of **Admin**. When the administrator adds more users to the business partner organization on a B2B site, a new customer record created for each user. This customer record is also added to the relevant customer hierarchy record for the business partner and has the role of a **User**. 

### Examples

For example, a person Sam J. submits an onboarding request on behalf of the Microsoft organization. Once the request is approved, two new customer accounts are created: one for Sam J. and one for Microsoft. Also, as shown in the example image below a new customer hierarchy record is created with the same name as the organization ("Microsoft") and Sam J. was assigned the role of **Admin**. Any additional Microsoft users of the B2B site are added to this hierarchy with the role of **User**, such as Sush R. in the example below.

![Example of a customer hierarchy record](../media/CustomerHierarchy2.png)

To determine if a customer is associated with a customer hierarchy, open the cutomer record. As shown in the exmaple image below, on the Retail FastTab of the customer record you can see if the customer is a part of a customer hierarchy and if the customer is an admininistrator of that hierarchy.

![Example of a customer record highlighting the B2B section with the customer hierarchy ID and B2B administrator toggle](../media/CustomerHierarchyMapping2.png)

> [!NOTE]
> In most cases, the property values of all customer records in a hierarchy should match. For example, because all business partner users should get similar prices for products, their price group and associated configurations should match. However, the system doesn't enforce this consistency, so the relevant Commerce headquarters users are responsible for ensuring that the property values and configurations match for all customers within a given hierarchy.

Headquarters users can inspect property values for all customer records of a hierarchy in a side-by-side view. As shown in the example image below, you can use the drop-down list option **General** on the **Hierarchy** FastTab and then select any section of the customer record to display the related properties. Users can edit the property values directly in this view. To copy all of the values from an administrator customer record to all users, select **Override** on the **Hierarchy** FastTab. 

![Customer hierarchy record highlighting the Override button and showing the drop-down list options](../media/HierarchyDetails2.png)



[!include [footer-include](../../includes/footer-banner.md)]
