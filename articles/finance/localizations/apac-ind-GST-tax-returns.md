---
# required metadata

title: Generate the GSTR report data for tax returns
description: This topic explains how to generate the GSTR report data for tax returns.
author: EricWang
manager: RichardLuan
ms.date: 06/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Generate the GSTR report data for tax returns

[!include [banner](../includes/banner.md)]

## Generate the GSTR1 report data

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **GER export to GSTR CSV**.
2. In the **From date** and **To date** fields, define a date range.
3. In the **Registration number** field, select a value.
4. In the **Configuration** field, select **GSTR-1 CSV**.
5. In the **File name** field, enter the file name to save the report in comma-separated values (CSV) format as. Include the path of the file.
6. Select **OK**.
7. Use the path that you defined to go to the GSTR1 report file that you created in CSV format. This file becomes the base document that the whole compliance structure in Goods and Services Tax (GST) is based on.

## Generate the GSTR2 report data

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **GER export to GSTR CSV**.
2. In the **From date** and **To date** fields, define a date range.
3. In the **Registration number** field, select a value.
4. In the **Configuration** field, select a **GSTR-2 CSV**.
5. In the **File name** field, enter file name to save the report in CSV format as. Include the path of the file.
6. Select **OK**.
7. Use the path that you defined to go to the GSTR2 report file that you created in CSV format. This file becomes the base document that the whole compliance structure in GST is based on.
