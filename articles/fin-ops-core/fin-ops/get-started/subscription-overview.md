---
# required metadata

title: Subscriptions, LCS projects, and Azure Active Directory tenants FAQ
description: This topic provides answers to frequently asked questions about subscriptions and licenses, Azure AD tenants, and LCS Implementation projects.
author: ClaudiaBetz-Haubold 
ms.date: 08/11/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Subscriptions, LCS projects, and Azure Active Directory tenants FAQ

[!include [banner](../includes/banner.md)]

When customers subscribe through a Microsoft Volume Licensing agreement or a Microsoft Cloud Solution Provider (CSP) agreement, they usually have one Microsoft Azure Active Directory (Azure AD) tenant, one Microsoft Dynamics Lifecycle Services (LCS) Implementation project and any number of sandbox environments that are deployed to one data center of the customer's choice, and one production environment. For more information about these core concepts, see [Finance and Operations application architecture](../imp-lifecycle/architecture-overview.md). Although this setup works well for most projects, more advanced scenarios are sometimes required, or changes during the implementation lifecycle must be accommodated.

This topic provides answers to frequently asked questions about subscriptions and licenses, Azure AD tenants, and LCS Implementation projects.

For more information, see the following topics:

- [Move environments between data centers](move-environments-data-center.md)
- [Move licenses between agreement types](move-licenses-between-agreement-types.md)
- [Move LCS implementation projects to different Azure AD tenants](move-lcs-implementation-project-tenant.md)
- [Multiple LCS projects and production environments on one Azure AD tenant](implement-multiple-projects-aad-tenant.md)

## Do I have to move Azure AD tenants when I move from a CSP agreement to a Volume Licensing agreement?

No. You can keep the existing Azure AD tenant, but you must make sure that the Volume Licensing subscriptions are purchased against the same Azure AD tenant as the CSP subscriptions.

## Do I get a new LCS Implementation project when I move from a CSP agreement to a Volume Licensing agreement?

No. The LCS project remains the same.

## Can I keep the existing LCS Implementation project when I move to different Azure AD tenant?

No. A new LCS project will be created.

## How long does it take to move from a CSP agreement to a Volume Licensing agreement?

For a Volume Licensing purchase, it can take a few days for the order to be processed and the subscriptions to be activated. Redeployment of add-on environments has a service level agreement (SLA) of two business days. It takes a few hours to deallocate and delete old add-on environments.

## What if I forget to delete the existing environments before I suspend the existing subscription?

If you don't deallocate and delete the existing environments before you suspend the subscriptions, the environments will remain in a **Deployed** state. However, if you try to access the full details of these environments, you will receive an error message.

## Can I have a CSP agreement and a Volume Licensing agreement in parallel?

Yes. However, you must maintain the minimum required number of licenses under each program.

## How can I find the Tenant name and Tenant ID within LCS?
1. Go to project home page in LCS.
2. In the **Environments** section, select **Subscriptions available**.
3. On the **Subscriptions available** page, you will find the **Tenant name** and the **Tenant ID**.

## How can I find the subscription status?
1. Go to the project home page in LCS.
2. In the **Environments** section, select **Subscriptions available**.
3. On the **Subscriptions available** page, you’ll find all **Service plans** available to the tenant.  
4. The **Assigned date** indicates the date that service plan status was changed. 

## How would the subscription status impact the environment?
Some of the environment's operations may be impacted by the subscription status:
- **Active** - Your subscription is in an operative state. You should be able to perform all environment operations. 
- **In Grace Period** - Your subscription has expired, but is within the grace period. You should renew your subscription soon. The subscription status won’t impact your license quantity, ability to deploy a new environment, or to perform environment operations.
- **Suspended** - Your subscription has expired beyond the grace period. This subscription status may reduce the license quantity, impact your ability to deploy a new environment, or impact your ability to perform environment operations. 
- **Deleted** - Your subscription has been deleted. This will impact your ability to deploy a new environment or perform environment operations.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]