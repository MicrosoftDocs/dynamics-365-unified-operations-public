---
# required metadata

title: Formula designer for TDS calculations
description: This article provides an example of how Tax Deducted at Source (TDS) is calculated based on the formula defined for each TDS tax code in the TDS group that's attached to the transaction.
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Formula designer for TDS calculations

[!include [banner](../includes/banner.md)]

This article provides an example of how Tax Deducted at Source (TDS) is calculated based on the formula defined for each TDS tax code. TDS tax codes are defined in the TDS group that's attached to the transaction. Before designing TDS formulas, complete the basic setup required for TDS as listed in the following steps. 

- Set up TDS component groups using the **Withholding tax component groups** page. 
- Set up TDS components and attach TDS component group to the TDS components using the **Withholding tax components** page. 
- Set up TDS tax codes and attach TDS components to the tax codes using the **Withholding tax codes** page. 
- Set up TDS tax groups using the **Withholding tax groups** page. Then attach the TDS tax codes to the tax group, and define the formula, using the **Formula designer** page. 

**Example formula**

In this example, the TDS group, Rent, is attached to a purchase invoice that's created for vendor A. The invoice amount is $100,000. Refer to the following table to view the TDS calculation for the invoice.

| TDS  group                                                   | TDS tax codes attached to the TDS group | Value              | Taxable basis  (Formula designer) | Calculation expression  (Formula designer) | Base amount | Calculated TDS amount |
| ------------------------------------------------------------ | --------------------------------------- | ------------------ | --------------------------------- | :----------------------------------------: | ----------- | --------------------- |
| Rent                                                         | TDS  (TDS component-TDS)                | 10%                | Gross amount                      |                                            | 100,000      | 10,000                 |
| Surcharge  (TDS component-Surcharge)                         | 10%                                     | Excl. gross amount | +TDS                              |                   10000                    | 1,000        |                       |
| PE-Cess  (TDS component- PE-Cess)                            | 2%                                      | Excl. gross amount | +TDS+Surcharge                    |                   11000                    | 220         |                       |
| SHE Cess  (TDS component- SHE Cess)                          | 1%                                      | Excl. gross amount | +TDS+Surcharge                    |                   11000                    | 110         |                       |
| **Total** **TDS**  **calculated** **for** **the** **invoice** | **11,330**                               |                    |                                   |                                            |             |                       |

The voucher entries are created as follows.

| Account           | Debit  | Credit |
| ----------------- | ------ | ------ |
| Rent              | 100,000 |        |
| Vendor A          |        | 100,000 |
| Vendor A          | 11,330  |        |
| TDS payable       |        | 10,000  |
| Surcharge payable |        | 1,000   |
| PE-Cess payable   |        | 220    |
| SHE Cess payable  |        | 110    |
