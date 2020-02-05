---
# required metadata

title: Generate the Standard Audit File for France (FEC)
description: This topic walks you through generating the Standard Audit File for France (FEC) in Microsoft Dynamics 365 Finance.
author: anasyash
manager: AnnBe
ms.date: 01/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Generate the Standard Audit File for France (FEC)

[!include [banner](../includes/banner.md)]

This procedure walks you through generating the Standard Audit File (FEC) for France in the electronic file format. French tax authorities require audit files that are generated in the FEC format.

Before you can generate a FEC audit file, you must:

1. Set up number sequences for vouchers. Each voucher series must contain a portion of text which is considered the **JournalCode** in the **FEC audit** report. For example, configure a voucher series for vendor invoice journals as **FRSIFACF-########** to get the **JournalCode**, "FRSIFACF" in the FEC.txt file.
2. Import the latest version of the Electronic reporting configuration **French FEC audit file**. 
For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
3. On the **Configurations** page, expand **Data export model**, select **French FEC model mapping**, and set **Default for model mapping** to **Yes**.

## Generate the Standard audit file for France
1. Go to **General Ledger** > **Periodic tasks** > **Data export** to open the **Data export** page.
2. In the **Format mapping** field, select **French FEC audit file**.
3. Select **OK**.
4. On the **Electronic report parameters** page, enter start and end dates for the period in the **Period - date from** and **Period - date to** fields. Select **OK**.
5. Review the generated file.

## Review the Standard audit file
When the Standard audit file is generated, an archive file with the following five reports is also generated.

- FEC.txt
- Vendor incoming.txt
- Customer incoming.txt
- Vendor balance.txt
- Customer balance.txt

Consider the following information for select fields in the reports:

- **JournalCode**: Contains the text portion of the voucher. If the voucher series doesn't have a text portion, the value will be blank. Be sure to correctly set up the voucher series in order to have the correct value in this field.
- **JournalLib**: 

   - In the **Vendor balance.txt** and **Customer balance.txt** reports, this needs to be the constant value **System**.
   - In the **Vendor incoming.txt** and **Customer incoming.txt** reports, this is the value of the **Transaction type** field from the reports, **Vendor transaction** or **Customer transaction**. Possible values could be **Purchase order** or **Payment**.
   - In the **FEC.txt** report, this is the value of the **Transaction type** field from the **Voucher transaction** report. If the **Transaction type** equals **General journal**, this is the value in the **Description** field of the ledger journal, which is the source of the voucher transaction. Verify by checking the value on the **Journal names** page.
