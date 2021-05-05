---
# required metadata

title: Usage management dashboard
description: This topic explains how to use the usage management dashboard to monitor the usage of Electronic Invoicing and remain compliant.
author: gionoder
ms.date: 05/05/2021
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

The usage management dashboard helps you monitor the usage of the Electronic Invoicing service and helps your organiazation remain compliant in monthly usage. Compliance is determined by calculating the submission volume and comparing it with the acquired volume of submissions, to identify deviations between the acquired volume and used volume.

The dashboard includes:

   - One cost Key Process Indicator (KPI), from which you can monitor the consumption for licensing compliance purposes:

        - KPI: Usage per month (exporting direction)

   - Three operational KPIs from which you can track the usage of the Electronic Invoicing service, for management purposes:

        - KPI: Usage by feature
        - KPI: Usage by environment
        - KPI: Usage per month (importing direction)

## Measurement scope

### Unit of measure

The Usage management dashboard counts business documents and electronic invoices.

### Organization

Counting is consolidated by the tenant ID of your organization, regardless of the number of instances of Dynamics 365 Finance, Dynamics 365 Supply Chain Management, or the number of Legal entities that have the Electronic Invoicing service enabled.

## KPI: Usage per month (export)

This KPI provides details about the electronic invoices your organization issues per month.

###  Usage per month: Counting criteria

- The number of submitted business documents, from Finance and Supply Chain Management to the Electronic Invoicing service, independent of number of lines they contain.
- The number of submitted business documents that are successfully processed by the Electronic Invoicing service. Successfully processed means the completed flow of actions that are defined in the feature setup.

> [!NOTE]
> When an electronic invoice is submitted to an external web service, counting is independent of the web service processing (accepted, rejected, or schema validation error) results. If the web services received and responded to the Electronic Invoicing service request, the submission is considered a valid counting.

###  Usage per month: Counting exception criteria

Business documents that are resubmitted from Finance and Supply Chain Management to the Electronic Invoicing service and that require changes in the state or status of the electronic invoice life cycle are not counted. For example, issuing a Brazilian electronic invoice (fiscal document) is counted as valid, but its cancellation request isn't counted.

###  Usage per month: Direction

Export or issuing of electronic invoices.

## KPI results calculation

The calculation of the KPI results from the components:

   - Free volume
   - Purchased volume
   - Used volume
   - Balance volume

### Free volume

Free volume is a free monthly invoicing service that the customer recieves, which includes a package of 100 business documents that can be submitted to the Electronic Invoicing service. Free volume isn't cumulative and any remaining balance isn't rolled over into the next period.

### Purchased volume

Purchased volume is a package of 1,000 business documents that can be submitted to the Electronic Invoicing service. This package must be acquired for your organization on a monthly basis. The Purchased volume isn't cumulative and any remaining balance isn't rolled over into the next period.

### Used volume

Used volume is the counting of business document submissions to the Electronic Invoicing service according to specified criteria.

### Balance volume

Balance volume is the result of the balance of business document submissions to the Electronic Invoicing service. For a given month, the formula for calculation of the Balance volume is:

   Balance volume = Free volume + Purchased volume - Used volume

> [!IMPORTANT]
> If your organization plans to exceed the monthly volume of 100 free submissions, purchase the peak volume to stay compliant with the Microsoft licensing policy for the Electronic Invoicing service.
>
> Currently, the Purchased volume must be entered manually, per the date of acquisition, as multiple packages of 1000 submissions.

## KPI: Usage by feature 

This KPI breaks down the usage of the electronic invoicing features deployed by your organization to the Electronic Invoicing service. This KPI shows the used electronic invoicing features for submissions during a defined period.

### Usage by feature: Counting criteria

The same as for KPI Usage per month (export).

### Usage by feature: Direction

The same as for KPI Usage per month (export).

### Usage by feature: calculation

The Used volume counts the submissions of business documents to the Electronic Invoicing service grouped by the processing of the electronic invoicing feature.

## KPI: Usage by environment

This KPI breaks down the usage of the electronic invoicing environments deployed by your organization to the Electronic Invoicing service. This KPI shows which electronic invoicing environment is used during a defined period.

### Usage by environment: Counting criteria

The same as for KPI Usage per month (export).

### Usage by environment: Direction

The same as for KPI Usage per month (export).

### Usage by environment: Calculation

Used volume is the counting of business document submissions to the Electronic Invoicing service grouped by processing from electronic invoicing environments.

## KPI: Usage per month (import)

This KPI provides details about the electronic invoices your organization receives per month.

### Usage per month: Counting criteria

The number of electronic invoices that are imported to Finance and Supply Chain Management, independent of the number of lines they contain.

### Usage per month: Direction

Import or receipt of electronic invoices.

### Usage per month: Calculation

Received volume is the sum of electronic invoices that are imported to Finance and Supply Chain Management per the defined criteria.


> [!NOTE]
> The Usage management dashboard doesn't show monetized amounts. Instead, only the volume of counted submissions and imported documents are shown.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
