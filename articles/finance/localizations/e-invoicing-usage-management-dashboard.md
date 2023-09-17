---
title: Usage management dashboard
description: This article explains how to use the Usage management dashboard to monitor usage of the Electronic Invoicing service and remain compliant.
author: gionoder
ms.date: 06/02/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
ms.assetid: 
ms.search.form: 
---

# Usage management dashboard

[!include [banner](../includes/banner.md)]

The **Usage management** dashboard helps you monitor usage of the Electronic Invoicing service, and therefore helps your organization remain compliant in terms of its monthly usage. Compliance is determined by calculating the submission volume and comparing it with the acquired volume of submissions to identify any deviations between the acquired volume and the used volume.

The dashboard includes the following indicators:

- One cost indicator that you can use to monitor consumption for licensing compliance purposes:

    - Usage per month (export)

- Three operational indicators that you can use to track usage of the Electronic Invoicing service for management purposes:

    - Usage by feature
    - Usage by environment
    - Usage per month (import)

## Measurement scope

- Unit of measure: 

    The **Usage management** dashboard counts the submission of business documents and imported electronic invoices.

- Organization: 

    Counting is summarized by the tenant ID of your organization, regardless of the number of instances of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or the number of legal entities where the Electronic Invoicing service is enabled.


## Indicator: Usage per month (export)

This indicator provides details about the electronic invoices that your organization issues during a defined period.

### Scope
- The number of business documents that are submitted from Finance and Supply Chain Management to the Electronic Invoicing service, regardless of number of lines that those business documents contain.
- The number of submitted business documents that are successfully processed by the Electronic Invoicing service. A document is considered successfully processed when the flow of actions that are defined in the feature setup is completed.

> [!NOTE]
> When an electronic invoice is submitted to an external web service, counting is independent of the results of web service processing (accepted, rejected, or schema validation error). If the web service received and responded to the request from the Electronic Invoicing service, the submission is considered a valid counting.

- **Exception:** Business documents aren't counted if they are resubmitted from Finance and Supply Chain Management to the Electronic Invoicing service, such as in the scenarios where a resubmission of the same business document is required to change the status of the electronic invoice. For example, issuance of a Brazilian electronic invoice (fiscal document) is counted as valid, but the cancellation request for it isn't counted.


### Calculation

The calculation of the balance is calculated as follows:

Balance = Free + Purchased – Used

Where:

- Free:
  
    A free volume of business documents the customer can submit per month. It includes a package of 100 business documents that can be submitted to the Electronic Invoicing service. Free volume isn't cumulative, and any remaining balance isn't rolled over to the next period.
  
- Purchased:
  
    A package of 1,000 business documents that can be submitted to the Electronic Invoicing service. This package must be acquired for your organization on a monthly basis. Purchased volume isn't cumulative, and any remaining balance isn't rolled over to the next period.
  
- Used: 

    The count of business document submissions to the Electronic Invoicing service according to defined criteria.
   
> [!IMPORTANT]
> If your organization plans to exceed the monthly volume of 100 free submissions, purchase the peak volume to ensure that you remain compliant with the Microsoft licensing policy for the Electronic Invoicing service.
>
> Currently, purchased volume must be manually entered, according to the date of acquisition, as multiple packages of 1,000 submissions.

## Indicator: Usage by feature

This indicator shows the usage of electronic invoicing features for issuance of electronic invoices during a defined period.

- Calculation:
  
    Used = The count of how many times each electronic invoicing feature was used during the submission of business documents to the Electronic Invoicing service.

## Indicator: Usage by environment

This indicator shows the usage of electronic invoicing service environments during a defined period.

- Calculation:
    
    Used = The count of how many times each electronic invoicing service environment was used during the submission of business documents to the Electronic Invoicing service.

## Indicator: Usage per month (import)

This indicator shows the volume of importation of electronic invoices by Electronic Invoicing service into Finance and Supply Chain Management during a defined period.

- Scope:

    Electronic invoices that are imported into Finance and Supply Chain Management, regardless of the number of lines that those electronic invoices contain.

- Calculation:

    Received = The count of imported electronic invoices into Finance and Supply Chain Management.

## Functions
### Purchase

On the **Usage per month (export)** tab, select **Purchase** to manually register the amount of acquired submissions.

For a given date, select **New** and enter the number of **Packages** acquired for on that date.

The **Quantity** is calculated as:

Quantity = Packages * 1.000

The calculated **Quantity** reflects in the **Purchased** from the indicator **Usage per month (export)**.

### Update

On the Action Pane, select **Update** to refresh the calculation and update the data shown on the page and in the chart.

### Reset history data

On the Action Pane, select **Reset history data** to refresh the database from where the indicators are calculated.




> [!NOTE]
> The **Usage management** dashboard doesn't show monetary amounts. Instead, it shows only the volume of counted submissions and imported documents.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
