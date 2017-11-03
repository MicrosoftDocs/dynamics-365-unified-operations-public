---
# required metadata

title: Subscription estimator
description: This topic provides information about how to use the subscription estimator tool in Lifecycle Services for Microsoft Dynamics 365 Finance and Operations, Enterprise edition.
author: manalidongre
manager: AnnBe
ms.date: 11/03/2017
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
4. Answer the mandatory questions on each tab. If you are a Retail customer, answer the questions in the **Retail and Commerce** tab.  
5. Save the Usage profile locally.  
6. To upload the Usage profile, click **New estimate**, name the estimate and then upload the Usage profile.  
7. After uploading an estimate, select Mark as Active to activate an estimate. Having an active estimate is pre-requisite for being able to configure a production deployment. 


After there is a valid active estimate, Configure button will be enabled to allow the customer to request a production environment deployment.  

Please note that while you can have multiple estimates, you need to mark one estimate as 'Active'. The active estimate is locked once the production environment is deployed or has been signed off for deployment. To mark another estimate as active, file a support request using Support portal in Lifecycle Services.  

## Frequently asked questions (FAQs) 

Configure button for deploying a production environment is disabled even though there is an active estimate and Action center in the project dashboard shows a warning message.  

The above issue is seen when the total number of users entered in Excel template (across all implementation projects for the organization) exceed the total purchased license counts. 


For customers that are on the pre-Dynamics 365 license plan there are 3 license types  - Plan 2, Self-serve and Task users. For Dynamics 365 customers the license types are Enterprise, Team Member and Activity Plan.  



You must purchase at least 20 licenses (Enterprise and/or equivalent). For more information, please contact your local Microsoft Dynamics 365 representative or see the Microsoft Dynamics 365 licensing guide. 





