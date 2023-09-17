---
# required metadata

title: Failed to access tax service
description: This article explains how to troubleshoot a failure to access the Tax Calculation service.
author: hangwan
ms.date: 03/04/2022
ms.topic: how-to
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

# Failed to access tax service

[!include [banner](../includes/banner.md)]


This article explains how to fix the "Failed to access tax service" error of the Tax Calculation service.

## Symptoms

In Microsoft Dynamics 365 Finance, you go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax service parameters**. On the **General** tab, you enable the **Enable tax calculation** option. If you then try to select a value in the **Feature setup name** field, an error occurs. The error message states, "Failed to access tax service."

## Cause

This error occurs because Finance can't access the Tax Calculation service.

## Resolution 

1. Sign in to Microsoft Dynamics Lifecycle Services (LCS).
2. On the **Environment** page, on the **Environment add-ins** tab, find the **Tax Calculation** item, and review its status. The status should be **Installing** or **Installed**. If the Tax Calculation service add-in isn't installed, you will receive the error.

## Mitigation

1. In LCS, on the **Finance** page, in the **Power platform integration** section, select **Install a new add-in**.
2. Scroll to the bottom of the page, and select the **Tax Calculation** add-in to install it.
3. Return to your Finance environment, and try to access the Tax Calculation service.

> [!NOTE]
> Before you install the Tax Calculation service, review the [Tax Calculation Service prerequisites](global-get-started-with-tax-calculation-service.md#prerequisites).
> 
> If you can't install the add-in because the **Power platform integration** section isn't available, see [Add-in overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md). If you still encounter the error after you install the add-in, contact your system administrator.
