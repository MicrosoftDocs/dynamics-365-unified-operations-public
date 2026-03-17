---
title: Usage management dashboard
description: Learn how to use the Usage management dashboard to monitor usage of the Electronic Invoicing service and remain compliant.
author: gionoder
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-07-08
ms.custom: 
  - bap-template
---

# Usage management dashboard

[!include [banner](../../includes/banner.md)]

Use the **Usage management** dashboard to monitor your usage of the Electronic Invoicing service. This dashboard helps your organization stay compliant with monthly usage requirements. It calculates compliance by comparing your submission volume with your acquired volume of submissions.

The dashboard includes the following indicators:

- One cost indicator to monitor consumption for licensing compliance:

  - Usage per month (export)

- Three operational indicators to track usage of the Electronic Invoicing service for management purposes:

  - Usage by feature
  - Usage by environment
  - Usage per month (import)

## Measurement scope

- Unit of measure:

    The **Usage management** dashboard counts the submission of business documents and imported electronic invoices.

- Organization:

    The dashboard summarizes counts by the tenant ID of your organization, regardless of the number of instances of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or the number of legal entities where you enable the Electronic Invoicing service.

## Indicator: Usage per month (export)

This indicator shows details about the electronic invoices that your organization issues during a defined period.

### Scope

- The number of business documents that Finance and Supply Chain Management submits to the Electronic Invoicing service, regardless of the number of lines that those business documents contain.
- The number of submitted business documents that the Electronic Invoicing service processes successfully. A document is considered successfully processed when the flow of actions defined in the feature setup is completed.

> [!NOTE]
> When you submit an electronic invoice to an external web service, counting is independent of the results of web service processing (accepted, rejected, or schema validation error). If the web service receives and responds to the request from the Electronic Invoicing service, the submission is considered a valid counting.

- **Exception:** The system doesn't count business documents if Finance and Supply Chain Management resubmits them to the Electronic Invoicing service. This exception applies to scenarios where you need to resubmit the same business document to change the status of the electronic invoice. For example, the system counts the issuance of a Brazilian electronic invoice (fiscal document) as valid, but it doesn't count the cancellation request for it.

### Calculation

Calculate the balance as follows:

Balance = Free + Purchased – Used

Where:

- Free:
  
    A free volume of business documents you can submit each month. It includes a package of 100 business documents that you can submit to the Electronic Invoicing service. The free volume isn't cumulative, and you can't roll over any remaining balance to the next period.
  
- Purchased:
  
    A package of 1,000 business documents that you can submit to the Electronic Invoicing service. You must acquire this package for your organization on a monthly basis. The purchased volume isn't cumulative, and you can't roll over any remaining balance to the next period.
  
- Used:

    The count of business document submissions to the Electronic Invoicing service according to defined criteria.

> [!IMPORTANT]
> - If your organization plans to exceed the monthly volume of 100 free submissions, purchase the peak volume to ensure that you remain compliant with the Microsoft licensing policy for the Electronic Invoicing service.
> - Currently, you must manually enter the purchased volume, according to the date of acquisition, as multiple packages of 1,000 submissions.

## Indicator: Usage by feature

This indicator shows the usage of electronic invoicing features for issuing electronic invoices during a defined period.

- Calculation:
  
    Used = The count of how many times each electronic invoicing feature was used during the submission of business documents to the Electronic Invoicing service.

## Indicator: Usage by environment

This indicator shows the usage of electronic invoicing service environments during a defined period.

- Calculation:

    Used = The count of how many times each electronic invoicing service environment was used during the submission of business documents to the Electronic Invoicing service.

## Indicator: Usage per month (import)

This indicator shows the volume of imported electronic invoices by the Electronic Invoicing service into Finance and Supply Chain Management during a defined period.

- Scope:

    Electronic invoices that are imported into Finance and Supply Chain Management, regardless of the number of lines that those electronic invoices contain.

- Calculation:

    Received = The count of imported electronic invoices into Finance and Supply Chain Management.

## Functions

### Purchase

On the **Usage per month (export)** tab, select **Purchase** to manually register the amount of acquired submissions.

For a given date, select **New** and enter the number of **Packages** acquired for that date.

The **Quantity** is calculated as:

Quantity = Packages * 1,000

The calculated **Quantity** appears in the **Purchased** section of the **Usage per month (export)** indicator.

### Update

On the action pane, select **Update** to refresh the calculation and update the data shown on the page and in the chart.

### Reset history data

On the action pane, select **Reset history data** to refresh the database from where the indicators are calculated.

> [!NOTE]
> The **Usage management** dashboard doesn't show monetary amounts. Instead, it shows only the volume of counted submissions and imported documents.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
