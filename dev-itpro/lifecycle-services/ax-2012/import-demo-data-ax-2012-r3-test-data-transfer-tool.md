---
# required metadata

title: Import demo data for AX 2012 R3 by using the Test Data Transfer Tool
description: In this walkthrough, you will use the Test Data Transfer Tool (beta) to import the demo data for Microsoft Dynamics AX 2012 R3.
author: kfend
manager: AnnBe
ms.date: 2015-12-02 17 - 01 - 09
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
ms.custom: 13401
ms.assetid: c16c9fb5-b1c1-4f22-a955-ff7325621a22
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Import demo data for AX 2012 R3 by using the Test Data Transfer Tool

In this walkthrough, you will use the Test Data Transfer Tool (beta) to import the demo data for Microsoft Dynamics AX 2012 R3.

We strongly recommend that you work locally on the database server where the business database for AX 2012 R3 is stored. This is both faster, and avoids any network communication issues during import.

## Prerequisites
**Caution:** The Test Data Transfer Tool (beta) is only supported for use in a development, test, or demo environment. Do not perform this procedure in a production environment.

## Download the demo data and Test Data Transfer Tool (beta)
1.  Download the AX 2012 R3 demo data from the Release Page on [PartnerSource](http://go.microsoft.com/fwlink/?LinkId=403073).
2.  Extract the demo data from the package to the database server that hosts the AX 2012 R3 business database for your environment.
3.  Download the Test Data Transfer Tool (beta) tool installer from the Downloadable tools section of [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com), and install it on the database server that hosts the AX 2012 R3 business database for your environment.
4.  Verify that you have appropriate permissions to import data. You must have read access to the location where the demo data is stored, and in SQL Server Management Studio, permission to execute **SELECT** statements and **BULK INSERT** statements. For more information, see [Install the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](install-test-data-transfer-tool-beta.md).

## Run the Test Data Transfer Tool (beta)
1.  Go to **Control Panel** &gt; **Services**, and stop the AOS instance associated with your environment.
2.  Using Windows Explorer, browse to the **Test Data Transfer Tool (beta)**.
3.  On the **File** menu in Windows Explorer, click **Open command prompt as administrator**.
4.  At the command prompt, enter the following command to import the demo data:**dp.exe import** location\_of\_demo\_data Name\_of\_AX\_business\_database ServernameInstanceNameWe assume that you are running the Test Data Transfer Tool (beta) on the local computer. If you have a named instance on the local computer, you can use the syntax localhostInstanceName or **.** InstanceName.In the following example, the data is on the E drive, in the demodata folder, and the business database is named MicrosoftDynamicsAX:**dp.exe import e:demodata MicrosoftDynamicsAX** **Note:** It may take over 30 minutes to import the demo data.If you encounter any issues during the import, you can open the log file **DPLog.xml**, which will be created in the folder where you ran the Test Data Transfer Tool (beta).
5.  Go to **Control Panel** &gt; **Services**, and restart the AOS instance associated with your environment.


See also
--------

[Test Data Transfer Tool (beta) for Microsoft Dynamics AX 2012](test-data-transfer-tool-beta-2012.md)

[Install the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](install-test-data-transfer-tool-beta.md)

[Run the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](run-test-data-transfer-tool-beta.md)

