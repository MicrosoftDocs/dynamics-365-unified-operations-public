---
# required metadata

title: Vendor aging report storage
description: This article describes the process of using external storage for vendor aging data. 
author: sunfzam
ms.date: 04/15/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---
# Vendor aging data storage

This article describes the process of using external storage for vendor aging data. In Microsoft Dynamics 365 Finance, the **Vendor aging data storage** process makes the output available for export to an external system. When you run the process, the same aging report options are available to external systems. The details are included in the exported data.

It can be useful to make vendor aging data available to an external system for storage in cases where the output contains a large number of transactions. If the existing **Vendor aging** report times out because there's too much data, this feature provides an alternative way to get the same data.

## Enable the Vendor aging data storage feature

Before you can use this feature, it must be enabled. Administrators can use the feature management settings to check the status of the feature and enable it if it's required. 

- In the **Feature management** workspace, enable the **Vendor aging data storage** feature.

## Run the Vendor aging data storage process

1. Go to **Accounts payable \> Inquiries and reports \> Vendor aging data storage**.
2. Select **New**.
3. In the **Name** field, enter a name for the process.
4. Set the remaining parameters as required.

    > [!NOTE]
    > Transaction details are always included, and the processing is always done in a batch job.

5. Select **OK**.
6. Refresh the **Vendor aging data storage** page to see the batch name, batch runtime, and processing status. When the batch job is completed, the **Processing status** field is set to **Ended**, and the **Number of aging lines** field is set. If the batch job is recurring, the **Processing status** field is set to **Waiting**. Record the **Execution name**.
7. Go to **Data management framework**, select the "Vendor aging data storage" entity.
8. Export the records after adding **Filter**. Set **Execution name** in **Vendor aging data storage** with the **Execution name**.

The **Vendor aging data storage** page doesn't include the results. However, the **Vendor aging data storage** data entity lets you export the output to any format that Data management supports.
