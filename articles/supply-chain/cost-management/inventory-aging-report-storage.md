---
# required metadata

title: Inventory aging report storage
description: This article describes the functionality that lets you run an Inventory aging report and make the output available as a form and a chart.
author: JennySong-SH
ms.date: 11/11/2019
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2019-01-10
ms.dyn365.ops.version: 

---

# Inventory aging report storage

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, you can run an **Inventory aging report storage** report and make the output available as a form and a chart. In the form, columns and aggregate balances are dynamically adjusted, depending on the layout that is configured. The chart provides a visual overview that supports filtering and lets you drill down into details. Additionally, a data entity that is named **Inventory aging report** lets you export the results of an **Inventory aging report storage** report run to a format such as a Microsoft Excel file or a PDF file.

This method of running an **Inventory aging report storage** report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have 50,000 items and 300 stores that are created as warehouses, and you request inventory aging by item, site, and warehouse.

## Turn the Inventory value storage report feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Inventory aging report storage* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Run an Inventory aging report storage

1. Go to **Cost management \> Inquiries and reports \> Inventory aging report storage**.
1. Select **New**.
1. In the **Process Identifier – Name** field, enter a unique name for the report.
1. Select the **Identification – ID** report, and filter it as you require.

    Report execution is always done in a batch job.

1. After the batch job is completed, the output is shown on the **Inventory aging report storage** page.
1. To view the output as a form that has a traditional grid layout, select **View details**. To view the output as an aggregated chart, select **View chart**.

    > [!NOTE]
    > The form won't include subtotals that are defined in the report layout.

The **Inventory aging report** data entity lets you export the output of an **Inventory aging report storage** report by applying a filter for the **Process Identifier – Name** field to any format that Data management supports.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]