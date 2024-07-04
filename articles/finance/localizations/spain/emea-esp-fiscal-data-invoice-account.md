---
title: Use fiscal data from the invoice account
description: Learn about the Use fiscal data from invoice account functionality and explains how to set it up, including an outline on procurement.
author: epodkolzina
ms.author: epodkolzina
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: CustParameters, VendParameters
ms.dyn365.ops.version: Version 1611
---

# Use fiscal data from the invoice account

[!include [banner](../../includes/banner.md)]

For legal entities in Spain, the Use fiscal data from invoice account functionality enables fiscal data on sales orders, free text invoices, and purchase orders to be updated automatically, based on information from the invoice account. This article provides information about the Use fiscal data from invoice account functionality and explains how to set it up.

For legal entities in Spain, the Use fiscal data from invoice account functionality enables fiscal data on sales orders, free text invoices, and purchase orders to be updated automatically, based on information from the invoice account. The fiscal data that is updated includes the customer or vendor name, address, and tax information. The Use fiscal data from invoice account functionality affects the following modules:

-   Accounts payable **Invoice account** change page
-   Procurement and sourcing
-   Accounts receivable
-   Sales and marketing

## Accounts payable and Procurement and sourcing
To manage the opportunity of fiscal data automatic update on Invoice account change in the Accounts payable module you need to set up a parameter Use fiscal data from invoice account on Invoice tab of the **Account payable parameters** page. The following options are available:

-   **Never** – Information is updated from the vendor account.
-   **Always** – Information is updated from the invoice account.
-   **Ask** – The user is prompted to specify whether information should be updated from the invoice account or the vendor account.

When the **Use fiscal data from invoice account** parameter is set, three fields on a purchase order may be updated according the value of the parameter. When the **Invoice account** field is changed, the following fields are updated with information from the invoice account:

-   Name
-   Sales tax group
-   Tax exemption

## Accounts receivable and Sales and marketing
To manage the opportunity of fiscal data automatic update on **Invoice account** change in the **Accounts receivable** module you need to set up a parameter “**Use fiscal data from invoice account**” on the **Invoice** fasttab of the **Updates** tab of the **Account receivable parameters** page. The following options are available:

-   **Never** – Information is updated from the customer account.
-   **Always** – Information is updated from the invoice account.
-   **Ask** – The user is prompted to specify whether information should be updated from the invoice account or the customer account.

When the **Use fiscal data from invoice account** parameter is set, the following documents from Accounts receivable can be updated:

-   Sales orders
-   Free text invoices

When the **Invoice account** field is changed, the following fields can be updated with information from the invoice account:

-   Name
-   Sales tax group
-   Tax exemption






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
