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

For more information how to enable features, see [Feature management overview](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/ilkond-bh-0003/articles/fin-and-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This feature is same as for European Union (EU) countries. For additional information, see [Invoice issue deadline](emea-invoice-issue-deadline.md).

## Setup

Complete the following steps for settings the invoice issue deadline functionality:

1.  Create a new date interval on **Date intervals** page list (**General ledger \> Ledger setup \> Date intervals**) and fill in the highlighted fields (the **To date +/-** field can be filled in different values, if needed
     
     ![Date interval](media/gcc-invoice-issue-deadline-date-interval.jpg)
     
      > [!NOTE]
      > If the date interval is set in this way, this means that the deadline for issuing the invoice will be set on the 15th of the next month following the month of issuing the packing slip.
      
     If the **To date period type** and **To date Start/End** is blank, this means that the deadline for issuing the invoice will be set on the 15th day after issurance of the packing slip.
       
2.  Create a new record in Country\ Region properties (**Tax \> Setup \> Foreign trade**, **Country/region properties** tab)
    
    ![Country/region properties](media/gcc-invoice-issue-deadline-Foreign-trade-parameters.jpg)

     Select the country in **Party country/region** and **Domestic** in **Country/region type**.

3.  Create a new record in **Set up calculation for invoice issue due date** page list (**Accounts receivable parameters \> Setup**)

   ![Invoice issue deadline calculation](media/gcc-invoice-issue-deadline-calculation-for-invoice-issue-deadline.jpg)
   
 4.  Set up invoice date control in the Accounts receivable parameters (**Accounts receivable parameters \> Setup \> Accounts receivable parameters**, **Updates** tab, **Invoice date control** FastTab)
     
     ![Accounts receiveble parameters](media/gcc-invoice-issue-deadline-ar-parameters.jpg)

You can select the following values:

- None: The control date does not execute
- Warning: The invoice is posted but the warning appears after
- Error: The invoice is not posted and an error message occurs

According to settings the system filled in **Invoice issue due date** field in packing slip journal. A user can overview all not invoiced packing slips in **Sales and Marketing \> Sales orders \> Order shipping \> Packing slip not invoiced**.  To review packing slips from a sales order go to **Sales order \> Pick and Pack tab \> Journals \> Packing slip journal**). 

 > [!NOTE] 
 > If the Invoice date control is set to **None**, the **Invoice issue due date** field is empty.
