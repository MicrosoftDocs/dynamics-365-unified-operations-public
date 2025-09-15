--- 
title: FR-00004 French bills of exchange and promissory notes
description: Learn how to create a French bill of exchange remittance journal and generate a bill of exchange remittance report in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak  
audience: Application User   
ms.search.region: France
ms.search.validFrom: 2016-06-30
ms.search.form: CustPaymMode, CustVendPaymFormat

---

# FR-00004 French bills of exchange and promissory notes

[!include [banner](../../includes/banner.md)]

This article explains how to create a French bill of exchange remittance journal and generate a bill of exchange remittance report in Microsoft Dynamics 365 Finance.

The French bill of exchange remittance report displays details about remitted bills of exchange. The report includes information about your bank account, legal entity, and remittance type. It also provides a list of customer transactions that are affected by the bill of exchange. The report is used by accounts receivable clerks and accounts payable clerks to maintain customer payments. 

The following procedure walks you through how to create the bill of exchange remittance journal and generate the bill of exchange remittance report, and was created using the demo data company FRSI.

Before you can complete this procedure, you must create, approve, and post draw the bill of exchange journal.

To create a French bill of exchange remittance journal and generate a bill of exchange remittance report

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments \> Bill of exchange \> Remittance journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. In the list, select the link in the selected row.  
1. Select the **Bill of exchange** tab.
1. In the **Bank account** field, enter or select a value.
1. In the list, find and select the desired record. For example, select "FRN".  
1. In the list, select the link in the selected row.
1. Select the **Setup** tab.
1. In the **Account type** field, select **Bank**.
1. In the **Offset account** field, enter a value. For example, enter "FRSI OPER".  
1. Select **Lines**.
1. In the **Account** field, enter a value. For example, enter "FR_SI_0020".  
1. Select **Settle transactions**.
1. Select the lines to include.  
1. Select **OK**.
1. Select **Generate remittance**.
1. In the **Method of payment** field, enter or select a value.
1. In the list, find and select the desired record. For example, select **BOEPDF**.  
1. In the **File name** field, enter a value.
1. Select **OK**. If asked to enter a processing date, enter a date.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
