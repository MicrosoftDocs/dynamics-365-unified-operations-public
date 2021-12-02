---
# required metadata

title: Finance and Operations apps in France
description: This topic provides information about the availability of Finance and Operations apps in France's data centers.
author: kfend
ms.date: 10/25/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: France
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2019-07-18
ms.dyn365.ops.version:  

---

# Finance and Operations apps in France

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance, Dynamics 365 Commerce, and Dynamics 365 Supply Chain Management are generally available in the France geography. These deployment options serve customers in regulated industry and commercial organizations that do business with entities in France that require local data residency.

The deployment of the Dynamics 365 services in France is built on the foundational principles of security, privacy, compliance, transparency, and reliability. This deployment gives customers in France a complete cloud infrastructure and platform that provides familiar productivity and business application tools. Therefore, customer data stays resident in France.

## Provisioning

The first prerequisite for deployment to France is to use the localized version of Microsoft Dynamics Lifecycle Services (LCS) that is referred to as [Go Local LCS, FR.LCS.Dynamics.com](https://fr.lcs.dynamics.com/Logon/Index). If you're interested in local deployment to a specific region, contact Microsoft to learn more about the onboarding process and the process for adding customers and partners.

## Features that aren't available

Microsoft strives to maintain functional parity between our commercially available service and Finance, Commerce, and Supply Chain Management in France. However, there are notable exceptions that are affected by dependent service or partner solution availability, market priorities, or compliance regulations. For more information about these exceptions, or for questions about services in France, contact [Microsoft Dynamics 365 Support](https://dynamics.microsoft.com/support/).

- Dynamics Regulatory Alert Submission service isn't available in France because it operates as a single global service. However, you can access the service from [Global LCS](https://lcs.dynamics.com/Logon/Index).
- No corporate libraries are available in the American Productivity & Quality Center (APQC) Business process modeler (BPM) library. For each Go Local region, LCS published only the Getting started library and the last published APQC library. You can copy libraries to your project library to edit and publish them as the corporate library.
- The Dynamics 365 Translation Service overview isn't available in Go Local LCS. However, you can access the service from Global LCS.
- Electronic reporting (ER) assets aren't visible in the Shared asset library. You can manually upload the assets from the LCS Global asset library. To work around this issue, you can run a script that Microsoft Engineering provides. Alternatively, you can access Microsoft Support ER assets by connecting to the Global repository. For more information, see [Regulatory Configuration Service (RCS) - Lifecycle Services (LCS) storage deprecation](../../../finance/localizations/rcs-lcs-repo-dep-faq.md).
- The embedded Power BI dashboard isn't available.
- Environment monitoring of LCS doesn't expose the same dashboard interface as Global LCS. However, the core key performance indicators (KPIs) are available.
- The production environment update cadence for automatic updates is missing in the user interface (UI).
- For an Azure build pipeline that uses hosted agents: The nuggets package from the LCS library isn't available in the Shared asset library.
- Environments are fully managed by Microsoft and don't support all customer self-service. Customers might have to create service requests for the Engineering team in LCS.
- Cloud scale unit for commerce, warehouse, and manufacturing isn't available.
- Planning optimization service isn't available.
- Local business data deployment isn't available.

## Additional resources

For information and links to resources that can help you set up legal entities that have a primary address in France, see [France](../../../finance/localizations/france.md).

For information about product availability per country and workload, see [Dynamics 365 and Power Platform availability](https://dynamics.microsoft.com/availability-reports/).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
