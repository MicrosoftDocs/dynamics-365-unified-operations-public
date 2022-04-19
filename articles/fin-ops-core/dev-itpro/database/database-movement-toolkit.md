---
# required metadata

title: Database movement toolkit
description: This topic explains how to download and use the Database movement toolkit. 
author: laneswenka
ms.date: 12/02/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 30
---

# Database movement toolkit

The Database movement toolkit is a ZIP file hosted in Microsoft Dynamics Lifecycle Services (LCS). This toolkit is available for download. It contains a series of scripts that enhance the customer experience for movement of data between developer environments and sandbox environments. This topic explains the components of the toolkit, how to download it, and any recent changes.

## Download the latest version

The toolkit is available in the LCS Shared Asset Library under the **Models** section.  Search for the entry titled **Database Movement Toolkit** and then download it to your Tier1 DevTest environment.  

## Toolkit components

The toolkit contains the following primary components:

- **Sqlpackage.exe** - This tool is used to perform extract and publish actions against Microsoft Azure SQL databases, as well as SQL Server databases hosted on Tier1 DevTest environments.  
- **PowerShell 7.0** - This is a self-contained version of PowerShell that includes capabilities for parallelism, which increases the performance of transferring data between environments.  
- **PowerShell script** - There are several scripts included to provide an enhanced and more automated experience for scenarios such as AX 2012 data upgrade.

## Supported scenarios

The toolkit currently supports the following scenarios. More will be added over time.  

* [Upgrade from AX 2012 - Data upgrade in sandbox environments](/d365F-O/fin-ops-core/dev-itpro/database/data-upgrade-self-service)

## Versions

### Version 5
| Feature | Details |
| :------ | :------ |
| Schema publish | Added CleanupSource and CleanupTarget scripts.|
| Data transfer | Added timer to capture transfer time.|

### Version 4
| Feature | Details |
| :------ | :------ |
| Schema publish | Minor improvements.|

### Version 3
| Feature | Details |
| :------ | :------ |
| Schema publish | Fixed the scripts to output errors in PublishDiag.log.|

### Version 2
| Feature | Details |
| :------ | :------ |
| Schema publish | Fixed the scripts to use current directory reference to Sqlpackage directory.|
| Schema publish | Fixed the scripts to delete local users from the source database, and tidy up environment-specific tables.|
| Data transfer | Fixed the scripts to install missing PowerShell modules.|

### Version 1
| Feature | Details |
| :------ | :------ |
| Initial | Toolkit uploaded to LCS Shared Asset Library.|




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]