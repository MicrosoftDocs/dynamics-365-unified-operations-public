---
# required metadata

title: Global withholding tax currency exchange rate type and date type setup
description: This article explains how to enable and setup global withholding tax currency exchange rate type and date type.
author: kailiang
ms.date: 07/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

---

# Global withholding tax currency exchange rate type and date type setup

This article explains how to enable global withholding tax currency exchange rate type and date type setup. You can now specify a dedicated withholding tax currency exchange rate type and an exchange rate calculate date type to determine the foreign currency exchange rate used for withholding tax amount (in withholding tax currency) calculation in the payment transactions.

This functionality is available in version 10.0.29 and later.

1. Go to **Navigation pane > Modules > Tax > Setup > Parameters > General ledger parameters > Withholding tax**.

2. Set the **Enable advanced withholding tax currency** field to **Yes**.

3. In **Exchange rate type** field, select an exchange rate type for withholding tax currency.

4. In **Calculation date type** field, select a calculation date type, which determines the withholding tax currency exchange rate.
   - Select **Payment date** to determine the exchange rate based on the posting date of the payment journal. 
   - Select **Invoice date** to determine the exchange rate based on the invoice date of the invoice journal; If the invoice date of the voucher is blank, the invoice posting date will be used. 
   - Select **Document date** to determine the exchange rate based on the document date of the payment journal; If the document date of the voucher is blank, the payment date will be used.

5. Click **Save**.

When the transaction currency is different to the withholding tax currency defined in the withholding tax code, the amount in withholding tax currency will be calculated from the transaction currency based on above settings and recorded in the posted withholding tax transactions.