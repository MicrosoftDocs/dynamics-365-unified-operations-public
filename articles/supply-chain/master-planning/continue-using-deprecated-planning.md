---
title: Continue to use deprecated master planning for some companies
description: This article explains how to continue using the deprecated master planning engine for some companies until they are ready to be migrated. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
ms.topic: how-to
ms.date: 09/18/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Continue to use deprecated master planning for some companies

[!include [banner](../../includes/banner.md)]

Starting with Supply Chain Management version 10.0.32, it's possible allow some companies (legal entities) to run Planning Optimization while others continue to use the [deprecated master planning engine](deprecated-master-planning-overview.md) until they are ready to be migrated, but you must obtain a special exception from Microsoft to do so (see also [Migration to Planning Optimization for master planning](new-master-planning-engine.md)).

Follow these steps to set a company to use the deprecated master planning engine on an environment that is otherwise enabled to use Planning Optimization:

1. Use the company picker to choose the company (legal entity) that you want to set up.
1. Go to **Master planning \> Setup \> Planning Optimization parameters**.
1. Open the **Company information** tab.

    [<img src="media/exclude-company-from-po.png" alt="Screenshot of the Company information tab." title="Screenshot of the Company information tab" width="350" />](media/exclude-company-from-po.png#lightbox)

1. Set **Exclude company from running Planning Optimization** to one of the following values
    - *Yes* – Use the deprecated master planning engine for this company.
    - *No* – Use Planning Optimization for this company.
1. Select **Save** on the Action Pane.
1. Repeat this procedure for each company you want to set up.
