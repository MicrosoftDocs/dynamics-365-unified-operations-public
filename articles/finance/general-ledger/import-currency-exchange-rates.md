---
title: Import currency exchange rates
description: Learn about the requirements for importing foreign exchange reference rates that are published by exchange rate providers.
author: twheeloc 
ms.author: twheeloc
ms.topic: article
ms.date: 01/12/2026
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2020-02-03
ms.search.form: ExchangeRateProviderConfiguration
ms.dyn365.ops.version: 10.0.9
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Import currency exchange rates

[!include [banner](../includes/banner.md)]

If a legal entity receives invoices in foreign currencies, you must convert the foreign currency into the local currency. This conversion requires up-to-date exchange rates for different currencies. This article provides an overview of the settings and processing required to import foreign exchange reference rates that exchange rate providers publish, such as OANDA Rates®, the European Central Bank, the Central Bank of Russia, and the Central Bank of the Republic of Türkiye (CBRT).

> [!NOTE]
> Beginning in Dynamics 365 Finance version 10.0.41, a new rate provider option, **OANDA Central Banks**, is available with an upgraded license key from OANDA.

The following sections describe the flow of information that's used for setting up and processing the import of foreign exchange rates.

## Configure an exchange rate provider

Before you can import exchange rates, set up the information that the providers who offer the exchange rates require. Use the **Configure exchange rate providers** page to select the exchange rate providers. Some exchange rate providers are included with the demo data in Dynamics 365 Finance. The following table provides descriptions for the controls on this page.

| Field | Description                   |
|-----------|-----------------------------------|
| **Name**  | The name of the exchange rate provider.                                                                                                          |
| **Key**   | The **Key** column is a unique identifier for each piece of configuration information that the provider requires. This information is automatically added for each exchange rate provider that you add. |
| **Value** | The **Value** column is the required information for each key. This information is added for each exchange rate provider that you add. |

You must configure specific information, depending on the provider that you select.

### OANDA

OANDA provider options require that you fill in the API key values that you receive directly from OANDA. The *OANDA Central Banks* provider lets you select a specific central bank value in the **Data set key** field.

### Central Bank of the Republic of Türkiye

The Central Bank of the Republic of Türkiye (CBRT) publishes indicative exchange rates at 3:30 PM local time (Türkiye) on business days. These rates take effect on the next business day. Therefore, you should import exchange rates from CBRT daily.

CBRT doesn't publish exchange rate information on weekends or official public holidays in Türkiye.

The CBRT provider configuration supports importing exchange rates for the following exchange rate types:

- Banknote buying
- Banknote selling
- Forex buying
- Forex selling

If you set the **Cross rate** and **Informative exchange rates** keys to **Yes**, you import cross rates and informative exchange rates together with standard currency exchange rates.
Cross rates and informative exchange rates use the same exchange rate type that you select on the **Import currency exchange rates** dialog page.

> [!NOTE]
> If you don't import cross rates, an error message is generated during ledger posting. To ensure that cross rates are correctly imported, the value of the **Cross rate** key is set to **Yes** by default in the configuration of the CBRT provider.

| **Key** | **Value** |
| ------ | -------------------------------------------------------------------------------|
| **Banknote buying** | Specifies the exchange rate type for *Banknote buying*. |
| **Banknote selling** | Specifies the exchange rate type for *Banknote selling*. |
| **Cross rate** | When set to **Yes**, imports cross rates in addition to standard exchange rates. |
| **Decimal places** | Specifies the number of decimal places for the exchange rate. The default value is *4*. |
| **Forex buying** | Specifies the exchange rate type for *Forex buying*. |
| **Forex selling** | Specifies the exchange rate type for *Forex selling*. |
| **Informative exchange rates** | When set to **Yes**, imports informative exchange rates in addition to standard exchange rates. |
| **ServiceInformativeUrl** | Specifies the service URL that is used to import informative exchange rates from CBRT. |
| **ServiceOnDateUrl** | Specifies the service URL that is used to import exchange rates from CBRT. |

## Import currency exchange rates

You can import exchange rates from the exchange rate provider's source and add them to the **Currency exchange rates** page. Use the **Import currency exchange rates** page to import the exchange rates. The following table provides descriptions of the fields that are required to successfully complete the import process.

| Field | Description                           |
|-----------|-----------------------------------|
| **Exchange rate type**                 | An exchange rate type.     |
| **Exchange rate provider**             | An exchange rate provider.      |
| **Import as of**                       | This parameter manages whether to import as of the current date or for a specific date range. If you want to use a date range, enter or select the start and end dates.  |
| **Create necessary currency pairs**    | This checkbox manages the automatic creation of currency pairs if the currency pairs that you import don't exist. This option might not be available for some providers.                |
| **Override existing exchange rates**   | This checkbox manages the update of the existing exchange rate for a currency pair when the exchange rate for a specific date already exists. If you don't select this checkbox, the exchange rate for the specific dates isn't imported if another exchange rate already exists.                                                                                       |
| **Prevent import on national holiday** | This checkbox manages the import of the exchange rate for public holiday's date. For example, if you select this checkbox and use the European Central Bank as the exchange rate provider, the system doesn't update the exchange rate on a public holiday that is related to the current legal entity. This option might not be available for some providers. |
| **Rate from the previous day** | This checkbox is only available for the provider, *Central Bank of Europe*. Select this checkbox to import the currency exchange rate that the European Central Bank publishes on the previous working day at approximately 16:00 CET. By default, the checkbox is selected. Clear this checkbox to import the currency exchange rate that the European Central Bank publishes on the same working day. This option might not be available for some providers.  

> [!NOTE]
> The import process loads the rates from the previous day and records them for the current day.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
