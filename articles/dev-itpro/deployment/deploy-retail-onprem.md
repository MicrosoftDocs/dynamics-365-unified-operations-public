---
# required metadata

title: Installation steps for Retail channel components in an on-premises environment
description: This topic covers the installation steps for Retail channel components in an on-premises environment. 
author: aamirallaqaband
manager: AnnBe
ms.date: 11/12/2018
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

# Installation steps for Retail channel components in an on-premises environment

[!include[banner](../includes/banner.md)]

This topic covers the installation steps for Retail channel components in an on-premises environment.

## Overview

Retail channel functionality, in an on-premises environment, is enabled exclusively via use of Retail Store Scale Unit. For an overview of Retail Store Scale Unit, see [Retail Store Scale Unit](../../retail/dev-itpro/retail-store-system-begin.md). 

Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of Retail channel components via Lifecycle Services (LCS). The only way to use Retail channel components is by installing Retail Store Scale Unit.

## Prerequisites 

Before you can start installation of Retail channel components, you must first complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 12 and later)](setup-deploy-on-premises-pu12.md).

You must also ensure that you use a secure network to connect Retail Store Scale Unit (RSSU) to Retail headquarters that is not publicly  accessible. You must also restrict network access to Retail headquarters only to known RSSU devices via network filtering or other means.

NEWNENWNEWNEWNENENWWNEENWNEWNWNENENEWNENEWNNEWENNWENEWNENWNENEW
NEWNENWNEWNEWNENENWWNEENWNEWNWNENENEWNENEWNNEWENNWENEWNENWNENEW
NEWNENWNEWNEWNENENWWNEENWNEWNWNENENEWNENEWNNEWENNWENEWNENWNENEW

## Installation steps

1.	On the previously created [file share](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu8-pu11#setupfile), create a new folder called **RetailSelfServicePackages**.
2.	On each AOS computer, run the following PowerShell script:

```powershell
.\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database -DatabaseName 'Database name for AOS database ' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages>’ -SendProductSupportTelemetryToMicrosoft <True/False>
```
  
3.	Download the binary update from LCS. For instructions, see [Get updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
4.	Extract the zip file and copy ModenPOSSetup.exe and StoreSystemSetup.exe found in the RetailSelfServicePackages folder that was created in the file share location above.
5.	Follow the installation steps for installing the Retail Store Scale Unit. For instructions, see [Configure and install Retail Store Scale Unit](../../retail/dev-itpro/retail-store-scale-unit-configuration-installation.md).

