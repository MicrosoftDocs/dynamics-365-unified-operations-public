---
# required metadata

title: Add data fields in tax configurations
description: This topic explains how to customize tax configuration with data fields.
author: kailiang
manager: tfehr
ms.date: 03/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18
---

# Add data fields in tax configurations

This topic explains how to customize **Tax configuration** with [data fields added in the tax integration](tax-service-add-data-fields-tax-integration-extension.md).

## Microsoft Dynamics Regulatory Service setup

### Customize tax data model

1. Go to **Electronic Reporting** > **Tax configurations**.
2. Select **Tax Data Model - Europe** and then select **Create configuration**.

    [![Create configuration](./media/tax-service-customize-image3.png)](./media/tax-service-customize-image3.png)

3. Select the **Taxable document model derived from Name: Tax Data Model -- Europe, Microsoft** radio button, enter a name, and then select **Create configuration**.
4. Select the tax data model you just created and then select **Designer**.
5. Expend the data model tree, select **Lines**, and then select **New**.

    [![Click new](./media/tax-service-customize-image6.png)](./media/tax-service-customize-image6.png)

6. In the **Create node** dialog box, add the name and item type, and then select **Add**.
7. Add any required columns, select **Save**, and the select **Complete**.
8. Close the page and view the **Completed** version of your tax data model.

### Customize tax configuration

1. Go to **Electronic reporting** > **Tax configurations**.
2. Select **Tax Configuration -- Europe**, and then select **Create configuration**.
3. Select the **Tax service configuration derived from Name: Tax Configuration -- Europe, Microsoft** radio button, enter a name for the tax configuration, and then select **Create configuration**.
4. Select the tax configuration you just created, and then select **Designer**.
5. In the **Properties** field group, in the **Data model** drop-down list, select your customized tax data model.
6. In the **Data model version** field, select the completed version of the tax data model.
7. Select **Add**, and add the required tax measures.
8. Select **Save** and then select **Complete**.
9. Close page and view the **Completed** version of your tax configuration.

### Implement tax features on the customized tax configurations

1. Go to **Globalization Features** \>\> **Tax**.

[[![Go to globalization features, tax](./media/tax-service-customize-image19.png)](./media/tax-service-customize-image19.png)](./media/tax-service-customize-image19.png)

2. Create a new Tax feature, click **Create feature.**

[![Create new tax feature](./media/tax-service-customize-image20.png)](./media/tax-service-customize-image20.png)

3. Click **Edit**.

[![Edit tax feature](./media/tax-service-customize-image21.png)](./media/tax-service-customize-image21.png)

4. In **General**, **Configuration version**, select the customized tax configuration and version.

[![Select tax configuration version](./media/tax-service-customize-image22.png)](./media/tax-service-customize-image22.png)

5. You shall now be able to configure your tax features with customized columns and tax measures in the "Tax codes applicability" table.

[![Add customized columns](./media/tax-service-customize-image23.png)](./media/tax-service-customize-image23.png)
