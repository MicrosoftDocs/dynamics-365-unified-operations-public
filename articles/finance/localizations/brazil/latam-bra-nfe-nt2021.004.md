---
title: NT2021.004 – Layout and validation updates in the electronic fiscal document (NF-e)
description: Learn about the updates to the XML layout and validation rules in technical note NT2021.004, including a step-by-step process on enabling technical notes.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2021-02-05
---

# NT2021.004 – Layout and validation updates in the electronic fiscal document (NF-e)

[!include [banner](../../includes/banner.md)]

This article describes the updates to the XML layout and validation rules that technical note NT2021.004 introduced for generating electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1. Sign in to your instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
1. Go to **Organization administration** > **Organizations** > **Fiscal establishments** > **Fiscal establishments**.
1. Select the fiscal establishment, and then select **Edit**.
1. On the **NF-e and NFC-e federal** tab, in the **NF-e technical notes** section, select **Enable NF-e technical note**.
1. In the **NF-e technical notes** field, select **2021.004 v1.00 technical note**.
1. Select **Save**.

## Scope for version 1.00 of the technical note

This technical note introduced a new tag that you use to send the information about the concessionary act. The tag is applicable only when the agency from the referenced process is SEFAZ (Brazilian tax authority). This technical note also introduced new validation rules to enforce the correct use of the freight information in the XML.

### Updates in the XML

#### New &lt;tpAto&gt; tag

The fiscal document source texts include new options for setting up the type of concessionary act. Use these options to populate the new **&lt;tpAto&gt;** tag in scenarios where the **Agency** value is **SEFAZ**.

1. Go to **Organization administration** > **Organizations** > **Setup** > **Fiscal document source texts**.
1. Select a fiscal document source text.
1. On the **Referenced process** tab, select **New**.
1. In the **Agency** column, select **SEFAZ**.
1. Enter the number of the referenced process.
1. In the **Type of Concessionary act** field, select the type of concessionary act, as defined in the technical note.
1. Select **Save**.

## Scope for version 1.31 of the technical note

### Updates in validation rules

New validation rules are active during the posting of fiscal documents. These rules help prevent the following NF-e rejection error codes:

- 847
- 849

During posting of outbound electronic fiscal documents, when the **&lt;tpNF&gt;** tag equals **1** (outgoing):

- If the tax registration ID (base CNPJ) of the transporter matches the tax registration ID (base CNPJ) of the issuer, the freight charges terms must be something other than **Prepaid** (**modFrete** = **0**). Otherwise, validation rule X04-50 is violated.
- If the tax registration ID (base CNPJ) of the transporter matches the tax registration ID (base CNPJ) of the receiver, the freight charges terms must be something other than **Collect** (**modFrete** = **1**). Otherwise, validation rule X04-90 is violated.

During posting of inbound electronic fiscal documents, when the **&lt;tpNF&gt;** tag equals **0** (inbound):

- If the tax registration ID (base CNPJ) of the transporter matches the tax registration ID (base CNPJ) of the issuer, the freight charges terms must be something other than **Collect** (**modFrete** = **1**). Otherwise, validation rule X04-100 is violated.
- If the tax registration ID (base CNPJ) of the transporter matches the tax registration ID (base CNPJ) of the receiver, the freight charges terms must be something other than **Prepaid** (**modFrete** = **0**). Otherwise, validation rule X04-60 is violated.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
