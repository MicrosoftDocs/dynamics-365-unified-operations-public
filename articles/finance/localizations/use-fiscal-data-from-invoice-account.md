---
# required metadata

title: Use fiscal data from the invoice account
description: The feature “Use fiscal data from invoice account” enables fiscal data, such as the customer or vendor name, their sales tax group and tax exempt number on sales orders, free text invoices or purchase orders to be updated automatically based on the information from the invoice account. This topic explains how to configure the feature.
author: 
manager: 
ms.date: 
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustParameters, VendParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 265224
ms.search.region: 
# ms.search.industry: 
ms.author:
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.9

---

# Use fiscal data from the invoice account

[!include [banner](../includes/banner.md)]

The feature “Use fiscal data from invoice account” enables fiscal data, such as the customer or vendor name, their sales tax group and tax exempt number on sales orders, free text invoices or purchase orders to be updated automatically based on the information from the invoice account. This topic explains how to configure the feature.

## Accounts payable and Accounts receivable parameters

In order to enable the feature for purchase orders, sales orders and free text invoices, set the **Use fiscal data from invoice account** parameter in the Accounts payable and Accounts receivable modules respectively. It is located on the Invoice tab of the **Accounts payable parameters** page and on the **Invoice** fasttab of the **Updates** tab of the **Accounts receivable parameters** page. The following options are available:

-	**Never** – the information is updated from the vendor or customer account.
-	**Always** – the information is updated from the invoice account.
-	**Ask** – The user is prompted to specify whether the information should be updated from the invoice account or from the vendor/customer account. If the user selects **Yes**, the information is updated from the invoice account; otherwise the information is defaulted from the vendor/customer account.
