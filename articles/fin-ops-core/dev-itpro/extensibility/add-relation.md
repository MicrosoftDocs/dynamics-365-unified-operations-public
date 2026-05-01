---
title: Add relations to tables through extension
description: Learn how to add a relation to a table to enable secure interactions with data, with a step-by-step example and troubleshooting information.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4
---

# Add relations to tables through extension

[!include [banner](../includes/banner.md)]

To enable rich and secure interactions with data in multiple tables, you must help guarantee referential integrity by defining relations that describe the link between two tables. By defining relations, you enable validation of the data that is entered and lookup capabilities for the related information. 

You can add a new relation by extending a table.

In the following example, you add a new field, **MyInventLocationId**, to the InventTable table. This field is a reference to the InventLocation table that contains warehouses.

1. In the new extension model, create an extension of the InventTable table.
1. Create a new relation, just as you would create a relation on a regular table.
1. Specify the **Related Table**, **Relationship Type**, and **Cardinality** properties, and any other properties that apply to the relation.
1. Add the link by specifying the fields from the InventTable table and the InventLocation table that have the same value. In this case, the fields are **MyInventLocationId** in the InventTable table and **InventLocationId** in the InventLocation table.

The following illustration shows the new relation.

:::image type="content" source="media/AddRelationToExistingTable.jpg" alt-text="Screenshot of the new relation added to the InventTable table.":::

## Troubleshooting

### Navigation property methods not working

**Issue** - Navigation property methods don't work when you create a foreign key relation by using a table extension. The compiler doesn't allow a call to a navigation method on the extended table.

**Solution** - Navigation methods aren't supported at this time.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
