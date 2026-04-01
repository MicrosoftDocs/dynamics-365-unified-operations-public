---
title: Create a security policy
description: Learn about how to create a simple security policy that secures access to customers and customer groups, based on a range for a customer group.
author: Peakerbl
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/13/2026
ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-07-31
ms.search.form: 
ms.dyn365.ops.version: 10.0.12
---

# Create a security policy

[!include [banner](../includes/banner.md)]

This article explains how to create a simple security policy that secures access to customers and customer groups, based on a range for a customer group.

## Add a new query

1. In Visual Studio, add a new query, such as XDSQCustGroup10, to your project or solution. Use the query to restrict data access from the **Constraint** table.

   :::image type="content" source="media/71c5206330564e8c2612a61a5a211dba.png" alt-text="Screenshot of adding a new query.":::

1. Right-click **Data Sources**, and then select **New Data Source**.
1. In the **Table** field, enter the primary table name **CustGroup**.
1. Right-click **Ranges**, and then select **New Range**.
1. Set the **Enabled** field to **Yes**.
1. In the **Data Source** field, enter the primary table name, in this case, `CustGroup`.
1. In the **Value** field, enter `10` to restrict access to data where `CustGroup` has value of 10, by defining the range for the `CustGroup` field.

   :::image type="content" source="media/c970ccc0649fcd2ee4e2b9a9819eb2fc.png" alt-text="Screenshot of the Value field with 10 entered.":::

## Add a new security policy

1. Add a new security policy, such as `XDSCustTableOnCustGroup10`.

   :::image type="content" source="media/118355845fa679f8f004e516f0691cff.png" alt-text="Screenshot of adding a security policy.":::

1. Set **Constrained Table** to **Yes**. This setting also secures access to the
    primary table. In this example, the primary table is **CustGroup**.
1. Set the **Context Type** field to **RoleName**.
1. Set the **Enabled** field to **Yes**.
1. Set the **Operation** field to **AllOperations**. Other available values for **Operation** include **Select**, **Insert**, **Update**, **Delete**, and **InsertUpdateDelete**.
1. Set **Primary Table** field to **CustGroup**.
1. Set the **Query** field to the name of the query created earlier, such as `XDSQCustGroup10`.
1. Set the **Role Name** field to `TradeSalesClerk`. Because **Context Type** is set to RoleName for this policy, you need to enter the AOT name for a user role.

   :::image type="content" source="media/9ad07f1e403cadfc3f1a52c2433e42c7.png" alt-text="Screenshot of the Role Name field with TradeSalesClerk entered.":::

1. Next, add constrained tables. In this simple example, add one table.

   :::image type="content" source="media/e366725fa084d308b7f02a89a3e6175b.png" alt-text="Screenshot of adding constrained tables.":::

   1. Right-click **Constrained tables**, and then select **New > Constrained Table**.
   1. Set **Constrained** to **Yes**.
   1. In the **Name** field, enter the constrained table, such as `CustTable`.
   1. In the **Table Relation** field, enter the relationship to the primary table, in this case `CustGroup`.

1. As a final step, build and synchronize the solution to activate the policy.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
