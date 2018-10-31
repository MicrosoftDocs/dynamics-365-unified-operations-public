---
# required metadata

title: Installation steps for Retail channel components in an on-premises envionrment
description: This article will cover installation steps for Retail channel components in an on-prem envionrment. 
author: aamirallaqaband
manager: AnnBe
ms.date: 10/31/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [retail
ms.author: aamiral
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# Installation steps for Retail channel components in an on-premises envionrment

[!include[banner](../includes/banner.md)]


This article will cover installation steps for Retail channel components in an on-prem environment.

Overview

Retail channel functionality, in an on prem environment, is enabled exclusively via use of Retail Store Scale Unit. Here is an overview of Retail Store Scale Unit (https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin). 

Unlike in a cloud deployment, an on-prem environment does not enable seamless high availability deployment of Retail channel components via LCS. The only way to use Retail channel components is via installation of Retail Store Scale Unit.

Pre-requisites 

Before you can start installation of Retail channel components, you must first complete all prior installation steps for an on-prem environment as listed here (https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-environments).

Installation steps

1.	On the previously created file share, create a new folder called RetailSelfServicePackages
2.	On each AOS computer, run the following PowerShell script

.\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database -DatabaseName 'Database name for AOS database ' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages>’ -SendProductSupportTelemetryToMicrosoft <True/False>

3.	Download binary update from LCS. For instructions, see [Download updates](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/download-hotfix-lcs).
4.	Extract zip file and copy ModenPOSSetup.exe and StoreSystemSetup.exe under the RetailSelfServicePackages folder created in the file share location above.
5.	Follow installation steps for installing Retail Store Scale Unit. For instructions, see [Configure and install Retail Store Scale Unit](../../retail/dev-itpro/retail-store-scale-unit-configuration-installation)

