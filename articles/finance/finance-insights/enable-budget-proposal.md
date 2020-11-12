---
# required metadata

title: Enable budget proposals (preview)
description: This topic explains how to turn on the Budget proposal feature in Finance Insights.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-24
ms.dyn365.ops.version: AX 10.0.13

---
# Enable budget proposals (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic explains how to turn on the Budget proposal feature in Finance Insights.

1. Use information from the environment page in Microsoft Dynamics Lifecycle Services (LCS) to connect to the primary instance of Azure SQL for that environment. Run the following Transact-SQL (T-SQL) command to turn on flights for the sandbox environment. (You might have to turn on access for your IP address in LCS before you can connect remotely to Application Object Server \[AOS\].)

    `INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('BudgetIntelligentBudgetRegisterProposalFeature', 1)`

    > [!NOTE]
    > If your deployment of Microsoft Dynamics 365 Finance is a Service Fabric deployment, you can skip this step. The Finance Insights team should already have turned on the flight for you. If you don't see the feature in the **Feature management** workspace, or if you experience issues when you try to turn it on, send email to the [Finance Insights App Preview team](mailto:fiap@microsoft.com).

2. After step 1 from the previous page, **Enabled cash flow forecasting**, open the **Feature management** workspace, and follow these steps:

    1. Select **Check for updates**.
    2. Search for **Budget proposal**, and turn on that feature.

3. Go to **Budgeting \> Setup \> basic Budgeting \> Budget proposal (preview)**, and select **Enable feature**.

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
