--- 
title: MY-00006 02 Print GST customer invoices with a relief clause
description: Learn how to print GST customer invoices for Malaysia that include a relief clause in Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak    
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: TaxGSTReliefCategory_MY, TaxGSTReliefGroup_MY
ms.custom: 
  - bap-template
---

# MY-00006 02 Print GST customer invoices with a relief clause

[!include [banner](../../includes/banner.md)]

This article explains how to print GST customer invoices for Malaysia that include a relief clause in Microsoft Dynamics 365 Finance. 

After you complete the following procedures, when you generate a tax invoice for a customer who has bought a GST relieved item or service, the relief clause is automatically included in the final printed invoice. 

You must be in the accounting supervisor role to complete these procedures, which use the demo data company MYMF.

## Create GST relief categories

To create GST relief categories, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Sales tax \> GST relief category**.
1. Select **New**.
1. In the **Relief item number** field, enter a value.
1. In the **Relief schedule** field, enter a value.
1. Repeat steps 3 and 4 for each additional GST relief category that you want to create.  
1. Select **Save**.

## Create GST relief groups

To create GST relief groups, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Sales tax \> GST relief group**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. In the **Description** field, enter a value.
1. Expand or collapse the **GST relief category** section.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **GST relief category** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Repeat steps 1 through 10 to create additional GST relief groups if necessary.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
