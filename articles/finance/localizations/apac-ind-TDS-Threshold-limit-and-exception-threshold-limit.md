---
# required metadata

title: Threshold limit and exception threshold limit
description: This article describes the threshold and exception limits for Tax Deducted at Source (TDS).
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

# Threshold limit and exception threshold limit

[!include [banner](../includes/banner.md)]

This article describes the threshold and exception limits for Tax Deducted at Source (TDS). The TDS on invoices and payments is always calculated considering the threshold limit and exception threshold limit defined for the TDS tax components on the **Withholding tax components** page. The TDS tax components are attached to TDS tax codes, which are included in the TDS tax groups. The TDS tax groups are attached to vendors and customers to calculate TDS at the invoice-level or payment-level.

TDS is calculated if the amount for a transaction or the cumulative transactions posted with a specific TDS group for a vendor exceeds the threshold limit specified on the **Withholding tax components** page. TDS will not be calculated until the cumulative transaction amount exceeds the specified threshold limit.

If an exception threshold limit is specified along with the threshold limit for a TDS component, TDS is calculated when a specific transaction amount exceeds the exception threshold limit even if the cumulative transaction amount does not exceed the specified threshold limit.

### Example
A tax component called TDS is set up and attached to the TDS tax group called Contractor. The threshold has been defined as 50,000 and exception threshold has been defined as 20,000 for TDS tax component. The TDS group contractor is defined as the default TDS group for vendor 1.

A purchase invoice 001 is posted for vendor 1 for 10000. TDS is not calculated for the invoice because the invoice amount has not crossed the threshold limit or exception threshold limit. A purchase invoice 002 is posted for vendor 1 for 25,000. TDS is calculated for the invoice because the invoice amount has crossed the exception threshold limit. A purchase invoice 003 is posted for Vendor 1 for 20,000. TDS is calculated for the invoice because the total invoice amount of the three invoices that are issued for the vendor has crossed the threshold limit. TDS is calculated on all invoices that are issued for the vendor on which the TDS has not been calculated earlier. Therefore, TDS is calculated on 30,000, which is the total invoice amount of invoice 001 and 003.

The threshold limit and exception threshold limit are not considered for the TDS calculation if the **Overlook threshold** check box is selected for TDS tax codes in the TDS group that is attached to the transaction. The threshold limit won't be used in the TDS tax codes in the TDS group that the **Overlook threshold** check box is for.

If the **Overlook threshold** check box is selected for a specific TDS group for some invoices, but not selected for other invoices that were created for a specific vendor/customer, the calculation of TDS without overlooking the threshold limit for few invoices may take place considering the cumulative amount on all invoices on which TDS hasn't been calculated earlier.

For example, the threshold limit is 25000. The following invoices are created for Vendor A.

- Invoice 1 – 2,0000 – (**Overlook threshold** check box is not selected): TDS is not calculated.

- Invoice 2 – 4,000 – (**Overlook threshold** check box is selected): TDS is calculated on 4,000.

- Invoice 2 – 3,000 – (**Overlook threshold** check box is not selected): TDS is calculated as the cumulative invoice amount, that is, 27,000 (20000+4000+3000) exceeded the threshold limit. TDS is calculated on the cumulative amount of invoices on which the TDS has not been calculated earlier, that is, 23,000 (20000+3000).
