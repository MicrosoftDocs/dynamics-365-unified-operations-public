---
title: Use the CNPJ validation in Brazil tax reform
description: Learn about CNPJ validation in the Brazilian tax reform for 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use the CNPJ validation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes the CNPJ validation in the Brazilian tax reform for 2026.

The key CNPJ change in Brazil's Tax Reform 2026 is the introduction of an alphanumeric CNPJ format, replacing the purely numeric model while keeping the same 14-character length. This update, effective from July 2026, is designed to expand the range of available business identifiers and modernize tax registration systems.Brazil's tax reform introduces two new tax attributes to support the new tax types: CBS, IBS, and the selective tax.

- Format，the first 12 characters of the CNPJ will include letters and numbers; the last 2 remain numeric check digits.
- Current validation checks do not require changes for the alphanumeric format.

To support flexible handling of CNPJ formats, a new configurable system parameter named CnpjFormat will be introduced in Brazilian tax reform 2026 solution.

## Configure the parameter

1. Go to **Organiaztion Adminstration** \> **Setup** \> **Brazilian parameter** to maintain the parameter.
1. Select **General** oage.
2. Checkbox under **CNPJ Validation group**，set the **Allow alphanumeric CNPJ** to be **YES** if required after July,2026.
   
> [!Note]
> Existing numeric CNPJs remain valid; new registrations will use the alphanumeric format starting **July 2026**.
> 

