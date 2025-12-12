---
title: Generate invoices XMLs using electronic document feature
description: Learn the configurations and steps needed to generate invoices XMLs.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 12/12/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Generate invoices XMLs using electronic document feature

This article explains how to configure and generate invoices XMLs using the native electronic document feature.
This method can be used to generate XMLs if the LATAM feature is not needed.

## Prerequisites

Before generating an invoice XML, make sure you meet the following prerequisites:

- Enable the country/region-specific Latin American (LATAM) feature, and the general LATAM feature.
- Set the company's address to a country/region within the LATAM Globalization expansion.
- Download the e-invoice format desired.
- Complete all the e-invoice configuration following the steps in the corresponding MS Learning article found in the country’s section.

## Configure Electronic Invoice feature to generate an invoice XML

To be able to generate an invoice XML first complete these configurations:

1. Go to **Accounts receivable > Setup > Accounts receivable parameters** and set the format desired for each type of transaction.
1. Go to **Accounts receivable > Customers > All customers** and for each customer in the **Invoice and delivery** section set the **eInvoice** option to **Yes**.

## Generate an invoice XML

Follow these steps to generate an invoice XML from the **Accounts receivable** module:

1. Go to ** Accounts receivable > Inquiries and reports > Invoices > Invoice journal **.
1. Select an invoice from the list.
1. In the action pane select **Invoice > Document > Send > Original**
1. Go to **Organization administration > Electronic reporting > Electronic reporting jobs** and select the finished batch job and then select **Show files** to download the XML.

Follow these steps to generate an invoice XML from the ** Project management and accounting** module:

1. Go to **Project management and accounting > Project invoices > Project invoices**.
1. Select an invoice from the list.
1. In the action pane select **Project invoice > Document > Send > Original**.
1. Go to ** Organization administration > Electronic reporting > Electronic reporting jobs** and select the finished batch job and then select **Show files** to download the XML.

