---
title: Move licenses between agreement types
description: Learn about how to move licenses between agreement types, including outlines on default and add-on environments.
author: markusotte08
ms.author: maotte
ms.topic: article
ms.date: 01/26/2022
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0
---

# Move licenses between agreement types

[!include [banner](../../../finance/includes/banner.md)]

Sometimes, a customer who originally purchased subscriptions through a Microsoft Cloud Service Provider (CSP) agreement decides to change to a Microsoft Volume Licensing agreement with Microsoft after the Microsoft Dynamics Lifecycle Services (LCS) Implementation project has been created. The customer can make this change even after the project has gone live in production.

Less often, a customer who originally purchased the subscriptions through a Volume Licensing agreement with Microsoft decides to change to a CSP agreement. In this case, the change must align with the renewal date of the Volume Licensing agreement.

The process of moving subscriptions from one type of agreement to another is primarily a commercial process. The technical implications for the LCS Implementation project are minimal.

> [!NOTE]
> The movement of subscriptions between agreement types isn't the same as the movement of a Microsoft Entra tenant. If the contractual changes in the agreements require that the **Microsoft Entra tenant** on the subscriptions be changed, you must also follow the process that is described in [Move LCS implementation projects to different Microsoft Entra tenants](move-lcs-implementation-project-tenant.md).

Subscriptions come with two standard environments: 

- A **production** environment 
- A **Tier-2 Standard Acceptance Test** environment

These environments aren't affected by the movement of subscriptions between agreement types. Impact is visible in LCS only if the customer has additional **add-on environments**. In this case, no explicit action related to the add-on environments is required by the partner or customer. However, during the time when both CSP and Volume Licensing agreements are active or in a grace period, additional slots for the add-on environments are visible in LCS. Those should simply be ignored, as they will disappear as soon as the redundant licensing agreement has expired. Those additional slots must **not** be deployed as this would violate the licensing agreement.

### Commercial activities

When a customer changes the licensing agreement through which they obtained their subscriptions, this is considered a *commercial transaction* that requires working with external parties which sell the subscriptions to Dynamics 365 services. The goal is to have uninterrupted access to the service during that time of transition. 

Use the following steps to complete the commercial transaction.


1. The customer places the order for subscriptions under the new agreement with the Volume Licensing reseller or the CSP.

    > [!IMPORTANT]
    > Make sure that the subscriptions are purchased against the same Microsoft Entra tenant that is used on the original agreement.

2. The customer activates the subscriptions.
3. In Microsoft 365 Admin Center, the customer verifies that both the new and the existing subscriptions are active for all user and device licenses, as well as for the add-on environment subscriptions. 
4. When the new subscriptions are active, the customer requests that the Volume Licensing reseller or the CSP suspend the existing subscriptions. Typically, there is an overlap to help guarantee continuity and avoid disruption of service.


## The customer only has default environments

If the customer has only the two standard environments that come with the Microsoft-managed subscription, and didn't purchase any add-on environments through the original CSP agreement or Volume Licensing agreement, no changes will be visible in LCS.


## The customer has add-on environments

If the customer purchased add-on environments through the original CSP agreement or Volume Licensing agreement, those environments will continue to function without any disruption. For each add-on environment that the customer has ordered on the old agreement, as well as on the new licensing agreement, they will now see two slots in LCS. Typically, the slot from the old agreement will be deployed, while the slot from the new agreement will show up as a new undeployed **DYNAMICS 365 OPERATIONS SANDBOX** slot in **Configure** state. Customers must not deploy more environments in total than they have purchased on the new licensing agreement, as the environment slots will disappear when the old licensing agreement expires.

It is important that customers verify that they do have the desired amount of add-on environments on the new licensing agreement. Customers can verify the number of purchased add-on environments on the **Subscriptions available** page in LCS, or in the Microsoft 365 admin center under **Billing > Your products**.

> [!NOTE]
> LCS displays the aggregate number of subscriptions across all licensing agreements. During the transition period, while the old and new license agreement are active, the numbers will probably be higher than the desired number of subscriptions after the old licensing agreement has expired.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]