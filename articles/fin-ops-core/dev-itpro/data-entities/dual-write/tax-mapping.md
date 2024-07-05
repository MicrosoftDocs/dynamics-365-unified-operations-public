---
title: Integrated tax
description: Learn about the integration of tax data between finance and operations and Dataverse, including a table that outlines various templates.
author: josaw
ms.author: josaw
ms.topic: article
ms.date: 09/06/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2019-07-15
---

# Integrated tax

[!include [banner](../../includes/banner.md)]



Tax setup data defines the setup for both indirect taxes (VAT, GST, Sales tax) and withholding tax. It describes the tax calculation rule, tax rate, tax accounting, settlement, and other concepts.

## Templates

Tax data includes a collection of table maps that work together during data interaction, as shown in the following table.

| Finance and operations apps | Customer engagement apps | Description |
|-----------------------------|-----------------------------------|-------------|
[Item sales tax group](mapping-reference.md#196) | msdyn_taxitemgroups | |
[Sales tax authorities](mapping-reference.md#193) | msdyn_taxauthorities | |
[Sales tax exempt code entity CDS](mapping-reference.md#194) | msdyn_taxexemptcodes | |
[Sales tax groups](mapping-reference.md#195) | msdyn_taxgroups | |
[Sales tax ledger posting groups V2](mapping-reference.md#197) | msdyn_taxpostinggroups | |
[Withholding tax codes](mapping-reference.md#210) | msdyn_withholdingtaxcodes | |
[Withholding tax groups](mapping-reference.md#211) | msdyn_withholdingtaxgroups | |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

