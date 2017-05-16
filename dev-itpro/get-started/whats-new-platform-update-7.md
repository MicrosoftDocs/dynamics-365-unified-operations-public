---
# required metadata

title: What's new or changed in Dynamics 365 for Operations platform update 7 (May 2017)
description: This topic describes features that are either new or changed in Dynamics 365 for Operations platform update 7. This version was released in May 2017 and has a build number of 7.0.XXXX.XXXX.
author: tonyafehr
manager: AnnBe
ms.date: 05/9/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 54cfeac5-e977-4c02-8e7a-4ddb4b336713
ms.search.region: Global
# ms.search.industry: 
ms.author: tonyafehr
ms.search.validFrom: 
ms.dyn365.ops.version: Platform update 7

---

# What's new or changed in Dynamics 365 for Operations platform update 7 (May 2017)


[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Operations platform update 7. This version was released in May 2017 and has a build number of 7.0.XXXX.XXXX.

## Configuration data projects ##
Using a configuration data project, you can easily export configuration data and move it from one instance to another instance. This feature provides an updated user interface, and the ability to easily manage templates and projects.

## Development tooling - New tabbed workspace pattern ##
A new tabbed workspace form pattern is now available. You can now include tab pages that house embedded Power BI reports. This feature is our first step toward moving away from horizontally-scrolling workspaces.

 ## Development and customization - Extending a group control ##
 The Dynamics 365 for Operations development tools and runtime platform now support extending an extended form, for example, extending a form that is already extended in a referenced model. This fixes an issue that originally prevented extending a field/button group control if the group control belongs to a form extension.
 
## Development and customization - Validating events on form data sources and form data source fields ##
Validation events on form data source (FormDataSourceEventType) and form data source fields (FormDataFieldEventType) now support invalidating user-specified values. The following example illustrates this feature. The example uses a form named **MyForm** that contains a data source named **abTable**, and a field named **FieldInt1**.


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
