---
# required metadata

title: Enable multi-batch processing for GSTR reports
description: This topic explains how to enable multiple batch processing for GSTR reports.
author: prabhatb
manager: RichardLuan
ms.date: 08/12/2019
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
ms.dyn365.ops.version: 10.0.6

---

[!include [banner](../includes/banner.md)]

# Enable multi-batch processing for GSTR reports 

Many tasks in Microsoft Dynamics 365 for Finance and Operations can be run as part of a batch job. Batch jobs are generally created for tasks such as processing reports, coordinating schedule maintenance, and creating and sending documents, such as invoices. By using batch jobs, users can avoid slowing down their computers or the server during typical working hours. The tasks in a batch job can run sequentially, or at the same time.

In India, GSTR returns are required to be filed by every legal entity and the trasaction volume is typically very high as all sales and purchase invoice details are reported to the government. Currently, GSTR reports can be generated directly through the report dialog box or through the batch process. However there are times when the report generation process can take quite a while. To make this process more dynamic and efficient, the multi-batch processing feature is provided for GSTR reports. This will significantly improve the performance of report generation.

## Enable multi-batch processing feature 
Go to **Work spaces** \> **Feature management** and enable the multi-batch process feature.  

![Enable Multi-batch process ](media/Multi-batchprocessing-001.png)

## Generate GSTR report 

1. Go to **Tax** \> **Sales tax report** \> **GER export to GSTR CSV**.
2. Set the **Batch processing** toggle to **Yes**.
3. In the **Number of days per batch’** field, enter a number greater than zero (0).
4. Click **OK**.

![Generate GSTR Report ](media/Multi-batchprocessing-002.png)

## Get CSV files

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting job**.
2. Select the CSV files that you want. For example, **GER export to GSTR CSV__Merged** which is generated as a **Merged** file.


![Get CSV Files ](media/Multi-batchprocessing-003.png)
 
