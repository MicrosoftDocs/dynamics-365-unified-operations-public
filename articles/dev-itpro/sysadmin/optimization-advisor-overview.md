---

# required metadata

title: Optimization advisor overview
description: This topic discusses what tools you have avaialble to ensure optimal cofiguration of your Dynamics 365 Finance and Operations, Enterprise Edition installation. 
author: roxanadiaconu
manager: AnnBe
ms.date: 02/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SelfHealingWorkspace
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core (Operations, Core)
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: roxanad
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: 7.3 

---

# Optimization advisor overview

[!include[banner](../includes/banner.md)]

This topic explains what tools you have available to ensure optimal configuration and smooth operation of your Dynamics 365 Finance and Operations, Enterpise Edition installation.

## Overview

The availability and performance of the ERP installation and the smooth operation of business processes are negatively affected by incorrect or incomplete module configuration and setup. Another major impacting factor is business data correctness, completeness and cleaness.   
The **Optimization advisor** is a tool that enables power users, business analysts, functional consultants and various IT support functions to identify configuration and business data issues. The **Optimization advisor** suggests configuration best practices and points out what business data is obsolete or incorrect.

The **Optimization advisor** runs a set of best practice rules, on a perodic basis. When a violation of a rule is detected, an optimization opportunity is created and displayed in the **Optimization advisor** page. A user can take corrective action from the **Optimization advisor** page direclty and fix the best practice violation.

Standard security policies apply to optimization opportunties. For example, optimization opportunities related to the **Warehouse management** module configuration are visible only to users that have access and can make changes to **Warehouse managemnet** setup.
Opportunites are displayed in the language of the end user.

To complement the set of rules that are shipped with the standard version, you can create rules that are specific to your customizations, ISV solutions and business data. The process of creating a new rule is described [in this article](./optimization-advisor.md).

For more information, watch the short YouTube video:

> [!Video https://www.youtube.com/embed/MRsAzgFCUSQ]




