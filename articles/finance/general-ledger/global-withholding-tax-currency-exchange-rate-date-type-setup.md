---
# required metadata

title: Enable the global withholding tax currency exchange rate type and date type setup
description: This article explains how to enable the global setup of the withholding tax currency exchange rate type and date type.
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
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29

---

# Enable the global withholding tax currency exchange rate type and date type setup

[!include[banner](../includes/banner.md)]

This article explains how to enable the global setup of the withholding tax currency exchange rate type and date type. You can now select a dedicated exchange rate type and exchange rate calculation date type for the withholding tax currency. These selections determine the foreign currency exchange rate that is used to calculate the withholding tax amount, in the withholding tax currency, in the payment transactions.

This functionality is available in Microsoft Dynamics 365 Finance version 10.0.29 and later.

1. Go to **Tax** \> **Setup** \> **Parameters** \> **General ledger parameters**.
2. On the **Withholding tax** tab, set the **Enable advanced withholding tax currency** option to **Yes**.
3. In the **Exchange rate type** field, select an exchange rate type for the withholding tax currency.
4. In the **Calculation date type** field, select a calculation date type that determines the withholding tax currency exchange rate:

    - **Payment date** – Determine the exchange rate based on the posting date of the payment journal.
    - **Invoice date** – Determine the exchange rate based on the invoice date of the invoice journal. If the invoice date of the voucher is blank, the invoice posting date will be used. 
    - **Document date**  – Determine the exchange rate based on the document date of the payment journal. If the document date of the voucher is blank, the payment date will be used.

5. Select **Save**.

If the transaction currency differs from the withholding tax currency that is defined in the withholding tax code, the amount in the withholding tax currency will be calculated from the transaction currency, based on the preceding settings, and will be recorded in the posted withholding tax transactions.
