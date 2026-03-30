---
title: Use fiscal data from an invoice account
description: Learn how to enable fiscal data to be automatically updated on sales orders or purchase orders based on information from the invoice account.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.validFrom: 2020-02-03
ms.search.form: CustParameters, VendParameters
---

# Use fiscal data from an invoice account

[!include [banner](../../includes/banner.md)]

You can use fiscal data, such as the customer or vendor name, or the sales tax group and tax-exempt numbers from an invoice account on sales orders, free text invoices, or purchase orders to update automatically based on the information from the invoice account. This article explains how to configure the feature.

## Accounts payable and Accounts receivable parameters

To enable this functionality for purchase orders, sales orders, and free text invoices, set the **Use fiscal data from invoice account** parameter in the Accounts payable and Accounts receivable modules, respectively. This field is on the **Invoice** tab on the **Accounts payable parameters** page, and on the **Invoice** FastTab on the **Updates** tab on the **Accounts receivable parameters** page. The following options are available:

-	**Never** - The information is updated from the vendor or customer account.
-	**Always** - The information is updated from the invoice account.
-	**Ask** - The user is prompted to specify whether the information should be updated from the invoice account or from the vendor or customer account. If the user selects **Yes**, the information is updated from the invoice account; otherwise the default is to update information from the vendor or customer account.

This functionality is managed by a feature named Enable defaulting of fiscal data from invoice account. This feature needs to be enabled to be able to see and configure the parameters in this page. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
