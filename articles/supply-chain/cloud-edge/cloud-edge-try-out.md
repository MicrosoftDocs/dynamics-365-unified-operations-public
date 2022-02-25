---
title: Try out Scale units in a distributed hybrid topology
description: This topic provides information about how to try out the cloud and edge scale units for manufacturing and warehouse management workloads.
author: 
ms.date: 022/08/2022
ms.topic: article
ms.search.form: ScaleUnitWorkloadsWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: 
ms.search.validFrom: 2022-02-01
ms.dyn365.ops.version: 10.0.25
---

# Try out scale units in a distributed hybrid topology

[!include [banner](../includes/banner.md)]

The process of trying out the distributed hybrid topology is simple. During the first stage, you should validate customizations to ensure that they work in the distributed topology, and here you have two options:

## Option 1: Evaluate customizations in development environments

Before you start to onboard your sandbox environments, we recommend that you explore scale units in a development setup such as a one-box environment (also known as a tier-1 environment) so that you can validate processes, customizations, and solutions. During this stage, data and customizations will be applied to the one-box environments. You can run on a single environment, which can run as both the enterprise hub and scale unit, or have two development environments, with one taking the role of the hub and the other taking the role of a scale unit. This setup provides the best way to identify and fix issues. The latest [early access (PEAP) build](https://forms.office.com/FormsPro/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxURUFWTjQzTzg0UUk5RkJHMDFEMVlSSDFEQy4u) can also be used to complete this stage.

You should use the [scale unit deployment tools for one-box development environments](https://github.com/microsoft/SCMScaleUnitDevTools) to install and maintain the environments. These tools let you configure hub and scale units in one or two separate one-box environments. The tools are provided as both a binary release and in source code on GitHub. Study the project wiki, which includes a [Step by step usage guide](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide) that describes how the tools are used. IF you are deploying [edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md), you must follow a different process.

## Option 2: Acquire add-ins and deploy in your sandbox environments

To try out the distributed hybrid topology, you need two sandbox environments (Tier 2), one with your data (enterprise hub) and one for the scale unit with "empty data".

You must acquire add-ins for at least one cloud or edge scale unit, which will grant corresponding project and environment slots in [LCS](https://lcs.dynamics.com/) so that the scale unit environments can be deployed using the [Scale Unit Manager portal](https://aka.ms/SCMSUM). Please contact Microsoft Support and we will enable these sandboxes for you.

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
