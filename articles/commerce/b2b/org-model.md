---
# required metadata

title: Org modeling of B2B organizations
description: This topic describes how to create org mdel heirarchies for B2B organizations.
author: josaw1
manager: AnnBe
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Org modeling of B2B organizations

[!include [banner](../../includes/banner.md)]

Business partner organizations are represented through customer & customer hierarchy entities in Dynamics 365 Commerce headquarters. The business partner organization and its users are represented as **Customers** & these customers are associated with each other using the customer **hierarchies**.

When a business partner request is approved, the flowing actions are performed:

1.  2 new customer records are created in the system, one customer of
    the **Type Organization** for the Business partner organization and
    second customer of the **Type Person** for the requestor

2.  A new customer hierarchy record is created under **Customer &gt;
    Customer hierarchy** and the header fields are populated as below:

    1.  Customer hierarchy id – unique id for the customer hierarchy using the number sequence defined in Commerce shared parameters

    2.  Name – Organization name of the business partner as specified in the onboarding request

    3.  Purpose – It is set to a pre-define value of B2B organization

    4.  Organization – the Business partner customer ID is associated with this field

    <!-- -->

    1.  The details of the customer hierarchy records are populated as below:

        1.  The customer record of the requestor is associated to the
            customer hierarchy and the role of **Admin** is associated
            to the requestor

When additional users are added to the Business partner organization by the Admin on the B2B website, a new customer record for the same is also created in HQ and the newly customer record is also added to the relevant business partner customer hierarchy record with the role of a **User**

> [!NOTE]
> In most cases, the fields of all the customers in the hierarchy should have the same value. For eg: all the users of the business partner should get similar prices for products and as such their price group & associated configuration must be the same. However, system does not enforce this, and it is up to the relevant HQ users to ensure that the field values and the configurations for the customers in the hierarchy are the same.
>
> HQ users can see the field values for all the customers in the hierarchy in a side by side view by choosing to see the relevant fields of the customer tab by selecting the tab name from the drop down list. Users can directly edit / maintain the field values directly from this view. Alternatively, if the user wants to apply all the values from the customer of the role **Admin** to all the other customers of the role **User**, the same can be done by clicking on the **Override** button on the customer hierarchy details.

<!-- link to create partner user topic at top of this topic-->

