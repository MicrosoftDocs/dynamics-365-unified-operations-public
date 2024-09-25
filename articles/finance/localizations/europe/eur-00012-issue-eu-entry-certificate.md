--- 
title: EUR-00012 Issue an EU entry certificate
description: Learn about enabling an EU entry certificate, configuring a customer account to use entry certificates and issue a certificate.
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2018
ms.reviewer: johnmichalak   
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: CustParameters, CustTable, SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines,  CustInvoiceJournal, CustEntryCertificateJour_W, SrsReportViewerForm  
ms.dyn365.ops.version: Version 7.0.0 
---
# EUR-00012 Issue an EU entry certificate

[!include [banner](../../includes/banner.md)]
This procedure walks you through enabling an EU entry certificate, configuring a customer account to use entry certificates and issue a certificate. This procedure was created using the demo data company DEMF.


## Enable entry certificate management

To enable entry certificate management, follow these steps.

1. Go to Accounts receivable > Setup > Accounts receivable parameters.
1. Select the **Shipments** tab.
1. Expand the **Entry certificate** section.
1. Select **Yes** in the **Enable entry certificate management** field.
1. Select **Yes** in the **Enable entry certificate issuing** field.
1. Select the **Number sequences** tab.
1. In the list, find and select the **Entry certificate** row.
1. In the **Number sequence code** field, enter or select a value.

## Set up a customer

To set up a customer, follow these steps.

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Use the Quick Filter to find records. For example, filter on the Account field with a value of 'DE-015'.
1. Open the customer account details.
1. Select **Edit**.
1. Expand the **Invoice and delivery** section.
1. Select **Yes** in the **Entry certificate** required field.
1. Select **Yes** in the **Issue entry certificate** field.
1. Select **Save**.

## Create an EU entry certificate automatically

To create an EU entry certificate automatically, follow these steps.

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. In the **Item number** field, enter or select a value.
1. Select **Save**.
1. On the **Action Pane**, select **Pick and pack**.
1. Select **Post packing slip**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select **All**.
1. Clear the **Issue entry certificate** check box.
    * An entry certificate can be issued during packing slip posting or during order invoicing. Leave the Issue entry certificate checkbox unchecked to issue it later.  
1. Select **OK**.
1. Select **OK**.
1. On the **Action Pane**, select **Invoice**.
1. Select **Invoice**.
    * Verify that the Entry certificate required and Issue entry certificate checkboxes in the Overview section are marked.  You can also select the **Print entry certificate** check box to allow printing of the certificate.  
1. Select **OK**.
1. Select **OK**.
1. On the **Action Pane**, select **Invoice**.
1. Select **Invoice**.
1. select **View issued entry certificates**.
1. Select **Print**.
1. Close the page.
1. Select **Change status**.
1. In the **New status** field, select an option.
1. Select **OK**.
1. Close the page.

## Create an EU entry certificate manually

To create an EU entry certificate manually, follow these steps.

1. On the **Action Pane**, select **Invoice**.
1. Select **Create entry certificate**.
1. Select **OK**.
1. On the **Action Pane**, select **Invoice**.
1. Select **View issued entry certificates**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
