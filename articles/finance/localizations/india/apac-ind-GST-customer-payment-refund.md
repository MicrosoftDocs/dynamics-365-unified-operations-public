---
title: Customer payment refunds
description: Learn about customer payment refunds, including step-by-step processes for validating tax details and validating financial entries.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 06/03/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Customer payment refunds

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts receivable \> Payments \> Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. On the **Setup** tab, select the **Amounts include sales tax** check box.
5. Select **Lines**.
6. Create a customer advance payment journal, and save the record.
7. Select **Tax information**.
8. On the **GST** tab, in the **HSN code** field, select a value.
9. Select the **Customer tax information** tab.
10. Select **OK**.

### Validate the tax details

1. Select **Tax document**.

    **Example**

    **IGST:** 20 percent

2. Select **Close**.
3. Select **Post \> Post**.
4. Close the message that you receive.

### Validate the financial entries

To validate the financial entries, select **Inquiries \> Voucher**. Here is an example.

![Example of financial entries.](../media/Annotation-2019-05-21-132929.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
