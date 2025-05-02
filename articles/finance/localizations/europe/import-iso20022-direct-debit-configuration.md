--- 
title: Import ISO20022 direct debit configuration
description: Learn how to import a customer payment electronic reporting configuration in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 03/27/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport
---

# Import ISO20022 direct debit configuration

[!include [banner](../../includes/banner.md)]

This article explains how to import a customer payment electronic reporting configuration in Microsoft Dynamics 365 Finance.

The following procedure demonstrates how to import a customer payment electronic reporting configuration using the ISO 20022 direct debit format as an example. 

The procedure was created using the demo data company DEMF, but you can use any demo data company.

To import a customer payment electronic reporting configuration, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Workspaces \> Electronic reporting**.
1. In the list of available configuration providers, select **Microsoft**.
1. Select **Set active**.
1. Select **Repositories**.
1. Select **Open**.
1. Select **Show filters**.
1. In the **Configuration name** field, using the **begins with** filter operator, enter a filter value of "ISO20022 Direct debit (DE)". Alternatively, you can find the configuration in the list and select it.  
1. Select **Import**. If the **Import** button is not available, it means that the configuration has been imported already.  
1. Select **Yes**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
