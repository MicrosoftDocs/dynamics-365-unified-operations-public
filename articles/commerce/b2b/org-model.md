---
# required metadata

title: Create org modeling hierarchies for B2B organizations
description: This topic describes how to create represent your business partners i.e. the customers of your business-to-business B2B e-commerce site using Customer hierarchies in Microsoft Dynamics 365 Commerce.
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

# Manage business partners using the Customer hierarchies

[!include [banner](../../includes/banner.md)]

## Turn on the B2B e-commerce feature in Commerce headquarters
To use the B2B e-commerce capabilities, you need to enable the feature **"Enable the use of B2B eCommerce capabilities"** from Feature management. To do so, follow the below steps:
- Go to Workspaces > Feature Management.
- On the All tab, filter on the Module field by using the term Retail and commerce.
- Find and select the feature that is named ** "Enable the use of B2B eCommerce capabilities" **, and then select Enable now.

## Define a number sequence for customer hierarchy
Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. For more information about number sequences, see Number sequences overview.

You need to define a number sequence that will be used to generate the ID for the Customer hierarchy. Follow the below steps to do so:
- Go to Retail and Commerce > Headquarters setup > Number sequences > Number sequences, and create a number sequence. You can reuse any existing number sequence as well.
- Go to Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters, and add the number sequence selected above to the "Customer hierarchy ID" reference. Refer the image below.

![Assign a number sequence](/articles/commerce/media/NumberSequenceCustHierarchy.png "Assign a number sequence to customer hierarchy")

## Customer hierarchies
In Commerce headquarters, a new entity named "Customer hierarchies" is used to represent the business partner organizations who will use your B2B e-commerce site. When a business partner requests to join the B2B e-commerce site, then the system saves this request as a Prospect. An headquarters persona such as Retail operations manager can Approve or Reject this request. 

> [!NOTE>
> More details on the business partner request and Prospects approval can be found here: Manage business partner users on B2B e-commerce websites - Commerce | Dynamics 365 | Microsoft Docs>
 
When a Prospect is approved, the system creates **two new customer records** - one as a type "Organization" to represent the organization which is requesting to become the business partner and another as a type "Person" to represent the person who submitted the request. Additionally, a new customer hierarchy record is created under the "Retail and Commerce -> Customers -> Customer hierarchies" node. This record has the following properties:

- Customer hierarchy ID – A unique ID for the customer hierarchy. This ID uses the number sequence that is defined in Commerce shared parameters.
- Name – The organization name of the business partner, as specified in the onboarding request. This field is editable.
- Purpose – This property is set to the predefined value "B2B organization".
- Organization – The customer ID of the business partner organization.

The person who submitted the onboarding request is added under the "Hierarchy" fast tab with the Admin role. When the administrator adds more users are to the business partner organization on a B2B site, a new customer record created for each user of the B2B e-commerce site. This customer record is also added to the relevant customer hierarchy record for the business partner and has the role of a "user". Referring to the below image, the person Sam Jarawan submitted the onboarding request on behalf of the Microsoft Organization. Once the request was approved, two new customer accounts got created i.e. one for Microsoft and one for Sam Jarawan. Additionally, a new customer hierarchy got created with the same name as the organization name. Microsoft got listed as the Organization and Sam was added as an Admin. Any additional users of the B2B site within Microsoft will need to be added to this hierarchy. For e.g. Sushma was added as a user to this hierarchy.

![Customer hierarchy](/articles/commerce/media/CustomerHierarchy.png "Customer hierarchy")


To know if a customer is associated to a customer hierarchy, you can open the customer details form. Referring to the below image, the Retail fast tab on the customer record shows if this customer is a part of any customer hierarchy and if this customer is an admin of that hierarchy.

![Customer hierarchy to customer mapping](/articles/commerce/media/CustomerHierarchyMapping.png "Customer hierarchy to customer mapping")


> [!NOTE]
> In most cases, the property values of all customer records in a hierarchy should match. For example, because all business partner users should get similar prices for products, their price group and associated configurations should match. However, the system doesn't enforce this consistency. Therefore, the relevant Commerce headquarters users are responsible for ensuring that the property values and configurations match for all customers in a given hierarchy.


Commerce headquarters users can look at the property values for all customer records in the hierarchy in a side-by-side view. Referring to the image below, you can use the dropdown showing "General" on the Hierarchy fast tab and select any section of customer record and display the related properties. Users can edit the property values directly in this view. Alternatively, if you want to copy all the values from the administrator customer record to all the users, then press the "Override" button on the Hierarchy fast tab. 

![Customer hierarchy details](/articles/commerce/media/HierarchyDetails.png "Customer hierarchy details")



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
