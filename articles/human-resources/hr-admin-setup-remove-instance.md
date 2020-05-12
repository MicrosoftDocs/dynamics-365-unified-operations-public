---
# required metadata

title: Remove an instance
description: This article walks you through the process of removing a test drive or production environment for Microsoft Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Remove an instance

This article walks you through the process of removing a test drive or production environment for Microsoft Dynamics 365 Human Resources.

## Remove a test drive environment

Human Resources test drives are provisioned with a 60-day expiration policy. However, owners of test drive environments have the option to end their trial early by completing the following steps. 

1. Navigate to the [Power Apps Admin center](https://admin.businessplatform.microsoft.com/).
2. Select **Environments**.
3. Select the test drive environment, which has a naming pattern similar to this: TestDrive - alias@domain
4. Select **Delete** and confirm the decision. 

The existing test drive environment will be removed. When it is removed, you can sign up for a new test drive environment. 

## Remove a production environment

This article assumes that you've purchased Human Resources through a Cloud Solution Provider (CSP) or an enterprise architecture (EA) agreement. 

Since a single Human Resources environment is contained within a single Power Apps environment, there are two options to consider. The first option involves removing the entire Power Apps environment; the second option involves removing only Human Resources. The first option is preferred when you have created a Power Apps environment expressly for the purpose of provisioning Human Resources, and you've just begun implementation, or you don’t have any established integrations. The second option is appropriate when you have an established Power Apps environment populated with rich data that's leveraged in Power Apps and Power Automate.

> [!Important]
> Before removing the Power Apps environment, ensure it is not being used for rich data integrations outside the scope of Human Resources. Also note that the default Power Apps environments cannot be removed. 

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
4.  Sign in to LCS using the account that you used to subscribe to Human Resources. 
5. Select the Human Resources project that contains the environment. 
6. In your LCS project, select the **Human Resources App Management** tile. 
7. Select the instance you would like to remove, which should be marked with a Deployment status of **Failed**.
8. Select **Remove instance** and confirm your decision. 
