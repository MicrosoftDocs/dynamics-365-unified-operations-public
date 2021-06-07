---
# required metadata
title: Cancellation and return of NFC-e
description: This topic gives an overview of the functionality for Cancellation and return of NFC-e for Brazil.
author: v-ankvik
manager: epopov
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 


# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---

# Cancellation and return of NFC-e 

[!include[banner](../includes/banner.md)]

## Introduction

The Commerce functionality for Brazil supports cancellation and return of sales issued with NFC-e. These formats are based on the national technical standards of the electronic fiscal documens: cancellation event and NF-e (model 55) for return. For more information about Electronic Fiscal Document (“Nota Fiscal Eletrônica” - NF-e), see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md).

It is only possible to cancel the NFC-e that is already authorized by the tax authority and if the goods and the consumer are still in the establishment. The maximum deadline for canceling of a NFC-e is up to 30 minutes after the granting of authorization for use. The Return NF-e must be issued after the allowed for the cancellation time ran out.

A NF-e is an electronic fiscal document that is generated and printed to register the return of goods sold to a final consumer. It enables tax and fiscal control from tax authorities, and allows the consumers verifying the validity and authenticity of the received fiscal documents.

This topic explains how to cancel sales within allowed timeframe, and issue NF-es and print Simplified DANFE for model 55 fiscal receipts when completing returns of retail sales on POS.

## Limitations

1. Cancellations and Returns are allowed only for the sales made within the same state, and inter-state operations are prohibited.
1. The cancellation process upon NFC-e authorized by POS terminals from other stores is not supported. Only authorized NFC-e issued by POS terminals within the same store can be cancelled. 
1. The cancellation and return processes with the POS terminal without internet connection or when the tax authority authorization service is down (offline contingency mode) are not supported.
1. Simplified DANFE for model 55 format is the only layout supported for returns.
1. Sales and returns of services are not supported.

## Supported scenarios

### Scenario 1: Make a cancellation of sold goods

1. Sign in to POS.
1. Open **Show journal** form.
1. Find the sale that needs to be cancelled.
1. Click on the **Cancel transaction** button.
1. Fill in a **justification** for the cancellation, and click OK.
1. [Add a named customer or specify customer information manually](latam-bra-customer-information.md).
1. Register payments refund for the transaction, and then finalize the transaction.

### Scenario 2: Make a return of sold goods

1. Sign in to POS.
1. Open **Show journal** form.
1. Find the sale that needs to be returned either fully or partially.
1. Click on the **Return** button, and mark returnable product(s) as needed, and again click on the **Return** button.
1. [Add a named customer or specify customer information manually](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Verify that the information including barcode on the printed Simplified DANFE for model 55 fiscal receipt corresponds to the sale.

## Simplified DANFE for model 55 fiscal receipt

In addition to the [common list of custom fields for DANFE](latam-bra-nfce.md#danfe-fiscal-receipts), Simplified DANFE for model 55 fiscal receipt can include the following custom fields:
- **Barcode (Código de barras)** – You can add a barcode field for Simplified DANFE for model 55 for returns.