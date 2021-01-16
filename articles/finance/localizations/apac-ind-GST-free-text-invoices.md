---
# required metadata

title: Free text invoices
description: This topic explains how to create a free text invoice.
author: EricWang
manager: RichardLuan
ms.date: 06/04/2019
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

# Free text invoices

[!include [banner](../includes/banner.md)]

## Create a free text invoice

1. Go to **Accounts receivable** \> **Free text invoices** \> **All free text invoices**.
2. Create a free text invoice for taxable services, and save the record.
3. Select **Tax information**.
4. On the **GST** tab, in the **SAC** field, select a value.
5. Select the **Customer tax information** tab.
6. Select **OK**.
7. On the Action Pane, on the **Invoice** tab, in the **Details** group, select **Tax document**.

    You should see something that resembles the following example:

    - **Taxable value:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

8. Select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, select **Post** \> **Post**.
2. Select **OK**, and then close the message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Related information** group, select **Invoice journal**.
2. Select **Voucher**.

![Financial entries for both the intrastate and interstate transactions](media/Annotation-2019-05-20-133425.png)
