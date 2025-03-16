---
title: Advanced quality management overview (preview)
description: 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Advanced quality management overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Advanced quality management is a suite of quality-management features introduced in Supply Chain Management version 10.0.44. It enhances the quality management features that were already available by adding many new tools that address core issues that manufacturers face to meet the U.S. Food and Drug Administration's (FDA) Quality System Regulation 21 CFR Part 11, cGMP and other various regulatory and international standards such as ISO and Six Sigma. <!-- KFM: is this too narrow a description? Should we describe this has having broader applications? Mention here (and/or in Prerequisites) that these features mostly require the Inventory module (not WMS)? -->

:::image type="content" source="media/advanced-quality-management-overview.png" alt-text="Overview of advanced quality management features." lightbox="media/advanced-quality-management-overview.png":::

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *Approved customer list* – <!-- KFM: briefly list/describe the capabilities added by this feature -->
    - *Dispense management* – <!-- KFM: briefly list/describe the capabilities added by this feature -->
    - *Electronic signature improvements* – <!-- KFM: briefly list/describe the capabilities added by this feature -->
    - *Advanced quality management* – <!-- KFM: briefly list/describe the capabilities added by this feature -->

## Key features of advanced quality management

Some of the key industry-specific capabilities of the solution are:

- **Corrective Actions/Preventive Actions (CAPA)** – This feature allows users to automate processes to manage, track, and correct root causes of issues and to implement action plans to prevent the same and similar issues going forward. Learn more in [Corrective and preventive action (CAPA) management overview (preview)](capa-overview.md).

- **Electronic signature requirement for CAPA case closure** – This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off. Learn more in [CAPA management administration (preview)](capa-admin.md)

- **Flexible sampling plans** – This feature enables companies to inspect a fraction of a lot, or to skip lots altogether, to realize reduced quality and material handling costs, faster material throughput, and less redundant and destructive testing. Learn more in [Flexible sampling plans (preview)](quality-flexible-sampling-plans.md)

- **Approved customer lists (ACL)** – This feature provides greater control over what products a given customer can buy and when they can buy them, which is especially important with a product line that involves controlled substances and branded products. Learn more in [Approved customer lists (preview)](../sales-marketing/approved-customer-lists.md)

- **Electronic signature** – This feature enhancement provides greater security of the digital signatures to meet the latest government requirements and regulations.

- **Electronic Batch Record (EBR)** – This feature enables users to view all the versions, methods, and characteristics for consumed BOM and Formula items. This is referred to as a Master Manufacturing Record that maintains all the methods that could be utilized to produce the item. This feature also allows users to view and print reports of the actual versions, test values, attribute values, quality order results of all the items produced and the ingredients consumed. This is referred to as a Batch Production Record that captures the actual version and methods used to produce the item.

- **Instrument calibration** – This new feature adds capability around tracking individual test instrument tags, supports an on-going calibration process for the instrument tag and tracks usage of given tags against the quality order tests.

- **Quality associations for return and transfer orders** – This feature enhances the capability of quality associations by offering the ability to automatically create quality orders triggered from a sales return or a transfer order. Learn more in [Quality associations](quality-associations.md).

- **Customer-specific COAs** – This feature supports the setup and application of customer COA requirements. The specific customer will drive details such as whether a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results (pass and/or fail) should be replaced with standard verbiage. In addition, customer-specific COA's can be generated automatically from the sales order packing slip posting process.

- **Production dispensing** – This feature enables users to segregate the dispensing area and activities from the picking activities.

- **Quick test results entry** – This feature enables users to very quickly and easily enter test results on a quality order from a consolidated view which includes visibility to test minimum, maximum and target values. Learn more in [Quick Results Entry](quality-quick-results-entry.md)

- **Quality order usability improvements** – Several usability improvements were added to the quality order process. The option to skip a quality order test has been added. When a decision is made not to perform a test on a given quality order, that can now be noted on the quality order without losing visibility to the original test. When a test is skipped, all validations on the test is by-passed and the test is changed to not be included in results so that AQL calculations are still performed on the remaining tests. Quality order "Priority" Level and "Assigned to" tester are new data elements on the quality order that can be used to sort and filter on the quality work that needs to be completed. Result notes can now also be recorded for a given test result line. Finally, test instrument tags are always checked to see if the selected tag is already on an open quality order. This validation is not important to all businesses so now there is a parameter that drives this functionality, and the validation can be skipped if not required.
