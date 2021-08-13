---
# required metadata

title: Tax calculation data model overview
description: This topic provides information about how the field values in the tax data model are determined during tax calculation transactions.
author: kailiang
ms.date: 08/13/2021
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

This topic provides information about how the fieldvalues in the tax data model are determined in tax calculation transactions.

The **tax data model** is made up of fields that are required for tax calculations. Microsoft provides the **Tax calculation data model** which is includes header fields and line fields of transaction documents in Dynamics 365 finance and operations apps. The fields defined in the tax calculation data model are the available columns of the applicability rules tables in the tax calculation feature configuration.

> [!NOTE] 
> Some nodes, such as **Record ID** and **Table ID** are defined in the data model are for technical purposes. They aren't available columns in the tax calculation feature configuration.

Conplete the following steps to view the Tax calculation data model.

1.  Log in to the Regulatory Configuration Service (RCS) and go to **Electronic reporting** > **Tax configurations**.
2.  Select **Tax Data Model** > **Tax Calculation Data Model**.
3.  On the **Versions** FastTab, select a version.
4.  Select **Designer**.

    [![Data model designer (button)](./media/tax-calculation-model-mapping-1.png)](./media/tax-calculation-model-mapping-1.png)

5.  Expand the **Tax service** node.
6.  Expand the **Header** node to view the header data models.
7.  Expand the **Lines** node to view the line data models.

    [![Data models](./media/tax-calculation-model-mapping-2.png)](./media/tax-calculation-model-mapping-2.png)

You can also view the Tax calculation data model and the available columns in the **Applicability rules** table.

1.  In RCS, go to **Globalization features** > **Tax calculation**.
2.  Find a tax feature with a status of **Draft** and then select **Edit**.
3.  On the **General** tab, select the configuration version based on the tax calculation data model version. For example, 40.46.212.
4.  On the **Tax group applicability** tab, select **Manage columns**.

    [![Manage columns](./media/tax-calculation-model-mapping-3.png)](./media/tax-calculation-model-mapping-3.png)

The Tax calculation data model is integrated with finance and operations apps. During each tax calculation related transaction, the values of the fields defined in the **Applicability** tables will be collected and sent to the tax calculation service for calculation. In version 40.46, there are 57 predefined data models available for the following transactions: purchase order, sales order, transfer order, purchase requisition, request for quotation and sales quotation.

There are 31 data models that can be included as fields on the header of a transaction. However, not all fields are applicable to all transaction types. The following table provides information about which header fields are available on specific transaction types. 




​                   <--table 1 header fields fetching logic-->



There are 26 data models that are included as fields in the lines of a transaction. As with the header fields, not all fields are applicable to all transaction types. The following table provides information about which line fields are available on specific transaction types. 


​                   <--table 2 line fields fetching logic-->

