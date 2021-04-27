---
# required metadata

title: Move licenses between agreement types
description: This topic explains how to move licenses between agreement types.
author: ClaudiaBetz-Haubold 
ms.date: 01/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Move licenses between agreement types

[!include [banner](../includes/banner.md)]

Sometimes, a customer who originally purchased subscriptions through a Microsoft Cloud Service Provider (CSP) agreement decides to change to a Microsoft Volume Licensing agreement with Microsoft after the Microsoft Dynamics Lifecycle Services (LCS) Implementation project has been created. The customer can make this change even after the project has gone live in production.

Less often, a customer who originally purchased the subscriptions through a Volume Licensing agreement with Microsoft decides to change to a CSP agreement. In this case, the change must align with the renewal date of the Volume Licensing agreement.

The process of moving subscriptions from one type of agreement to another is primarily a commercial process. The technical implications for the LCS Implementation project are minimal.

> [!NOTE]
> The movement of subscriptions between agreement types isn't the same as the movement of an Azure Active Directory (Azure AD) tenant. If the contractual changes in the agreements require that an Azure AD tenant be moved, you must also follow the process that is described in [Move LCS implementation projects to different Azure AD tenants](move-lcs-implementation-project-tenant.md).

Subscriptions come with two standard environments: a production environment and a Tier-2 Standard Acceptance Test environment. These environments aren't affected by the movement of subscriptions between agreement types. Action might be required in LCS only if the customer has additional add-on environments. In this case, action that is related to the add-on environments requires minimal effort on the part of partner or customer resources. To streamline the movement of data between environments, you should plan in advance to determine the best sequence.

## The customer has only default environments

If the customer has only the two standard environments that come with the Microsoft-managed subscription, and didn't purchase any add-on environments through the original CSP agreement or Volume Licensing agreement, the activities that are required are purely commercial.

1. The customer places the order for subscriptions under the new agreement with the Volume Licensing reseller or the CSP.

    > [!IMPORTANT]
    > Make sure that the subscriptions are purchased against the same Azure AD tenant that is used on the original agreement.

2. The customer activates the subscriptions.
3. In Microsoft 365 Admin center, the customer verifies that both the new and subscriptions and the existing subscriptions are active.
4. When the new subscriptions are active, the customer requests that the Volume Licensing reseller or the CSP suspend the existing subscriptions. Typically, there is an overlap to help guarantee continuity and avoid disruption of service.

## The customer has add-on environments

If the customer purchased add-on environments through the original CSP agreement or Volume Licensing agreement, those environments should be redeployed.

### Prerequisites

Before you begin the move, you must complete the following tasks:

- Save the data from your existing environments. Follow one of the options described in [Database movement operations home page](../../dev-itpro/database/dbmovement-operations.md).

- Verify that all code packages have been uploaded to the Shared asset library in LCS.

### Commercial activities

1. The customer places the order for the subscriptions under the new agreement with the Volume Licensing reseller or the CSP. These subscriptions include the subscriptions for the add-on environments.

    > [!IMPORTANT]
    > Make sure that the subscriptions are purchased against the existing Azure AD tenant.

2. The customer activates the subscriptions.
3. In Microsoft 365 Admin center, the customer verifies that both the new subscriptions and the existing subscriptions are active.

### Deploy new environments

1. When the new subscriptions are active, additional add-on environments that you can configure appear in LCS. Deploy the add-on environments, and configure them as appropriate.
2. Apply the deployable packages, and restore the data.

### Delete environments under the obsolete agreement

Follow these steps for every environment that was deployed under the old agreement. After you've deleted the environments, don't use or redeploy them again.

1. In LCS, on the **Environment details** page, select **Full details**.
2. Stop the environment, and when the environment has stopped, select **Deallocate**.
3. When the deallocation is completed, select **Delete**.
4. When the environment has been deleted, select **Configure**.

### Update environments

1. The Volume Licensing reseller or the CSP suspends the existing subscriptions.
2. Any original add-on environments no longer appear in LCS.

> [!NOTE]
> Until physical redeployment of the add-on environments is completed, both existing subscriptions and new subscriptions must be kept in an active state.

> - The movement of files that are stored in Azure Blob storage isn't supported in sandbox environments.
> - Commerce customers should be aware that extra steps are required in order for components to work correctly after the move. For more information, see [Data management overview](../../dev-itpro/data-entities/data-entities-data-packages.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]