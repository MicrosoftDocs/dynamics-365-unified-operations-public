---
# required metadata

title: Data entity wizard rules
description: This article provides information about the natural key expansion of surrogate foreign key fields and the expansion of child/parent relations.
author: peakerbl
ms.date: 10/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 6234
ms.assetid: 551ac5d6-980c-487f-a15c-66d7ab80924a
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entity wizard rules

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article provides information about the natural key expansion of surrogate foreign key fields and the expansion of child/parent relations.

## Natural key expansion of surrogate foreign keys

A surrogate foreign key field's extended data type must be **RefRecId** or a derivative. The natural key expansion of a surrogate foreign key field uses the rules in the following list. These rules are listed in the order of evaluation.

1. **Replacement key** – The replacement key fields
2. **Primary key** – The primary index key fields
3. **Alternate key** – The first unique alternate key
4. **Auto-identification key** – The auto-identification fields

Surrogate foreign key fields that are nested in the natural key are recursively expanded. Recurring nested surrogates are limited to the first occurrence. If you select the `is mapped` property of a surrogate foreign key (that is, if you set the property to **true**), the related data source is automatically added to the entity, and the `is mapped` property of each field in the related data source's natural key is selected. In addition, any nested surrogate foreign key data sources are recursively added to the entity. If you clear the `is mapped` property of a surrogate foreign key (that is, if you set the property to **false**), the related data source are automatically removed and unmapped from the entity and any nested surrogate foreign key data sources. The effect of selecting and clearing the **is mapped** property of a surrogate foreign key field differs from the effect of using the **Add data source** and **Remove data source** buttons. If you add a surrogate foreign key data source, the **is mapped** property of the parent data source surrogate foreign key field isn't automatically set to **true**. If you are removing a surrogate foreign key data source, the **is mapped** property of the parent data source surrogate foreign key field isn't automatically set to **false**. By default, the **is mapped** property of the root data source's surrogate foreign key field is set to **true**. Therefore, by default, surrogate foreign key relations are expanded to one level.

## Expansion of parent/child relations
Parent/child relations are composition/extension relations that are stored as a relation on the child table. The parent table doesn't detect the relation. A parent/child relation can be either a surrogate foreign key relation or a natural foreign key. Parent/child relations use the following rules:

- The collection of child tables is obtained by querying the cross-reference database for "type reference" relations to the parent table.
- The child table must belong to the same table group as the parent table.
- The relation between the child and parent **relationship type** property must be **association**, **composition**, **link**, or **aggregation**.
- The relation between the child and parent **cardinality** property must be **exactly one** or **zero or one**.
- The relation between the child and parent **related table cardinality** property must be **exactly one** or **zero or one**.

By default, parent/child relations aren't expanded. You must add them by using the **Add data source** button. To change the default behavior for a project in Microsoft Visual Studio, set the **Expand parent/child** option to **true**.

### Using label text as field names

The following rules enable label text to be used as the field name when the option is selected (**true**):

- All whitespace is removed from the label text.
- The label text is truncated to 77 characters, and then a unique three-digit numeric identifier (000 through 999) is added.
- The label text is passed to the **NamedElement.IsValid** method. If the name is valid, it can be used as the field name. Otherwise, the label text isn't used, and the field name remains unchanged.

### The Is mandatory field

The default value of data entity fields is **auto**. This value is used unless it's explicitly changed. For relations, the related field's **Is mandatory** property is set based on the value of the field's **Is mandatory** value.

- If the field's **Is mandatory** property and the related field's **Is mandatory** are both **true**, both fields are explicitly set to **true**.
- If the field's **Is mandatory** property and the related field's **Is mandatory** are both **false**, both fields are explicitly set to **false**.

If the field's **Is mandatory** property and the related field's **Is mandatory** property differ in value, both fields remain unchanged. In this case, the default value of **auto** is used.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
