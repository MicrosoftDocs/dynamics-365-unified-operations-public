---
# required metadata

title: Enable global withholding tax currency exchange rate type and date type setup
description: This article explains how to enable and setup global withholding tax currency exchange rate type and date type.
author: kailiang
ms.date: 08/02/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 13131
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29

---

# Enable global withholding tax currency exchange rate type and date type setup

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/preview-banner.md)]


This article explains how to enable the global withholding tax currency exchange rate type and date type setup. You can now specify a dedicated withholding tax currency exchange rate type and an exchange rate calculate date type. These selections determine the foreign currency exchange rate used for the withholding tax amount calculation, in withholding tax currency, in the payment transactions.

This functionality is available in Dynamics 365 Finance version 10.0.29 and later.

1. Go to **Tax** > **Setup** > **Parameters** > **General ledger parameters** > **Withholding tax**.
2. Set the **Enable advanced withholding tax currency** field to **Yes**.
3. In **Exchange rate type** field, select an exchange rate type for withholding tax currency.
4. In **Calculation date type** field, select a calculation date type which determines the withholding tax currency exchange rate.

   - Select **Payment date** to determine the exchange rate based on the posting date of the payment journal. 
   - Select **Invoice date** to determine the exchange rate based on the invoice date of the invoice journal. If the invoice date of the voucher is blank, the invoice posting date will be used. 
   - Select **Document date** to determine the exchange rate based on the document date of the payment journal. If the document date of the voucher is blank, the payment date will be used.

5. Select **Save**.

When the transaction currency is different from the withholding tax currency defined in the withholding tax code, the amount in withholding tax currency will be calculated from the transaction currency based on above settings and recorded in the posted withholding tax transactions.
