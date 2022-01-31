---
# required metadata

title: Apply a payment schedule to the invoice journal
description: This topic describes how to add a payment to the vendor invoice journal.
author: sunfzam
ms.date: 01/31/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.25

---

# Apply a payment schedule to the invoice journal

[!include [banner](../includes/preview-banner.md)]

With release 10.0.25, **Payment schedule** is now supported on the **Vendor invoice journal**. 

> [!NOTE]
> To use this new functionality, enable the **Apply payment schedule to invoice journal** feature in **Feature management**.

After this feature is enabled, a new field **Payment schedule** will be added to the **Invoice journal** page. When creating a new invoice journal line, if payment terms are 
maintained on the **Vendor** and the **Payment term** is selected on the **Payment schedule**, then the **Payment schedule** field will be updated on the **Invoice journal** page. 

The **Payment schedule** can be updated to a different one according to business needs. During the posting of the **Vendor invoice journal**, 
vendor open transactions will be created according to the **Payment schedule**.

To check multiple vendor open transactions generated from payment schedule, go to **Accounts payable->Invoices->Open vendor invoices**, enter the **Invoice number** or the
**Vendor account**.

To check or configure the **Payment schedule**, go to **Accounts payable->Payment Setup->Payment schedule**.

To configure the **Payment terms** and assign a **Payment schedule**, go to **Accounts payable->Payment setup->Terms of payment**.

To maintain the **Terms of payment** on a **Vendor**, go to **Accounts payable->All Vendors->Choose Vendor Account->Payment tab->Terms of payment**.

The **Payment schedule** feature is also available in the **Vendor invoice register** process. If a **Payment schedule** is select on the **Invoice register journal**, 
multiple vendor payment lines will NOT be generated when the **Invoice register** is posted. The vendor payment lines will be generated when the invoice is approved. 

## Limitation

In a pending **Vendor invoice**, if the **Payment schedule** is on the invoice header, there is an advanced page that allows users to edit the payment lines.
For example, the **Due date** and value for each payment line. Payment lines that are generated from the **Invoice journal** will have the value from the **Payment schedule**.
This functionality in the **Vendor invoice journal** and a **Pending invoice** will be available in a future release. 
