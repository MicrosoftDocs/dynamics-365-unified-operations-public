---
# required metadata

title: Custom fields
description: While Microsoft Dynamics 365 for Finance and Operations provides an extensive set of fields out-of-the-box for managing a broad range of business processes, sometimes there is a need for a company to track additional information in the system. To accommodate this need, Finance and Operations allows you to create custom fields to tailor the application to fit your business.
author: jasongre
manager: AnnBe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  SysCustomFieldManageFields
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Operations Platform 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: Platform update 13
---

# Custom fields

[!include[banner](../includes/banner.md)] 

## Overview 
While Microsoft Dynamics 365 for Finance and Operations, Enterprise edition provides an extensive set of fields out-of-the-box for managing a broad range of business processes, sometimes there is a need for a company to track additional information in the system. To accommodate this need, Finance and Operations allows you to create custom fields to tailor the application to fit your business.

## Creating custom fields
Once you’ve identified additional information you would like to track in the application, you can create the custom field on the appropriate table and expose that new field on a page.   

The following steps describe the process for creating a custom field and placing that field on a form.  

1.   Navigate to the form where the new field is needed. 
2.   As the end goal is exposing the custom field on a form, the entry point for creating custom fields exists inside the personalization experience.  Open the personalization toolbar by selecting **OPTIONS**, and then **Personalize this form**. 
3.   Click **Insert** and then **Field**.  
4.   Select the region of the form where you want to expose the new field.  After selection, the **Insert fields** dialog will be opened showing a list of available existing fields that can be inserted into the selected region of the form.  
5.   Double check to ensure that the field you are interested in does not already exist in the list. If it does, you can simply mark that field in the list and select **Insert**.   
6.   Click the **Create new field** button above the list to initiate the process of creating a custom field. This will open the Create new field dialog.  
7.   In the Create new field dialog, enter the appropriate information.
     1.   Select the appropriate database table where this field should be added.  Note that only tables that support custom fields will appear in the drop-down list. See the section below for technical details on supported tables.  
     2.   Select the data type for the new field.  The available data types are checkbox, date, date time, decimal, number, picklist, and text.   
          - If you choose the Text data type, you may also specify the maximum length of the text that can be entered in this field. 
          - If you choose the Picklist data type, you may also select the set of valid values for the field.  
     3.   Provide a name, label, and help text for the field.  The name corresponds to the physical field name in the database, whereas the label and help text are the text used to represent this field in the user interface.  
8.   If this is the only field you need to create for this form, click **Save**.  If you need to create additional fields, click **Save and new** and go back to step 7. Note that there is currently a limit of 20 custom fields per table.
9.   Leaving the Create new field dialog will return the user to the Insert fields dialog.  Any custom fields that were just added will be automatically marked in the field list to be inserted into the form.  
10.   Click **Insert** to insert the marked fields into the selected region of the form. 
11.   **Optional:** Enable **Move** mode from the personalization toolbar to move the new fields to their desired location in the selected region. See [Personalize the user experience](personalize-user-experience.md) for more information about how to use the various personalization capabilities to optimize a form for your personal usage.  

### Sharing custom fields with other users
After you have created a custom field and exposed it on a form, you may want to provide this updated page view that includes the new field to other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

-   The recommended route is through the system administrator, who has the ability to push a personalization to all users or a subset of users. See [Personalize the user experience](personalize-user-experience.md) for more details. 

-   Alternatively, you can export your changes (called *personalizations*), send them to one or more users, and have each of those users import your changes.  The **Manage** option on the personalization toolbar enables you to export and import personalizations.

## Managing custom fields

Management of all the custom fields in the system can be accomplished through the **Custom fields** page in the System administration module.  This page allows users with access to a number of capabilities including: 
-   Seeing a list of all custom fields in the system
-   Limited editing of existing custom fields
-   Deleting custom fields
-   Exposing custom fields on data entities
-   Providing translations of custom field labels and help text

### Viewing all custom fields
The **Custom fields** page provides visibility to all the custom fields that have been defined in the system.  Simply select the table you are interested in, and the page will update to show a list of the custom fields associated with that table.  Choosing a custom field from the list will allow you to view all the details about the field.

### Editing custom fields
Once a custom field has been created, only certain pieces of information about the custom field can be modified from the **Custom fields** page.   

You *can* modify these attributes: 
-   Label 
-   Help text
-   Length, for Text fields

You *cannot* edit the following attributes: 
-   Field name
-   Data type

Additionally, for Picklist fields, the set of valid values for the custom field can be reordered, and new values can be added; however, existing values for the picklist field cannot be removed.   

### Exposing custom fields on data entities
It may also be important to allow custom fields to be visible on data entities.  Data entities are utilized in the [Open in Office](../../dev-itpro/office-integration/office-integration.md) feature, as well as for data import/export scenarios.  

Follow these steps to expose a custom field on a data entity: 
1.   Select the custom field of interest on the **Custom fields** form. 
2.   Expand the **Entities** section to see the set of relevant entities.  
3.   Click the **Edit** button.
4.   Modify the **Enabled** field to be checked for each entity that should expose this field.  
5.   Click **Apply changes** to save your selections.  

### Allowing custom fields to be displayed in other languages
Because custom fields may need to be accessed by users in a variety of languages, the **Custom fields** page provides a mechanism to allow the label and help text for a custom field to be translated into other languages.  

The following steps describe the process for translating custom fields in other languages: 
1.   Select the custom field of interest on the **Custom fields** page. 
2.   Select the **Translations** button in the action pane.  This will open a drop-down dialog with existing translations for this field.
3.   The **Language** drop-down shows the set of languages for which translations have already been provided. 
     1.   If you want to edit an existing translation, simply select the desired language from the drop-down and modify the values for the label and help text.  
     2.   Otherwise, click the **Add language** button, select the desired language from the dropdown, and then provide translated values for the label and help text.  
4.   Click **OK** when you are finished.  

### Deleting custom fields
In some rare cases, you may decide that a custom field is no longer needed. When this occurs, you can choose to delete the field from the **Custom fields** page. Note, however, this action cannot be undone, and will result in the data associated with the field being permanently deleted from the database. 

## Appendix 
### Tables that support custom fields
For performance and technical reasons, only tables that meet the following conditions currently allow custom fields to be added.

1.   The table must be tagged as one of these groups: 
     -   Group
     -   WorksheetHeader
     -   Main
     -   Miscellaneous
     -   Parameter
     -   Reference
     -   TransactionHeader
2.   The table cannot not extend another table.
3.   The table cannot be marked as a system table.
4.   The table cannot be a temporary table.
