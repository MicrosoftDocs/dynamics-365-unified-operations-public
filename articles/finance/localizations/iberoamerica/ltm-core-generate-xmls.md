---
title: Generate invoices XMLs using electronic document feature
description: Learn the configurations and steps needed to generate invoices XMLs.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Generate invoice XMLs by using the electronic document feature

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

This article explains how to configure and generate invoice XMLs by using the native electronic document feature. Use this method to generate XMLs if you don't need the LATAM feature.

## Prerequisites

Before generating an invoice XML, make sure you meet the following prerequisites:

- Enable the country/region-specific Latin American (LATAM) feature, and the general LATAM feature.
- Set the company's address to a country/region within the LATAM Globalization expansion.
- Download the e-invoice format you want.
- Complete the e-invoice configuration by following the steps in the corresponding Microsoft Learning article found in the section for the country/region.

## Configure Electronic Invoice feature to generate an invoice XML

To configure Electronic Invoice feature to generate an invoice XML, follow these steps:

1. Go to **Accounts receivable > Setup > Accounts receivable parameters** and set the format you want for each type of transaction.
1. Go to **Accounts receivable > Customers > All customers** and for each customer in the **Invoice and delivery** section, set the **eInvoice** option to **Yes**.

## Generate an invoice XML

To generate an invoice XML from the **Accounts receivable** module, follow these steps:

1. Go to **Accounts receivable > Inquiries and reports > Invoices > Invoice journal**.
1. Select an invoice from the list.
1. In the action pane, select **Invoice > Document > Send > Original**.
1. Go to **Organization administration > Electronic reporting > Electronic reporting jobs**, select the finished batch job, and then select **Show files** to download the XML.

To generate an invoice XML from the **Project management and accounting** module, follow these steps:

1. Go to **Project management and accounting > Project invoices > Project invoices**.
1. Select an invoice from the list.
1. In the action pane, select **Project invoice > Document > Send > Original**.
1. Go to **Organization administration > Electronic reporting > Electronic reporting jobs**, select the finished batch job, and then select **Show files** to download the XML.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
