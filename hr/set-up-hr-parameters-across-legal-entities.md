---
# required metadata

title: Set up HR parameters across legal entities
description: You must set up shared parameters for records that are shared across companies, such as Position records. This article explains how to set up Human resources parameters across legal entities.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmSharedParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 51891
ms.assetid: c7d8f58c-d78a-4035-abbf-2b0ce16109fe
ms.search.region: Global
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up HR parameters across legal entities

[!include[banner](includes/banner.md)]


You must set up shared parameters for records that are shared across companies, such as Position records. This article explains how to set up Human resources parameters across legal entities.

Some types of records, such as Position records, are shared across companies. For these records, you must set up shared parameters. For example, you use the **Human resources shared parameters** page to set up Human resources parameters across legal entities. 

On the **Human resources shared parameters** page, parameters are grouped into areas, based on their functionality. 

On the **Identification** tab, you must select the identification types that represent the identification numbers that are listed on the page. You must set up identification types before you can enter identification information for workers. Information about the Social Security number, national ID number, alien ID number, and personal ID code is maintained on the **Identification type** page. To define a new identification type or review the list of existing types, click **Human resources** &gt; **Setup** &gt; **Identification types**. You can enter a simple code and description. 

On the **Number sequences** tab, you can select the number sequences that are used for the following records: Personnel number, Position, User request ID, I-9 document, Applicant, Discussion, Benefit ID, and Personnel action (if this record type is enabled). To maintain number sequence references and codes, use the **Number sequences** list page. To find this page, use the page search feature. 

On the **Positions** tab, indicate whether new positions are available for assignment by default:

-   **Always** – You can assign workers to new positions when positions are created. When positions are created, the **Available for assignment** date and time on the **General** tab of the **Position** page are automatically set to the creation date and time.
-   **Never** – You can't assign workers to new positions when positions are created. If you select this option, you must open the **Position** page for each new position as it becomes available, and then, on the **General** tab, enter the **Available for assignment** date to enable worker assignment.


See also
--------

[Set up company specific HR parameters](set-up-company-specific-hr-parameters.md)



