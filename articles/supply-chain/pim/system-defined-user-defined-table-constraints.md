---
# required metadata

title: System-defined and user-defined table constraints
description: This article explains the two types of table constraints for components in a product configuration model -  user-defined and system-defined. Table constraints represent matrices of the allowed attribute combinations, where each row defines one set of possible attribute values.
author: t-benebo
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PCTableConstraintAttachAttributeTree, PCTableConstraintColumnSystem, PCTableConstraintContentUserDef, PCTableConstraintDefinition, PCTableConstraintWizard
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 0a4ea930-b344-43a8-871e-d5cd077892c4
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# System-defined and user-defined table constraints

[!include [banner](../includes/banner.md)]

This article explains the two types of table constraints for components in a product configuration model -  user-defined and system-defined. Table constraints represent matrices of the allowed attribute combinations, where each row defines one set of possible attribute values.

Table constraints represent matrices of the combinations of attributes that are allowed for components in a product configuration model. Each row in the table defines one set of possible attribute values. You can declare two types of constraints in a product configuration model:

-   **Expression constraint** – Create an expression that defines relations between attributes to guarantee that only compatible values can be selected during product configuration.
-   **Table constraint** – Create a table that defines all the combinations that are allowed for a specified set of attributes. Two types of table constraints are available: user-defined table constraints and system-defined table constraints.

This article describes user-defined and system-defined table constraints for components in a product configuration model.

## User-defined table constraints
A user-defined table constraint is a type of matrix that is used to describe the combinations of attribute values that are defined by attribute types. For example, if you produce speakers, you can include columns for the cabinet finish and the front grill in the user-defined table constraint. The attribute type for the cabinet finish has four values, and the attribute type for the front grill has three values. Therefore, if constraints aren't used, there are 4 × 3 = 12 possible combinations. However, in this example, only six combinations are allowed, as shown in the following table. This information is displayed on the **Allowed combinations** tab on the **Edit table constraint** page.

| Cabinet finish | Front grill |
|----------------|-------------|
| Black          | Black       |
| Black          | Metal       |
| Oak            | Black       |
| Rosewood       | White       |
| White          | Black       |
| White          | White       |

User-defined table constraints are defined by static table input that works the same way as an expression constraint. When you use a user-defined table constraint, the advantage is that tables are often easier to create, understand, and maintain than long expression constraints.

## System-defined table constraints
A system-defined table constraint creates a dynamic mapping between an attribute type and a field in a table. When a system-defined table constraint is included in a product configuration model, the mapping guarantees that the data in the table is shown instead of the values of the attribute type. The result is a dynamic constraint, because the table contents can be modified (for example, by other modules).  

When you create a system-defined table constraint, you select a table, optionally define the query to use, and then associate attribute types to the fields in the selected table. The types of fields must match the types of attribute types.  

Before a table constraint can take effect on a product configuration model, the table constraint must be included in a constraint on one of the model's components. The procedure is to create a new constraint, select the table constraint type, and then select the table constraint definition to use. Finally, all fields in the table constraint must be mapped to attributes in the product configuration model.

## Additional resources

[Product configuration models overview](product-configuration-models.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]