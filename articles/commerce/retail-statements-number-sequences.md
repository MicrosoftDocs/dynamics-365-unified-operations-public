---
# required metadata

title: Retail statements number sequence setup
description: This topic describes how to configure the number sequences required for retail statements in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 04/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: analpert
ms.search.validFrom: 2022-04-12
ms.dyn365.ops.version: 10.0.21
---

# Retail statements number sequence setup

[!include [banner](includes/banner.md)]

This topic describes how to configure the number sequences required for retail statements in Microsoft Dynamics 365 Commerce.

There are two types of retail statements used within Dynamics 365 Commerce: 

- **Transactional statements** are intended to be created and posted at a high frequency and are used to post all non-financial transactions within the store to Dynamics 365 Commerce headquarters. 
- **Financial statements** are intended to be created and posted a single time per business day and will only include closed shifts from the retail stores that have been uploaded to headquarters through the p-job.

## Configure number sequence for statement posting

After you have completed the setup of a retail store, you must configure a unique number sequence in Commerce headquarters that will be used for statements during the statement creation process.

To configure number sequence for statement posting in headquarters, follow these steps.

1. Go to **Organization administration \> Number sequences \> Number sequences**.
1. Under **New**, select **Number sequence** to create a new record.
1. On the **Identification** FastTab, for **Number sequence code** enter a number sequence code.
1. For **Number sequence name**, enter a name.
1. On the **Scope parameters** FastTab, under **Scope** select **Operating unit** from the drop-down list.
1. For  **Operating unit**, select the store for which this number sequence will be used from the drop-down list.
1. On the **Segments** FastTab, define the segments.
1. On the **References** FastTab, define the reference **Area** as **Retail store**.
1. Define **Reference** as **Statement number**, and then select **OK**.
1. Update the **Number allocation** to match the length of the **Alphanumeric** segment.
1. It is recommended that you set the **Preallocation** option to **Yes**, and set the **Quantity of numbers** to **25**.
1. Save the new **Number sequence** and close the form.

![Statement number sequence setup sample 1](media/retail-statements-num-seq-setup-01.png)

![Statement number sequence setup sample 2](media/retail-statements-num-seq-setup-02.png)
