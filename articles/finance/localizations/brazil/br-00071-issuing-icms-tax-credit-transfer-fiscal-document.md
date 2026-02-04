---
title: Issue ICMS tax credit transfer fiscal documents (Brazil)
description: This article describes how to create and issue a new tax fiscal document and generate a Nota Fiscal eletrônica (NF-e) in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Issue ICMS tax credit transfer fiscal documents (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create and issue a new tax fiscal document and generate a Nota Fiscal eletrônica (NF-e) in Brazil with Microsoft Dynamics 365 Finance.

You can create a new tax fiscal document and generate a NF-e. When you post the document, an NF-e XML message is generated and submitted to the Secretaria da Fazenda (SEFAZ). 

The following procedure uses the BRMF demo company.

To create and issue a new tax fiscal document and generate a NF-e, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Journal entries \> All tax fiscal documents**.
1. Select **New**.
1. In the **Tax fiscal document type** field, select the type of tax transfer fiscal document (**ICMS tax transfer between fiscal establishments** or **ICMS tax credit installment**).  
1. In the **Fiscal establishment ID** field, enter or select a value.
1. In the **Account type** field, select an option. When you're doing an ICMS tax transfer, select a vendor to receive the tax credit from another fiscal establishment, or select a customer to transfer the tax credit to another fiscal establishment.  
1. In the **Account number** field, enter or select a value. The fiscal establishment must be a vendor or customer.  
1. In the **Document model** field, enter or select a value.
1. In the **Access key** field, enter a value.
1. In the **Date** field, enter a date.
1. Select **Save**.
1. Select **Add line**.
1. In the **Item description** field, enter a value.
1. In the list, mark the selected row.
1. In the **CFOP** field, enter or select a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Amount** field, enter a number.
1. Select **Save**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
