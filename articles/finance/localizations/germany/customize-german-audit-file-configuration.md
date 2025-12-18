--- 
title: Customize German audit file configuration
description: Learn how to customize the German audit file configuration by adding a new table group and selecting a table with fields for data export definition in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak    
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, ERTableNameLookup, ERModelGDPdUFunctionEditor,  ERExpressionDesignerFormula
---

# Customize German audit file configuration

[!include [banner](../../includes/banner.md)]

This article explains how to customize the German audit file configuration by adding a new table group and selecting a table with fields for data export definition in Microsoft Dynamics 365 Finance.

The following procedure was created using the demo data company DEMF with Germany as the country/region of legal entity primary address.

To add a new table group and select a table with fields for data export definition, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration > Workspaces > Electronic reporting**.
1. Select **Configurations**.
1. Select **Show filters**.
1. Add filter.
1. Select **Apply**.
1. Select **Model designer**.
1. In the tree, select **enumTableGroup**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Enter a value in the **Description** field.
1. Select **Map model to datasource**.
1. Select **Designer**.
1. In the tree, select **Dynamics Ax\Table records**.
1. Select **Add root**.
1. In the **Name** field, enter a value.
1. In the **Table** field, enter or select a value.
1. Select **OK**.
1. In the tree, select **Functions\Table metadata**.
1. Select **Add root**.
1. In the **Name** field, enter a value.
1. In the **Label** field, enter a value.
1. Select **Editor**.
1. In the tree, select **AssetTable**.
1. Select **Add**.
1. In the **Name** field, enter a value.
1. In the tree, expand **AssetTable**.
1. In the tree, select **AssetTable\Fixed asset number(AssetId)**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Name** field, enter a value.
1. Close the page.
1. Select **Yes**.
1. Select **OK**.
1. In the tree, select **TblGroup**.
1. Select **Edit**.
1. Select **Edit formula**.
1. In the **expressionAsStringText** field, enter a value.
1. In the tree, expand **enumTableGroup**.
1. In the tree, select **enumTableGroup\Anlagen**.
1. Select **Add data source**.
1. In the **expressionAsStringText** field, enter a value.
1. In the tree, select **_05Anlagen(TblGroup5)**.
1. Select **Add data source**.
1. In the **expressionAsStringText** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. Close the page.
1. Select **Yes**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Enter a value in the **Description** field.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
