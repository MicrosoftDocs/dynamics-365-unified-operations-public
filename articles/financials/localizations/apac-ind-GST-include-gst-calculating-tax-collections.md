---
# required metadata

title: Include GST when calculating tax collections
description:  This topic includes information about how to include GST when calculating tax collections.
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
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Include GST when calculating tax collections

## Set up GST requirements

1. Click **Tax** \> **Indirect Tax** \> **Withholding tax** \> **Withholding tax groups**.
2. Select a withholding tax group.
3. On the **General** FastTab, in the **Include GST tax components for TDS or TCS calculation** field, select the required GST components.
4. Click **Close**.

## Create a sales order

1. Click **Accounts receivable > Sales orders > All sales orders**.
2. Create a sales order.
3. Click **OK**.

### Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document** to review the calculated taxes.

For example, you should see something like this:

- Taxable value: 10,000.00
- IGST: 20 percent

2. Click **Close**.
3. Click **Product and supply** \> **Withholding tax**
4. Click **Close**.

### Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. Click **OK**.
3. Click **OK**.
4. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. 
5. On the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-21-134958.png)
