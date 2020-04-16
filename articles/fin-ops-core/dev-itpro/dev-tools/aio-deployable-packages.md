---
# required metadata

title: All-in-one deployable packages (ADP)
description: This topic describes the all-in-one deployable package (ADP) concept and its use. 
author: laneswenka
manager: AnnBe
ms.date: 04/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang:
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: 10.0.9

---
#
# All-in-one deployable packages (ADP)

Customers can update the software of their environments by applying a Software deployable package.  These packages can originate from the customer themselves in the form of customizations, and they can also be provided by partners and Independent Software Vendors (ISVs).  Microsoft&#39;s recommendation is to combine these various packages into a single package before applying to an environment.  This is also a hard requirement for customers with self-service environments.

This topic outlines the best practice strategy for creating and managing a All-in-one deployable package (ADP).

## **What is an All-in-one deployable package?**

An All-in-one deployable package is a software deployable package that contains all of the models and binaries you currently have on an environment.  Think of it as if you were to represent all of the non-Microsoft software of an environment into a single package.

For example, let&#39;s take a look at two environments one called SandboxTest and another called SandboxPreProd.

<img src="media/AIO_PKG.png" width="500px" alt="All-in-one deployable package comparison" />

If your software deployable package contains CustomizationA, CustomizationB, and ISV1 then it is a fully deployable package for both **SandboxTest** as it matches the model list exactly.

It is also a fully deployable package for **SandboxPreProd** because it has all of the models installed here too, plus the extra CustomizationB.

If your software deployable package contains only CustomizationA, then it is not fully deployable for either environment, as it is missing models as compared to what is already installed.

## **How do I create an ADP?**

There are two primary methods for creating a ADP.  If you are using our continuous integration / continuous deployment model, you&#39;re already creating ADPs.

If you don&#39;t have a build environment, you can create a package from Visual Studio following this document: [https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/create-apply-deployable-package](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/create-apply-deployable-package)

## **What about my ISV packages that don&#39;t contain source code?**

ISVs can choose whether to share their source code with you or not.  If they don&#39;t then they will be providing a binary-only package.  This can also easily be managed in to a ADP by following this document:[https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/manage-runtime-packages](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/manage-runtime-packages)

**Why are these packages important?**

The best practice of using fully deployable packages is to reduce the complexity and number of packages that are applied to a given environment.  There are circumstances where installing disparate packages can change the behavior of your environment if you install ModelA and then ModelB, as compared to ModelB then ModelA.

In addition, this is a hard requirement for Self-service environments.  That is because these environments use containerization technology and build a brand new environment each time you apply a package.  If you apply ModelA today, and then only ModelB tomorrow you will effectively uninstall ModelA.