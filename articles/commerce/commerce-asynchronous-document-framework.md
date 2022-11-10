---
title: Commerce asynchronous document framework
description: This article describes capabilities and configurations of Commerce asynchronous document framework.
author: hhainesms
ms.date: 09/17/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: hhaines
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.9
ms.custom: 
ms.assetid: 
ms.search.industry: Retail
ms.search.form: 
---

# Commerce asynchronous document framework

[!include [banner](includes/banner.md)]

Store inventory operations such as Inbound, Outbound, Stock Count, Adjustment, and Movement  include performance improvements to ensure that users who have high volumes of receipt postings across many stores or companies, and large inventory documents, can process those documents to Commerce Headquarters without experiencing time-outs or failures. These improvements require use of an asynchronous document framework.

When an asynchronous document framework is used, you can commit inventory document changes from POS to Commerce Headquarters and then move on to other tasks while the processing to Commerce Headquarters occurs in the background. You can check the status of a document through each operation's document list page in POS to make sure that posting was successful. In the POS application, you can also use each operation's document list to see any documents that could not be posted to Commerce Headquarters. If a document fails, POS users can make corrections to it and then try again to process it to Commerce Headquarters.

## Configure an asynchronous document framework

> [!IMPORTANT]
> The asynchronous document framework must be configured before a company tries to use the store inventory operations in POS.

To configure an asynchronous document framework, complete the following procedures.

### Create and configure a number sequence

1. Go to **Organization administration \> Number sequences \> Number sequences**.
2. On the **Number sequences** page, create a number sequence.
3. In the **Number sequence code** and **Name** fields, enter user-defined values.
4. On the **References** FastTab, select **Add**.
5. In the **Area** field, select **Commerce parameters**.
4. In the **Reference** field, select **Retail document operation identifier**.
5. On the **General** FastTab, in the **Setup** section, set the **Continuous** option to **No** to ensure that there are no performance issues.

### Create and schedule two batch jobs for the document processing and monitoring tasks

> [!NOTE]
> In Commerce version 10.0.13 and later, you don't have to configure these batch jobs through the batch job framework. The batch processes can be configured from the **Retail and Commerce  >Retail and Commerce IT** menu. Use the **Retail document operation monitor** and **Retail document operation processing** menu options to configure the batch jobs.

The batch jobs that you create will be used to process documents that fail or time out. They will also be used when the number of active inventory documents that are being processed from POS exceeds a system-configured value.

1. Go to **System administration \> Inquiries \> Batch jobs**.
2. On the **Batch job** page, create two batch jobs:

    - Configure one job to run the **RetailDocumentOperationMonitorBatch** class.
    - Configure the other job to run the **RetailDocumentOperationProcessingBatch** class.

2. Schedule the new batch jobs to run on a recurring basis. For example, set the schedule so that the jobs are run every five minutes.

## Related articles

[Inbound inventory operation in POS](pos-inbound-inventory-operation.md)

[Outbound inventory operation in POS](pos-outbound-inventory-operation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
