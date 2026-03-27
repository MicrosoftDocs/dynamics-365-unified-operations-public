---
title: Ledger account combinations
description: Learn about combinations of ledger accounts in the dimension framework, including outlines of the dimension framework and dimension enumerations.
author: twheeloc
author: ethanrimes
ms.author: ethankallett
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: twheeloc
audience: Developer
ms.assetid: 20e6b97e-30ed-48d4-b63c-a073f80300b2
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Ledger account combinations

[!include [banner](../includes/banner.md)]

## Introduction

In Microsoft Dynamics 365 finance and operations, the dimension framework expands to allow up to about 50 dimensions, due to SQL database limits on total column counts in tables. You can dynamically create dimensions and enter them in any order. The unlimited nature of the model, the advantages that come from relational database design, and optimization for performance requirements lead to a data model that is more complex than any earlier data model.

## Part 1: What happens when I create a ledger account combination?

This part of the article describes the various areas of the dimension framework and how they work together. This information helps you better understand what happens when you create a combination of ledger accounts.

The following illustration shows a model of the various areas of the dimension framework.

[![Dimension framework.](./media/DimensionsFrameworkGraph.png)](./media/DimensionsFrameworkGraph.png)

This part of the article covers the "Dimensions," "Dimension Values," "Categorizations," and "Backing Entities" regions that are highlighted in yellow in the preceding illustration.

### Dimension attributes

A dimension attribute, which will be referred to as just a dimension, represents an additional piece of classifying information that a user wants to associate with a ledger account combination. It represents classes of things, not specific instances. All the things that can be used to create a dimension are either classes of entities that already exist in the system (for example, department, cost center, expense purpose, customer, vendor, and item) or custom entities that are specific to a particular installation (for example, license plate number, event name, and ticket number).

When you create a dimension, you choose where its values come from. Dimension values can come from an existing entity in the system, such as Customer or Department entities, or from a custom list that you create. For each dimension that you define, the dimension framework keeps track of a reference to a table in the system. For example, for the existing Customer entity, a reference to the CustTable table is used. For custom entities that you define, a reference to the DimensionFinancialTag table is used. The metadata about what each dimension represents is stored in the DimensionAttribute table.

In the example in the following illustration, there are two dimensions on the **Financial dimensions** page. The Customer dimension represents customers that already exist in the application, and the LicensePlate dimension represents a new custom list.

[![Financial dimensions page.](./media/FinancialDimensions.png)](./media/FinancialDimensions.png)

The data about each dimension is stored in the DimensionAttribute table. The SQL query in the following illustration shows some of the basic information that is associated with each dimension.

[![Query results for DimensionAttribute storage.](./media/FinancialDimensionSQL.png)](./media/FinancialDimensionSQL.png)

The **Type** value indicates whether the dimension is backed by an existing entity in the system or a custom list. The dimension framework doesn't directly reference the backing table for an existing entity, such as CustTable. Instead, it creates a custom view to make an entity available in the system, so that it can be used in the dimension framework. By default, you can use 36 existing entities as dimensions.

You can create more than one dimension based on the same entity. Sometimes, an entity in the system serves multiple purposes when classifying transaction activity. In this case, you can define multiple dimensions for the entity, one for each purpose. A typical example is a cost center backing entity that represents both the primary cost center (for example, selling) and the cost center that the transaction is being traded against (for example, purchasing).

Internally, special dimensions exist that the system automatically creates to support key functionality of the dimension framework. A primary example is the MainAccount dimension. This functionality lets the dimension framework treat a main account as a dimension. However, it also prevents users from using a main account to create a dimension. The other types of special dimensions are system-generated dimensions that the dimension framework uses for internal purposes.

### Dimension attribute values

A dimension attribute value is a specific instance of a dimension that you use in the dimension framework. The **ViewName** property on the DimensionAttribute record determines the values for a dimension. For an existing entity, such as CustTable, values consist of the records in that table. For a custom list, values consist of a specific set of records in the DimensionFinancialTag table. You can view the values that are available for a specific dimension by selecting the **Financial dimension values** button on the **Financial dimensions** page.

If an existing entity, such as CustTable, provides the list of values, you can't edit it from the **Financial dimensions** page. To create a new dimension value for Customer, you must go directly to the **Customer** page and create a new customer. After you create the new customer, you can use it in the dimension framework. If you provide the list of values as a custom list, you can edit the list directly on the **Financial dimensions** page.

The following illustration shows an example of a list of values that CustTable provides. In this case, no values are stored in the dimension framework.

[![Financial dimensions values page (existing list).](./media/FinancialDimensionValuesForm.png)](./media/FinancialDimensionValuesForm.png)

The following illustration shows an example of a list of values that a custom list provides. In this case, values are stored in the dimension framework.

[![Financial dimensions page (custom list).](./media/FinancialDimensionValuesFormCustom.png)](./media/FinancialDimensionValuesFormCustom.png)

The following illustration shows the query results from the dimension setup tables for the preceding example.

[![Query results for dimension setup tables.](./media/DimensionSetupDataSQL.png)](./media/DimensionSetupDataSQL.png)

In both these examples, the **Financial dimension values** page shows the values that exist for the entity, not the values that the dimension framework uses. Because the representation of these values in the dimension framework isn't created until the framework uses these values, it must still hold a reference to the backing value. Therefore, you can delete values that the framework doesn't use yet. This behavior optimizes storage size and performance.

After the dimension framework references a dimension value, it stores the value in the DimensionAttributeValue table. This table links the DimensionAttribute record to the specific **RecId** value of the record in the ViewName view or table that the DimensionAttribute record references. Both the DimensionAttribute and DimensionAttributeValue records are required to go back to the originating value that the user entered.

In a system where the dimension framework doesn't reference any values, the DimensionAttributeValue table has no records.

## Part 2: Dimension enumerations and default dimensions

This part of the article covers the "Dimension Enumerations" and "Default Dimensions" regions that are highlighted in yellow in the following illustration.

[![Sets in the framework.](./media/SetsInFramework.png)](./media/SetsInFramework.png)

Dimension enumerations and default dimensions are two mechanisms that are used to store a set of references to either dimensions or dimension values. Both are typically exposed on a **Financial dimensions** tab on primary data pages, such as **Customers** (CustTable) or **Vendors** (VendTable).

### Dimension enumerations

A dimension enumeration is a set of references to existing dimensions that are persisted for later use. These dimensions have no particular ordering, and the dimension framework imposes no constraints on the dimensions that appear in the set. However, in most cases, the consuming code constrains the set to the set of dimensions that are available in the current ledger. Dimension enumerations are stored in the DimensionAttributeSet and DimensionAttributeSetItem tables.

Each set specifies an enumeration type. This enumeration type is the enumeration ID of the BaseEnum that represents the source of enumeration values that are associated with each dimension. You can find the enumeration number by using the **enumNum()** method. Therefore, it isn't a list of user-entered values from backing entities but a list of enumeration values that are defined by the developer. An example is the storage of a list of dimensions that are associated with each main account, and that are either fixed (labeled **Fixed value**) or not fixed (**Not fixed**).

The following illustration shows an example of dimension enumerations on a page.

[![Dimension enumerations on a page.](./media/DimensionEnumerationsOnForm.png)](./media/DimensionEnumerationsOnForm.png)

For the preceding example, the **DimensionFixed** enumeration is used to constrain the list of values in the drop-down list.

[![Dimension enumeration BaseEnum.](./media/DImensionEnumerationBaseEnum.png)](./media/DImensionEnumerationBaseEnum.png)

The value that you select represents one item by using a value of **1** for **EnumerationValue** (= **DimensionFixed::Fixed**) and the other item uses the default value of **0** for **EnumerationValue** (= **DimensionFixed::NotFixed**). The following illustration shows how the DimensionAttributeSet record is stored.

[![Query results for dimension enumeration storage.](./media/DimensionENumerationSQL.png)](./media/DimensionENumerationSQL.png)

The MainAccountLegalEntity record references the DimensionAttributeSet record by using its **FixedDimensions** field. The DimensionAttributeSet record represents the combination of dimensions for the enumeration type. The DimensionAttributeSetItem records represent each pair of a dimension and an enumeration value in the set. The enumeration value is represented by its integer value.

### Default dimensions

Dimension enumerations hold a set of dimensions that have associated enumeration values. A default dimension holds a set of dimensions that have specific dimension values. The term *default dimensions* comes from the fact that you typically enter these sets on master data records, not directly on transactions. Use them to enter default values in a ledger account combination. As with dimension enumerations, no specific structure is associated with default dimensions. In most instances, the consuming code constrains the set to the dimensions that are available for the current ledger. The DimensionAttributeValueSet and DimensionAttributeValueSetItem tables store default dimensions.

The following illustration shows an example of default dimensions on a page.

[![Default dimensions on a page.](./media/DefaultDimensionsOnForm.png)](./media/DefaultDimensionsOnForm.png)

In the preceding example, the user selects a dimension value to associate with each dimension. The following illustration shows how these values are stored in the DimensionAttributeValueSet and DimensionAttributeValueSetItem tables.

[![Query results for dimension value tables.](./media/DImensionValueTablesSQL.png)](./media/DImensionValueTablesSQL.png)

The MainAccountLegalEntity record holds a foreign key reference to the DimensionAttributeValueSet table that represents the combination of entered values. Specifically, this table represents the set of pairs of dimension values that are stored in the DimensionAttributeValueSetItem table.

The DimensionAttributeValueSetItem table holds one record for each dimension value that you enter. The record references a DimensionAttributeValue. The system stores no records for dimensions that you didn't enter (that is, records that are left blank). When you enter a default dimension, the system creates two records in the DimensionAttributeValue table, because the dimension value is now used in the dimension framework. In this way, the dimension framework values link with the backing entities. For performance reasons, the natural key (display value) of a dimension value is stored on the DimensionAttributeValueSetItem table.

To get to the source of the values, follow the link that is stored in the **EntityInstance** field on the DimensionAttributeValue table, together with the associated **ViewName** field on the **DimensionAttribute** table, to find the record in the originating tables of CustTable (via the DimAttributeCustTable view) and DimensionFinancialTag.

## Part 3: Structures and constraints

This part of the article covers the "Structures" and "Constraints" regions that are highlighted in yellow in the following illustration.

[![Structures and constraints in the framework.](./media/StructuresAndConstraintsInFramework.png)](./media/StructuresAndConstraintsInFramework.png)

As stated earlier, the dimension framework allows for an unlimited number of dimensions. Additionally, when users enter a ledger account combination, they can specify which dimensions to include, and in which order. They can also constrain the values that can be entered for each segment in that ledger account combination.

### Account structures

The following illustration shows an example of an account structure.

[![Account structures page.](./media/AccountStructureConfigurationForm.png)](./media/AccountStructureConfigurationForm.png)

As the following illustration shows, this account structure is stored in the DimensionHierarchy table in the database. It's set up to require that a main account be entered as the first segment of a ledger account combination, and that a customer and license plate number be entered as subsequent segments. This setup is the hierarchical order definition. It's stored in the DimensionHierarchyLevel table in the database.

[![Query results for account structures.](./media/StructureSQL.png)](./media/StructureSQL.png)

In addition to the order, you must set up the constraints. Constraints are the criteria that define the valid combinations of values. In this example, all segments must have a value for the combination. Otherwise, they're not considered valid. You can enter any existing value (that is, any value that already exists in the backing entity), and there are no specific restrictions on the combinations of values that are valid. The DimensionConstraintTree, DimensionConstraintNode, and DimensionConstraintNodeCriteria tables store this criterion.

[![Query results for simple constraints.](./media/SimpleConstraintsQueryResults.png)](./media/SimpleConstraintsQueryResults.png)

The example in the preceding illustration shows the most basic constraint tree. An asterisk (\*) constraint criterion is associated with each of the three constraint nodes. This constraint criterion represents any existing value. It's stored as a percent sign (%) in the database and is shown as "\<all values\>" in the UI. These constraints are used both to show the values that can be entered for each segment via a lookup and to validate values that are entered in the segment. Eventually, if incorrect values are entered for a ledger account combination, these constraints produce validation errors.

The dimension framework allows for much more complex constraint trees, where the value that is entered in one segment drives the valid values that can be entered in the next segment. The following illustration shows an example of the versatility.

[![Constraint builder on the Account structures page.](./media/ConstraintbuilderonConfigureAccountStructureForm.png)](./media/ConstraintbuilderonConfigureAccountStructureForm.png)

The following illustration shows a more complex constraint tree.

[![Advanced constraint tree expanded on a page.](./media/AdvancedConstraintTreeExpandedOnForm.png)](./media/AdvancedConstraintTreeExpandedOnForm.png)

The following illustration shows the resulting constraint definition.

[![Query results for advanced constraint trees.](./media/AdvancedConstraintTreeSQL.png)](./media/AdvancedConstraintTreeSQL.png)

If a user enters **150-B** for a main account and customer, a specific license plate number must also be entered. However, if the user enters **150-W**, no license plate number is required. In both cases, the user always sees three segments in the ledger account combination, even if one of those segments is left blank. For examples of the effects that these structures, segments, and constraints have when ledger dimension accounts are entered, see the [part 5](#part-5-ledger-dimensions) section of this article that discusses the entry and storage of ledger account combinations.

If a user wants to show trailing segments only when they must be entered, advanced rules can be combined with the account structure to provide the additional versatility.

## Part 4: Advanced rules

This part of the article covers the **Advanced Rules** region, which is highlighted in yellow in the following illustration.

[![Advanced rules in framework.](./media/AdvancedRulesGraph.png)](./media/AdvancedRulesGraph.png)

Account structures and constraints let you build simple to complex trees of valid combinations. However, sometimes there's a business requirement to show a dimension as a segment in a ledger account combination only at specific times, instead of just constraining the valid values that are allowed and showing the dimension all the time. Advanced rules support this requirement.

### Advanced rules

You can add advanced rules to an account structure and its constraints. Although advanced rules are versatile, follow these guidelines to help guarantee the best usability, performance, and understanding:

- Rules can't replace the account structure. A structure must always exist, and it must have at least a main account segment.
- Rules can't add dimensions before other segments that are already in the account structure.
- Rules should not be used to replace constraints in the account structure for additional dimensions that are always required, regardless of the main account.
- Don't use rules to replicate segments that already exist in the account structure, or to replicate other rules.
- Any duplication automatically joins and uses the most restrictive constraint.
- The location of the duplicated segment appears only in the first occurrence of the segment.

To set up an advanced rule, define a filter that controls when to add extra segments to a ledger account combination. Then, link rule structures that specify the extra segments to add, their order in the hierarchy, and any constraints between them. (Rule structures resemble account structures.)

For example, the following account structure is set up.

![Basic structure and constraints for two accounts.](./media/BasicStructureAndConstraint.png)

You configure the following advanced rule to optionally add one or more segments only if the user enters main account 145 and customers G through Q.

[![Advanced rule page.](./media/AdvancedRuleForm.png)](./media/AdvancedRuleForm.png)

After the rule is configured, you must create a structure and constraint definition to define what segments should be added to the ledger account combination. To complete this step, you create the following rule structure. The process for creating a rule structure resembles the process for creating an account structure. These structures aren't immediately bound to the rule. Therefore, they can be shared across multiple rules as you require.

[![Advanced rule structure page.](./media/AdvancedRuleStructureForm.png)](./media/AdvancedRuleStructureForm.png)

After you create the structure, add it to the dimension rule. Then, activate the account structure, together with the rule.

[![Added advanced rule structure to rule.](./media/AddedAdvancedRuleStructureToRule.png)](./media/AddedAdvancedRuleStructureToRule.png)

The storage of this data uses some of the same tables as the storage of the account structures (see [part 3](#part-3-structures-and-constraints)). The `DimensionRule`, `DimensionRuleAppliedHierarchy`, and `DimensionRuleCriteria` tables hold the data that is specific to the definition of the rule. They also hold the link to the definition of the rule structures. The remaining tables are shared with the account structure definition.

[![Query results for the combined structure, rule, and all constraints.](./media/CombinesStructureRuleandAllConstraintsSQL.png)](./media/CombinesStructureRuleandAllConstraintsSQL.png)

## Part 5: Ledger dimensions

This section of the article covers the **Ledger Dimensions** region, which is highlighted in yellow in the following illustration.

[![Ledger dimension storage in framework](./media/LedgerDimensionStorageInFramework.png)](./media/LedgerDimensionStorageInFramework.png)

After you set up all the configuration data, you can enter, validate, and persist ledger account combinations. The application uses this area as the primary consumption of the dimension framework.

### Ledger dimension storage without rules

To understand ledger dimensions, you need to understand how users enter ledger account combinations.

This section uses the account structure and rule setup from [part 4](#part-4-advanced-rules) of this article. It explains the user interaction with the account entry control when an account is entered. Here's the account structure as a reminder.

![Basic structure and constraints got My Account Structure.](./media/BasicStructureAndConstraintForm.png)

A single account rule is associated with the account structure.

[![Single rule added.](./media/SingleRuleAdded.png)](./media/SingleRuleAdded.png)

The following illustration shows the structure that was added.

[![Single structure added.](./media/SingleStructureAdded.png)](./media/SingleStructureAdded.png)

The following illustration shows what a ledger account field looks like when a user first sees it on a page, and it doesn't have the focus.

[![Empty ledger account field (without focus).](./media/EmptyLedgerAccountField.png)](./media/EmptyLedgerAccountField.png)

When the user clicks in the field, nothing changes. However, if the user selects the drop-down arrow, the lookup appears and shows the possible segments. In the following illustration, there are two possible segments.

[![In-edit ledger account field with lookup.](./media/InEditLedgerAccountFieldWithLookup.png)](./media/InEditLedgerAccountFieldWithLookup.png)

For this example, the user enters the combination **150-A**.

![Completed ledger account field with value 150-A.](./media/CompletedLedgerAccountField.png)

As soon as the second segment is entered, and the user presses **Tab** to move out of the control, the dimension framework saves the combination and then validates it, based on the constraints. In this example, the combination is valid. The user can enter segments either as a string or by using the lookup.

For this example, the following information is known about the combination:

- The account structure is named **MyAccountStructure**.
- The first segment is the MainAccount dimension. It has a value of **150**.
- The second segment is the Customer dimension. It has a value of **A**.
- No additional segments were added, because the values didn't match any advanced rules that are associated with this account structure.

Therefore, the two segment values are stored across the four tables, as shown in the following illustration.

![Query results for ledger dimension storage across four tables.](./media/LedgerDimensionStorageSQL.png)

The first table is named **DimensionAttributeValueCombination**. It stores a full multisegment account combination, together with some denormalized information about the combination. For example, it stores the concatenated segments as a single string, a foreign key reference to the account structure, and a foreign key to the main account that was used (150).

The second table is named **DimensionAttributeValueGroupCombination** and is explained later.

The third table is named **DimensionAttributeValueGroup**. It stores each related group of segments that is associated with each structure that is present in the combination. In this case, because there's only one structure (the account structure), there's only one record.

The fourth table is named **DimensionAttributeLevelValue**. It stores the individual segment values for each segment in the associated group or structure. One record exists for each segment that is entered. If a segment is empty, no values are stored for it. Each record references the corresponding DimensionAttributeValue record. If an existing DimensionAttributeValue record is found for the value, it's referenced. If an existing DimensionAttributeValue record isn't found for the value, one is created. This data links the DimensionAttribute to the real backing entity record. In this case, one DimensionAttributeLevelValue is for the MainAccount record that has an ID of 150, and one DimensionAttributeLevelValue is for the CustTable record that has an ID of A.

To link the group of account structure values and segment values to the main record in the DimensionAttributeValueCombination table, a record is inserted into the second table, DimensionAttributeValueGroupCombination.

To save a single segment in a new combination, insert at least one record into each of these four tables. For each additional segment that you enter, insert an additional record into the DimensionAttributeLevelValue table. Abstractly, these four tables are referred to as a Ledger Dimension. A Ledger Dimension is expressed as a foreign key that references the **RecId** value in the DimensionAttributeValueCombination table.

### Ledger dimension storage with rules

This section builds on the ledger dimension storage example that started in the previous section. Here, you change the values from **150-A** to **145-Q**. As you know from the advanced rules that you set up previously, this change adds a third segment to the account structure.

[![In-edit ledger account segment (before Tab is pressed).](./media/LedgerAccountSegmentBeforeTab.png)](./media/LedgerAccountSegmentBeforeTab.png)

When you type a hyphen (–) after the second segment, the control adds a third segment and receives the focus.

[![In-edit ledger account segment (after Tab is pressed).](./media/LedgerAccountSegmentAfterTab.png)](./media/LedgerAccountSegmentAfterTab.png)

If you open the lookup while the third segment has the focus, it shows the possible valid values for the third segment.

[![Lookup while the focus is in the new segment.](./media/LookupInSegment.png)](./media/LookupInSegment.png)

You can now enter a license number.

![Completed ledger account field with license number.](./media/CompletedLedgerAccountFieldWithAllRules.png)

As soon as you enter a value in the third field and press **Tab** to move out of the control, the combination is validated. If the combination is valid, it's saved as a Ledger Dimension.

For this example, the following information is known about the new combination:

- The account structure is named **MyAccountStructure**.
- The first segment is the MainAccount dimension. It has a value of **145**.
- The second segment is the Customer dimension. It has a value of **Q**.
- Because the values match the rule for the first two segments, an account rule structure that is named **MyRuleStructure1** was added. Therefore, one additional segment was added.
- The third segment is the LicensePlate dimension. It has a value of **AAA 111**.

![Query results for ledger dimension storage with value AAA 111.](./media/LedgerDimensionValuesStorageSQL.png)

For this combination, a total of eight rows was inserted across the four tables that store the ledger dimension. The difference between the first ledger account combination that was discussed in the previous post([part 4](#part-4-advanced-rules)) and this ledger account combination is that multiple structures are used to drive the dimensions that make up this ledger account combination. Two records are stored in the DimensionAttributeValueGroupCombination and DimensionAttributeValueGroup tables. Each record represents a structure that is used and joined to the full combination.

Notice that each record is assigned a new **RecId** value. The combination of the previous values isn't updated. Instead, a new combination is created. Therefore, the Ledger Dimensions are immutable, because no reference counting is maintained for the use of the combination. The same **150-Q** combination that you originally entered might have been referenced from multiple tables in the application before you decided to change an instance to **145-Q-AAA 111**. Therefore, you must create a new combination, and change the reference to it only from the table that the ledger account combination is changed on.

Because you create a new Ledger Dimension when you change the combination on a record by adding or removing segment values, you might end up with unreferenced or orphaned Ledger Dimensions. By allowing orphaned combinations, you can help improve performance of the overall dimension framework by not deleting records across the tables in question each time a combination is changed. After a combination is used one time, it's likely to be reused. Therefore, if it's immediately removed when the last reference is removed, it might be re-created. Orphaned Ledger Dimensions are still structurally valid and can be reused later if the combination of values in relation to the structures and rules is entered again. If a combination is ever entered another time, no records are inserted, and the existing reference is reused. Therefore, performance is improved.

When advanced rules are used, optimizations are also made for the storage size and insertion cost. For example, in the following illustration, a new account combination is entered.

[![Changed ledger account field.](./media/ChangedLedgerAccountField.png)](./media/ChangedLedgerAccountField.png)

In this case, the only difference between the new combination and the previous combination is that the license plate number that was provided by the advanced rule was changed. The following illustration shows how the data storage of the combination will look. New records are highlighted in white.

[![Query results for additional ledger dimension storage.](./media/AdditionalLedgerDimensionStorageQueryResults.png)](./media/AdditionalLedgerDimensionStorageQueryResults.png)

When the new combination is created, the following five records are inserted. (These records are the records that are highlighted in white in the preceding illustration.)

- One record in DimensionAttributeValueCombination
- Two records in DimensionAttributeValueGroupCombination
- One record (instead of two) in DimensionAttributeValueGroup
- One record (instead of three) in DimensionAttributeLevelValue

This behavior occurs because the values that are stored as part of the account structure "group" are the same in the previous combination (DAVC2) and this combination (DAVC3). Those DimensionAttributeValueGroup and DimensionAttributeLevelValue records didn't have to be re-created. Instead, three records could be reused, and their insertion cost could be saved.

Alternatively, if the structure that is associated with the account rule allows blank values for the license plate number, and a combination of just **145-Q** is created, only two new records are inserted:

- One record in DimensionAttributeValueCombination
- One record in DimensionAttributeValueGroupCombination
- Zero records in DimensionAttributeValueGroup
- Zero records in DimensionAttributeLevelValue

This behavior occurs because all the `DimensionAttributeValueGroup` and `DimensionAttributeLevelValue` records already exist and you can fully reuse them in the new combination. Primarily for this reason, never modify data directly in the Ledger Dimension storage tables. A change to a single record might affect not only all references to that ledger dimension, but also one or more other ledger dimensions and references to them.

Although it's partially collapsed in the examples shown in this part of the article, the system assigns a hash code to the `DimensionAttributeValueCombination` and `DimensionAttributeValueGroup` tables.

## Part 6: Advanced topics

To conclude this article, this part discusses some advanced topics to explain some of the deeper design and implementation decisions that drive the way the dimension framework works.

The model in the following illustration shows the various areas in the dimension framework.

[![Overall framework.](./media/OverallFramework.png)](./media/OverallFramework.png)

### Hashes

The design of the database storage in the dimension framework supports the following functionality:

- Support immutable data, where data is only inserted, never updated or deleted.
- Reuse previously created combinations to lower insertion costs.
- Avoid reference counting and maintenance of it.
- Provide fast performance to find an existing combination that can be reused.

Because the dimension framework allows for an unlimited number of dimensions and an unlimited number of structures on a ledger account combination, it's difficult to create a single large query or multiple smaller queries to find an existing set or combination. Because the number of records and the order of those records might differ for every combination, a hash-based solution was implemented.

This hash represents the unique information that the records of the associated tables contain, and it allows for fast querying. The framework stores a single binary container field (160-bit, 20-byte hash column) to uniquely identify the data that the set or combination contains.

The dimension framework uses hashes to uniquely identify data in the following tables:

- **DimensionAttributeValueCombination** – This table consists of data from all the linked records in the DimensionAttributeValueGroup and DimensionAttributeLevelValue tables.
- **DimensionAttributeValueGroup** – This table consists of data from the linked records in the DimensionAttributeLevelValue table.
- **DimensionAttributeSet** – This table consists of data from the associated DimensionAttributeSetItem records.
- **DimensionAttributeValueSet** – This table consists of data from the associated DimensionAttributeValueSetItem records.

### Hash messages

To produce a hash, a message is created that contains individual pieces of ordered information about the contents of the set or combination. Although this message varies, depending on the hash that is being generated, the hash message basically includes information about the dimensions, values, and structures, and the order within the set or combination, if applicable. This information is internally calculated in a prescribed manner and passed on to a hashing routine. This hashing routing then generates a hash to generate a hash key by using a binary container. The exact order and contents of these messages are provided by the methods in the storage supporting classes of the dimension framework. These classes include **DimensionAttributeSetStorage**, **DimensionAttributeValueSetStorage**, and **DimensionStorage**.

> [!NOTE]
> The internal hash function was updated in Dynamics 365 Finance. For more information, see [Verify hash function changes after update to Dynamics 365 Finance 2020 release wave 2](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/03/verify-hash-function-changes-after-update-to-dynamics-365-finance-2020-release-wave-2/).

### Hash keys

To generate a hash message, you need something that uniquely identifies each dimension, value, and structure that makes up the combination. Although a **RecId** value can serve as a unique identifier, it's considered only a surrogate because it isn't immutable and can change if, for example, the record is exported and then imported into a different system or partition. The **RecId** value can be reassigned during the import process. If you create a hash with a hash message that uses a **RecId** value, you can't use it to identify a combination in the dimension framework for that new system or partition. Instead, use a GUID. This GUID resides on the DimensionAttribute, DimensionAttributeValue, and DimensionHierarchy tables, and is stored in the **HashKey** column. Every time that you create a new record, you assign a GUID that remains with that record to uniquely identify it.

### Risks of changing data directly

For detailed information about why you must not modify financial dimension data directly, which tables are affected, and what to do instead when dimension values are incorrect, see [Modifying financial dimension data](/dynamics365/fin-ops-core/dev-itpro/financial/modifying-financial-dimension-data).

### Apparent duplicate combinations

When you browse the tables of the dimension framework and view only the **DisplayValue** field that is stored on the records, it might appear that combinations are duplicated. However, this apparent duplication just indicates that data in the hash or joined tables differs, even though the **DisplayValue** strings appear the same. The **DisplayValue** strings are stored on the records to improve performance for some scenarios, but they aren't used to uniquely identify the record.

For example, an account structure has **MainAccount-Department** in one company and another account structure has **MainAccount-CostCenter** in a different company. In this scenario, the **DisplayValue** string of two combinations, one for each account structure, can appear as **145-A**. For the first account structure, **A** represents a department in the first company. However, for the second account structure, it represents a cost center in the second company. Additionally, multiple types of a Ledger Dimension are stored in the DimensionAttributeValueCombination table. For example, special types for budgeting might appear the same to have the types as other combinations when you examine the **DisplayValue** fields. However, they hold different information internally and hold uniquely different hash values.

This same behavior applies to the **DimensionCombinationEntity** and **DimensionSetEntity**. Querying these entities can return seemingly duplicate rows based on **DisplayValue**, but the underlying records differ. Common reasons include:

- **Company-striped data** — Dimension data is stored globally but can reference company-specific backing records. A default dimension of "Department 001 - Project P012" could exist separately for USMF, USSI, and RUMF, producing three unique rows. The entity doesn't expose the data area; that's held by the owning table with the foreign key reference.
- **Integration format excludes dimensions** — If the integration format exports only "Department - Project" but the system tracks "Department - Customer - Project - Employee", two records with different Customer/Employee values collapse to the same DisplayValue in the entity output.
- **Different ledger dimension types** — Default accounts, ledger accounts, budget accounts, budget control accounts, and focus balance accounts are all stored in DimensionAttributeValueCombination. Records of different types can share the same DisplayValue.
- **Hash algorithm migration** — The HashV2 update required creating new records for some combinations that couldn't be re-hashed in place. The old and new records differ only in the Hash and HashVersion columns, which aren't exposed on the entity.

### You can't share dimension foreign key references between data areas

Dimension foreign key columns (such as **DefaultDimension** on **CustTable**) must not be replicated between companies through cross-company data sharing (SysDataSharing, DuplicateRecordSharing) or manual record copying.

The dimension tables (**DimensionAttributeValueSet**, **DimensionAttributeValueCombination**) aren't company-specific (SaveDataPerCompany = No), but the records they reference internally often are. A default dimension set can contain segment references that point back to RecId values in company-specific tables like **CustTable** or **ProjTable**. Consider this example:

**CustTable (SaveDataPerCompany: Yes)**

| AccountNum | DataArea | RecId | DefaultDim |
|------------|----------|-------|------------|
| CUST001 | USMF | 201 | 401 |

**DimensionAttributeValueSet (SaveDataPerCompany: No)**

| RecId |
|-------|
| 401 |

**DimensionAttributeValueSetItem (SaveDataPerCompany: No)**

| DimensionSource | DimensionValueReference | ParentRecId | Segment |
|-----------------|-------------------------|-------------|---------|
| CustTable | 201 | 401 | 1 (CUST001) |
| ProjTable | 301 | 401 | 2 (ProjA) |

If you replicate the **CustTable** record to another company (RUMF) by copying the row, the new record inherits **DefaultDim = 401**. That dimension set still contains segment references to RecId 201 in USMF's **CustTable** and RecId 301 in USMF's **ProjTable**. Customer CUST001 in RUMF now carries default dimensions that reference the wrong company's data, and this corruption propagates into posted combinations and can split trial balance rows for the same visual key.

There's no workaround. Don't replicate dimension foreign key values between data areas.

> [!NOTE]
> An exception exists when all financial dimensions are global (not company-specific) and all companies use a single chart of accounts. In that configuration, you can configure single record sharing (SRS) for dimension foreign key references, because no company-specific backing records are involved.

### AccountStructure column on DimensionAttributeValueCombination

Many rows in the **DimensionAttributeValueCombination** (DAVC) table have a blank **AccountStructure** column. This is by design and doesn't indicate data corruption.

The framework only populates **DAVC.AccountStructure** when all of the following conditions are true:

- The combination is a multisegment Account type ledger dimension (**LedgerDimensionType::Account**).
- The referenced **DimensionHierarchy** type is Account Structure.
- The hierarchy isn't system-generated (**DimensionHierarchy.IsSystemGenerated = No**).

Default accounts from posting profiles (containing only a main account), budget combinations, single-segment journal accounts, and focus balance combinations all have this field blank by design.

### Unpivoted columns and indexes

The **DimensionAttributeValueCombination** and **DimensionAttributeValueSet** tables contain "unpivoted" columns and 50-100+ supporting indexes that were added in Dynamics 365 version 7.0. These columns store denormalized dimension values directly on the combination or set record, replacing the need for complex multitable joins when querying by dimension value.

The indexes on these columns are mandatory. Without them, queries against unpivoted columns fall back to table scans, which would be worse than the original normalized approach. Don't remove these indexes.

Some account types (such as Customer, Vendor, Bank, and Project) are entered through the [Segmented Entry Control](/dynamics365/fin-ops-core/dev-itpro/financial/segmented-entry-control-migration-guidance) on journal lines but are single-value references rather than multisegment ledger accounts. Because they share the same control and data model, the system autogenerates these as **SystemGeneratedAttribute** dimension types, which also produce unpivoted columns and indexes.

#### Insert performance and highly variable dimensions

The dimension framework is designed to insert data only on first use of each unique set of values and reuse references for each subsequent request. Over time, the number of inserts should decrease as combinations are reused.

If insert performance to dimension tables isn't improving over time, the most common cause is the use of **highly variable dimensions** - dimension values with such high volatility that they're rarely reused. Examples include dates, serial numbers, license plates, ticket numbers, and inventory dimensions (size, color, site/warehouse/location). Implement these dimensions as [financial tags](/dynamics365/finance/general-ledger/financial-tag) or custom fields rather than financial dimensions. For more information, see [Highly variable dimensions](/dynamics365/finance/cost-accounting/high-var-dimensions).

### Versioning/date-effective data

The dimension framework doesn't directly support versioning or date-effective data. The platform assigns new RecID's to the latest version row in date-effective tables. As the dimension framework takes reference to backing values by the **RecId** at the time of original entry, the introduction of a new record causes the system to no longer be able to join to the older versions because the date context isn't persisted with the dimension data.

Using dimension data where the same backing entity record is used, and another joined table tracks historical revisions to itself in the owning module, the dimension framework won't be able to determine the difference because the **RecId** value of the backing entity won't differ between versions. This effectively allows the dimension framework to always see the current version just like non-versioned tables.

None of the dimension framework tables, such as dimensions, structures, rules, and constraints, support versioning internally. The system replaces previous versions with a new version, and it doesn't maintain history.

When a structure or rule is changed, if ledger account combinations have been saved on unposted transactions, the dimension framework creates new combinations and updates any foreign key references to them on unposted transaction tables. It doesn't change the original combinations, because those combinations might be referenced from posted transactions. The two combinations aren't linked in any way. There is no way to determine what a structure and its rules looked like before the change. Some information can be determined by the data that is stored in the combination. However, because blank values aren't stored, this data is incomplete and can't be used to reconstruct a previous version.

The dimension framework supports "valid from" and "valid to" dates at the level of a dimension value. These dates indicate when the value is considered "valid." They don't represent the historical state of the value in the same way that date-effective data does.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
