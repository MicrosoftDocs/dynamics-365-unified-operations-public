---
# required metadata

title: Usage management dashboard
description: This topic explains how to use the Usage management dashboard to monitor usage of the Electronic Invoicing service and remain compliant.
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

The **Usage management** dashboard helps you monitor usage of the Electronic Invoicing service, and therefore helps your organization remain compliant in terms of its monthly usage. Compliance is determined by calculating the submission volume and comparing it with the acquired volume of submissions to identify any deviations between the acquired volume and the used volume.

The dashboard includes the following key process indicators (KPI):

- One cost KPI that you can use to monitor consumption for licensing compliance purposes:

    - KPI: Usage per month (exporting direction)

- Three operational KPIs that you can use to track usage of the Electronic Invoicing service for management purposes:

    - KPI: Usage by feature
    - KPI: Usage by environment
    - KPI: Usage per month (importing direction)

## Measurement scope

### Unit of measure

The **Usage management** dashboard counts business documents and electronic invoices.

### Organization

Counting is consolidated by the tenant ID of your organization, regardless of the number of instances of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or the number of legal entities where the Electronic Invoicing service is enabled.

## KPI: Usage per month (exporting direction)

This KPI provides details about the electronic invoices that your organization issues each month.

### Counting criteria

- The number of business documents that are submitted from Finance and Supply Chain Management to the Electronic Invoicing service, regardless of number of lines that those business documents contain.
- The number of submitted business documents that are successfully processed by the Electronic Invoicing service. A document is considered successfully processed when the flow of actions that are defined in the feature setup is completed.

> [!NOTE]
> When an electronic invoice is submitted to an external web service, counting is independent of the results of web service processing (accepted, rejected, or schema validation error). If the web service received and responded to the request from the Electronic Invoicing service, the submission is considered a valid counting.

### Counting exception criteria

Business documents aren't counted if they are resubmitted from Finance and Supply Chain Management to the Electronic Invoicing service, and if they require changes to the state or status of the electronic invoice life cycle. For example, issuance of a Brazilian electronic invoice (fiscal document) is counted as valid, but the cancellation request for it isn't counted.

### Direction

Export or issuance of electronic invoices.

## Calculation of KPI results

The calculation of KPI results uses the following components:

- Free volume
- Purchased volume
- Used volume
- Balance volume

### Free volume

Free volume is a free monthly invoicing service that the customer receives. It includes a package of 100 business documents that can be submitted to the Electronic Invoicing service. Free volume isn't cumulative, and any remaining balance isn't rolled over to the next period.

### Purchased volume

Purchased volume is a package of 1,000 business documents that can be submitted to the Electronic Invoicing service. This package must be acquired for your organization on a monthly basis. Purchased volume isn't cumulative, and any remaining balance isn't rolled over to the next period.

### Used volume

Used volume is the count of business document submissions to the Electronic Invoicing service according to defined criteria.

### Balance volume

Balance volume is the result of the balance of business document submissions to the Electronic Invoicing service. For a given month, the following formula is used to calculate the balance volume:

Balance volume = Free volume + Purchased volume – Used volume

> [!IMPORTANT]
> If your organization plans to exceed the monthly volume of 100 free submissions, purchase the peak volume to ensure that you remain compliant with the Microsoft licensing policy for the Electronic Invoicing service.
>
> Currently, purchased volume must be manually entered, according to the date of acquisition, as multiple packages of 1,000 submissions.

## KPI: Usage by feature

This KPI breaks down the usage of the electronic invoicing features that your organization deployed to the Electronic Invoicing service. It shows which electronic invoicing features are used for submissions during a defined period.

### Counting criteria

The same as for KPI: Usage per month (exporting direction).

### Direction

The same as for KPI: Usage per month (exporting direction).

### Calculation

Used volume is the count of business document submissions to the Electronic Invoicing service, grouped by the processing of an electronic invoicing feature.

## KPI: Usage by environment

This KPI breaks down the usage of the electronic invoicing environments that your organization deployed to the Electronic Invoicing service. It shows which electronic invoicing environment is used during a defined period.

### Counting criteria

The same as for KPI: Usage per month (exporting direction).

### Direction

The same as for KPI: Usage per month (exporting direction).

### Calculation

Used volume is the count of business document submissions to the Electronic Invoicing service, grouped by the processing from an electronic invoicing environment.

## KPI: Usage per month (importing direction)

This KPI provides details about the electronic invoices that your organization receives each month.

### Counting criteria

The number of electronic invoices that are imported into Finance and Supply Chain Management, regardless of the number of lines that those electronic invoices contain.

### Direction

Import or receipt of electronic invoices.

### Calculation

Received volume is the number of electronic invoices that are imported into Finance and Supply Chain Management according to defined criteria.

> [!NOTE]
> The **Usage management** dashboard doesn't show monetized amounts. Instead, it shows only the volume of counted submissions and imported documents.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
