---
# required metadata

title: Vendor electronic invoices in Italy
description: This topic explains how to configure and submit vendor electronic invoices in Italy.
author: ikondo
ms.date: 10/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 3984823
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-12-01
ms.dyn365.ops.version: 10.0.21

---

# Vendors electronic invoices export

[!include [banner](../includes/banner.md)]

According to Italian legislation, invoices received from foreign vendors which are not tax residents in Italy, must be submitted to the Exchange system (SDI).
This topic describes how configure and submit vendor electronic invoices in the electronic format **FatturaPA**.

## Prerequisites

The primary address of the legal entity must be in Italy.

The export of vendors electronic invoices is implemented symmetrically to Italian customers electronic invoices export and uses common **Electronic invoice parameters** defined in **Accounts receivable** module. For details, see the article for [Customer electronic invoices](emea-ita-e-invoices.md).


## <a id="apparameters"></a>Accounts payable parameters

In **Accounts payable** \> **Setup** \> **Accounts payable parameters**, on the **Electronic documents** tab, select the configuration that is used to create electronic invoice  export XML files for vendor invoices.

![Electronic documents in Accounts payable parameters](media/emea-ita-AP-parameter-e-invoices.jpg)

> [!NOTE]
> The configurations must be imported before they can be selected. For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- [Accounts receivable parameters](#apparameters)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]

