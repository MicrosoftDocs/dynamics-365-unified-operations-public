--- 
title: EUR-00012 Issue an EU entry certificate
description: Learn about how to enable an EU entry certificate, configure a customer account to use entry certificates, and issue a certificate with Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/16/2025
ms.reviewer: johnmichalak   
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: CustParameters, CustTable, SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines,  CustInvoiceJournal, CustEntryCertificateJour_W, SrsReportViewerForm  

---

# EUR-00012 Issue an EU entry certificate

[!include [banner](../../includes/banner.md)]

This article explains how to enable an EU entry certificate, configure a customer account to use entry certificates, and issue a certificate with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to enable an EU entry certificate, configure a customer account to use entry certificates, and issue a certificate. The procedures use the demo data company DEMF.

## Enable entry certificate management

To enable entry certificate management, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Select the **Shipments** tab.
1. Expand the **Entry certificate** section.
1. In the **Enable entry certificate management** field, select **Yes**.
1. In the **Enable entry certificate issuing** field, select **Yes**.
1. Select the **Number sequences** tab.
1. In the list, find and select the **Entry certificate** row.
1. In the **Number sequence code** field, enter or select a value.

## Set up a customer

To set up a customer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Use the Quick Filter to find records. For example, filter on the **Account** field with a value of "DE-015".
1. Open the customer account details.
1. Select **Edit**.
1. Expand the **Invoice and delivery** section.
1. In the **Entry certificate** field, select **Yes**.
1. In the **Issue entry certificate** field, select **Yes**.
1. Select **Save**.

## Create an EU entry certificate automatically

To create an EU entry certificate automatically, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. In the **Item number** field, enter or select a value.
1. Select **Save**.
1. On the Action Pane, select **Pick and pack**.
1. Select **Post packing slip**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select **All**.
1. Clear the **Issue entry certificate** checkbox. You can issue an entry certificate during packing slip posting or during order invoicing. To issue it later, leave the **Issue entry certificate** checkbox unchecked.  
1. Select **OK**.
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**. In the **Overview** section, verify that the **Entry certificate required** and **Issue entry certificate** checkboxes are marked.  You can also select the **Print entry certificate** checkbox to allow printing of the certificate.  
1. Select **OK**.
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **View issued entry certificates**.
1. Select **Print**.
1. Close the page.
1. Select **Change status**.
1. In the **New status** field, select an option.
1. Select **OK**.
1. Close the page.

## Create an EU entry certificate manually

To create an EU entry certificate manually, follow these steps:

1. On the Action Pane, select **Invoice**.
1. Select **Create entry certificate**.
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Select **View issued entry certificates**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
