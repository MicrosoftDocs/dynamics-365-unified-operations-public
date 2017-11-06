---
# required metadata

title: Subscription estimator
description: This topic explains how to use the Subscription estimator tool that is available in Lifecycle Services (LCS) for Microsoft Dynamics 365 Finance and Operations, Enterprise edition.
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

Subscription estimator is a tool that is available in Microsoft Dynamics Lifecycle Services (LCS). Microsoft uses this tool to estimate the initial size of the production environment that must be provisioned for a customer. Before customers can request deployment of a production environment, they must estimate their peak workloads in terms of transaction counts and then upload that information to LCS. By using the details of user licenses and transaction counts to infer subscription requirements, the Subscription estimator tool helps guarantee that the provisioned environment meets the customer's business requirements.

Follow these steps to use the Subscription estimator tool.

1. In LCS, open the project that is associated with the implementation project for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
2. At the top of the page, select the hamburger icon, and then select **Subscription estimator**.
3. Download the sample usage profile.
4. Answer the mandatory questions on each tab. If you're a Retail customer, be sure to answer the questions on the **Retail and Commerce** tab.
5. Save the usage profile locally.
6. To upload the usage profile, select **New estimate**, name the estimate, and then upload the usage profile.
7. After the upload is completed, select **Mark as Active** to activate an estimate. An active estimate is required in order to configure a production deployment.

When there is a valid active estimate, the **Configure** button becomes available. You can use this button to request a production environment deployment.

> [!NOTE]
> Although you can have multiple estimates, one estimate must be marked as **Active**. After the production environment has been deployed, or deployment of the environment has received sign-off, the active estimate is locked. To mark a different estimate as the active estimate, create a support request by using the Support portal in LCS.

## Frequently asked questions

**Question:** Why isn't the **Configure** button for deploying a production environment available, even though there is an active estimate? And why does a warning message appear in the Action center on the project dashboard?

**Answer:** The **Configure** button becomes unavailable, and you receive a warning message, when the total number of users across all implementation projects for the organization, as entered in the Microsoft Excel template, exceeds the total number of licenses that you purchased.

For customers that are on the pre-Microsoft Dynamics 365 license plan, there are three license types:

- Plan 2
- Self-serve
- Task users

For Microsoft Dynamics 365 customers, there are three license types:

- Enterprise
- Team Member
- Activity Plan

You must purchase at least 20 licenses (of the Enterprise type or an equivalent). For more information, contact your local Microsoft Dynamics 365 representative, or see the [Microsoft Dynamics 365 licensing guide](http://download.microsoft.com/documents/en-us/dynamics/pricing/Dynamics_365_Enterprise_edition_Licensing_Guide.pdf).

**Question:** Why does an error occur when I mark an estimate as **Active**?

**Answer:** When you mark an estimate as **Active**, you might receive one of the following error messages:

- **Estimate cannot be marked as active** – This error occurs because the number of primary users that you provided in the usage profile exceeds the number of licenses that you purchased. To resolve this error, select **Purchase history** to verify whether the counts that you provided in the usage profile exceed the number of licenses that you purchased. If those counts exceed the number of purchased licenses, edit the profile, and then try to mark the estimate as **Active** again.
- **Estimate created but does not meet requirements** – This error occurs if transaction lines that are entered aren't within the limits of the Subscription estimation tool. To resolve this error, create a support request, and attach the usage profile. Your instance can then be manually sized.

If you receive any other error message or encounter any other issue, create a support request, and attach your active estimate so that the support team can address the issue.
