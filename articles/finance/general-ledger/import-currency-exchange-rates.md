---
# required metadata

title: Import currency exchange rates
description: This topic provides information about the requirements for importing foreign exchange reference rates that are published by exchange rate providers.
author: EvgenyPopovMBS
manager: AnnBe
ms.date: 03/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ExchangeRateProviderConfiguration
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 261374
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
ms.search.region: Global
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: 10.0.9

---

# Import currency exchange rates

[!include [banner](../includes/banner.md)]

If a legal entity has received invoices in foreign currencies, the foreign currency must be converted into the local currency. This means that up-to-date exchange rates for different currencies are required. This topic provides an overview of the settings and processing required to import foreign exchange reference rates that are published by exchange rate providers, such as the European Central Bank and the Central Bank of Russia.

The following sections describe the flow of information that is used for setting up and processing the import of foreign exchange rates.

## Configure an exchange rate provider
Before you can import exchange rates, you must set up the information that is required by the providers who offer the exchange rates. Use the **Configure exchange rate providers** page to select the exchange rate providers. Some exchange rate providers are included with the demo data in Dynamics 365 Finance. The following table provides descriptions for the controls on this page.

|           |                                                                                                                                                                                                                             |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Field** | **Description**                                                                                                                                                                                                             |
| **Name**  | The name of the exchange rate provider.                                                                                                                                                                                     |
| **Key**   | The unique identifier for each piece of configuration information that is required by the provider. This information is automatically added for each exchange rate provider that you add. |
| **Value** | Information for each key. This information is added for each exchange rate provider that you add.                                                                                         |

## Import currency exchange rates
You can import exchange rates from the exchange rate providers source and add them to the **Currency exchange rates** page. Use the **Import currency exchange rates** page to import the exchange rates. The following table provides descriptions of the fields that are required to successfully complete the import process.

|                                        |                                                                                                                                                                                                                                                                                                                                                                             |
|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Field**                              | **Description**                                                                                                                                                                                                                                                                                                                                                             |
| **Exchange rate type**                 | An exchange rate type.                                                                                                                                                                                                                                                                                                                                                      |
| **Exchange rate provider**             | An exchange rate provider.                                                                                                                                                                                                                                                                                                                                                  |
| **Import as of**                       | This parameter manages whether to import as of the current date or for a specific date range. If you want to use a date range, enter or select the start and end dates.                                                                                                                                                                                                                |
| **Create necessary currency pairs**    | This check box manages the automatic creation of currency pairs, if the currency pairs that are imported do not exist. This option might not be available for some providers.                                                                                                                                                                                               |
| **Override existing exchange rates**   | This check box manages the update of the existing exchange rate for a currency pair when the exchange rate for a specific date already exists. If you do not select this check box, the exchange rate for the specific dates is not imported if another exchange rate already exists.                                                                                       |
| **Prevent import on national holiday** | This check box manages the import of the exchange rate for public holiday's date. For example, if you select this check box and use the European Central Bank as the exchange rate provider, the system will not update the exchange rate on a public holiday that is related to the current legal entity. This option might not be available for some providers. |
| **Rate from the previous day** | This check box is available if you enable **ECB import on the current or previous date** feature on the **Feature management** page. This check box is only available for the provider, *Central Bank of Europe*. Select this check box to import the currency exchange rate that is published by the European Central Bank on the previous working day at approximately 16:00 CET. By default, the check box is selected. Clear this check box to import the currency exchange rate that is published on the same working day.  |
