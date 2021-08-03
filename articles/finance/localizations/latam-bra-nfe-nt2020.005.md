---
# required metadata

title: NT2020.005 – Layout and validation updates in the Electronic fiscal document (NF-e) 
description: This topic provides informartion about the updates in the XML layout and validation rules of temchincal note NT2020.005.
author: gionoder
ms.date: 08/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: 8.0

---

# NT2020.005 – Layout and validation updates in the Electronic fiscal document (NF-e) 

[!include [banner](../includes/banner.md)]

This topic describes the updates in the XML layout and validation rules introduced by the technical note NT2020.005 in the generation of electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1. Sign in to your instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
2. Go to **Organization administration** > **Organizations** > **Fiscal establishments** > **Fiscal establishments**.
3. Select the fiscal establishment, and then select **Edit**.
4. On the **NF-e and NFC-e federal** FastTab, in the **NF-e technical notes** field group, select **Enable NF-e technical note**.
5. In the **NF-e technical notes** field, select **2020.005 v1.10 technical note** for version 1.10 of the technical note.

## Scope from version 1.00/1.10 of the Technical Note

The following updates and additions are now available in the scope of the new Technical Note. 

- Added new options to **&lt;tpViaTransp&gt;** tag
- Updated the structure of the node &lt;adi&gt;
- Added new tags to the nodes &lt;ICMS10&gt;, &lt;ICMS70&gt; and &lt;ICMS90&gt;:

    - &lt;vICMSSTDeson&gt;
    - &lt;motDesICMSST&gt;

- Added new tags to the node &lt;ICMS51&gt;:

    - &lt;pFCPDif&gt;
    - &lt;vFCPDif&gt;
    - &lt;vFCPEfet&gt;

- Updated the validation rules NA15-20 and NA17-10 during posting of fiscal documents.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
