---
title: MX-00006 Set up sales tax code
description: Legal financial documents that are submitted to tax authorities in Mexico must contain different types of tax registration IDs and other related information.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/01/2024
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: TaxVatReportCategory_MX, TaxTable
ms.dyn365.ops.version: Version 7.0.0
---

# MX-00006 Set up sales tax code

[!include [banner](../../includes/banner.md)]

This article describes how to create the tax report category codes and to assign a tax report category code to a sales tax code to use in sales, purchase, and summary tax reports. Use these categories to group all transactions as required by the authorities.

To create tax report category codes, follow these steps.

1. Got to **Tax** > **Setup** > **Tax category codes**.
1. Select **New**.
1. In the **Tax report category code** field, enter a unique value. This code is used to classify the VAT report generation.
1. In the **Tax report category description** field, enter a brief description.
1. Select **Save**, and then close the page.

To set up a sales tax code, follow these steps.

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select **New**.
1. In the **Sales tax code** field, type a value.
1. In the **Name** field, type a value.
1. In the **Settlement period** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record and select the link in the selected row.
1. In the **Ledger posting group** field, select the drop-down button to open the lookup and in the list, find and select the link in the selected row.
1. In the **Tax type field**, select an option.
   - _ISR_ – Income tax
   - _IVA_ – Value added tax
   - _IEPS_ – Special product and service tax
   
   Tax type is used in electronic invoices (CFDI) to summarize the taxes per type in the Subtotal section of the invoice.
1. Select or clear the **Additional information** check box. This checkbox is used to allow users to introduce more information such as RFC, CURP, type of operation and other information for nonmanaged vendors. When a purchase transaction is registered with this tax and a vendor account is not specified, more information is required. This configuration is used for the generation of DIOT declaration report.
1. Expand the **Report setup** section.
1. In the **Tax category report** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record and select the link in the selected row.
1. Select the tax category report created before.
1. Select **Save**, and then close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
