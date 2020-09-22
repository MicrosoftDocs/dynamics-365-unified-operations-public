---
# required metadata

title: Experimentation in Dynamics 365 Commerce
description: Experimentation enables the creation, editing, and management of page layout and content treatments in site builder. End-to-end experimentation support is enabled for e-commerce pages and entities within a page.
author:  sushma-rao 
manager: AnnBe
ms.date: 10/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: sushmar
ms.search.validFrom: 2020-09-30
ms.dyn365.ops.version: AX 10.0.13
---

# Experimentation in Dynamics 365 Commerce

## Overview
You can run controlled experiments such as A/B tests in Dynamics 365 Commerce to validate hypotheses about the effectiveness of your e-Commerce pages and make decisions with data-driven confidence. e-Commerce experimentation enables you to scientifically measure the impact of proposed changes to your website and drive higher conversion rates as a result.

Commerce supports the creation, editing, and management of page and content treatments (known as **variations**) within site builder. Commerce integrates with third-party services which you use to enable the creation of experiments and treatment assignments. Real-time event streams are captured in Commerce and enable the analytics that define the experiment results in the third-party service. You then use the analytics help support or refute your hypothesis.

> [!NOTE]
> Commerce supports A/B testing on pages, modules, and fragments. Multi-variate and multi-page tests can currently only be accomplished using fragments.

## Set up prerequisites
1. **Get the correct version of Commerce** - Upgrade your module library, online channel extensibility SDK, and Commerce scale unit to Commerce version 10.0.13 or later.
1. **Set up an experimentation connector** - An experimentation connector allows Commerce to connect with third-party services to retrieve the list of experiments and determine when to show an experiment a user. You can purcahse a third-party connector from [AppSource](https://appsource.microsoft.com). Follow the setup instructions provided by the publisher. You can alternatively use the sample test connector from Commerce to test the experimentation workflow without needing to configure an external service. For more information, see the [Configure and enable connectors](e-commerce-extensibility/connectors.md) topic. 
1. **Turn on the experimentation feature flags** - You can enable experimentation at the tenant level by going to **Tenant Settings -> Features** or at the site level at **Site Settings -> Features**.
    - Enable the **Experimentation** flag to create experiment variations of modules within a page without affecting or copying other content that isn't part of the experiment. This ensures that ongoing content updates outside the experiment stay in sync during the experiment lifecycle. Disabling this flag stops all experiments from being shown to users and removes all editing functions within site builder.
    - Enable the **Experimentation on pages or fragments** flag to run experiments on a page or fragment. This creates a full instance copy of the entire page or fragment for all modules within the page or fragment. Use this mode when you want to test comprehensive content changes, or where synchronizing ongoing content changes across instances isn't a concern. Disabling this flag prevents creation and editing of new experiments on pages and fragments.
    
## Experimentation lifecycle
Setting up an experiment, creating variations, and running an experiment is an iterative process. You may want to re-do some of the steps along the way to get the results you want. The image below illustrates the exerimentation lifecycle in Commerce and the third-party service. 

![Experimentation lifecycle](./media/TEST.svg "Experimentation lifecycle")

To learn more about each step in the experimentation process, refer to the following topics.
1. [Identify the goals for your experiment](experimentation-identify.md)
1. [Set up your experiment](experimentation-setup.md)
1. [Connect and edit your experiment](experimentation-connect-edit.md)
1. [Preview and publish your experiment](experimentation-preview-publish.md)
1. [Run and monitor your experiment](experimentation-run-monitor.md)
1. [Review and complete your experiment](experimentation-review-complete.md)

To learn where an experiment is in the lifecycle, go to the **Experiments** tab in site builder. A list of experiments is diplayed with the status of each experiment in both Commerce and the third-party service. For more information, refer to the [Review the status of an experiment](experiment-status.md) topic.
