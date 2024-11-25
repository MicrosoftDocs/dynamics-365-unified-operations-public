---
# required metadata

title: Remove an instance
description: This article describes the process of removing a test drive or production environment for Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/11/2021
ms.topic: article
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


> [!IMPORTANT]
> For more information about how to delete an environment, see [Delete an environment](../fin-ops-core/dev-itpro/deployment/deployenvironment-newinfrastructure.md#delete-an-environment).

This article explains the process of removing a test drive or production environment for Microsoft Dynamics 365 Human Resources.

## Remove a test drive environment

Human Resources test drives are provisioned with a 60-day expiration policy. However, owners of test drive environments have the option to end their trial early by completing the following steps. 

1. Navigate to the [Power Apps Admin center](https://admin.businessplatform.microsoft.com/).
2. Select **Environments**.
3. Select the test drive environment, which has a naming pattern similar to this: TestDrive - alias@domain
4. Select **Delete** and confirm the decision. 

The existing test drive environment will be removed. When it is removed, you can sign up for a new test drive environment. 

## Remove a production environment

This article assumes that you've purchased Human Resources through a Cloud Solution Provider (CSP) or an enterprise architecture (EA) agreement. 

Because a single Human Resources environment is contained in a single Power Apps environment, there are two options to consider when you remove an environment: 
- **Remove the entire Power Apps environment.** This option is preferred when the Power Apps environment was created for the purpose of provisioning Human Resources, implementation has just begun, or you don't have any established integrations.  
- **Remove only Human Resources.** This option is appropriate when there is an established Power Apps environment that is populated with data that is used in Microsoft Power Apps and Power Automate.


> [!Important]
> Before removing the Power Apps environment, ensure it's not being used for data integrations outside the scope of Human Resources. Note that the default Power Apps environments can't be removed. 

To remove the entire Power Apps environment, including Human Resources and the associated apps and flows:

1. Navigate to the [Power Apps Admin center](https://admin.businessplatform.microsoft.com/).
2. Select **Environments**.
3. Select the environment to be removed.
4. Select **Delete** and confirm the decision. 
5. Wait until the deletion is complete.
6. Sign in to [Lifecycle Services](https://lcs.dynamics.com/Logon/Index) (LCS) using the account that you used to subscribe to Human Resources. 
7. Select the Human Resources Project that contains the environment. 
8. In your LCS project, select the **Human Resources App Management** tile. 
9. Select the instance to remove. 
10. Select **Remove instance** and confirm your decision.  

To remove a Human Resources environment from an existing Power Apps environment, complete the following steps. Note that the need to involve support and contact the Human Resources DevOps team is temporary until this feature is enabled directly in LCS.

1. Contact Support to initiate a removal request.
2. The Support team will initiate a removal request with the Human Resources DevOps team. 
3. Continue after you receive word that the environment has been removed.
4. Sign in to LCS using the account that you used to subscribe to Human Resources. 
5. Select the Human Resources project that contains the environment. 
6. In your LCS project, select the **Human Resources App Management** tile. 
7. Select the instance you would like to remove, which should be marked with a Deployment status of **Deleted**.
8. Select **Remove instance** and confirm your decision. 

## Recover a soft-deleted environment

If you delete the Power Apps environment that your Human Resources environment is connected to, the status of the Human Resources environment in LCS will be **Soft deleted**. In this case, users can't connect to Human Resources.

To restore the environment:

1. Follow the instructions in [Recover the Power Apps environment](/power-platform/admin/recover-environment).

2. Contact Support to restore the Human Resources environment. For more information, see [Get support](../fin-ops-core/dev-itpro/lifecycle-services/lcs-support.md).

> [!Warning]
> Power Apps environments are only saved for seven days after deletion. You must recover the environment within the seven-day period.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
