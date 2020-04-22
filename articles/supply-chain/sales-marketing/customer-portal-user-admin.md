---
# required metadata

title: Create and manage Customer portal users
description: How to create Customer portal user accounts and set permissions for them
author: dasani-madipalli
manager: tfehr
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-04-22
ms.dyn365.ops.version: Release 10.0.13
---

# Create and manage Customer portal users

Out of the box, there is no way for users to self-register for websites that are created using the Customer portal. To sign in and use the website, users must be invited by the admin. Microsoft has intentionally blocked the ability of users to self-register.

Before a user can use the website, a contact record must be created for that user. This contact record indicates which customer account and legal entity the user belongs to. This information is essential for ensuring that the user can create and view sales orders.

When users self-register, contact records are automatically created for them. Therefore, you can't ensure that a user selects the correct customer account and legal entity. On the other hand, the invitation process lets an admin assign the correct customer account and legal entity to the contact record before an invitation is sent. If you're thinking about customizing the solution so that users can self-register, be sure to consider the possible consequences.

## Prerequisite setup

Contacts in Power Apps portals are stored as records in the **Contacts** entity in Common Data Service. Dual-write then syncs these records to Supply Chain Management as required.

![Customer portal contacts system diagram](media/customer-portal-contacts.png "Customer portal contacts system diagram")

Before you start to invite new customers, make sure that you've enabled the **Contact** entity mapping in dual-write.

## The invitation process

To invite an existing contact to the Customer portal, follow the steps in [Invite contacts to your portals](https://docs.microsoft.com/powerapps/maker/portals/configure/invite-contacts) in the Power Apps portals documentation.

Before you invite a customer to join the Customer portal, make sure that the customer's [contact record](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-contacts) is available and set up in the following way:

1. Set the **Company** field to the legal entity that you want the customer to belong to in Supply Chain Management.
2. Set the **Account Number** field to the customer account number that you want the user to have in Supply Chain Management.

After a contact is created, you should be able to see the same contact in Supply Chain Management.

For more information, see [Configure a contact for use on a portal](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-contacts) in the Power Apps portals documentation.

## Out-of-box web roles and entity permissions

User roles in Power Apps portals are defined by [web roles](https://docs.microsoft.com/powerapps/maker/portals/configure/create-web-roles) and [entity permissions](https://docs.microsoft.com/powerapps/maker/portals/configure/assign-entity-permissions). A few roles are defined for the Customer portal out of the box. You can create new roles, and you can modify or remove existing roles.

### Out-of-box web roles

This section describes the web roles that are delivered with the Customer portal.

For more information about how to modify the out-of-box user roles, see [Create web roles for portals](https://docs.microsoft.com/powerapps/maker/portals/configure/create-web-roles) and [Add record-based security by using entity permissions for portals](https://docs.microsoft.com/powerapps/maker/portals/configure/assign-entity-permissions) in the Power Apps portals documentation.

#### Administrator

The administrator oversees and maintains the website. This person will provision and set up the Customer portal. The administrator maintains the IT and security aspects of the portal, and makes sure that everything runs smoothly. The administrator might also customize and/or change the portal by adding new functionalities, creating new roles, and more.

#### Customer representative

A customer representative works for a customer company and is responsible for managing the orders that the company places. The customer representative can see all the orders that have been placed for the company and the users who placed them. Additionally, the customer representative can see information about the overall account and which contacts can place orders on behalf of that account.

#### Authorized users

Authorized users can place orders and view the status of the orders that they have placed, but not the orders that other users at their company have placed.

#### Unauthorized users

Unauthorized users can't view any data. They can see only public information, such as terms and conditions, and details about the company that is running the Customer portal.

#### Example

The following table shows which sales orders the users in each web role will be able to see in the system.

| **Sales order** | **Administrator** | **Customer representative for customer X** | **Authorized user: Jane** | **Authorized user: Sam** | **Unauthorized user: May** |
| --- | --- | --- | --- | --- | --- |
| Customer&nbsp;X Orderer:&nbsp;Jane | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; |
| Customer&nbsp;X Orderer:&nbsp;Sam | &#10004; | &#10004; | &#10007; | &#10004; | &#10007; |
| Customer&nbsp;Y Orderer:&nbsp;May | &#10004; | &#10007; | &#10007; | &#10007; | &#10007; |

> [!NOTE]
> Even though both Sam and Jane are contacts who work for customer X, they can see only the orders that they themselves have placed and nothing else. Although May has an order in the system, she can't see that order in the Customer portal, because she is an unauthorized user. (Additionally, she must have placed the order through some channel other than the portal.)

