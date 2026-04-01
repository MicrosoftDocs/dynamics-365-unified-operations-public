---
title: All-in-one deployable packages
description: Learn about the all-in-one deployable package concept and its use, including best practices for creating and managing packages.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: 10.0.9
---

# All-in-one deployable packages

[!include [banner](../includes/banner.md)]

Customers can update the software in their environments by applying software deployable packages. These packages can originate from the customers themselves in the form of customizations. They can also come from partners and independent software vendors (ISVs). Microsoft recommends that customers combine all these various packages into a single package before they apply them to an environment. For customers who have self-service environments, this approach is a hard requirement.

This article outlines the best practices for creating and managing an all-in-one deployable package.

> [!IMPORTANT]
>
> - The enforcement of all-in-one packages is done in phases. Requests to extend the support for deployable packages that aren't all-in-one deployable packages ended on October 31, 2020.
> - If you currently deploy a payment connector in your environment, you need to [create a payment connector package](../../../commerce/dev-itpro/payment-connector-package.md) and include it in the all-in-one deployable package.
> - If you currently use Microsoft Dynamics 365 Commerce functionality for the retail point of sale, you also need to [synchronize self-service installers](../../../commerce/dev-itpro/Synchronize-installers.md). For Commerce Scale Unit, see [Deploy the package to CSU](../../../commerce/dev-itpro/retail-sdk/retail-sdk-packaging.md#deploy-the-package-to-csu).

## What is an all-in-one deployable package?

An all-in-one deployable package is a software deployable package that contains all the models and binaries that you currently have in an environment. Think of it as a single package that represents all the non-Microsoft software in an environment.

For example, you have two environments: **SandboxTest** and **SandboxPreProd**.

:::image type="content" source="media/AIO_PKG.png" alt-text="Screenshot of all-in-one deployable package comparison.":::

If your software deployable package contains CustomizationA, CustomizationB, and ISV1, it's a fully deployable package for the SandboxTest environment. This status exists because it exactly matches the model list. It's also a fully deployable package for the SandboxPreProd environment because it has all the models that are installed, plus CustomizationB.

However, if your software deployable package contains only CustomizationA, it isn't fully deployable for either environment. The package is missing some of the models that are already installed.

## How do I create an all-in-one deployable package?

Use one of the following methods to create an all-in-one deployable package:

- Use the continuous integration and continuous deployment (CI/CD) model to create all-in-one deployable packages.
- Use Microsoft Visual Studio to create a package if you don't have a build environment. For more information, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md).

## What if my ISV packages don't contain source code?

ISVs decide whether to share their source code with you. If they don't share it, they provide a binary-only package. You can easily manage this package into an all-in-one deployable package. For instructions, see [Manage third-party models and runtime packages by using source control](manage-runtime-packages.md).

## How can I deploy ISV licenses?

ISVs can send license deployable packages to provide or update a license. However, for self-service environments, include licenses in an all-in-one deployable package. You can add a task to your build or release pipelines to add any licenses you have to a deployable package. For more information, see [Add license files to a deployable package in Azure Pipelines](pipeline-add-license-package.md).

## Why are these packages important?

Using fully deployable packages reduces the complexity and number of packages that you apply to a given environment. In some circumstances, installation of different packages can change the behavior of your environment. For example, if you install ModelA and then ModelB instead of ModelB and then ModelA.

In addition, this approach is a hard requirement for self-service environments. These environments use containerization technology and build a brand-new environment every time that you apply a package. If you apply ModelA today and then apply only ModelB tomorrow, you effectively uninstall ModelA.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
