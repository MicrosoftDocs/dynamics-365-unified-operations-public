---
title: ER Generate electronic documents for payments using a format configuration
description: This article describes how to use a new Electronic reporting (ER) format configuration to generate electronic documents for processing payments.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: VendPaymMode, LedgerJournalTable, LedgerJournalTransVendPaym, BankAccountTableLookUp
---

# ER Generate electronic documents for payments using a format configuration

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can use a new Electronic reporting (ER) format configuration to generate electronic documents for processing payments. You can perform these steps in the GBSI sample company.

To complete these steps, you must first complete the steps in the "Create a configuration with format of payment document" procedure.

## Change the configuration of the electronic payment method

1. Go to **Accounts payable** > **Payment setup** > **Methods of payment**.
1. Toggle the **File format** section to expand it, if needed.
1. Use the Quick Filter to find records. For example, filter on the **Method of payment** field with a value of **Electronic**.
1. Select **Edit**.
1. Set the **General electronic reporting** field to **Yes**.
    * Select **Yes** to use the General electronic reporting pattern for payment files generation.  
1. In the **Name** field, select the drop-down button to open the lookup.
1. Select **BACS (UK fictitious)** format configuration.
1. Select **Save**.
1. Close the page.

## Test the format of generated payment files

1. Go to **Accounts payable** > **Payments** > **Payment journal**.
1. Select **New**.
1. In the list, select the row.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
    * Select **VendPay**.  
1. Select **Save**.
1. Select **Lines**.
1. In the **Company** field, enter `DEMF`.
    * Enter **DEMF**  
1. In the **Account** field, enter `DE-01001`.
    * Enter **DE-01001**  
1. In the **Description** field, enter `Payment`.
    * Enter **Payment**  
1. In the **Debit** field, enter a number.
    * 1000  
1. Select the **Payment** tab.
1. In the **Method of payment** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
    * Select the **Electronic** value.  
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Select **Generate payments**.
1. In the **Method of payment** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
    * Select the **Electronic** value.  
1. In the list, select the link in the selected row.
    * Select the **Electronic** value.  
1. In the **File name** field, enter a value.
    * For example, enter `payments`.  
1. In the **Bank account** field, select the dropdown button to open the lookup.
1. In the list, select the link in the selected row.
    * Select the value **GBSI OPER**.  
1. Select **OK**.
1. Select **OK**.
    * Analyze the created payment file in XML format. Compare it with the designed document layout and defined payment transaction attributes.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
