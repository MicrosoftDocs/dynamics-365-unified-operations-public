---
# required metadata

title: Remove an instance
description: This article describes the process of removing a test drive or production environment for Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Remove an instance

[!include [LCS freeze](includes/lcs-freeze-banner.md)]

> [!IMPORTANT]
> For more information about how to delete an environment, see [Delete an environment](../fin-ops-core/dev-itpro/deployment/deployenvironment-newinfrastructure.md#delete-an-environment).

This article explains how to remove a test drive or production environment for Microsoft Dynamics 365 Human Resources.

## Remove a test drive environment

Human Resources test drives are provisioned with a 60-day expiration policy. However, owners of test drive environments can end their trial early by completing the following steps.

1. Go to the [Power Apps Admin center](https://admin.businessplatform.microsoft.com/).
1. Select **Environments**.
1. Select the test drive environment, which has a naming pattern similar to this: TestDrive - alias@domain
1. Select **Delete** and confirm the decision.

The existing test drive environment is removed. When it's removed, you can sign up for a new test drive environment.

## Remove a production environment

This article assumes that you purchased Human Resources through a Cloud Solution Provider (CSP) or an enterprise architecture (EA) agreement.

Because a single Human Resources environment is contained in a single Power Apps environment, consider two options when you remove an environment:

- **Remove the entire Power Apps environment.** Choose this option when the Power Apps environment was created for the purpose of provisioning Human Resources, implementation has just begun, or you don't have any established integrations.  
- **Remove only Human Resources.** Choose this option when there's an established Power Apps environment that's populated with data used in Microsoft Power Apps and Power Automate.

> [!IMPORTANT]
> Before removing the Power Apps environment, ensure it's not used for data integrations outside the scope of Human Resources. You can't remove the default Power Apps environments.  

To remove the entire Power Apps environment, including Human Resources and the associated apps and flows:

1. Go to the [Power Apps Admin center](https://admin.businessplatform.microsoft.com/).
1. Select **Environments**.
1. Select the environment to remove.
1. Select **Delete** and confirm the decision.
1. Wait until the deletion is complete.
1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/Logon/Index) (LCS) by using the account that you used to subscribe to Human Resources.
1. Select the Human Resources project that contains the environment.
1. In your LCS project, select the **Human Resources App Management** tile.
1. Select the instance to remove.
1. Select **Remove instance** and confirm your decision.  

To remove a Human Resources environment from an existing Power Apps environment, complete the following steps. The need to involve support and contact the Human Resources DevOps team is temporary until this feature is enabled directly in LCS.

1. Contact Support to initiate a removal request.
1. The Support team initiates a removal request by using the Human Resources DevOps team.
1. Continue after you receive word that the environment is removed.
1. Sign in to LCS by using the account that you used to subscribe to Human Resources.
1. Select the Human Resources project that contains the environment.
1. In your LCS project, select the **Human Resources App Management** tile.
1. Select the instance you want to remove, which is marked with a Deployment status of **Deleted**.
1. Select **Remove instance** and confirm your decision.

## Recover a soft-deleted environment

If you delete the Power Apps environment that your Human Resources environment connects to, the status of the Human Resources environment in LCS changes to **Soft deleted**. In this case, users can't connect to Human Resources.

To restore the environment:

1. Follow the instructions in [Recover the Power Apps environment](/power-platform/admin/recover-environment).

1. Contact Support to restore the Human Resources environment. For more information, see [Get support](../fin-ops-core/dev-itpro/lifecycle-services/lcs-support.md).

> [!Warning]
> Power Apps environments are only saved for seven days after deletion. You must recover the environment within the seven-day period.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
