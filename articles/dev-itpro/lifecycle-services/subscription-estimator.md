---
# required metadata

title: Subscription estimator
description: This topic provides information about how to use the subscription estimator tool in Lifecycle Services for Microsoft Dynamics 365 Finance and Operations, Enterprise edition.
author: manalidongre
manager: AnnBe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform update 12

---
# Subscription estimator

[!include[banner](../includes/banner.md)]


Subscription estimator is a tool in Lifecycle Services that is used by Microsoft to estimate the initial size of the production environment that needs to be provisioned for a customer. Before a customer can request deployment of a Production environment, they must estimate their peak workloads in terms of transaction count and upload that information to Lifecycle Services. Using user license details and transaction count to infer the subscription needs, the Subscription estimator tool ensures that the provisioned environment meets the customer's business needs.  

Complete the following steps to use the Subscription estimator tool.
1. In Lifecycle Services, navigate to the project associated with the Implementation project for Dynamics 365 for Finance and Operations, Enterprise edition.  
2. At the top of the page, click the hamburger icon and then select **Subscription estimator**.
3. Download the **Sample Usage Profile**.  
4. Answer the mandatory questions on each tab. If you are a Retail customer, make sure to answer the questions in the **Retail and Commerce** tab.  
5. Save the Usage profile locally.  
6. To upload the Usage profile, click **New estimate**, name the estimate, and then upload the Usage profile.  
7. After the upload is complete, select **Mark as Active** to activate an estimate. An active estimate is required to configure a production deployment. 

After there is a valid active estimate, the **Configure** button will be enabled. You cna use this button to request a production environment deployment.  

Note that while you can have multiple estimates, one estimate must be marked as **Active**. After the production environment is deployed or has been signed off for deployment, the active estimate is locked. To mark another estimate as active, file a support request using Support portal in Lifecycle Services.  

## Frequently asked questions (FAQs) 

**Question:** Why is the **Configure** button for deploying a production environment not enabled even though there is an active estimate and why is there a warning message in the Action center on the project dashboard?  

**Answer:** The **Configure** button is no longer enabled and the warning occurs when the total number of users, across all implementation projects for the organization, entered in the Microsoft Excel template exceed the total purchased license counts. 
For customers that are on the pre-Dynamics 365 license plan there are 3 license types:
  - Plan 2
  - Self-serve
  - Task users
  
  For Dynamics 365 customers the license types are: 
  - Enterprise
  - Team Member
  - Activity Plan  

You must purchase at least 20 licenses (Enterprise or equivalent). For more information, contact your local Microsoft Dynamics 365 representative or see the [Microsoft Dynamics 365 licensing guide](http://download.microsoft.com/documents/en-us/dynamics/pricing/Dynamics_365_Enterprise_edition_Licensing_Guide.pdf). 

**Question:** Why does an error occur when I mark an estimate as **Active**?

**Answer:** When you mark an estimate as **Active**, you might receive one of the following errors:
  - **Estimate cannot be marked as active**: This error occurs because the number of Primary users that you provided in the Usage profile exceeds the amount that you purchased. To resolve the error, click **Purchase history** to check whether the counts you provided in the Usage profile exceed the number of purchased licenses. If they do, edit the profile and try again. 
  -  **Estimate created but does not meet requirements**: This error occurs if transaction lines are entered that are not within the estimation tool limits. To resolve this error, create a support request and attach the usage profile. This will allow for your instance to be manually sized. 
  
If you receive any other errors or run into additional issues, log a support request and attach your active estimate so that the support team can address the issue.



