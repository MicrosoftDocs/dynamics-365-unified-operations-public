---
# required metadata

title: End of mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3
description: This article provides details about the end of  mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3.
author: sericks007
ms.date: 06/13/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: sericks
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# End of mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3

[!include[banner](../includes/banner.md)]

Mainstream support for Dynamics AX 2009 Service Pack 1 (SP1), Dynamics AX 2012, and Dynamics AX 2012 R2 ended on October 9, 2018. Security hotfixes were provided for those three versions through the extended support period, which ended on April 12, 2022. For more information, see [Microsoft Lifecycle Policy](/lifecycle/products/?terms=Dynamics%20AX).

Mainstream support for Dynamics AX 2012 R3 ended on October 12, 2021.  Only security hotfixes will continue to be provided through the extended support period that continues until January 10, 2023.  For more information, see [Microsoft Lifecycle Policy](/lifecycle/products/?terms=Dynamics%20AX).

Customers are advised to upgrade to the latest version of finance and operations apps, such as Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations:

- Dynamics AX 2009 Service Pack 1 customers should use the [migration tool](../../dev-itpro/migration-upgrade/upgrade-home-page.md) that is available.
- Dynamics AX 2012 and Dynamics AX 2012 R2 customers should upgrade to finance and operations apps through Dynamics AX 2012 R3 using the upgrade tool that is available. For additional upgrade information, see [Upgrade from AX 2012 to finance and operations apps](../../dev-itpro/migration-upgrade/upgrade-overview-2012.md).

## Frequently asked questions

### When does the mainstream support for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2 end?

Mainstream support ended on October 9, 2018.

### When does the mainstream support for Dynamics AX 2012 R3 end?

Mainstream support ended on October 12, 2021.

### Was the information of the end date of the mainstream support for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, Dynamics AX 2012 R2 and Dynamics AX 2012 R3 available before?

Yes, it was always publicly available on the Microsoft Support Lifecycle site at [support.microsoft.com](https://support.microsoft.com/lifecycle/search?alpha=Dynamics%20AX).

### Can customers on Premier Extended Hotfix Support or on Unified Support Advanced and Performance Levels get a non-security hotfix or regulatory update?

No. Neither non-security hotfixes nor regulatory updates will be available for the Dynamics AX products during the Extended Support phase of the product lifecycle (Dynamics AX 2009 SP1, Dynamics AX 2012, Dynamics AX 2012 R2, or Dynamics AX 2012 R3).

While the ability to request a non-security hotfix for select products is included with Unified Support Advanced and Performance Levels, Microsoft has determined that non-security hotfixes cannot be provided with a *commercially reasonable* effort for these products. As a result, no requests for non-security hotfixes or regulatory updates will be accepted. 

### I knew about the regulatory change before October 9, 2018, but it has the law enforcement date after October 9, 2018. Will I still get a regulatory update for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2?

No, we will only provide regulatory updates for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2 for regulatory changes with the law enforcement dates on or earlier than October 9, 2018.

### A customer or partner can already download a fix through LCS and inspect the code by installing it into a test Dynamics AX 2012 R3 environment. Is there any difference with the approach that you have proposed?

No, there is no difference.

### How are binary hotfixes handled for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3?

If a hotfix is needed for a part of the system where Microsoft does not provide the source code and it is not a security bug, the hotfix will not be provided.

### Can I access information about upcoming legislation changes in supported countries/regions?

Yes, all legislation changes regardless of source (such as vendors, Microsoft research, or the localization community) are stored in the Lifecycle Service (LCS) alerting project. To access the LCS alerting project, follow these steps:
1. **Sign up**: Send an email request to join the localization community (under NDA) at DynRegW@microsoft.com.
2. **Access**: Sign in to the LCS project **Regulatory Alerts - Worldwide** (available only for companies with NDA or individuals who signed up for the Insider Program).
3. **Alerting guide**: Inform Microsoft about country/region regulation alerts and track the status of regulatory features. For more information, see [Submit alerts about country/region-specific regulatory features](../../dev-itpro/lcs-solutions/submit-localization-alerts.md).

Note that the LCS alerting project includes all identified/reported legislation changes (alerts) but not actual Microsoft plans.

### Can I get visibility into Microsoft plans for releases of new regulatory features?

Yes, in LCS Issue Search, information is published regarding upcoming regulatory updates for Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations.  

#### Are details about released regulatory features available?

Yes, for larger features, we publish this information in [Globalization resources](../../dev-itpro/lcs-solutions/country-region.md).

### Can I view and try actual regulatory features in Dynamics 365 prior to a release?
Yes, you can do this if you have purchased cloud licenses for Dynamics 365. All service updates are made available for preview through the Shared Asset Library in Lifecycle Services. For regulatory changes specified by authorities early, the features will be available in Preview prior to the law-enforced date (or latest date for first filing).

### Can I access the code and configurations for regulatory features prior to a release?
Yes, beginning with 10.0.26, preview packages for every service update are made available to all customers through the Shared Asset Library in LCS, under **Software deployable package**. 

Configurations are available in the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../dev-itpro/analytics/er-download-configurations-global-repo.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

