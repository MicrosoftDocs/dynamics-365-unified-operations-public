---
# required metadata

title: Revise an advance payment that includes tax
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
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

# Revise an advance payment that includes tax

1. Click **Accounts receivable > Payments > Payment journal**.
2. Create a new record, and in the **Name** field, select a value.
3. On the **Setup** tab, select the **Amounts include sales tax** check box.
4. Click **Lines**.
5. Create a customer advance payment journal and save the record.
6. Click **Tax information**
7. On the **GST** tab, in the **HSN code** field, select a value.
8. Click the **Customer tax information** tab.
9. Click OK.
10. On the **General** tab, in the **Invoice type** field, select **Revised**.
11. In the **Original transaction ID** field, select a value.
12. Verify that the **Original transaction date** field is automatically set, based on the original transaction ID that you selected.

## Validate the tax details

1. Click **Tax document**.

Example:

- IGST: 20 percent

2. Click **Close**.
3. Click **Post > Post**.
4. Close the message.

### Validate the financial entries

To validate the financial entries, click **Inquiries > Voucher**.

![](media/Annotation-2019-05-21-132745.png)



