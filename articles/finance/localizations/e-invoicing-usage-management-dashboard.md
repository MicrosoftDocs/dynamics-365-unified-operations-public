---
# required metadata

title: Usage management dashboard
description: This topic explains how to use the Usage management dashboard to monitor usage of the Electronic Invoicing service and remain compliant.
author: gionoder
ms.date: 05/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Usage management dashboard

[!include [banner](../includes/banner.md)]

The **Usage management** dashboard helps you monitor usage of the Electronic Invoicing service, and therefore helps your organization remain compliant in terms of its monthly usage. Compliance is determined by calculating the submission volume and comparing it with the acquired volume of submissions to identify any deviations between the acquired volume and the used volume.

The dashboard includes the following indicators:

- One cost indicator that you can use to monitor consumption for licensing compliance purposes:

    - Usage per month (exporting direction)

- Three operational indicators that you can use to track usage of the Electronic Invoicing service for management purposes:

    - Usage by feature
    - Usage by environment
    - Usage per month (importing direction)

## Measurement scope

- Unit of measure: 

    The **Usage management** dashboard counts the submission of business documents and imported electronic invoices.

- Organization: 

    Counting is summarized by the tenant ID of your organization, regardless of the number of instances of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or the number of legal entities where the Electronic Invoicing service is enabled.


## Indicator: Usage per month (exporting direction)

This indicator provides details about the electronic invoices that your organization issues during a defined period.

### Counting criteria
- The number of business documents that are submitted from Finance and Supply Chain Management to the Electronic Invoicing service, regardless of number of lines that those business documents contain.
- The number of submitted business documents that are successfully processed by the Electronic Invoicing service. A document is considered successfully processed when the flow of actions that are defined in the feature setup is completed.

> [!NOTE]
> When an electronic invoice is submitted to an external web service, counting is independent of the results of web service processing (accepted, rejected, or schema validation error). If the web service received and responded to the request from the Electronic Invoicing service, the submission is considered a valid counting.

- **Exception:** Business documents aren't counted if they are resubmitted from Finance and Supply Chain Management to the Electronic Invoicing service, such as in the scenarios where a resubmission of the same business document is required to change the status of the electronic invoice. For example, issuance of a Brazilian electronic invoice (fiscal document) is counted as valid, but the cancellation request for it isn't counted.


### Calculation

The calculation of the balance volume is calculated as follows:

Balance volume = Free volume + Purchased volume – Used volume

Where:

- Free volume:
  
    The free monthly invoicing service that the customer receives. It includes a package of 100 business documents that can be submitted to the Electronic Invoicing service. Free volume isn't cumulative, and any remaining balance isn't rolled over to the next period.
  
- Purchased volume:
  
    A package of 1,000 business documents that can be submitted to the Electronic Invoicing service. This package must be acquired for your organization on a monthly basis. Purchased volume isn't cumulative, and any remaining balance isn't rolled over to the next period.
  
- Used volume: 

    The count of business document submissions to the Electronic Invoicing service according to defined criteria.
   
> [!IMPORTANT]
> If your organization plans to exceed the monthly volume of 100 free submissions, purchase the peak volume to ensure that you remain compliant with the Microsoft licensing policy for the Electronic Invoicing service.
>
> Currently, purchased volume must be manually entered, according to the date of acquisition, as multiple packages of 1,000 submissions.

## Indicator: Usage by feature

This indicator shows the usage of electronic invoicing features for issuance of electronic invoices during a defined period.

- Counting criteria:

    Electronic invoices issued by electronic invoicing features.

- Calculation:
  
    Quantity = Total counting of times each electronic invoicing feature service was used

## Indicator: Usage by environment

This indicator shows the usage of electronic invoicing service environments during a defined period.

- Counting criteria:

    Electronic invoices issued by electronic invoicing service environments.

- Calculation:
    
    Quantity = Total counting of times each electronic service environment was used

## Indicator: Usage per month (importing direction)

This indicator shows the volume of importation of electronic invoicing features by Electronic Invoicing service into Finance and Supply Chain Management during a defined period.

- Counting criteria:

    Electronic invoices that are imported into Finance and Supply Chain Management, regardless of the number of lines that those electronic invoices contain.

- Calculation:

    Received = Total counting of imported electronic invoices.

> [!NOTE]
> The **Usage management** dashboard doesn't show monetary amounts. Instead, it shows only the volume of counted submissions and imported documents.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
