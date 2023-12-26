--- 
# required metadata 
 
title: Semansys XBRL integration
description: This procedure walks you through using Dutch functionality to export financial data in the XML format. 
author: mrolecki
ms.date: 05/28/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Dialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Netherlands
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Deliver XBRL to the Dutch Regulatory body via Semansys XBRLOne

[!include [banner](../../includes/banner.md)]

This article walks you through the steps to map, export, and deliver eXtensible Business Reporting Language (XBRL) to the Dutch regulatory body.  

The high-level process is a system-to-human-to-system process. The first system involved is Microsoft Dynamics 365 Finance. This system is responsible for creating all the necessary entries, chart of accounts, and mappings. After this is complete, a user will export the data into the Semansys DataBridge format. This exported data can then be uploaded into the XBRLOne portal to convert to XBRL, and then validated and delivered to the correct Dutch regulatory body. 

The following prerequisites are needed for this process:

- The report data is available for mapping by using the General Ledger in Finance.
- Knowledge of the correct taxonomy for which you're reporting and the confirmation that you're delivering to a Dutch regulatory body.
- Import **Dutch XBRL integration model** and **Semansys XBRL (NL)** electronic reporting configurations.

For more information about how to download ER configurations from Microsoft Dynamics Lifecycle Services (LCS), see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

The following example shows the steps needed for a user to export the data for reporting a 2019 annual report. 

1. Go to **General ledger** > **Periodic tasks** > **Export financial data to XBRL**.
2. In the **From date** field, enter a date. For example, *2019-01-01*.  
3. In the **To date** field, enter a date. For example, *2019-12-31*.
4. In the **Format mapping** field, enter the correct formats.
5. Select **OK**.

You can now take the Semansys DataBridge format package to the XBRLOne portal for next steps in the process.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]