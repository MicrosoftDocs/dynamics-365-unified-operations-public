---
# required metadata

title: Microsoft Dynamics 365 Finance business performance planning requirements
description: This article describes the requirements to install Microsoft Dynamics 365 Finance business performance planning.
author: ShielaSogge
ms.date: 11/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: 
---
# Microsoft Dynamics 365 Finance business performance planning requirements

This article describes the requirements to install business performance planning.

## System requirements

A Tier-2 environment (multi-box) is required to install business performance planning. For more information about environments, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md). Business performance planning is currently supported in the following geographies: Australia, Brazil, UK, USA, Europe, Canada, France, Germany, India, Norway, Switzerland, UAE, South America, South Africa and Japan. Confirm the environment where you plan to install Business performance planning is in one of the above mentioned regions.

## Version requirements

While not required, Dynamics 365 Finance version 10.0.37 and PU 61 provides additional options for getting general ledger information into a balance format via process automations.

## Prerequisites

Before you can install business performance planning, the Power Platform environment must be created.

In order to use the functionality in Dynamics 365 Finance business performance planning, a finance premium license must be purchased, and available on the tenant.

>[!Important]
>If a finance license isn't purchased, business performance planning will not display in the Power Platform Admin Center as a Dynamics 365 app to install. To perform any planning operations, you will need a finance premium license.

To find out more about finance licensing, see [Finance pricing](https://dynamics.microsoft.com/finance/pricing/).

## Install

There are two main components for installing Dynamics 365 for Finance business performance planning (preview):

1.  Install the planning application from Power Platform admin center [Install the business performance planning app](bpp-App-install.md)
2.  Installing the Power BI visuals from Appsource (Link to PBI Install doc)
