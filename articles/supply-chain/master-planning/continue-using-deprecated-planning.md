---
title: Continue to use deprecated master planning with existing companies
description: Learn how to continue using the deprecated master planning engine for existing companies until they're ready to be migrated.
author: Henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 09/18/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
---

# Continue to use deprecated master planning with existing companies

[!include [banner](../../includes/banner.md)]

Starting in Supply Chain Management version 10.0.41, the deprecated master planning engine is blocked for all new legal entities (companies) added to existing deployments. There is no manual way to enable the deprecated master planning engine for these companies. However, for existing companies, it is possible to continue to use the [deprecated master planning engine](deprecated-master-planning-overview.md) until they're ready to be migrated.

> [!IMPORTANT]
> The deprecated master planning engine is only available to existing companies that are already using it.

## Companies where planning processes are disabled

Starting with release 10.0.32, you must install the Planning optimization add-in before you can enable planning processes, even if you plan to continue using the deprecated master planning engine. If the company where you want to use deprecated master planning has planning processes disabled, follow these steps to enable them:

1. Make sure Planning Optimization is installed and enabled as described in [Get started with master planning](planning-optimization/get-started.md).
1. Make sure Planning Optimization is enabled on the **Planning Optimization parameters** page.
1. Enable planning processes for the relevant company by setting **Disable all planning processes** to *No*, on the **Master planning parameters** page.

## Excluding companies from using Planning Optimization and continue to use deprecated master planning

Follow these steps to set a company to continue to use the deprecated master planning engine on an environment that is otherwise enabled to use Planning Optimization:

1. Use the company picker to choose the company (legal entity) that you want to set up.
1. Go to **Master planning \> Setup \> Planning Optimization parameters**.
1. Open the **Company information** tab.

    [<img src="media/exclude-company-from-po.png" alt="Screenshot of the Company information tab." title="Screenshot of the Company information tab" width="350" />](media/exclude-company-from-po.png#lightbox)

1. Set **Exclude company from running Planning Optimization** to one of the following values
    - *Yes* – Use the deprecated master planning engine for this company.
    - *No* – Use Planning Optimization for this company.
1. Select **Save** on the Action Pane.
1. Repeat this procedure for each company you want to set up.
