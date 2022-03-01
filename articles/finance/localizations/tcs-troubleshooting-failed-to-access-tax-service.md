---
# required metadata 

title: Access the Tax Calculation service
description: This topic explains how to access the Tax Calculation service. 
author: hangwan
ms.date: 03/01/2022
ms.topic: business-process 
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxIntegrationTaxServiceParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: hangwan
ms.search.validFrom: 02/16/2022
ms.dyn365.ops.version: Version 10.0.21 
---

# Access the Tax Calculation service

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic explains how to resolve the error of the Tax Calculation service, **Failed to access tax service.**


## Symptoms

The following describes the symptoms you might experience as a result of the error.

You navigate to **Tax** > **Setup** > **Tax configuration** > **Tax service parameter**. On the **General** tab, if enable the switch name **Enable tax calculation** and then select the **Feature setup name**  drop-down list, an error occurs. The error message reads, **Failed to access tax service**. 

## Cause

This error occurs because Dynamics 365 Finance can't access the Tax Calculation service.

## Resolution 

1. Log in to Lifecycle Services (LCS), and on the **Environment** page, on the **Environment add-ins** tab, and locate the **Tax Calclation** item.
2. Check the status. The status should be **Installing** or **Installed**. If the Tax Calculation service add-in isn't installed, you will receive the error.

## Mitigation

1. In LCS, open the **Finance** page.
2. In the **Power platform integration** section, select **Install a new add-in**
3. Scroll to the end of the page, and select the **Tax Calculation** add-in to install.
4. Go back to your Finance environment and try to access the Tax Calculation service.

> [!NOTE]
> Before you install the Tax Calculation service, check the [Tax Caclualtion Service prerequisites](global-get-started-with-tax-calculation-service.md#prerequisites).
> 
> If the **Power platform integration** section isn't avaliable to install the add-in, see [Add-in overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md). If you still face the error after installing the add-in, contact your system administrator.

