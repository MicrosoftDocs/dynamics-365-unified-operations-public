---
# required metadata

title: Subscriptions, LCS projects, and Azure Active Directory tenants
description: 
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 05/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Subscriptions, LCS projects, and Azure Active Directory tenants
[!include [banner](../includes/banner.md)]

When a customer subscribes to Microsoft Dynamics 365 for Finance and Operations through a Volume Licensing (VL) or Cloud Service Provider (CSP) agreement, they usually have one Azure Active Directory (AAD) tenant, one LCS implementation project with any number of sandbox environments deployed to one data center of the customer’s choice, and one production instance of Microsoft Dynamics 365 for Finance and Operations. For more information about these core concepts, see Architecture Overview for a description of the core concepts. While this setup works well for most projects, sometimes more advanced scenarios are required and/or changes during the implementation lifecycle must be accommodated.  This article addresses frequent questions projects have around subscriptions and licenses, Azure Active Directory tenants, and Lifecycle Services (LCS) implementation projects. 

- [Move environments between data centers](move-environments-data-center.md)
- [Move licenses between agreement types](move-licenses-between-agreement-types.md)
- [Move an LCS Implementation project to another Azure Active Directory tenant](move-lcs-implementation-project-tenant.md)
- Implement multiple LCS projects and production environments on the same Azure Active Directory tenant 

## Frequently asked questions
**Question:** Do I need to move AAD tenants when moving from CSP to VL?

**Answer:** No. You can keep the existing AAD tenant, but you must make sure the VL subscriptions are purchased against the same Azure Active Directory tenant as the CSP subscriptions.

**Question:** Do I get a new LCS Implementation Project when moving from CSP to VL?

**Answer:** No. The LCS project remains the same.

**Question:** Can I keep the existing LCS Implementation Project when moving to different AAD tenant?

**Answer:** No. A new LCS project will be created. 

**Question:** How long will it take to move from CSP to VL?

**Answer:** The VL purchase process can take a few days until the order is processed and the subscriptions are activated. Redeploying the add-on environments has an SLA of 2 business days. Deallocating and deleting the old add-on environments takes a few hours.

**Question:** What if I forget to delete the existing environments before suspending the existing subscription?

**Answer:** If you do not deallocate and delete the existing environments before you suspend the subscriptions, the environments will remain in ‘Deployed’ state, but users will get an error message when they try to access ‘Full details’ on those environments 

**Question:** Can I have a CSP and an VL agreements in parallel?

**Answer:** Yes, you can. You must maintain the minimum required number of licenses under each program.  

