--- 
title: Update vendor invoice declarations and generate the report
description: Learn how to post a vendor invoice with invoice declaration information attached and generate an invoice declaration report in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: Iceland
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendInvoice

---

# Update vendor invoice declarations and generate the report

[!include [banner](../../includes/banner.md)]

This article explains how to post a vendor invoice with invoice declaration information attached and generate an invoice declaration report in Microsoft Dynamics 365 Finance.

The demo data company used to create the following procedures is DEMF, with the country/region of legal entity primary address updated to Iceland.

## Post a vendor invoice

To post a vendor invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable > Invoices > Invoice journal**.
1. Select **New**.
1. In the **Name** field, select **APInvoice**.
1. Select **Lines**.
1. In the **Account** field, enter `IS-001`.
1. In the **Invoice** field, enter `IS-001-01`.
1. In the **Credit** field, enter a number.
1. In the **Offset account** field, enter `200130--`.
1. Select the **Invoice** tab.
1. In the **Document** field, enter a value.
1. In the **Invoice date** field, enter today's date.
1. In the **Invoice declaration** field, select the drop-down button to open the lookup.
1. In the list, select the **Invoice declaration** category.
1. Select **Post**.

## Generate an invoice declaration

To generate an invoice declaration, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Inquiries and reports \> Invoice \> Vendor invoice declaration report**.
1. In the **Authority** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select the **Create report file** checkbox.
1. In the **Name** field, select **Vendor invoice declaration report (IS)**.
1. Select the **Create text file** checkbox.
1. In the **Name** field, select **Vendor invoice declaration (IS)**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
