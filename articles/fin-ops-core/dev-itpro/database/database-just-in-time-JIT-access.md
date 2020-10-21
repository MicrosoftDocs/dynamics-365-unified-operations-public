---
# required metadata

title: Enable just-in-time database access
description: This topic provides the steps necessary to enable database access in a just-in-time (JIT) fashion.
author: laneswenka
manager: AnnBe
ms.date: 10/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 20
---

# Enable just-in-time database access

[!include [banner](../includes/banner.md)]

This topic provides the steps necessary to enable database access in a just-in-time (JIT) fashion.  Access to the database is required for various troubleshooting efforts, running adhoc queries, data upgrade problem solving, and more.  This process is available for both Self-service as well as Microsoft Managed sandbox acceptance test environments.  For more information on available environment types, visit the [Deployment overview](../deployment/cloud-deployment-overview.md).

## Microsoft managed environments without RDP access

If you no longer have Remote Desktop Protocol (RDP) access to your sandbox, you can add your IP address to the allow-list in a self-service manner from Lifecycle Services (LCS). When RDP is removed from an environment, the machine credentials section of the environment details page is removed.  This leaves just the database accounts section, as shown below:
![SQL-JIT1](media/sql-jit1.png)

From the environment details page for your sandbox environment, select **Maintain** > **Enable access**, and then, in the dialog box, add the IP address of your source environment. This entry will expire, with the expire date shown alongside the IP address you entered.  It also will be lost after the database is replaced by a database movement operation, such as database refresh or database import.

You can now use tools like SQL Server Management Studio (SSMS) to connect to the database, using the accounts from LCS and the IP address you enabled.

## Self-service environments

This environment type has never had Remote Desktop Protocol (RDP) access, nor has it had static database accounts.  However it is still possible to access the database.

From the environment details page for your sandbox environment, select **Maintain** > **Enable access**, and then, in the dialog box, add the IP address of your source environment. This entry will not expire, however it also will be lost after the database is replaced by a database movement operation, such as database refresh or database import.

Thereafter, under the Database Accounts section fill out which type of access you require.  The options include read, or read-write access.  Enter a short reason description and then click **Request access**.
![SQL-JIT2](media/sql-jit2.png)

When the page is refreshed, the database account will be shown with its expiry time as shown below:
![SQL-JIT3](media/sql-jit3.png)

You can now use tools like SQL Server Management Studio (SSMS) to connect to the database, using the accounts from LCS and the IP address you enabled.