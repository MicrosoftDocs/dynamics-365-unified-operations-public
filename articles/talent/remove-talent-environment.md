---
# required metadata

title: Remove Talent environments
description: This topic walks you through the process of removing a test drive or production environment for Microsoft Dynamics 365 Talent. 
author: andreabichsel
manager: AnnBe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2017-11-20
ms.dyn365.ops.version: Talent July 2017 update

---
# Remove Talent environments

[!include [banner](includes/banner.md)]

This topic walks you through the process of removing a test drive or production environment for Microsoft Dynamics 365 Talent.

## Removing a test drive environment

Talent test drives are provisioned with a 60-day expiration policy. However, owners of test drive environments have the option to end their trial early by completing the following steps. 

1. Navigate to the [PowerApps Admin center](https://admin.businessplatform.microsoft.com/).
2. Select **Environments**.
3. Select the test drive environment, which has a naming pattern similar to this: TestDrive - alias@domain
4. Select **Delete** and confirm the decision. 

The existing test drive environment will be removed. When it is removed, you can sign up for a new test drive environment. 

## Removing a production environment

This topic assumes that you've purchased Talent through a Cloud Solution Provider (CSP) or an enterprise architecture (EA) agreement. 

Since a single Talent environment is “contained” within a single PowerApps environment, there are two options to consider. The first option involves removing the entire PowerApps environment; the second option involves removing only Talent. The first option is preferred when you have created a PowerApps environment expressly for the purpose of provisioning Talent, and you've just begun implementation, or you don’t have any established integrations. The second option is appropriate when you have an established PowerApps environment populated with rich data that's leveraged in PowerApps and Flows.

> [!Important]
> Before removing the PowerApps environment, ensure it is not being used for rich data integrations outside the scope of Talent. Also note that the default PowerApps environments cannot be removed. 

To remove the entire PowerApps environment, including Talent and the associated Apps and Flows:

1. Navigate to the [PowerApps Admin center](https://admin.businessplatform.microsoft.com/).
2. Select **Environments**.
3. Select the environment to be removed.
4. Select **Delete** and confirm the decision. 
5. Wait until the deletion is complete.
6. Sign in to [Lifecycle Services](https://lcs.dynamics.com/Logon/Index) (LCS) using the account that you used to subscribe to Talent. 
7. Select the Talent Project that contains the environment. 
8. In your LCS project, select the **Talent App Management** tile. 
9. Select the instance to remove. 
10. Select **Remove instance** and confirm your decision.  

To remove a Talent environment from an existing PowerApps environment, complete the following steps. Note that the need to involve support and contact the Talent DevOps team is temporary until this feature is enabled directly in LCS.

1. Contact Support to initiate a removal request.
2. The Support team will initiate a removal request with the Talent DevOps team. 
3. Continue after you receive word that the environment has been removed.
4.  Sign in to LCS using the account that you used to subscribe to Talent. 
5. Select the Talent project that contains the environment. 
6. In your LCS project, select the **Talent App Management** tile. 
7. Select the instance you would like to remove, which should be marked with a Deployment status of **Failed**.
8. Select **Remove instance** and confirm your decision. 

