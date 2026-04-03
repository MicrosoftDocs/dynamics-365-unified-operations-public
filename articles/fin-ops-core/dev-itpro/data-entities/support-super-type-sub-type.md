---
title: Super types and sub types
description: Describes support for inheritance patterns in data entities.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 02/26/2026
ms.reviewer: twheeloc
ms.assetid: d59cefc0-be94-42e9-a22e-87493985dbcd
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Super types and subtypes

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Describes support for inheritance patterns in data entities.

## Patterns

You can create entities for tables that involve inheritance in several ways:

- **Leaf/concrete type as data source:** If a concrete type is used as a data source, fields are displayed for both the base type and the current type. For example, in the following screenshots, if DirPerson is the data source, you can see data source fields from both DirPerson and DirPartytable.

    :::image type="content" source="./media/sub1.png" alt-text="Screenshot of data entity fields showing DirPerson as a data source.":::

    :::image type="content" source="./media/sub2.png" alt-text="Screenshot of data entity fields from both DirPerson and DirPartyTable.":::

- **Abstract type/non-leaf as data source**: If you use a non-leaf type as a data source, you see fields for both the base type and the current type, but you don't see fields from any derived types. To add fields from derived types, you must add derived data sources, as shown in the following screenshot.

    :::image type="content" source="./media/sub3.png" alt-text="Screenshot of derived data sources added for non-leaf type fields.":::

## Data Entity View wizard

Use the **Data Entity View** wizard to create data entities where the primary data source (and additional data sources) can be tables that use inheritance.

> [!NOTE]
> Currently, the wizard doesn't support derived data sources. It shows only fields from the current type or the base type. After you create an entity, you can manually modify it to display derived data sources.

The following screenshots show a data entity that you create by using the wizard, where DirPartyTable is the primary data source.

:::image type="content" source="./media/sub4.png" alt-text="Screenshot of the Data Entity View wizard with DirPartyTable as the primary data source.":::

1. Update the data source table to **DirPartyTabl**.

    :::image type="content" source="./media/sub5.png" alt-text="Screenshot of the data source table updated to DirPartyTabl.":::

1. Update the data source table to **DirPartyTable**.

    :::image type="content" source="./media/sub6.png" alt-text="Screenshot of the data source table updated to DirPartyTable.":::

## Run time

There's run-time behavior for entities that relate to inheritance.

### Creating entities for specified types

In this example, you create separate **Person** and **Organization** entities. The primary data source for the **Person** entity is DirPerson, and the primary data source for the **Organization** entity is DirOrganization. This approach, which is reflected in the following screen shots, doesn't require that you write any special run-time code.

:::image type="content" source="./media/sub7.png" alt-text="Screenshot of the Person entity with DirPerson as the primary data source.":::

:::image type="content" source="./media/sub8.png" alt-text="Screenshot of the Organization entity with DirOrganization as the primary data source.":::

### Creating entities for generalized types

In this example, you create a single entity, **Party**, that you can use for both **Person** and **Organization**. The primary data source is DirPartyTable, and the derived data sources are DirPerson and DirOrganization. The new entity contains the following kinds of fields:

- **Common attributes** – Attributes that aren't specific to **Person** or **Organization**, such as **Name**. These fields map to DirPartyTable.
- **Person-specific attributes** – **Gender**, **Marital Status**, and so on. These fields map to the derived data source DirPartyTable\_DirPerson.
- **Organization-specific attributes** – **OrgNumber**, **ABC**, and so on. These fields map to the derived data source DirPartyTable\_DirOrganization.

:::image type="content" source="./media/sub9.png" alt-text="Screenshot of the Party entity with fields mapped from base and derived types.":::

Mapping fields from base and multiple derived types in a single data entity is a design-time task. However, at run time, you must specify when each derived type should be created. This specification can be based on fields such as **InstanceRelationType**, or you can create a computed column that uses **String** to represent different types. In the **Party** entity example, you can create a **PartyType** computed column to represent the **Person** and **Organization** derived types. The following code snippet illustrates this approach.

:::image type="content" source="./media/sub10.png" alt-text="Screenshot of the PartyType computed column code snippet using InstanceRelationType.":::

In this example, the **Party** type is computed by using the **InstanceRelationType** column on DirPartyTable. This approach works for reading data. However, to perform **Create** or **Update** operations, you must write code that overrides the **initializeEntityDataSource** method on the data entity, and set the correct instance of the derived type for the data source run-time context buffer.

:::image type="content" source="./media/sub11.png" alt-text="Screenshot of the initializeEntityDataSource method override code for setting derived type context buffer.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
