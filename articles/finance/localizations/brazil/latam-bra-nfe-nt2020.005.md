---
title: NT2020.005 - Layout and validation updates in the electronic fiscal document (NF-e)
description: Learn about the updates to the XML layout and validation rules in technical note NT2020.005, including an overview on enabling technical notes.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: 8
---

# NT2020.005 – Layout and validation updates in the electronic fiscal document (NF-e)

[!include [banner](../../includes/banner.md)]

This article describes the updates to the XML layout and validation rules that were introduced by technical note NT2020.005 for the generation of electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1. Sign in to your instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
2. Go to **Organization administration** \> **Organizations** \> **Fiscal establishments** \> **Fiscal establishments**.
3. Select the fiscal establishment, and then select **Edit**.
4. On the **NF-e and NFC-e federal** FastTab, in the **NF-e technical notes** section, select **Enable NF-e technical note**.
5. In the **NF-e technical notes** field, select **2020.005 v1.10 technical note** for version 1.10 of the technical note.

## Scope from version 1.00/1.10 of the technical note

The following updates and additions are now available in the scope of the new technical note:

- New options have been added to the **&lt;tpViaTransp&gt;** tag.
- The structure of the &lt;adi&gt; node has been updated.
- New tags have been added to the &lt;ICMS10&gt;, &lt;ICMS70&gt;, and &lt;ICMS90&gt; nodes:

    - &lt;vICMSSTDeson&gt;
    - &lt;motDesICMSST&gt;

- New tags have been added to the &lt;ICMS51&gt; node:

    - &lt;pFCPDif&gt;
    - &lt;vFCPDif&gt;
    - &lt;vFCPEfet&gt;

- Validation rules NA15-20 and NA17-10 during posting of fiscal documents have been updated.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
