--- 
title: Generate German audit file
description: Learn how to generate a German audit file with Germany as the region of legal entity primary address in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 04/04/2025
ms.custom:
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
---

# Generate German audit file

[!include [banner](../../includes/banner.md)]

This article explains how to generate a German audit file with Germany as the region of legal entity primary address in Microsoft Dynamics 365 Finance.

The following procedure shows how to generate the German audit file. This procedure was created using the demo data company DEMF with Germany as the country/region of legal entity primary address.

To generate a German audit file with Germany as the region of legal entity primary address, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Periodic tasks \> Data export**.
1. In the **Format mapping** field, enter or select a value. If the list is empty, there's no German audit file export format configuration imported and active. You must import a German audit file export format configuration before you can continue.  
1. Select **OK**.
1. In the **Comment** field, enter a value.
1. In the **Media** field, enter a value.
1. In the **Version** field, enter a value.
1. In the **Table Group** field, enter or select a value. For example, select **Kunden** to export customer master data and transactions.  
1. In the **Period - date from** field, enter a date.
1. In the **Period - date to** field, enter a date.
1. Select **OK**.

> [!NOTE]
> As of version 70 of the **Data export model**, the following replacements are implemented for some of the special symbols in text that's being written in column 11 (**BUCHUNGSTEXT**) of the Sachkontobuchungen output file:
> - Any sequence of symbols or individual symbols Carriage Return (ASCII code 13) and Line Feed (ASCII code 10) are replaced with space (ASCII code 32).
> - The double quotes symbol (ASCII code 34) is replaced with the single quote symbol (ASCII code 39).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
