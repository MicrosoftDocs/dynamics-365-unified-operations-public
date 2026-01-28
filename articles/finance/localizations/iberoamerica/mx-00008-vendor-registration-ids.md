---
title: MX-00008 - Vendor registration IDs
description: Learn how to create a vendor for Mexico to support the DIOT declaration and other legal reports in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: VendTable
---

# MX-00008 - Vendor registration IDs

[!include [banner](../../includes/banner.md)]

This article explains how to create a vendor for Mexico to support the Declaración Informativa de Operaciones con Terceros (DIOT) declaration and other legal reports in Microsoft Dynamics 365 Finance.

The following procedure uses the MXMF demo company data.

To create a vendor to support the DIOT declaration and other legal reports, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. Select **New**.
1. In the **Name** field, enter the vendor's name.
1. In the **Group** field, select a group for the vendor.
1. Expand or collapse the **Invoice and delivery** section.
1. In the **Company type** field, select an option.
1. In the **RFC number** field, enter the 12 or 13-character Registration for Taxpayers (RFC) number of the vendor.

    > [!NOTE]
    > The RFC number is the tax identification number assigned by tax authorities to a person or corporation. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.  

1. In the **CURP number** field, enter the 18-character Clave Única de Registro de Población (CURP) number of the vendor. If the company type for this vendor is **Legal Person**, this field is required.  
1. In the **State inscription** field, enter a value.
1. In the **Type of vendor** field, select an option.
1. In the **Type of operation** field, select an option. The option you select becomes the default selection when you create purchase transactions for the vendor. For foreign vendors, enter the tax registration ID, the country/region code, and the nationality.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
