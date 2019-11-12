---
# required metadata

title: Improvement of bank accounts setup
description: This topic provides information about how to save time and simplify bank data registration for customers and vendors.
author: ilkond
manager: AnnBe
ms.date: 11/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-29
ms.dyn365.ops.version: 10.0.7

---

# Bank data usability enhancement

[!include [banner](../includes/banner.md)]

Companies often need to enter and maintain a large amount of banking information. The cost of entering incorrect bank information can be very high. This topic explains how to save time and simplify bank data registration by importing Italian bank information from reliable sources, and how reduce the risk of making mistakes using bank data for customers and vendors.

## Prerequisites
Before you begin, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The feature, **Bank account setup enhancement** must be enabled in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Import bank groups

Import the list of banks using the **Bank groups** entity and the **Data management** framework.
For more information, see [Data import and export jobs overview](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/data-import-export-job?toc=/fin-and-ops/toc.json).

The source data for bank import can be presented as a Microsoft Excel file with the following column structure:

| Column names        |
|---------------------|
| BANKGROUPID         |
| ADDRESSCITY         |
| ADDRESSCOUNTRY      |
| ADDRESSCOUNTY       |
| ADDRESSDESCRIPTION  |
| ADDRESSDISTRICTNAME |
| ADDRESSLATITUDE     |
| ADDRESSLOCATIONID   |
| ADDRESSLONGITUDE    |
| ADDRESSSTATE        |
| ADDRESSSTREET       |
| ADDRESSTIMEZONE     |
| ADDRESSVALIDFROM    |
| ADDRESSVALIDTO      |
| ADDRESSZIPCODE      |
| NAME                |
| ROUTINGNUMBER       |
| ROUTINGNUMBERTYPE   |
| STATEMENTFORMATID   |
| SUFFIX              |
| BRANCHNAME_IT       |

> [!NOTE]
> The **BANKGROUPID** must have the same value as the **ROUTINGNUMBER**.

## Use the enhanced list of bank groups

When the **Bank account setup enhancement** feature is enabled, additional descriptive fields  **Bank branch name** and **City** are available for bank groups.

![Clearing the main account](media/emea-ita-exil-bank-pic.jpg)

During the bank account set up, the list of bank groups additional descriptive fields are available for more precise banks selection.

![Clearing the main account](media/emea-ita-exil-bank-pic2.jpg)
