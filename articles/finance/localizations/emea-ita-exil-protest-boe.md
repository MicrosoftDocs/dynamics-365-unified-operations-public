---
# required metadata

title: Bills of exchange protest import 
description: This topic explains how to set up and import Protest information from an electronic Bill of exchange protest file.
author: anasyash
ms.date: 04/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.10

---

# Bills of exchange protest import 

[!include [banner](../includes/banner.md)]

This topic explains how to set up and import Protest information from the electronic Bill of exchange protest file received from the bank.

## Prerequisites

Before you can use the Bill of exchange protest import functionality, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The Protest handling for bills of exchange feature must be turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Import Electronic reporting configurations

The Electronic Reporting configuration, **RIBA bill of exchange protest (IT)**, must be imported from LCS before you can use it. After you import the configuration, the corresponding **Payment model** and **Payment model mapping to destination RIBA configurations** will be imported automatically.

## Set up method of payment

On the **Method of payments – customers** page, enable the **Generic electronic import format** parameter, and then select **RIBA bill of exchange protest (IT)**. 

## Import protest information from an electronic file

1. To import the file, create a **Protest bill of exchange** journal, and then select **Journal lines**.
2. Select **Functions** \> **Import protest**.
3. In the dialog box, select the method of payment for the protest import, and then attach the file. The journal lines are created based on information in the file.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
