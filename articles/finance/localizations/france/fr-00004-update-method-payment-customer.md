--- 
title: FR-00004 Update method of payment for a customer
description: Learn how to add a bank account to a customer record in France and update the customer method of payment in Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 08/29/2018
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: France
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable, CustBankAccounts, LogisticsPostalAddress, LogisticsPostalAddressGrid, SysLookupMultiSelectGrid
---

# FR-00004 Update method of payment for a customer

[!include [banner](../../includes/banner.md)]

This article explains how to add a bank account to a customer record in France and update the customer method of payment in Microsoft Dynamics 365 Finance. 

The following procedure was created using the demo data company FRSI.

Before you can complete this procedure, you must first import the following electronic reporting configurations:
- payments.initial.version.xml
- BillsOfExchangeRemittance_FR.xml

To add a bank account to a customer record and update the customer method of payment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the list, find and select the desired record.
1. Select the link in the selected row.
1. On the Action Pane, select **Customer**.
1. Select **Bank accounts**.
1. Select **New**.
1. In the **Bank account** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Bank account number** field, enter a value.
1. In the **Routing number** field, enter a value.
1. Expand the **Address** section.
1. Select **New**.
1. In the **Name or description** field, enter a value.
1. In the **Country/region** field, enter or select a value.
1. In the list, select **FRA**.  
1. Select **OK**.
1. Close the page.
1. Expand the **Addresses** section.
1. Select **Edit**.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Expand the **Payment defaults** section.
1. Select **Edit**.
1. In the **Method of payment** field, enter or select a value.
1. In the list, find and select the desired record.
1. In the **Method of payment** field, select **BOEPDF**.  
1. In the list, select the link in the selected row.
1. In the **Bank account** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Bank account** field, select **1**.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
