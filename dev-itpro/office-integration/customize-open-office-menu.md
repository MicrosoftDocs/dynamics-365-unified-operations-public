---
# required metadata

title: Customize the Open in Microsoft Office menu
description: Most pages include an Open in Microsoft Office menu. This topics provides information about the Open in Office menu, and explains how customize it by adding, removing, and changing options.
author: ChrisGarty
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 270774
ms.assetid: 3ff1184b-1a8a-4102-9600-f1776634d95f
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4

---

# Customize the Open in Microsoft Office menu

[!include[banner](../includes/banner.md)]


Most pages include an Open in Microsoft Office menu. This topics provides information about the Open in Office menu, and explains how customize it by adding, removing, and changing options.

Overview
--------

The **Open in Microsoft Office** menu button (**Open in Office** menu) is a system-defined button that appears on pages. The **Open in Office** menu contains menu items that let you export data to various Office products, such as Microsoft Excel and Microsoft Word. The following table describes the menu items on the **Open in Office** menu.

| Menu item       | Description                                                                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Export to Excel | The data is exported to an Excel workbook. The workbook contains no references back to Microsoft Dynamics 365 for Operations, and the data can't be refreshed.                                                                                               |
| Export to Word  | The data is exported to a Word document. The document contains no references back to Dynamics 365 for Operations, and the data can't be refreshed.                                                                                                           |
| Open in Excel   | A workbook is created that contains the Microsoft Dynamics Office add-in. The workbook contains a reference back to Dynamics 365 for Operations, and the data can be refreshed, updated, and published from the Data Connector that is hosted in the add-in. |

## How menu items are added to the Open in Office menu
The export options are added to the **Open in Office** menu in the following manner:

1.  In the **Export to Excel** group, a menu item is added for each visible grid.
2.  For each root data source on the page, the set of data entities that have the same root data source is determined. For each of these data entities, the following menu items are added:
    -   In the **Open in Excel** group, a menu item is added for a default export of the data entity.
    -   In the **Open in Excel** group, a menu item is added for each Document Template record of the **Excel** type that has the same root data entity and is marked for inclusion on the **Open in Office** menu.
    -   In the **Export to Word** group, a menu item is added for each Document Template record of the **Word** type that has the same root data entity and is marked for inclusion on the **Open in Office** menu.

## Default exports
The **Open in Office** menu provides a default export for each data entity. This export includes all the fields in the **AutoReport** group on the data entity. If **SaveDataPerCompany** is set to **Yes** for the data entity, a filter is applied to limit the data to the current company.

## Document templates
Document templates can be added from the **Document templates** page. Several fields that are associated with each Document Template record control the behavior of that template on the **Open in Office** menu.

| Field                | Description                                                                                                                                                         |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Root data entity     | The root data entity of the template. The root data entity is used to determine which pages the template can be included on.                                        |
| List in Office menu  | If this field is selected, the template will be included on the **Open in Office** menu on applicable pages. (The applicable pages depend on the root data entity). |
| Apply record filter  | If this field is selected, the data will be filtered, based on the record that is currently selected on the page.                                                   |
| Apply company filter | If this field is selected, the data will be filtered, based on the current company.                                                                                 |

### Trimmed template columns and fields

For Excel templates that are included on the **Open in Office** menu, columns and fields will be trimmed from the workbook, based on the configuration keys that are applied to the system and the applicable country/region context. If a configuration key is associated with a column or field in the workbook, the column or field will be removed if the configuration key is disabled. If a set of country/region codes is associated with the column or field in the workbook, the column or field will be removed if the country/region code isn't in scope.

## Open in Office menu customization
There are several methods for customizing the content that appears on the **Open in Office** menu on a given page. For example, you can customize the content statically through metadata properties on model element and code attributes. However, customization via code gives you the finest level of control. In code, you can either implement one or more interfaces on a page, or use extensions and event subscriptions. The following sections describe the customization scenarios that are most often used.

### Modifying the Open in Office menu through interfaces

If you must modify a page that you own, interfaces are the most appropriate customization method, because they give access to all private members of the page and allow for deeper customization. You can apply the following interfaces to the code for a page.

| Interface                              | Description                                                                                                    |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------|
| OfficeIMenuCustomizer                  | Use this interface to modify the set of data entities that is considered for a page and add custom menu items. |
| OfficeIGeneratedWorkbookCustomExporter | Use this interface to do a custom export of a workbook that is generated at run time.                          |
| OfficeITemplateCustomExporter          | Use this interface to do a custom export that is based on a Document Template record.                          |

### Modifying the Open in Office menu through extensions and event subscriptions

If you must modify a page that you don't own, you should avoid using interfaces, because that approach will require over-layering. Instead, you should do the customization through extensions and event subscriptions. To use this approach, implement an extension class that subscribes to the **OnIntializing** event of the page that you're customizing. From this event handler, get the **OfficeFormRunHelper** for the page, and subscribe to its **OfficeMenuInitializing** event. The following example shows sample code for this approach.

    public static class MyForm_Extension
    {
        [FormEventHandler(formStr(MyForm), FormEventType::Initializing)]
        public static void ExportToExcel_DataEntityCustom_OnInitializing(xFormRun sender, FormEventArgs e)
        {
            FormRun formRun = sender as FormRun;
            if (formRun)
            {
                OfficeFormRunHelper officeHelper = formRun.officeHelper();
                if (officeHelper)
                {
                    officeHelper.OfficeMenuInitializing += eventhandler(MyForm_Extension::officeMenuInitializingHandler);
                }
            }
        }
        private static void officeMenuInitializingHandler(FormRun _formRun, OfficeMenuEventArgs _eventArgs)
        {
            // Modify the OfficeMenuOptions available on the OfficeMenuEventArgs.menuOptions() as necessary.
        }
    }

## Typical customization scenarios
The following examples assume that the **\_menuOptions** variable contains the **OfficeMenuOptions** instance that you're customizing.

### Modifying the set of data entities that is considered for a page

Many of the menu items on the **Open in Office** menu are added automatically, based on the data entities that are considered for the page. However, in some cases, the algorithm that is used to determine the set of data entities might not determine the correct set. To modify the set of data entities that is considered for the page, you can use the **OfficeMenuOptions** that is available from either the **OfficeIMenuCustomizer.customizeMenuOptions** method or the **OfficeFormRunHelper.OfficeMenuInitializing** delegate.

    // Add an entity to the list
    OfficeMenuDataEntityOptions entityOptions  = OfficeMenuDataEntityOptions::construct(tableStr(MyEntity));
    _menuOptions.dataEntityOptions().addEnd(entityOptions);
    // Remove an entity from the list
    ListIterator dataEntityOptionsIterator = new ListIterator(_menuOptions.dataEntityOptions());
    while (dataEntityOptionsIterator.more())
    {
        OfficeMenuDataEntityOptions dataEntityOptions = dataEntityOptionsIterator.value();
        if (dataEntityOptions.dataEntityName() == tableStr(MyOtherEntity))
        {
            dataEntityOptionsIterator.delete();
        }
        else
        {
            dataEntityOptionsIterator.next();
        }
    }

### Specifying the default data entity–related options that are included

The **OfficeMenuDataEntityOptions** class lets you specify whether to include a menu item for a default export or a menu item that is related to a document template.

    // Find the entity options if they were included by default.
    OfficeMenuDataEntityOptions entityOptions = _menuOptions.getOptionsForEntity(tableStr(MyEntity));
    if (!entityOptions)
    {
        // The entity options were not included. Add them.
        entityOptions = OfficeMenuDataEntityOptions::construct(tableStr(MyEntity);
        _menuOptions.dataEntityOptions().addEnd(entityOptions);
    }
    entityOptions.includeDefault(false); // Don't include the default export menu item.
    entityOptions.includeTemplates(false); // Don’t include Document Template related menu items.

### Adding a custom export menu item – Generating a workbook

To explicitly add a menu item, you must add it to the **OfficeMenuOptions.customMenuItems()** list. To add a menu item that corresponds to a workbook that is generated at run time, use an **OfficeGeneratedExportMenuItem**.

    OfficeGeneratedExportMenuItem menuItem = OfficeGeneratedExportMenuItem::construct(tableStr(MyEntity), "MyCustomGeneratedExportId");
    menuItem.setDisplayNameWithDataEntity();
    _menuOptions.customMenuItems().addEnd(menuItem);

To define what is actually exported, use an **ExportToExcelDataEntityContext**. The method for specifying the **ExportToExcelDataEntityContext** depends on whether you're using interfaces or extensions and event subscriptions to customize the **Open in Office** menu.

#### Using interfaces

If you're using interfaces, you must implement the **OfficeIGeneratedWorkbookCustomExporter.getDataEntityContext()** method.

    public ExportToExcelDataEntityContext getDataEntityContext(OfficeGeneratedExportMenuItem _menuItem)
    {
        ExportToExcelDataEntityContext context = null;
        if (_menuItem.id() == "MyCustomGeneratedExportId")
        {
            context = ExportToExcelDataEntityContext::construct(tableStr(MyEntity), tableFieldGroupStr(MyEntity, MyFieldGroup);
        }
        return context;
    }

#### Using extensions and event subscriptions

If you're using extensions and event subscriptions, the **OfficeGeneratedExportMenuItem.getDataEntityContext** delegate should be subscribed to before you add the menu item to the **OfficeMenuOptions.customMenuItems()** list. The code for the event handler should resemble the preceding code for the interface. The following example shows how to do the event subscription.

    menuItem.getDataEntityContext += eventhandler(MyForm_Extension::getDataEntityContextHandler);

### Adding a custom export menu item – Specifying a document template

To explicitly add a menu item, you must add it to the **OfficeMenuOptions.customMenuItems()** list. To add a menu item that corresponds to a Document Template record, use an **OfficeTemplateExportMenuItem**.

    OfficeTemplateExportMenuItem menuItem = OfficeTemplateExportMenuItem::construct(OfficeAppApplicationType::Excel, "MyTemplateId", "MyCustomTemplateExportId");
    _menuOptions.customMenuItems().addEnd(menuItem);

To modify the template at run time, you can supply a set of initial filters. These filters will replace any filters in the template for the specified data entities. Additionally, you can modify filters and specify many settings by using **WorkbookSettingsManager**. The following sections show examples.

#### Using interfaces

If you're using interfaces, you must implement the **OfficeITemplateCustomExporter.getInitialTemplateFilters()** and **OfficeITemplateCustomExporter.updateTemplateSettings()** methods.

    public Map getInitialTemplateFilters(OfficeTemplateExportMenuItem _menuItem)
    {
        Map initialFilters = new Map(Types::String, Types::Class);
        if (_menuItem.id() == "MyCustomTemplateExportId")
        {
            // Add an initial filter.
            ExportToExcelFilterTreeBuilder bldr = new ExportToExcelFilterTreeBuilder(_menuItem.dataEntityName());
            FilterNode filter = // create the filter…
            initialFilters.insert(_menuItem.dataEntityName(), filter);
        }
        return initialFilters;
    }
    public void updateTemplateSettings(OfficeTemplateExportMenuItem _menuItem, Microsoft.Dynamics.Platform.Integration.Office.SettingsManager _settingsManager)
    {
        if (_menuItem.id() == "MyCustomTemplateExportId")
        {
            // Set a new filter.
            ExportToExcelFilterTreeBuilder bldr = new ExportToExcelFilterTreeBuilder(_menuItem.dataEntityName());
            FilterNode filter = // create the filter…
            Excel.WorkbookSettingsManager workbookSettingsManager = _settingsManager as Excel.WorkbookSettingsManager;
            workbookSettingsManager.SetEntityFilter(entityMetadata.PublicEntityName, filter);
            // Adjust settings.
            DataConnectorAppletSettings settings = settingsManager.DataConnectorSettings;
            DataConnectorAppletUserOptions options = settings.DataOptions;
            options.RefreshOnOpen = true;
            options.EnableDesign = false;
            workbookSettingsManager.DataConnectorSettings = settings;
        }
    }

#### Using extensions and event subscriptions

If you're using extensions and event subscriptions, the **OfficeTemplateExportMenuItem.getInitialTemplateFilters** and **OfficeTemplateExportMenuItem.updateTemplateSettings** delegates should be subscribed to before you add the menu item to the **OfficeMenuOptions.customMenuItems()** list. The code for the event handlers should resemble the preceding code for the interface. The following example shows how to do the event subscription.

    menuItem.getInitialTemplateFilters += eventhandler(MyForm_Extension::getInitialTemplateFiltersHander);
    menuItem.updateTemplateSettings += eventhandler(MyForm_Extension::updateTemplateSettingsHandler);

## Additional customizations
The following customizations let you modify the contents of the **Open in Office** menu for a page without using interfaces or extensions and event handlers.

### Removing an Export to Excel menu item for a grid

On the **Open in Office** menu, the **Export to Excel** group will contain a menu item for each visible grid. To remove a grid from the **Open in Office** menu, set the **ExportAllowed** metadata property on the grid to **No**. After you make this change, users won't be able to export the grid by using the shortcut menu for the grid.

### Renaming an Export to Excel menu item for a grid

To rename the **Export to Excel** menu item that is related to a grid, set the **ExportLabel** metadata property on the grid to the appropriate label.

### Removing all menu items for a data entity from all pages

Integration scenarios require that some data entities be publicly available via the OData Service. However, it isn't always appropriate that these data entities appear on the **Open in Office** menu by default. In this scenario, you can add the **OfficeMenuOmit** code attribute to the entity declaration.

    [OfficeMenuOmit]
    public class MyEntity extends common
    {
        // Entity code…
    }

After you make this change, by default, the entity won't appear on the **Open in Office** menu on pages that have a matching root data source. However, if the entity should be added to a specific page, you can use other customization mechanisms to add it.

### Adding a menu item button to a page that corresponds to an Open in Office menu entry

Sometimes, it's appropriate that the Action Pane of a page have a menu item button that corresponds to a custom menu item on the **Open in Office** menu. In this case, you can model a menu item button that has the following properties:

-   **Menu Item Type:** **Action**
-   **Menu Item Name:** **ExportToExcelExportForm**
-   **Parameters:** The ID of the menu item

Then, a mouse click of this menu item button is equivalent to a mouse click of the corresponding menu item on the **Open in Office** menu.



