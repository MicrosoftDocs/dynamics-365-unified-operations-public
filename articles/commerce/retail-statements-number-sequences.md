---
# required metadata

title: Retail statements number sequence setup
description: This topic describes how to configure the number sequences required for retail statements in MIcrosoft Dynamics 365 Commerce.
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

This topic describes how to configure the number sequences required for retail statements in MIcrosoft Dynamics 365 Commerce.

There are two types of retail statements used within Dynamics 365 Commerce. **Transactional statements** are intended to be created and posted at a high frequency and are utilized to post all non-financial transactions within the store to Dynamics 365 Commerce Headquarters. **Financial statements** are intended to be created and posted a single time per business day and will only include closed shifts from the retail stores that have been uploaded to headquarters through the p-job.

## Configure number sequence for statement posting

After you have completed the setup of a retail store, you must configure a unique number sequence in Commerce headquarters that will be used for statements during the statement creation process.

To configure number sequence for statement posting, follow these steps.

1. Go to **Organization administration \> Number sequences \> Number sequences**.
1. Enter the following information on the form:
    1. Under **Identification**, for **Number sequence code*** enter a number sequence code.
    1. FOr **Number sequence name**, enter a name.
    1. Under **Scope parameters** select **Operating unit** from the **Scope** drop-down list.
    1. Under **Segments**, select the store for which this number sequence will be used from the  the **Operating unit** drop-down list.
    1. Define the segments.
    1. Update the **Number allocation** to match the length of the **Alphanumeric** segment.
    1. Define the reference **Area** as **Retail store** and **Reference** as **Statement number** and select **Ok**.
    1. A recommendation is to enable the **Preallocation** toggle to **Yes** and set the **Quantity of numbers** to **25**.
 1. Save the new **Number sequence** and close the form.

[!Statement number sequence setup sample 1](./media/retail-statements-num-seq-setup-01.png)](./media/retail-statements-num-seq-setup-01.png)

[!Statement number sequence setup sample 2](./media/retail-statements-num-seq-setup-02.png)](./media/retail-statements-num-seq-setup-02.png)
