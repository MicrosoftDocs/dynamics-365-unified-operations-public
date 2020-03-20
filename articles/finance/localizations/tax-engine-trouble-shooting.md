---
# required metadata

title: Troublshooting GTE 
description: This topic provides information about some of the more common issues you might run in to while using GTE, and how to resolve them.
author: yijialuan
manager: Annbe
ms.date: 03/18/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable
audience: Application User
# ms.devlang:
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.search.region: India
# ms.search.industry:
ms.author: riluan
ms.search.validFrom: 07/30/2019
ms.dyn365.ops.version: 7.3
---

# Troubleshooting GTE

[!include [banner](../includes/banner.md)]

The tax engine is a highly configurable engine that handles tax applicability, calculation, posting, and settlement. This topic lists the common issues that users run in to while using it, and how to resolve those issues..

> [!NOTE]
> The tax engine functionality is available only for legal entities with a primary address in India.

For a quick overview of the tax engine, watch [Tax engine overview (YouTube video)](https://www.youtube.com/watch?v=jAFpEBOtNWI&feature=youtu.be).

## Debug mode

Familiarity with the debug mode of the tax engine can help you to identify the root causes of issues related to the tax engine.

To enable debug mode, you should append **&debug=vs%2CconfirmExit&** to the URL of Dynamics 365 Finance.

![Enable debug model](media/GTE-debug-mode.png)

With debug mode enabled, the system will generate a dump file that contains runtime details when you open the tax document.

![Dump tax engine runtime information](media/GTE-debug-mode-download-file.png)

The structure of the dump file as below. The section, **Data model mapping mismatch** is only available if **Check model mapping discrepancies** is enabled.

```
======Tax engine calculation parameter======
...
===========Taxable document JSON===========
...
=====Tax engine runtime posting profiles=====
...
========Data model mapping mismatch========
Unmatched data provider fields
...
Unmatched taxable document fields
...

=====Tax engine runtime posting profiles=====
Header - TaxDocLine: TableId=6791 RecId=68719507754:
Line - TaxDocLine: TableId=13307 RecId=68719685245:
Path of the tax component 1:
-"Posting profile 1 description(Hit)"
-"osting profile 2 description"
...
Path of the tax component 2:
-"Posting profile 1 description(Hit)"
-"Posting profile 2 description"
...
Line - TaxDocLine: TableId=13307 RecId=68719685245:
...
```

## Possible issues

### Imbalanced voucher with GST

The issue can happen after you extend the GST configuration by adding or modifying the posting profile.

Per the current design, each tax component has a set of posting profiles to handle all possible tax postings. The tax engine picks up the first matched posting profile in runtime.

![GST posting profiles](media/GST-posting-profiles.png)

Sometimes, if you add or modify the posting profiles without carefully handling the condition of each posting profiles, it might result in the pick up of unexpected posting profiles during runtime.

In debug mode, you can easily find the selected posting profiles in the **Tax engine runtime posting profiles** section of the dump file.

### Incorrect tax rate/tax component

The tax engine relies on the input from taxable documents, such as sales and purchase invoices to work properly. If you extend the configuration by adding new fields, it's possible that fields may inadvertantly be mapped incorrectly or that the writing to the data provider wasn't correct. To identify the issue, turn on **Check model mapping descrepancies**. You can view an addtional section to show the descrepancies.

![GTE model mapping descrepancies](media/GTE-model-mapping-deprepancies.png)

### Incorrect tax component

When you can't see the expected tax components, it means the transaction can't satisfy the [applicability](../general-ledger/tax-engine-applicability.md) rules of the tax component or the tax type. If you extended the configuration, verify that there are no descrepancies and then compare the fields value in the section **Taxable document JSON** in the dump file, with the applicability rules of the tax component.

### Incorrect tax rate

When you can't see the expected tax rate, check the field values that are used in the [tax setup](apac-ind-GST-set-up-rate-percentage-tables.md) and compare them with the fields value in **_Taxable document JSON_** section in the dump file.

## Can't post the voucher with GST

YOu may encounter an error similar to the following:

<span style="color:red">Unable to find ## in the setoff hierarchy ## version ##, please check and try again</span>. 

Typically, this error occurs because the configuration was extended by adding a new tax component or modifying the credit pool.

1. To work around this issue, add a newer version into the current **Sales tax hierarchies**, select **Synchronize** and then activate it. 
2. Next, following the [Set up a sales tax hierarchy](apac-ind-GST-set-up-activate-tax-hierarchy-tree.md) steps, enable the new version in the **Maintain setoff hierarchy profiles** page.

![Add new version of sales tax hierarchies](media/IND-GST-add-new-hierarchy.png)
