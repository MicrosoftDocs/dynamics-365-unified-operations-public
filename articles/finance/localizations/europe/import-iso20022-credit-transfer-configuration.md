--- 
title: Import ISO20022 credit transfer configuration
description: Learn how to import a vendor payment electronic reporting configuration with Microsoft Dynamics 365 Finance.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/01/2026
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport 
---

# Import ISO20022 credit transfer configuration

[!include [banner](../../includes/banner.md)]

This article explains how to import a vendor payment electronic reporting configuration using Microsoft Dynamics 365 Finance.

Complete the steps in the following procedure to import a vendor payment electronic reporting configuration. The German ISO 20022 credit transfer format is used as an example. You can use these steps for other available electronic reporting formats.

The procedure uses the demo data company DEMF, but you can use any demo data company.

1. In Dynamics 365 Finance, go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. In the list of available configuration providers, select **Microsoft**.
3. Select **Set active**.
4. Select **Repositories** to open the repositories page.
5. Select **Dataverse** and click **Open**.
6. Select **Show filters**.
7. In the **Configuration name** field, use the **Begins with** filter operator, and enter one of the following filter values:

- For an unstructured payment file, enter **ISO20022 Credit transfer (DE)**.
- For a structured payment file, enter **ISO20022 Credit transfer 2019 (DE)**.

Alternatively, find the configuration in the list, select it, and then move it to the **Import** task.

1. Select **Import**.
2. Select **Yes**.

  > [!NOTE]
  > If the **Import** button isn't available, the configuration has been imported.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
