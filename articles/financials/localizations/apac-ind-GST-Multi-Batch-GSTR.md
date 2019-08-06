# required metadata

title: Enable multi batch processing for GSTR reports
description: This topic explains how to enable multiple batch processing for GSTR reports.
author: prabhatb
manager: RichardLuan
ms.date: 08/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.5

---

# Enable Multi-batch processing for GSTR reports 

Many tasks in Finance and Operations can be run as part of batch jobs. Batch jobs are generally created for task like processing reports,
co-ordinating schedule maintenance,and creating and sending document such as invoices. By using batch jobs, user can avoid slowing 
down his computer or the server during typical working hours. The tasks in a batch job can run either sequentially or at the same time . 
India GSTR returns are required to be file by every legal entity and the volumn of transaction general very high as all the sales and purchase
Invoice details are reported to Government. Even exectution of  report generation through Batch takes substaintial time some times. To make 
this process more dynamic and efficent Multi batch processing feature is enable for GSTR reports for India. 

## 1．	Enable this feature

First user has to enable Multi-batch process feature 

![Enable Multi-batch process ](media/Multii-batch processing-001.png)
