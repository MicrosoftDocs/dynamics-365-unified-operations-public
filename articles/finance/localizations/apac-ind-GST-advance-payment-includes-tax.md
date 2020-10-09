---
# required metadata

title: Advance payments that include tax
description: This topic explains how to create a customer advance payment journal, and then validate the tax information and financial entries.
author: EricWang
manager: RichardLuan
ms.date: 06/03/2019
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
ms.author: kfend
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Advance payments that include tax

[!include [banner](../includes/banner.md)]

Complete the following procedures to create a customer advance payment journal, and then validate the tax information and financial entries.

## Create a customer advance payment journal

1. Go to **Accounts receivable \> Payments \> Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. On the **Setup** tab, select the **Amounts include sales tax** check box.
5. Select **Lines**.
6. Create a customer advance payment journal.
7. Save the record.
8. Select **Tax information**.
9. On the **GST** tab, in the **HSN code** field, select a value.
10. Select the **Customer tax information** tab, and then select **OK**.

## Validate the tax details

1. Select **Tax document**.

    **Example**

    **IGST:** 20 percent

2. Select **Close**.
3. Select **Post \> Post**.
4. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, in the journal, select **Inquiries \> Voucher**. Here is an example.

![Example of financial entries](media/Annotation-2019-05-21-131638.png)
