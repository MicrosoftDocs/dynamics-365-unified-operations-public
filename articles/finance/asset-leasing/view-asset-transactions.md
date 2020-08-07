---
# required metadata

title: View liability, asset, and expense transactions
description: 
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

Like the Fixed asset module, the Asset leasing module allows the user to view all transactions made on the leased asset and lease liability, as well as any executory cost expenses that have been posted. The carrying values of the liability and right-of-use asset are used in many leasing reports in addition to calculating adjustment values.
1.	To view the lease liability transactions, select a lease from the Lease summary form and click Books to open the books for that lease. Click Liability transactions after an initial recognition, an invoice, or an interest journal has been posted.
2.	A form will open showing the transactions that either increase or decrease the lease liability. Negative amounts in this form represent credit transaction in the standard application. Any interest accruals will show as a negative and increase the total lease liability. Any lease adjustment will show as positive or negative depending on the nature and impact of lease book. The net total current balance of the lease liability for the selected lease is shown in the bottom left of the form.
3.	To view the lease asset transactions, select a lease from the Lease Summary form and click Books to open the attached lease books on the lease record and then click on Asset transactions.
4.	A form will open showing the transactions that either increase or decrease the lease asset and accumulated depreciation accounts. Like the liability transactions form, debits will show as positive values and credits shown as negative values. The carrying balance of the right-of-use asset, net of accumulated depreciation is shown in the bottom left of the form.
5.	To view the lease expense transactions, select a lease from the Lease Summary form and click Books to open the attached lease books on the lease record and then click on Expense transactions. This form will show all expenses posted against a lease such as interest expense, depreciation expense, and any executory costs.
