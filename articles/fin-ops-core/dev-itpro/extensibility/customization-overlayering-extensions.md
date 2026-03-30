---
title: Customize through extension and overlayering
description: Learn about the two methods of customizing source code and metadata of model elements, overlayering and extensions.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 8a2b3107-247d-4362-8d4d-6ee6257abfcc
---

# Customize through extension and overlayering

[!include [banner](../includes/banner.md)]

This article discusses two methods for customizing the source code and metadata of model elements: overlayering and extensions. It also details the supported extension capabilities.

## Overlayering

You can customize the source code and metadata of model elements that Microsoft or third-party Microsoft partners ship. To customize the metadata and source code of a model, create a new model that overlays the model you want to customize. For example, solution developers can provide code in the SLN layer, independent software vendors can use the ISV layer, and value-added resellers can use the VAR layer. Functionality defined in higher layers (the VAR layer in this example) can override the functionality of lower layers. The overlaying model must belong to the same **Package** as the source model and belong to a layer that is higher than the source model. Overlayering is a powerful tool for performing advanced customizations of metadata and source code, but it can increase the cost of upgrading a solution to a new version.

## Extensions

You can customize an application by using *extensions*. An extension enables you to add functionality to existing model elements and source code. Extensions provide the following capabilities:

- Creating new model elements.
- Extending existing model elements.
- Extending source code by using class extensions.
- Customizing business logic. Ways to customize business logic include:
  - Creating event handlers to respond to framework events, such as data events.
  - Creating event handlers to respond to event delegates that the application defines.
  - Creating new plug-ins.

To get started, review or complete this tutorial: [Customize model elements through extension](customize-model-elements-extensions.md).

## Extension models and packages

You can create a model that contains only new model elements, new code, or extensions. Compile this model into its own separate assembly. You can package these assemblies, along with related metadata and runtime artifacts, as a deployable package file. Deploy the package on a runtime sandbox or production environment. To create an extension model, go through the **Create model** wizard and select **Create new package** on the second step.

:::image type="content" source="./media/1_cust.png" alt-text="Screenshot of the Create model wizard with Create new package option selected.":::

Extension models offer several advantages, including:

- **Application lifecycle management (ALM):** Extension models simplify and improve the performance of deployments, builds, test automation, and delivery to customers.
- **Design time performance:** Building your model or project doesn't require you to recompile the entire application.
- **Servicing:** In the cloud, Microsoft can install, patch, upgrade, and change internal APIs without affecting your customizations.
- **Upgrades:** Unlike overlayering, extensions reduce the cost of upgrading to a new version, as this approach eliminates costly code and metadata conflicts.

The following diagram illustrates how extensions get isolated in their assemblies.

:::image type="content" source="media/ax7customization1.png" alt-text="Screenshot of a diagram illustrating how extensions get isolated in their assemblies.":::

## Code extensions

You can extend source code in three ways:

- By subscribing to events (framework events and delegates).
- By writing plug-ins.
- By creating class extensions (also known as class augmentation), see the following section.

Understand the following characteristics of framework events:

- Events are implemented as multicast delegates, which means that more than one event handler can subscribe to any particular event.
- Events are broadcast; there's no sequencing of calls to event handlers.
- Event handlers execute within the transaction scope of the base methods.

### Events

Raise events as preceding and succeeding operations around the base methods. This approach means that you can run code before a base method is called and after it finishes. Microsoft Dynamics AX 2012 introduced XPP events, which are also available in this release and can be subscribed to in your extensions.

### Plug-ins

Plug-ins are extension points that the base application defines. By using a class-factory pattern, plug-ins enable you to replace the base functionality. To learn how to implement a plug-in, see the tutorial [Customize model elements through extension](customize-model-elements-extensions.md).

### Class extensions

Class extensions enable you to augment a class by adding methods and variables to existing classes, tables, and forms. For more information, see the article [Class extension model in X++](class-extensions.md).

## Form extensions

You can extend the functionality of a form by extending its controls and data sources. For example, in a form extension, you can:

- Add a new control.
- Enable or disable a control.
- Change the text or label property of a control.
- Change a control's visibility.
- Change a form's help text.
- Change a form's caption.
- Add a new data source.
- Add a form part.

Other ways to customize a form, such as reordering controls in the form, are planned for a future release. In Microsoft Dynamics AX 2012, you could override form methods. In the current version, use extensions to implement event handlers that the base implementations of form methods call. The following table lists each method and its associated events.

|**Published form DataSource method**|**Preceding event**|**Succeeding event**|
|---|---|---|
|active|N/A|Activated|
|delete|Deleting|Deleted|
|validateWrite|ValidatingWriting|ValidatedWrite|
|write|Writing|Written|
|create|Creating|Created|
|executeQuery|N/A|QueryExecuted|
|linkActive|N/A|PostLinkActive|
|init|N/A|Initialized|
|validateDelete|ValidatingDelete|ValidatedDelete|
|reread|N/A|Reread|
|selectionChanged|N/A|SelectionChanged|
|markChanged|N/A|MarkChanged|
|leaveRecord|LeavingRecord|LeftRecord|

|**Published form Object method**|**Preceding event**|**Succeeding event**
|---|---|---|
|init|Initializing|Initialized
|close|Closing|N/A
|run|N/A|PostRun
|activate|N/A|Activated

|**Published form Control method**|**Preceding event**|**Succeeding event**
|---|---|---|
|modified|N/A|Modified
|validate|Validating|Validated
|leave|Leaving|LostFocus
|enter|N/A|Enter
|gotFocus|N/A|GotFocus
|clicked|N/A|Clicked
|selectionChange|SelectionChanging|N/A
|pageActivated|N/A|PageActivated
|allowPageDeactivate|AllowPageDeactivate|N/A
|expand|Expanding|Expanded
|tabChanged|N/A|TabChanged
|dialogClosed|N/A|DialogClosed

### Code behind extension forms

Use class extensions to add X++ logic to form extensions. This approach defines state variables that form and control event handlers can access. It also enables you to override form methods without overlayering code. For an example, see [this](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/10/11/code-behind-extension-forms-how-to-add-state-variable-and-override-methods-without-overlayering) blog article.

## Table extensions

Create a table extension to extend a table's design and logic. You can add new fields, field groups, indexes, mappings, and relations. You can also add new fields to existing field groups, change the label of a table field, and change the Created By, Created Date Time, Modified By, and Modified Date Time properties. By using table extensions, you can also change the Extended Data Type property on fields and set it to an EDT that is derived from the current EDT. (*This feature is available as of platform update 8*).

In Microsoft Dynamics AX 2012, you override the virtual methods of a table's base class to control the behavior that occurs during table operations, such as when creating, reading, updating, or deleting. In the current version, you use extensions to implement event handlers that the base implementations of the table methods call. The following table lists each table method and its events.

|**Published Table method**|**Preceding event**|**Succeeding event**|
|---|---|---|
|validateWrite|ValidatingWrite|ValidatedWrite|
|validateDelete|ValidatingDelete|ValidatedDelete|
|validateField|ValidatingField|ValidatedField|
|validateFieldValue|ValidatingFieldValue|ValidatedFieldValue|
|modifiedField|ModifyingField|ModifiedField|
|modifiedFieldValue|ModifyingFieldValue|ModifiedFieldValue|
|Insert|Inserting|Inserted|
|Update|Updating|Updated|
|Delete|Deleting|Deleted|
|Initvalue|InitializingRecord|InitializedRecord|
|FinalDeleteValidation|Executed when a delete operation is performed on a table object, before the operation is committed to the underlying database table|N/A|
|FinalInsertValidation|Executed when an insert operation is performed on a table object, before the operation is committed to the underlying database table|N/A|
|FinalReadValidation|Executed when a read operation is performed on a table object.|N/A|
|FinalUpdateValidation|Executed when an update operation is performed on a table object, before the operation is committed to the underlying database table.|N/A|

Validation events use the **DataEventArgs** parameter to capture and return results. The display and edit method modifiers are supported on table extensions.

## View and Data entity extensions

To get much of the functionality that table extensions provide, extend a view or data entity.

## Enum extensions

You can extend any enum that's marked extensible (`IsExtensible=True`).

:::image type="content" source="./media/extensibleenums-300x158.png" alt-text="Screenshot of extensible enums settings." lightbox="./media/extensibleenums.png":::

When you extend an enum, you can add new enum values to it. Keep the following points in mind when working with extensible enums:

1. You can't use X++ logic that depends on the integer value of enum values. For example, `If (Enum1.v1 > Enum1.v2) ...` isn't supported for extensible enums.
1. When you synchronize enum values of extensible enums into the database:
    - Integer values that belong to the baseline enum come from the metadata and are deterministic.
    - Integer values that are an extension are generated during the synchronization process and aren't deterministic.

## EDT extensions

Extend an EDT element to modify any of the following properties:

- Form help
- Label
- String size
- Help text

## Query extensions

Extend a Query element to:

- Add ranges to an existing data source.
- Add new (embedded) data sources to an existing data source.
- Add new fields to an existing data source.

## Menu extensions

Extend a Menu element to:

1. Add new menu items, submenus, menu references, and tile references to an existing menu.
1. Hide an existing menu item, tile, or submenu in a menu by setting the **Visible** property to No.

:::image type="content" source="./media/menuextensions-300x137.png" alt-text="Screenshot of menu extensions settings." lightbox="./media/menuextensions.png":::

## Security role and duty extensions

Extend a Security Role or a Security Duty to add new duties and privileges to these elements.

## Report extensions

You can customize reports and business docs by using extensions. The following tutorials help you learn more about report extensions.

[Customize App Suite reports by using extensions](../analytics/customize-app-suite-reports-with-extensions.md): Use a pure extension model to fully support customizations to reporting solutions in the standard application. This article offers guidance on how to add the most common customizations to standard application reports without over-layering Application Suite artifacts.

[Create custom designs for business documents](../analytics/custom-designs-business-docs.md): This article focuses on the steps involved in crafting a custom report design for an existing application business document by using a pure extension model. Follow the steps to associate a custom report design with an application document instance.

[Expand Application Suite report data sets](../analytics/expand-app-suite-report-data-sets.md): This article focuses on the expansion of an existing report data set produced by using X++ business logic in a Report Data Provider (RDP) class. Use custom delegate handlers and table extensions to include extra field data and calculations without...

[Extend report menu items to redirect user navigation](../analytics/extend-report-menu-items.md): This article focuses on the process of extending existing application menu items to redirect navigations with minimal code changes. By using this technique, you avoid the hassle of tracking down and replacing all references to an existing application...

## Label extensions

Create label extension files to modify the string value of a label, add new labels to the same label file, or add new languages. To create a label extension file, name it with a `_extension` suffix. For example, to extend the **FLM** labels of the Fleet Management model, follow these steps:

1. Create a project that belongs to a model that references Fleet Management (the model Fleet Management Extension is an example).
1. Add a new label file to the project and name it **FLM\_Extension**.
1. Within the FLM\_Extension label file, create new labels or modify the value of labels that are defined in the **FLM** label file of the Fleet Management model. Use the standard label editor to define new labels or redefine labels that already exist in the original FLM label file.
1. If your goal is to create translations of the FLM label, right-click on the FLM\_Extension element in your project and select **Add new languages**. Follow the wizard to add translation files to the FLM labels.

> [!NOTE]
> If the FLM\_Extension file already exists in another model, you can name your file **FLM\_ExtensionN** where N is any integer (for example, FLM\_Extension2, FLM\_Extension3, and so on).

## Extension of country/region codes

> [!NOTE]
> This functionality is available as of Platform update 7.

The **Country Region Codes** property enables developers to restrict functionality to certain regions or countries based on the current legal entity’s primary address. Developers can extend this functionality by setting the Country Region Codes property on the following extension element types: Menu extension, Menu Item extension, Table extension (and fields), Form extensions (form controls), EDT extensions, Enum extensions, and View extensions.

You can specify additional country/region codes in their extension. The effective country/regions (at runtime) associated with an element are the union of all codes from the baseline element and all its extensions.

## Event argument types

When an event takes place, the delegates described in the preceding sections get triggered. This section provides the details of the types of the arguments that are passed as the event arguments. Some of the entries in the following table have a null in the column designating the event args. This value means that no arguments are passed - the relevant information is in the first argument (typically called sender) in this case.

| Event                           | Argument type                |
|---------------------------------|----------------------------------|
| onDefaultedField                | DefaultFieldEventArgs            |
| onDefaultedRow                  | null                             |
| onDefaultingField               | DefaultFieldEventArgs            |
| onDefaultingRow                 | null                             |
| onDeleted                       | null                             |
| onDeletedEntityDataSource       | DataEntityContextResultEventArgs |
| onDeleting                      | null                             |
| onDeletingEntityDataSource      | DataEntityContextResultEventArgs |
| onFindingEntityDataSource       | DataValidationEventArgs          |
| onFoundEntityDataSource         | DataEntityContextRecordEventArgs |
| onGettingDefaultingDependencies | DefaultingDependenciesEventArgs  |
| onGotDefaultingDependencies     | DefaultingDependenciesEventArgs  |
| onInitializedEntityDataSource   | DataEntityContextEventArgs       |
| onInitializedRecord             | null                             |
| onInitializingEntityDataSource  | DataEntityContextEventArgs       |
| onInitializingRecord            | null                             |
| onInserted                      | null                             |
| onInsertedEntityDataSource      | DataEntityContextResultEventArgs |
| onInserting                     | null                             |
| onInsertingEntityDataSource     | DataEntityContextResultEventArgs |
| onMappedDatasourceToEntity      | DataEntityContextEventArgs       |
| onMappedEntityToDataSource      | DataEntityContextEventArgs       |
| onMappingDatasourceToEntity     | DataEntityContextEventArgs       |
| onMappingEntityToDataSource     | DataEntityContextEventArgs       |
| onModifiedField                 | ModifyFieldEventArgs             |
| onModifiedFieldValue            | ModifyFieldValueEventArgs        |
| onModifyingField                | ModifyFieldEventArgs             |
| onModifyingFieldValue           | ModifyFieldValueEventArgs        |
| onPersistedEntity               | DataEntityContextEventArgs       |
| onPersistingEntity              | DataEntityContextEventArgs       |
| onPostedLoad                    | null                             |
| onPostingLoad                   | null                             |
| onUpdated                       | null                             |
| onUpdatedEntityDataSource       | DataEntityContextResultEventArgs |
| onUpdating                      | null                             |
| onUpdatingEntityDataSource      | DataEntityContextResultEventArgs |
| onValidatedDelete               | ValidateEventArgs                |
| onValidatedField                | ValidateFieldEventArgs           |
| onValidatedFieldValue           | ValidateFieldValueEventArgs      |
| onValidatedWrite                | ValidateEventArgs                |
| onValidatingDelete              | ValidateEventArgs                |
| onValidatingField               | ValidateFieldEventArgs           |
| onValidattingFieldValue         | ValidateFieldValueEventArgs      |
| onValidatingWrite               | ValidateEventArgs                |

## Development tools support

The development tools in Visual Studio provide integrated features to help you create and work with extensions. For example, when you right-click an element name in **Application Explorer**, you can create an extension for that element.

:::image type="content" source="./media/3_cust.png" alt-text="Screenshot of Create extension on context menu.":::

To create an extension, the current project in **Solution Explorer** must belong to a model that references the model of the selected element in **Application Explorer**. To view the model for a particular project, view the project properties.

:::image type="content" source="./media/4_cust.png" alt-text="Screenshot of Property page for project.":::

Visual Studio creates the extension file for you, either in the current project or in a new project. You can then work with the extension file either as source code or by using a designer. You package a code-extension model for deployment exactly like you would package any other model. On the **Dynamics 365** menu, point to **Deploy**, click **Create Deployment Package**, and then select the check box for the package name.

### Framework events

Tables, form data sources, form controls, and other element types that support extension events list the available events (and delegates) under an **Events** collection node. For example, viewing the **Events** node of a table extension shows events that the framework defines, and delegate methods that application developers define.

:::image type="content" source="./media/5_cust.png" alt-text="Screenshot of the list of framework events.":::

> [!NOTE]
> The designer exposes events on different element and sub-element types, like table events, form events, form data source events, form control events, and others. Open the context menu of an event node to interact with events:

:::image type="content" source="./media/6_cust.png" alt-text="Screenshot of Copy event handler method on context menu.":::

- **Copy event handler method**: This option copies a method signature to the clipboard. You can paste it in any X++ code editor to define a method that subscribes to the selected event.
- **Find event handlers**: Searches and lists all methods subscribed to the selected event.

## Additional resources

[Customize model elements through extension](customize-model-elements-extensions.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
