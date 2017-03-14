---
# required metadata

title: Install the Test Data Transfer Tool (beta) for Dynamics AX (AX 2012)
description: This topic describes how to install the Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta). Only advanced users should use this tool. 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 19 - 13 - 07
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17551
ms.assetid: 1681290d-93f0-489d-9746-7793b2ffe690
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Install the Test Data Transfer Tool (beta) for Dynamics AX (AX 2012)

This topic describes how to install the Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta). Only advanced users should use this tool. 

You must be a database administrator or a developer who has experience using Microsoft SQL Server. You must also have permission to read from or write directly to the Microsoft Dynamics AX 2012 database that you are working with, and to execute applications directly on the computer that is hosting the database. Before you begin, your environment must include the following components:

-   An Microsoft Dynamics AX 2012 database that has been configured for your business.
-   The SQL Server client tools installed on the local computer, and on the database server that you are transferring data to, so that the SQL Server bulk copy tool (bcp) is in the command-prompt path.

During export, the tool creates three files for each table. Make sure that there is enough hard disk space for all the tables that are exported.

## Install the Test Data Transfer Tool (beta)
1.  Get the tool from the Downloadable tools section of [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?LinkId=228148), and extract it to a local folder.
2.  Right-click **AX2012TestDataTransferTool.msi**, and then click **Run as administrator**.
3.  In the **Setup** **Wizard**, accept the license terms, and then select the location in which to install the binaries and files for the tool. By default, the tool is installed to %Program Files%/Microsoft Dynamics AX 2012 Test Data Transfer Tool (Beta).

 

See also
--------

[Test Data Transfer Tool (beta) for Microsoft Dynamics AX 2012](test-data-transfer-tool-beta-2012.md)

[Run the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=371)

