---
title: Use the CNPJ validation in Brazil tax reform
description: Learn about CNPJ validation in the Brazilian tax reform for 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 11/19/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use the CNPJ validation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes the CNPJ validation in the Brazilian tax reform for 2026.

The key CNPJ change in Brazil's Tax Reform 2026 is the introduction of an alphanumeric CNPJ format. This format replaces the purely numeric model while keeping the same 14-character length. This update, effective from July 2026, expands the range of available business identifiers and modernizes tax registration systems. Brazil's tax reform introduces two new tax attributes to support the new tax types: CBS, IBS, and the selective tax.

- Format，the first 12 characters of the CNPJ include letters and numbers; the last two characters remain numeric check digits.
- Current validation checks don't require changes for the alphanumeric format.

To support flexible handling of CNPJ formats, the Brazilian tax reform 2026 solution introduces a new configurable system parameter named CnpjFormat.

## Configure the parameter

1. Go to **Organization Administration** \> **Setup** \> **Brazilian parameter** to maintain the parameter.
1. Select **General** page.
1. Checkbox under **CNPJ Validation group**，set the **Allow alphanumeric CNPJ** to be **YES** if necessary after July 2026.
   
> [!NOTE]
> Existing numeric CNPJs remain valid. New registrations use the alphanumeric format starting **July 2026**.
>

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
