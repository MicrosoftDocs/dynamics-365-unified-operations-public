---
# required metadata

title: Account structure activation performance enhancement 
description: This article explains the new performance enhancements for the account structure activation process.
author: RyanCCarlson2
ms.date: 10/31/2022
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2022-10-08
ms.dyn365.ops.version: 10.0.31

---

# Account structure activation performance enhancement

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


This performance enhancement allows you to activate account structures faster by running multiple transaction updates at the same time. In addition, the structure itself is marked as active after it's validated and transaction processing can continue while existing unposted transactions are updated to the new structure. Because updating transactions may take some time, you can track the status of your activation by selecting **View activation status**. You can also select **View** and then select **Activation status** in the drop-down menu to view your activation status.  

 [![Account Structure page](./media/AccountStructure1.png)](./media/AccountStructure1.png)

After you select **View activation status**, a dialog box opens that contains the individual tasks that are running as part of the activation process. Each task has a corresponding status for you to view and a completed date and time once it completes. 

 [![Account Structure activation timeline](./media/AccountStructureTimeline.png)](./media/AccountStructureTimeline.png)
 
## Account structure activation tips 

The account structure activation dialog box that appears when you select **Activate** for a draft account structure has a tab section called **Update unposted transactions**. This section has an option to select titled **Force update**. USe this option to update all unposted transactions to the current structure. This option should only be selected when a prior error has happened or you have been directed by Microsoft support to do so. 

Some factors that can impact the performance of the activation process are: 
 
 - A high number of unposted journal records.
 - A high number of open source document records such as Free Text invoices, Vendor Invoices and related documents that use the source document framework and have open accounting distributions. 
 - The amount of data in TaxUncommitted.
 - The amount of open budget data. 
 - Importing journal data while activation tasks are still running. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
