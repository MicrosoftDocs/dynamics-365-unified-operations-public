---
# required metadata

title: Naming guidelines for extensions
description: This topic describes the naming guidelines for extensions. Artifacts added via extension must have a name that is unique across all models at installation time. 
author: LarsBlaaberg
manager: AnnBe
ms.date: 07/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Naming guidelines for extensions

[!include [banner](../includes/banner.md)]

**High level guidance: use prefixes to reduce conflicts and improve identification**

## Naming model elements
Every element in a model must have a name that is unique across all models at installation time. However, at installation time, you don't know the names of all the models that your model might be installed together with. To accommodate this situation, every element name should include a prefix that is specific to your solution. By including this prefix when you name elements in your model, you significantly reduce the risk of naming conflicts.

+ If a model contains multiple solutions, each solution in the model can be identified by a different prefix. 
+ You must carefully choose the prefix to minimize the risk that other models from other parties use the same prefix for their elements.

When you extend functionality in other models, elements that are being extended already contain a prefix. However, you should not add your prefix to the extension elements, so that the names include multiple successive prefixes. Instead, you should include your prefix or another term or abbreviation as an infix when you name extension elements.

## Naming extensions

An extension element, such as a table extension, view extension, or form extension, must have a unique name that minimizes the risk of conflicts with extensions in other models. To minimize the risk of conflicts, the name should include a term, abbreviation, or infix that distinguishes the extension from other extensions to the same element in other models.

+ Include either the name of the model where the extension element resides or the prefix that the extension is associated with. For example, a Warehousing module extends the HCMWorker table and uses the **WHS** prefix in the name of all other elements. In this case, the extension might be named **HCMWorker.WHSExtension**. Notice that the prefix that is used to name other elements in the module is inserted as an infix in the name. As another example, an extension of the ContactPerson table in the ApplicationSuite model might be named **ContactPerson.ApplicationSuiteExtension** if the extension is intended to contain all extensions to the ContactPerson table from the ApplicationSuite model.
+ Suffix the name with the term **Extension**. For example, an extension of the InventLocation table should follow the pattern **InventLocation.&lt;Model&gt;Extension**.
+ Don't name the extension just **&lt;Element that is being extended&gt;.Extension**. For example, an extension of the InventLocation table must not be named **InventLocation.Extension**, because the risk of conflicts is too high.

## Naming extension classes

Extension classes that are used to augment the logic on tables, classes, or other elements must have a name that is unique across all types in all models. Preferably, the extension class should include the name of the type that is being extended. However, the name must also include a term, abbreviation, or prefix that distinguishes the class from other types.

+ Start the name of the extension class with the name of the type that is being augmented, and end the name with the term **\_Extension**.
Therefore, an extension class that augments the ContactPerson table should start with the name **ContactPerson** and end with **\_Extension**. For example, one extension class might be named **ContactPersonWHS\_Extension**.
+ Include either the name of the model where the extension element resides or the prefix that the extension is associated with. For example, a Warehousing module uses an extension class to augment the ContactPerson table and uses the **WHS** prefix in the name of all other elements. In this case, the extension class might be named **ContactPersonWHS\_Extension**. Notice that the prefix that is used to name other elements in the module is inserted as an infix in the name. As another example, an extension class that augments the ContactPerson table in the ApplicationSuite model might be named **ContactPersonApplicationSuite\_Extension** if the extension class is intended to contain all extensions to the ContactPerson table in the ApplicationSuite model.
+ Consider adding additional element type information in case you create a class extension for elements that can't be declared in the code (like Forms, DataSources, or FormControls). For example, **CustTableFormWHS\_Extension** is the extension for the **CustTable** form.
+ Don't name the extension just **&lt;Element that is being extended&gt;\_Extension**. For example, an extension class that augments the InventLocation table must not be named **InventLocation\_Extension**, because the risk of conflicts is too high.

## Naming fields, field groups, indexes, relations, and metadata elements added in extensions

Fields, field groups, indexes, relations, and metadata elements added in extensions must have a name that is unique across both the element that is being extended and other extension elements. Therefore, **these artifacts should include a prefix** that minimizes the risk of conflicts across models. In addition, these artifacts should have clear terms and abbreviations so that they can be easily understood. 

+ Include a prefix, term, or abbreviation at the beginning of the name of the metadata node. For example, an approving worker foreign key field is added as part of a table extension, and **WHS** is one of prefixes that are dedicated to other elements in the hosting model. In this case, the field might be named **WHSApprovingWorker**.

## Naming variables and methods added in extension classes
Variables and methods added in extension classes must have a name that is unique across both the type that is being extended and all other extension classes that extend the same type. Therefore, **these variables and methods should include a prefix** that minimizes the risk of conflicts across models. 

+ Include a prefix, term, or abbreviation at the beginning of the member name. For example, an approving worker class-level variable might be named **WHSApprovingWorker** if **WHS** is one of the prefixes that are used by other elements in the model. An **approveWork** method might be named **WHSApproveWork** if **WHS** is one of the prefixes that are used by other elements in the hosting model.

## Alternative naming convention

Implementation team could choose another way of naming objects with following convention.

### Simple naming rule

The naming rule is quite simple and straighforward - to use suffixes instead of prefixes:

- Use suffix <b>_PRJ_Extension</b> (hereafter <b>_PRJ</b> is capitalized model acronym) to name the class extension.

  Example:
  ```
  Classes\InventJournalTrans_PRJ_Extension  
  Classes\PurchTableForm_PurchTableDS_PRJ_Extension
  Classes\SalesFormLetter_PRJ_Extension
  ```

- Use suffix <b>_PRJ</b> to name any other application object/element (including methods and form artifacts on extensions).

  Example:
  ```
  BaseEnums\BankClientStreamType_PRJ
  BaseEnums\DayNight_PRJ
  BaseEnums\GanttBorderType_PRJ
  ExtendedDataTypes\DirOrganizationRoles_PRJ
  ExtendedDataTypes\ProjCategoryItemId_PRJ
  ExtendedDataTypes\EcoResProductTypeCategoryId_PRJ
  Tables\EcoResCategoryGroupsTable_PRJ
  Tables\CustomerEntityStaging_PRJ
  Tables\DispatchBoardProfile_PRJ
  Views\WorkflowCommentList_PRJ
  Views\PurchTableLastReqView_PRJ
  Queries\ActivityListOpen_PRJ
  Queries\AssetRecordList_PRJ
  BaseEnumExtensions\CaseCategoryGroupType.Extension_PRJ
  BaseEnumExtensions\NumberSeqModule.Extension_PRJ
  ExtendedDataTypesExtensions\CalendarId.Extension_PRJ
  ExtendedDataTypesExtensions\Description.Extension_PRJ
  ExtendedDataTypesExtensions\Name.Extension_PRJ
  TableExtensions\EcoResCategory.Extension_PRJ
  ViewsExtensions\CaseCategoryGroupType.Extension_PRJ
  ViewsExtensions\NumberSeqModule.Extension_PRJ
  QueryExtensions\smmActivities.Extension_PRJ
  FormExtensions\RetailStoreTable.Extension_PRJ
  FormExtensions\SalesAgreement.Extension_PRJ
  DataEntities\InventJournalTableEntity_PRJ
  Tables\InventJournalTableStaging_PRJ
  SecurityPrivileges\InventJournalTableEntityMaintain_PRJ
  SecurityPrivileges\InventJournalTableEntityView_PRJ
  Forms\PurchTable.Extension_PRJ\Datasources\PurchTable_PRJ
  Classes\SalesFormLetter_PRJ_Extension
  Classes\PurchReqWFExpendiParticipantProvider_PRJ_Extension
  ```

- Use special naming for Jobs(Runnable classes) to find them by Work Item Id.

  Example:
  
  ```
  PRJ00101_UpdateSalesOrder (where 00101 is Work Item Id) 
  ```

- For implementing event handlers we should use <b>EventHandler_PRJ</b> suffix, accompanying table name.

  ```
  class EcoResAttributeValueEventHandler_PRJ
  {
      [DataEventHandler(tableStr(EcoResAttributeValue), DataEventType::Inserting)]
      public static void EcoResAttributeValue_onInserting(Common sender, DataEventArgs e)
      {
          EcoResAttributeValue ecoResAttributeValue = sender as EcoResAttributeValue;
          // Call the method as if it was defined directly on EcoResAttributeValue.
          ecoResAttributeValue.defaultCategoryGroupId_PRJ();
      }
  }
  ```

- For implementing event handlers on the forms, please use <b>FormEventHandler_PRJ</b> suffix, accompanying with form name.

  ```
  class EcoResAttributeValueFormEventHandler_PRJ
  {
      [FormEventHandler(formStr(EcoResAttributeValue), FormEventType::Closing)]
      public static void EcoResAttributeValue_OnClosing(xFormRun sender, FormEventArgs e)
      {
          FormDataSource ecoResProduct_ds = sender.dataSource(formDataSourceStr(EcoResAttributeValue, EcoResProductAttributeValue));
          EcoResProductAttributeValue ecoResAttributeValue = ecoResProduct_ds.cursor();
      }
  }
  ```

### Benefits

- Proposed naming will help the developer easily find the existing extensions or customizations for the object.<br/>Thus class-extentions will be aligned with extended class as well as inherited-classes.

  Example:

  ```
  Tables\EcoResProduct
  Tables\EcoResProductType_PRJ
  Table Extensions\EcoResProduct.Extension_PRJ
  ...
  Classes\SalesFormLetter
  Classes\SalesFormLetter_PRJ_Extension
  ...
  Classes\SalesFormLetter_Invoice  
  Classes\SalesFormLetter_Invoice_PRJ_Extension
  ```

- Code extentions well-aligned with standard methods

  Example:

  ```
  [ExtensionOf(tableStr(EcoResCategory))]
  final class EcoResCategory_PRJ_Extension
  {
      public static EcoResCategory findByCode_PRJ(EcoResCategoryCommodityCode _ecoResCategoryCommodityCode,
                                                  EcoResCategoryHierarchyId   _ecoResCategoryHierarchyId,
                                                  boolean                     _forUpdate = false)
      {
        ...
      }
  }


  // example of using

  class PRJ0001_TutorialJob
  {
     EcoResCategory ecoResCategory = EcoResCategory::findByCode_PRJ(...);
  }

  ```

- VisualStudio IntelliSense helps to the developer to code with looking up of standard and new objects, alphabetically ordered.
Naming conventions contribute to consistency and to making the application easier to understand.

- The naming rule is well-determined leaving the developer from doubts in naming. 

- Present naming convention is fully align with having several models used in implementation projects.

  Example (with single _global_ model with models by countries\regions):

  ```
  Table Extensions\PurchTable\Fields\PaymClassId_PRJ (sample model 'Project' with arconym 'PRJ')
  Table Extensions\PurchTable\Fields\IntrastatCode_PRJEU
  Table Extensions\PurchTable\Fields\PaymClassId_PRJAPAC
  Table Extensions\PurchTable\Fields\PaymClassId_PRJUS
  ```
  
