---
# required metadata

title: Invoice issue deadline
description: This topic provides information about how to calculate the due dates for issuing customer invoices in Gulf Cooperation Council (GCC) countries.
author: v-oloski
manager: Annbe
ms.date: 08/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: GCC
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2020-07-03
ms.dyn365.ops.version: 10.0.13

---


# Invoice issue deadline (GCC)

[!include [banner](../includes/banner.md)]

|                     |  |
|------------------------------|-------------------|
| **COUNTRY/REGION**           | Gulf Cooperation Council (GCC) countries include Bahrain, Kuwait, Oman, Qatar, Saudi Arabia, and United Arab Emirates|
| **FEATURE TITLE**            | Invoice issue deadline    |
| **FEATURE REFERENCE**        | GCC-00001 |
| **BLUEPRINT CLASSIFICATION** | INVOICING: Invoice processing|
| **CONFIGURABLE**             | No|
| **INTERNAL REFERENCE**       | [Compliance 3982487](https://vstsmbs.visualstudio.com/web/wi.aspx?pcguid=bf66efc0-4097-46c2-80a1-746442695fc7&id=3982487)|
| **FIRST AVAILABLE IN**       | 2020 Release Wave 2 (Monthly update 10.0.13)|
| **FEATURE UPDATE HISTORY**   ||
| **FEATURE MANAGEMENT**       | Yes. See [Features enabling](#features-enabling)|
| **BUSINESS NEED**            | The Tax Invoice issue date must be compliant with the GCC legal requirements and should be no later than set in the legislation|
| **FEATURE DESCRIPTION**      | The topic explains how to configure Dynamics 365 Finance so that it is compliant with GCC legal requirements on tax invoice issue deadline. |

## Prerequisites

The primary address of the legal entity must be in a GCC country. GCC countries include Bahrain, Kuwait, Oman, Qatar, Saudi Arabia, or United Arab Emirates.

## <a name="features-enabling"></a>Features enabling

In the **Feature management** workspace, enable the following feature:

- Invoice issue deadline availability for additional countries

For more information how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This feature is same as for European Union (EU) countries. For additional information, see [Invoice issue deadline](emea-invoice-issue-deadline.md).

## Setup

Complete the following steps to set up the invoice issue deadline functionality.

1. Go to **General ledger** \> **Ledger setup** \> **Date intervals**.
2. On the **Date intervals** page, create a new date interval and on the **General** FastTab, enter the appropriate field information in the **Interval start** and **Interval end** field groups.
     
     ![Date interval](media/gcc-invoice-issue-deadline-date-interval.jpg)
     
      > [!NOTE]
      > The graphic shows an interval of 15 days. If the date interval is set in this way, this means that the deadline for issuing the invoice will be set on the 15th of the next month following the month of issuing the packing slip. If the **To date period type** and **To date Start/End** is blank, the deadline for issuing the invoice will be set on the 15th day after the packing slip is issued.
       
3. Go **Tax** \> **Setup** \> **Foreign trade**.
4. On the **Country/region properties** tab, select **New**.
    
    ![Country/region properties](media/gcc-invoice-issue-deadline-Foreign-trade-parameters.jpg)

5. On the new record line, in the **Party country/region** field, select a country, and in the **Country/region type** field, select **Domestic**.
6. Go to (Need navigation path to the page - the previous navigation is incorrect )**Set up calculation for invoice issue due date page** and create a new record.

   ![Invoice issue deadline calculation](media/gcc-invoice-issue-deadline-calculation-for-invoice-issue-deadline.jpg)
   
7. Go to **Accounts receivable** \> **Setup** \> **Parameters**, and on the **Updates** tab, on the **Invoice date control** FastTab, set up the invoice date control.
     
     ![Accounts receiveble parameters](media/gcc-invoice-issue-deadline-ar-parameters.jpg)

     You can select from the following values:

     - **None**: The control date does not execute
     - **Warning**: The invoice is posted but the warning appears after
     - **Error**: The invoice is not posted and an error message occurs

According to the settings, the system populates the **Invoice issue due date** field in the packing slip journal. You can  view all of the packing slips that are not yet invoiced by going to **Sales and Marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip not invoiced**.  To review packing slips from a sales order, go to **Sales and marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip**). 

 > [!NOTE] 
 > If the **Invoice date control** field is set to **None**, the **Invoice issue due date** field is empty.
