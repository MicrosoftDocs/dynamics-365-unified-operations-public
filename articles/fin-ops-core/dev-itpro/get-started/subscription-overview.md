---
title: Subscriptions, Lifecycle Services projects, and Microsoft Entra tenants FAQ
description: Access answers to frequently asked questions about subscriptions and licenses, Microsoft Entra tenants, and Lifecycle Services Implementation projects.
author: skaue-ms
ms.author: toskaue
ms.topic: overview
ms.date: 03/26/2026
ms.reviewer: joihnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0
---

# Subscriptions, Lifecycle Services projects, and Microsoft Entra tenants FAQ

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../../includes/lcs-freeze-banner.md)]

When customers subscribe through a Microsoft Volume Licensing agreement or a Microsoft Cloud Solution Provider (CSP) agreement, they usually have one Microsoft Microsoft Entra tenant, one Microsoft Dynamics Lifecycle Services Implementation project, and any number of sandbox environments that are deployed to one data center of the customer's choice, and one production environment. For more information about these core concepts, see [finance and operations application architecture](../organization-administration/architecture-overview.md). Although this setup works well for most projects, more advanced scenarios are sometimes required, or changes during the implementation lifecycle must be accommodated.

This article provides answers to frequently asked questions about subscriptions and licenses, Microsoft Entra tenants, and Lifecycle Services Implementation projects.

For more information, see the following topics:

- [Move environments between data centers](../../fin-ops/get-started/move-environments-data-center.md)
- [Move licenses between agreement types](move-licenses-between-agreement-types.md)
- [Move Lifecycle Services implementation projects to different Microsoft Entra tenants](move-lcs-implementation-project-tenant.md)
- [Multiple Lifecycle Services projects and production environments on one Microsoft Entra tenant](implement-multiple-projects-aad-tenant.md)

## Do I have to move Microsoft Entra tenants when I move from a CSP agreement to a Volume Licensing agreement?

No. You can keep the existing Microsoft Entra tenant, but you must make sure that the Volume Licensing subscriptions are purchased against the same Microsoft Entra tenant as the CSP subscriptions.

## Do I get a new Lifecycle Services Implementation project when I move from a CSP agreement to a Volume Licensing agreement?

No. The Lifecycle Services project remains the same.

## Can I keep the existing Lifecycle Services Implementation project when I move to different Microsoft Entra tenant?

No. A new Lifecycle Services project is created.

## How long does it take to move from a CSP agreement to a Volume Licensing agreement?

For a Volume Licensing purchase, it can take a few days for the order to process and the subscriptions to activate. Redeployment of add-on environments has a service level agreement (SLA) of two business days. It takes a few hours to deallocate and delete old add-on environments.

## What if I forget to delete the existing environments before I suspend the existing subscription?

If you don't deallocate and delete the existing environments before you suspend the subscriptions, the environments stay in a **Deployed** state. However, if you try to access the full details of these environments, you receive an error message.

## Can I have a CSP agreement and a Volume Licensing agreement in parallel?

Yes. However, you must maintain the minimum required number of licenses under each program.

## How can I find the Tenant name and Tenant ID within Lifecycle Services?

1. Go to the project home page in Lifecycle Services.
1. In the **Environments** section, select **Subscriptions available**.
1. On the **Subscriptions available** page, you find the **Tenant name** and the **Tenant ID**.

## How can I find the subscription status?

1. Go to the project home page in Lifecycle Services.
1. In the **Environments** section, select **Subscriptions available**.
1. On the **Subscriptions available** page, you see all **Service plans** available to the tenant.  
1. The **Assigned date** indicates the date that service plan status changed.

## How does the subscription status affect the environment?

The subscription status can affect some of the environment operations:

- **Active** - Your subscription is active. You can perform all environment operations.
- **In Grace Period** - Your subscription expired, but is still within the grace period. Renew your subscription soon. The subscription status doesn't affect your license quantity, ability to deploy a new environment, or ability to perform environment operations.
- **Suspended** - Your subscription expired and is beyond the grace period. This subscription status might reduce the license quantity, affect your ability to deploy a new environment, or affect your ability to perform environment operations.
- **Deleted** - Your subscription is deleted. This status affects your ability to deploy a new environment or perform environment operations.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
