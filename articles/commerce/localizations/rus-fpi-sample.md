---
# required metadata

title: Fiscal printer integration sample for Russia
description: This topic provides an overview of the fiscal integration sample for Italy.
author: EvgenyPopovMBS
manager: annbe
ms.date: 08/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-8-2
ms.dyn365.ops.version: 10.0.21

---
# Fiscal printer integration sample for Russia

[!include [banner](../includes/banner.md)]

## Introduction

The Dynamics 365 Commerce functionality for Russia includes a sample integration of the point of sale (POS) with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and supports the application programming interface (API) of fiscal printers from [ATOL](http://integration.atol.ru/). The sample enables communication with a fiscal printer that is connected via a communication (COM) port by using a native software driver. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from ATOL. For information about how to get the fiscal printer and operate it, contact [ATOL](https://www.atol.ru/).

> [!NOTE]
> This sample code is intended to be used with certain cash register software from ATOL, a third party. You are responsible for your use of ATOL services, and any use is subject to a separate [end user agreement](http://integration.atol.ru/eula/) between you and ATOL. You understand that the data handling, compliance and security standards of ATOL may
not be the same as Microsoft Dynamics 365 Commerce. Your privacy is important to us. To learn more read our [Privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Scenarios

The following scenarios are covered by the fiscal printer integration sample for Russia:

- Sales scenarios:

    - Print a fiscal receipt for cash-and-carry sales and returns.
    - Capture a response from the fiscal printer, and store it in the channel database.
    - Taxes:

        - Map the tax rates to the fiscal printer's tax types.
        - Transfer mapped tax data to the fiscal printer.

    - Payments:

        - Map the store's payment methods to the fiscal printer's payment types.
        - Print payments on a fiscal receipt.
        - Print change information.

    - Print line discount information.
    - Send the [customer information](rus-customer-information.md) that is specified for a sales transaction with a fiscal receipt. An example of this information is the customer's email address.

- Daily reports (fiscal X and fiscal Z reports).
- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal printer isn't connected, isn't ready, or isn't responding, the printer is out of paper, or there is a paper jam.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal printer before a new sales transaction is opened or a sales transaction is finalized.

### Limitations of the sample

- The fiscal printer supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.
- **Customer orders**
- **Rounding in case of discounts**
- **Petty cash operations**
- Daily reports (fiscal X and fiscal Z) are printed by using the fiscal printer's embedded format.
- The fiscal printer doesn't support mixed transactions. The **Prohibit mixing sales and returns in one receipt** option should be set to **Yes** in POS functionality profiles.
