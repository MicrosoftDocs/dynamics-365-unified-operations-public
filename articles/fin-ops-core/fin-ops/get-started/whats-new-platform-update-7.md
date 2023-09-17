---
title: What's new or changed in Dynamics 365 for Operations platform update 7 (May 2017)
description: This article describes features that are either new or changed in Dynamics 365 for Operations platform update 7. This version was released in May 2017 and has a build number of 7.0.4542.16189.
author: sericks007
ms.date: 05/19/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 
ms.dyn365.ops.version: Platform update 7
ms.custom: 
ms.assetid: 54cfeac5-e977-4c02-8e7a-4ddb4b336713
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Operations platform update 7 (May 2017)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Operations platform update 7. This version was released in May 2017 and has a build number of 7.0.4542.16189.

## Configuration data projects

Using a configuration data project, you can easily export configuration data and move it from one instance to another instance. This feature provides an updated user interface, and the ability to easily manage templates and projects. For more details, refer to [Configuration data projects](../../dev-itpro/data-entities/configuration-data-projects.md).

## Static export to Excel limit increase from 2k to 10k

The static Export to Excel limit has been increased from 2k to 10k to allow more rows to be exported from a grid. If there is an entity representing the data in the grid we recommended that you use Open in Excel and the Excel Add-in instead, since there is no hard row limit. In addition, if there is an entity and the user has admin privileges then DIXF (data management) is also an option. For more information, see [Open entity data in Excel and update it by using the Excel add-in](../../dev-itpro/office-integration/use-excel-add-in.md).

## Development tooling – New tabbed workspace pattern

A new tabbed workspace form pattern is now available. You can now include tab pages that house embedded Power BI reports. This feature is our first step toward moving away from horizontally-scrolling workspaces. For more information, see [Workspace form pattern](../../dev-itpro/user-interface/workspace-form-pattern.md).

## Development and customization – Extending a group control

The Dynamics 365 for Operations development tools and runtime platform now support extending an extended form, for example, extending a form that is already extended in a referenced model. This fixes an issue that originally prevented extending a field/button group control if the group control belongs to a form extension.

## Development and customization – Extending the Country Region Codes property

The **Country Region Codes** property enables developers to restrict functionality to certain regions or countries/regions based on the current legal entity's primary address. The **Country Region Codes** property is editable on the following extension element types: Menu extension, Menu Item extension, Table extension (and fields), Form extensions (form controls), EDT extensions, Enum extensions, and View extensions.

A developer can specify additional country/region codes in their extension. The effective country/regions associated with an element will be the union of all codes from the baseline element and all its extensions.

## Development and customization – Validating events on form data sources and form data source fields

Validation events on form data source (FormDataSourceEventType) and form data source fields (FormDataFieldEventType) now support invalidating user-specified values. For more information, see [Customize model elements through extension](../../dev-itpro/extensibility/customize-model-elements-extensions.md).

The following example illustrates this feature. The example uses a form named **MyForm** that contains a data source named **abTable**, and a field named **FieldInt1**.

```
public class abFormEvent
{
    /// <summary>
    /// Disallows inserting records on the form data source if the Field1 field contains the integer value 1
    /// </summary>

    [FormDataSourceEventHandler(formDataSourceStr(MyForm, abTable), FormDataSourceEventType::ValidatingWrite)]

    public static void abTable_OnValidatingWrite(FormDataSource sender, FormDataSourceEventArgs e)
    {
        var datasource = sender as FormDataSource;
        var args = e as FormDataSourceCancelEventArgs;
        if (args != null && datasource != null)
        {
            var record = datasource.cursor() as abTable;
            if (record.recId == 0)
            {
                if (record.FieldInt1 == 1)
                {
                    boolean doCancel = !checkFailed("Value 1 is not allowed");
                    args.cancel(doCancel);
                }
            }
        }
    }

    /// <summary>
    /// Disallow changing the Field1 value on the form data source field, if the Field1 value contains the integer value 10
    /// </summary>

    [FormDataFieldEventHandler(formDataFieldStr(MyForm, abTable, FieldInt1), FormDataFieldEventType::Validating)]

    public static void FieldInt1_OnValidating(FormDataObject sender, FormDataFieldEventArgs e)
    {
        var dataObject = sender as FormDataObject;
        var args = e as FormDataFieldCancelEventArgs;
        if (args != null && dataObject != null)
        {
            var datasource = dataObject.datasource() as FormDataSource;
            if (datasource != null)
            {
                var record = datasource.cursor() as abTable;
                if (record.RecId > 0)
                {
                    if (record.FieldInt1 == 10)
                    {
                        boolean doCancel = !checkFailed("FormDataFieldEventType::Validating: Value 10 is not allowed");
                        args.cancel(doCancel);
                    }
                }
            }
        }
    }
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
