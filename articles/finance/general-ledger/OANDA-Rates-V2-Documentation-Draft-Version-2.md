---
# required metadata

title: OANDA Rates provider (preview)
description: The (Preview) OANDA Rates V2 provider lets you import real-time exchange rates, configure multiple OANDA data sets, and select from a wider range of quote types in Dynamics 365 Finance.
author: courtneicokerdickens-collab
ms.author: courtneic
ms.date: 09/29/2026
ms.topic: concept-article
ms.reviewer: twheeloc 

---

# OANDA Rates V2 provider (preview)

The OANDA Rates V2 provider (preview) lets you import real-time exchange rates, configure multiple OANDA data sets, and select from a wider range of quote types in Dynamics 365 Finance.

## Configure the provider and import rates

Contact OANDA directly to obtain an API key that supports the V2 provider and confirm access to the data sets you plan to use.

To configure the provider, follow these steps:

1. On the **Configure exchange rate providers** page, add **(Preview) OANDA Rates V2**.
1. Enter the API key.  
1. Select the required data sets in the **Data set configuration** field.
1. On the **Import currency exchange rates** page, select the exchange rate type and **(Preview) OANDA Rates V2** as the provider. 
1. Select the data set, quote type, and import date option.

### Import real-time exchange rates

You can import the latest available spot exchange rates from OANDA when an import runs. This feature supports business processes that require a current exchange rate. Select **Spot bid**, **Spot ask**, or **Spot midpoint** as the quote type and use **Current time** as the import date option.

### Use multiple subscribed data sets

You can configure multiple data sets from your OANDA subscription, then select the data set to use for each import. If you need different exchange rate sources for different legal entities or business processes, such as rates from different central banks, you can choose from the configured data sets without repeatedly changing the shared provider configuration.

### Choose from a wider range of quote types

You can import opening and closing bid, ask, and midpoint quotes, as well as high and low midpoint quotes. For example, if your business process requires a closing rate, you can select the appropriate closing quote when importing exchange rates. You select the quote type for each import. This feature lets you use different quote types for different business processes without changing the shared provider configuration.

Confirm with OANDA which quotes are available for the data sets in your subscription.

