---
# required metadata

title: Include GST when calculating tax collections
description: This topic explains how to include Goods and Services Tax (GST) when you calculate tax collections.
author: EricWangChen
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
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
ms.author: wangchen
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Include GST when calculating tax collections

[!include [banner](../includes/banner.md)]

## Set up GST requirements

1. Go to **Tax** \> **Indirect Tax** \> **Withholding tax** \> **Withholding tax groups**.
2. Select a withholding tax group.
3. On the **General** FastTab, in the **Include GST tax components for TDS or TCS calculation** field, select the required Goods and Services Tax (GST) components.
4. Select **Close**.

## Create a sales order

1. Go to **Accounts receivable \> Sales orders \> All sales orders**.
2. Create a sales order.
3. Select **OK**.

### Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    Here is an example of what you should see:

    - **Taxable value:** 10,000.00
    - **IGST:** 20 percent

2. Select **Close**.
3. Select **Product and supply** \> **Withholding tax**.
4. Select **Close**.

### Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. Select **OK**.
3. Select **OK**.
4. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
5. On the **Overview** tab, select **Voucher**.

![Example.](media/Annotation-2019-05-21-134958.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
