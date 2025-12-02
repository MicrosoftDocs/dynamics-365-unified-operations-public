---
title: Enable the JBA payment file format
description: Learn how to enable the Japanese Bankers Association (JBA) payment file format for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/25/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport
  - VendPaymMode
ms.custom: 
  - bap-template
---

# Enable the JBA payment file format

[!include [banner](../../includes/banner.md)]

This article explains how to enable the Japanese Bankers Association (JBA) payment file format for Japan in Microsoft Dynamics 365 Finance.

In Japan, the JBA has specified a file format for electronic fund transfers (EFT). 

The following procedure walk you through how to import the JBA payment model and enable the JBA payment file for vendor methods of payment. The procedures were created using the demo data company JPMF.

## Import the JBA payment model

To import the JBA payment model, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Workspaces \> Electronic reporting**.
1. Select **Repositories**.
1. Select **Open**.
1. In the tree, select **Payment model\JBA Payment model\JBA Payment file (JP)**.
1. Select **Import**.
1. Select **Yes**.

## Use the JBA payment file in the vendor method of payment

To use the JBA payment file in the vendor method of payment, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Methods of payment**.
1. Select **Edit**.
1. Expand or collapse the **File formats** section.
1. Select the **Generic electronic reporting** checkbox.
1. In the **Export format configuration** field, select the drop-down button to open the lookup.
1. In the list, select **JBA Payment file (JP)**.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
