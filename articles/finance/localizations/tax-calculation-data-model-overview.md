---
# required metadata

title: Tax calculation data model overview
description: This topic provides information about how the values for the fields in tax data model are determined during tax calculation transactions.
author: kailiang
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
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
ms.author: kailiang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21

---
# Tax calculation data model overview

This topic provides information about how the values for the fields in tax data model are determined in tax calculation transactions.

**Tax Data Model** is constructed with fields required for tax calculations. Microsoft provides the **Tax Calculation Data Model** which is composed of the header fields and line fields of transaction documents in Dynamics 365 F&O. The fields defined in the tax calculation data model are the available columns of the applicability rules tables in the tax calculation feature configuration.

> [!Note] A few special nodes (such as Record id, Table id, etc.) defined in the data model are for technical purposes. They are not available columns in the tax calculation feature configuration.

To explore the **Tax Calculation Data Model**.
1.  Log in **Regulatory Configuration Service > Electronic reporting > Tax configurations**.
2.  Select **Tax Data Model > Tax Calculation Data Model**.
3.  Select a version (E.g., 40.46) in the **Versions** FastTab.
4.  Click the **Designer** button on the menu.
[![Data model designer (button)](./media/tax-calculation-model-mapping-1.png)](./media/tax-calculation-model-mapping-1.png)
5.  Expand the Tax service node.
6.  Expand Header node to explore the header data models.
7.  Expand Lines node to explore the line data models.
[![Data models](./media/tax-calculation-model-mapping-2.png)](./media/tax-calculation-model-mapping-2.png)

You can also explore the tax calculation data model as the available columns in the applicability rules table.
1.  Log in **Regulatory Configuration Service > Globalization features > Tax calculation**.
2.  Click **Edit** button of a tax feature in draft version.
3.  Select the **Configuration version** which is based on the tax calculation data model version (E.g., 40.46.212) in the **General** tab.
4.  Click **Tax group applicability** tab.
5.  Click **Manage columns** button.
[![Manage columns](./media/tax-calculation-model-mapping-3.png)](./media/tax-calculation-model-mapping-3.png)

The **Tax Calculation Data Model** is integrated to the Dynamics 365 F&O. During each tax calculation related transaction, the values of the fields defined in the applicability tables will be collected and sent to tax calculation service for tax calculations. Find the logic in the attached "*tax-calculation-data-model-logic.xlsx*" for each supported transaction.
