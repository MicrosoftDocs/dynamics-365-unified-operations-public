---
# required metadata

title: View liability, asset, and expense transactions
description: This topic lists the steps for viewing transactions for a leased asset, including lease liability, and executory expenses that have been posted. 
author: moaamer
manager: Ann Beebe
ms.date: 08/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: 10.0.14
---

# View liability, asset, and expense transactions

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists the steps for viewing transactions for a leased asset, including lease liability, and executory expenses that have been posted. The carrying values of the liability and right-of-use asset are used on a number of reports. The carrying values are also used to calculate adjustment values.

## Liability transactions
To view the lease liability transactions, select a lease from the **Lease summary** page and click **Books** to open the books for that lease. Click **Liability transactions** after an initial recognition, an invoice, or an interest journal has been posted.

The **Liability transactions** page displays the transactions that either increase or decrease the lease liability. Negative amounts on this page represent credit transaction in the standard application. Any interest accruals will show as negative and increase the total lease liability. Any lease adjustment will show as positive or negative depending on the nature and impact of the lease book. The current net total balance of the lease liability for the selected lease is shown at the bottom left of the dialog.

## Asset transactions
To view the lease asset transactions, select a lease from the **Lease Summary** page and click **Books** to open the lease books that are attached to the lease record. Then click **Asset transactions**.

The **Asset transaction** page diplays the transactions that either increase or decrease the lease asset and accumulated depreciation accounts. Debits will display as positive values and credits shown as negative values, which is similar to the **Liability transactions** dialog. The carrying balance of the right-of-use asset, net of accumulated depreciation, is shown at the bottom left area of the page.

## Expenses transactions
To view the lease expense transactions, select a lease from the **Lease Summary** page and click **Books** to open the attached lease books on the lease record. Then click **Expense transactions**. This page will display all the expenses posted against a lease, such as interest expense, depreciation expense, and any executory costs.
