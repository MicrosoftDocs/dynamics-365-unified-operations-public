---
title: MX-00010 Enter tax registration IDs for Mexican legal entities
description: Learn how to enter tax registration IDs for Mexican legal entities in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: OMLegalEntity, OMNewLegalEntity
---

# MX-00010 Enter tax registration IDs for Mexican legal entities

[!include [banner](../../includes/banner.md)]

This article explains how to enter tax registration IDs for Mexican legal entities in Microsoft Dynamics 365 Finance.

Legal financial documents such as tax declarations or electronic invoices that are submitted to the tax authorities in Mexico must contain different types of tax registration IDs and other related information. 

The following procedure provides all of the necessary steps to complete the information about registration IDs for Mexican legal entities.

To enter tax registration IDs for Mexican legal entities, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Select **New**. If you have already created your Mexican legal entity, you can edit an existing legal entity instead of creating a new one.  
1. In the **Name** field, enter a value.
1. In the **Company** field, enter a value.
1. In the **Country/region** field, select the country/region code.
1. Select **OK**.
1. Expand or collapse the **Registration numbers** section.
8. In the **Company type** field, select an option.
9. In the **RFC number** field, enter the 12-character Federal Registration for Taxpayers (RFC) number of the legal entity.

    > [!NOTE]
    > The RFC number is the tax identification number assigned by tax authorities to a person or a corporation. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.  

1. In the **CURP number** field, Enter the 18-character Clave Única de Registro de Población (CURP) number of the legal entity. This field a mandatory when the **RFC** field is empty.

    > [!NOTE]
    > The CURP number is the tax identification number assigned by the tax authorities to a person. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.   

1. In the **State inscription** field, enter a value.
1. In the **Legal representative** field, enter a value.
1. In the **Legal representative RFC** field, enter the 12-character RFC number of the legal entity representative. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.  
1. In the **Legal representative CURP** field, Enter the 12-character CURP number of the legal entity representative. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
