---
# required metadata

title: Customize field Help
description: This article describes how you can customize existing field descriptions and add your own descriptions.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-06-14 13 - 38 - 47
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 92013
ms.assetid: 1256848b-5321-421c-9f51-520f80ee79a4
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.dyn365.ops.intro: May-16
ms.dyn365.ops.version: AX 7.0.1

---

# Customize field Help

This article describes how you can customize existing field descriptions and add your own descriptions.

Microsoft Dynamics 365 for Operations has descriptions for some of the more complex fields. These descriptions appear when you hover over a field. You can customize these descriptions if, for example, you want to add company-specific information. You can also add descriptions for additional fields. You create field descriptions by using the **HelpText** property for field controls. The **HelpText** property is no longer specified for table fields and data types, as it was in previous versions of Microsoft Dynamics 365 for Operations. Additionally, the inheritance of the **HelpText** property from data types and table fields to form controls is obsolete. Field descriptions are intended to be specific to an individual field, in the context of the other controls and information that are available on the page. To add and customize field descriptions, you must have access to the Dynamics 365 for Operations development environment. Like other metadata changes, new descriptions should be added in a new model to prevent them from being overwritten when a new version of Operations is released. For more information, see [Customization: Overlayering and extensions](customization-overlayering-extensions.md).

## Customize a field description or add a new description
The same procedure is used to customize existing field descriptions and to add new field descriptions. However, when you customize an existing description, you replace the existing label reference.

1.  In Application Explorer, find the relevant page (form), and add it to your project.
2.  In the node for the page, find the relevant field control. Make a note of the name, so that you can use it as part of the label ID.
3.  Add a new label for your description. You can follow the conventions that Microsoft uses to name the label files for field descriptions and to create the label file IDs. For more information, see the next section.
4.  In the **HelpText** property of the field control, add a reference to the label.

## Label file names and label IDs
The field descriptions that are provided by Microsoft are stored in separate label files. There is one label file per module per model. The pattern for the label file names is FieldDescriptions\_*ModuleName*\_*ModelName*.*CountryCode*.label.txt. Here are some examples:

-   FieldDescriptions\_AccountsPayable\_ApplicationFoundation.en-US.label.txt
-   FieldDescriptions\_SystemAdministration\_ApplicationFoundation\_en-US.txt

The pattern for label IDs is @FieldDescriptions\_*ModuleName:PageName*\_*ControlName*. Here are some examples:

-   @FieldDescriptions\_AccountsPayable:CustSettlement\_CustSettlement\_OffsetCompany is the ID for the label for the **Company accounts** field (CustSettlement\_OffsetCompany) on the **Customer settlement** page (CustSettlement).
-   @FieldDescriptions\_ProcurementAndSourcing:PurchLineBackOrder\_LinkViewCheckBox is the ID for the label for the **Link on change view** option (LinkViewCheckBox) on the **Backorder purchase lines** page (PurchLineBackOrder).


See also
--------

[Create and use localizable labels in the client](create-localizable-labels-client.md)

[View and export field descriptions](view-export-field-descriptions.md)

