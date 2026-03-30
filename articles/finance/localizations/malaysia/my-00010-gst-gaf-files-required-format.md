--- 
title: MY-00010 GST - Generate GAF files in the required format
description: Learn how to generate a Malaysia GAF file in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak    
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionTable, DefaultDashboard, LedgerParameters, EnumLookupForm_RU
ms.custom: 
  - bap-template
---

# MY-00010 GST - Generate GAF files in the required format

[!include [banner](../../includes/banner.md)]

This article explains how to generate a Malaysia GAF file in Microsoft Dynamics 365 Finance.

Before you can complete the following procedures, you must first upload your GAF format files into your active electronic reporting configuration. You must be in the accounting manager role to complete the procedures. 

The procedures use the demo data company MYMF.

## Specify the GAF file format to use in the General ledger parameters

To specify the GAF file format to use in the General ledger parameters, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Ledger setup \> General ledger parameters**.
1. Select the **Sales tax** FastTab.
1. Expand or collapse the **GST options** section.
1. In the **Format mapping** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.

## Generate a GAF XML report for posted transactions

To generate a GAF XML report for posted transactions, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Sales tax \> Generate GAF file**.
1. In the **Settlement period** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **From date** field, enter a date.
1. In the **Creation date** field, enter a date.
1. In the **Posting layer** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **OK**. 
1. Select **Save as** to save the GAF XML report file.    
1. Select **Open**, and then select **Microsoft Edge**.
1. Validate the GAF XML file, and then close the file.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
