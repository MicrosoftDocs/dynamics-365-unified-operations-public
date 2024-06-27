---
title: NT2021.004 – Layout and validation updates in the electronic fiscal document (NF-e)
description: Learn about the updates to the XML layout and validation rules in technical note NT2021.004, including a step-by-step process on enabling technical notes.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: 10.0.30
---

# NT2021.004 – Layout and validation updates in the electronic fiscal document (NF-e)

[!include [banner](../../includes/banner.md)]

This article describes the updates to the XML layout and validation rules that were introduced by technical note NT2021.004 for the generation of electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1. Sign in to your instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
2. Go to **Organization administration** \> **Organizations** \> **Fiscal establishments** \> **Fiscal establishments**.
3. Select the fiscal establishment, and then select **Edit**.
4. On the **NF-e and NFC-e federal** FastTab, in the **NF-e technical notes** section, select **Enable NF-e technical note**.
5. In the **NF-e technical notes** field, select **2021.004 v1.00 technical note**.
6. Select **Save**.

## Scope for version 1.00 of the technical note

This technical note introduced a new tag that is used to send the information about the concessionary act. The tag is applicable only when the agency from the referenced process is SEFAZ (Brazilian tax authority). This technical note also introduced new validations rules to enforce the correct use of the freight information in the XML.

### Updates in the XML

#### New &lt;tpAto&gt; tag

New options are added to the fiscal document source texts to enable the setup of the type of concessionary act, so that the new **&lt;tpAto&gt;** tag can be populated in scenarios where the **Agency** value is **SEFAZ**.

1. Go to **Organization administration** \> **Organizations** \> **Setup** \> **Fiscal document source texts**.
2. Select a fiscal document source text.
3. On the **Referenced process** tab, select **New**.
4. In the **Agency** column, select **SEFAZ**.
5. Enter the number of the referenced process.
6. In the **Type of Concessionary act** field, select the type of concessionary act, as defined in the technical note.
7. Select **Save**.

## Scope for version 1.31 of the technical note

### Updates in validation rules

New validation rules are updated during the posting of fiscal documents, to help prevent the following NF-e rejection error codes:

- 847
- 849

During posting of outbound electronic fiscal documents, when the **&lt;tpNF&gt;** tag equals **1** (outgoing):

- If the tax registration ID (base CNPJ) of the transporter equals the tax registration ID (base CNPJ) of the issuer, the freight charges terms must be something other than **Prepaid** (**modFrete** = **0**). Otherwise, validation rule X04-50 is violated.
- If the tax registration ID (base CNPJ) of the transporter equals the tax registration ID (base CNPJ) of the receiver, the freight charges terms must be something other than **Collect** (**modFrete** = **1**). Otherwise, validation rule X04-90 is violated.

During posting of inbound electronic fiscal documents, when the **&lt;tpNF&gt;** tag equals **0** (inbound):

- If the tax registration ID (base CNPJ) of the transporter equals the tax registration ID (base CNPJ) of the issuer, the freight charges terms must be something other than **Collect** (**modFrete** = **1**). Otherwise, validation rule X04-100 is violated.
- If the tax registration ID (base CNPJ) of the transporter equals the tax registration ID (base CNPJ) of the receiver, the freight charges terms must be something other than **Prepaid** (**modFrete** = **0**). Otherwise, validation rule X04-60 is violated.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
