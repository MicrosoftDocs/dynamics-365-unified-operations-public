---
# required metadata

title: Create and work with custom fields
description: This topic shows you how to create custom fields through the user interface to tailor the application to fit your business.
author: jasongre
ms.date: 05/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysCustomFieldManageFields
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2018-1-31
ms.dyn365.ops.version: Platform update 13
---

# Create and work with custom fields

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

While there is an extensive set of fields out-of-the-box for managing a broad range of business processes, sometimes there is a need for a company to track additional information in the system. While programmers can be used to add those fields as extensions in the developer tools, the custom fields feature allows fields to be added directly from the user interface, thereby allowing you to tailor the application to fit your business using your web browser.

*Only users with special permissions have access to this feature.*

This video shows how easy it is to add a custom field to a page: [Adding custom fields](https://www.youtube.com/watch?v=gWSGZI9Vtnc).

## Creating custom fields

After you've identified additional information that you would like to track in the application, you can create the custom field on the appropriate table and expose that new field on a page.

The following steps describe the process for creating a custom field and placing that field on a form.

1. Navigate to the form where the new field is needed.
2. Because the end goal is to expose the custom field on a form, the entry point for creating custom fields exists inside the personalization experience. Open the personalization toolbar by selecting **Options**, and then **Personalize this form**.
3. Click **Insert** and then **Field**.
4. Select the region of the form where you want to expose the new field. After selection, the **Insert fields** dialog box will display a list of existing fields that can be inserted into the selected region of the form.
5. Ensure that the field you are interested in does not already exist in the list. If it does, you can simply select that field in the list and click **Insert**.
6. Click the **Create new field** button above the list to initiate the process of creating a custom field. This will open the **Create new field** dialog box.

    If you do not see the **Create new field** button, you do not have the necessary permissions to use this feature.

7. In the **Create new field** dialog box, enter the following information.
   
    1. Select the database table where this field should be added. Note that only tables that support custom fields will appear in the drop-down list. See the section below for technical details on supported tables.

    2. Select the data type for the new field. The available data types are checkbox, date, date time, decimal, number, picklist, and text.

        - If you choose the text data type, you can also specify the maximum length of the text that can be entered in this field.
        - If you choose the picklist data type, you can also select the set of valid values for the field.

    3. Provide a name, label, and help text for the field. The name corresponds to the physical field name in the database, whereas the label and help text are the text used to represent this field in the user interface.

8. If this is the only field that you need to create for this form, click **Save**. If you need to create additional fields, click **Save and new** and go back to step 7. Note that there is currently a limit of **20 custom fields per table**.
9. Leaving the **Create new field** dialog box will return you to the **Insert fields** dialog box. Any custom fields that were just added will be automatically marked in the field list to be inserted into the form.
10. Click **Insert** to insert the marked fields into the selected region of the form.
11. **Optional:** Enable **Move** mode from the personalization toolbar to move the new fields to their desired location in the selected region. See [Personalize the user experience](personalize-user-experience.md) for more information about how to use the various personalization capabilities to optimize a form for your personal usage.

> [!WARNING]
> The ability to enter values in a custom field added to a page is dependent on whether the table associated with the custom field is editable or read only. When the associated table is read only, all fields linked to that table, including any custom fields, will also be read only.


## Sharing custom fields with other users

After you have created a custom field and exposed it on a page, you might want to provide this updated page view that includes the new field to other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

- The recommended route is to **publish a [saved view](saved-views.md)** with the custom field added to the page to the appropriate set of users. If the saved views feature is not enabled, the system administrator can apply the personalization to the desired users from the Personalization form. For more information, see [Personalize the user experience](personalize-user-experience.md).
- Alternatively, you can export your changes (called *personalizations*), send them to one or more users, and have each of those users import your changes. The **Manage** option on the personalization toolbar enables you to export and import personalizations.

## Managing custom fields

Management of all the custom fields in the system can be accomplished through the **Custom fields** page in the System administration module. This page allows users access to many capabilities, including:

- Viewing a list of all custom fields in the system.
- Limited editing of existing custom fields.
- Deleting custom fields.
- Exposing custom fields on data entities.
- Providing translations of custom field labels and help text.

### Viewing all custom fields

The **Custom fields** page provides visibility to all the custom fields that have been defined in the system. Simply select the table that you are interested in, and the page will update to show a list of the custom fields associated with that table. Choosing a custom field from the list will allow you to view all the details about the field.

### Editing custom fields

After a custom field has been created, only certain pieces of information about the custom field can be modified on the **Custom fields** page.

You *can* modify these attributes:

- Label
- Help text
- Length, for Text fields

You *cannot* edit the following attributes:

- Field name
- Data type

Additionally, for picklist fields, the set of valid values for the custom field can be reordered, and new values can be added; however, existing values for the picklist field cannot be removed. Remember to click **Apply changes** when you are done editing fields for a particular table so the changes are saved.

### Exposing custom fields on data entities

It may also be important to allow custom fields to be visible on data entities. Data entities are utilized in the [Office integration overview](../../dev-itpro/office-integration/office-integration.md) feature, as well as for data import/export scenarios.

Follow these steps to expose a custom field on a data entity:

1. Select the custom field on the **Custom fields** form.
2. Expand the **Entities** section to view the set of relevant entities.
3. Click the **Edit** button.
4. Modify the **Enabled** field to be selected for each entity that should expose this field.
5. Click **Apply changes** to save your selections.

### Allowing custom fields to be displayed in other languages

Because custom fields may need to be accessed by users in a variety of languages, the **Custom fields** page provides a mechanism to allow the label and help text for a custom field to be translated into other languages.

The following steps describe the process for translating custom fields in other languages:

1. Select the custom field on the **Custom fields** page.
2. Select the **Translations** button in the Action Pane. This will open a drop-down menu with existing translations for this field.
3. The **Language** drop-down menu shows the set of languages for which translations have already been provided.

    If you want to edit an existing translation, select the desired language from the menu and modify the values for the label and help text.

    Otherwise, click the **Add language** button, select the desired language from the menu, and then provide translated values for the label and help text.

4. Click **OK** when you are finished.

### Deleting custom fields

In some rare cases, you may decide that a custom field is no longer needed. When this occurs, a system administrator can choose to delete the field from the **Custom fields** page. To do this, ensure the correct field is selected, click **Delete**, click **Yes** to confirm the deletion, and finally click **Apply changes**.

> [!NOTE]
> This action cannot be undone, and will result in the data associated with the field being permanently deleted from the database.

## Appendix

### Why can't I enter a value in my custom field? 

If you can't type a value into the custom field when the page is in Edit mode, this may be because the table that the field was added to is currently read only. All fields in a table become read only if the backing table is currently configured as read only on the page.   

### Who can create custom fields?

As a safeguard to the system, only system administrators are able to create custom fields by default. However, those power users whom the organization deems necessary can be given rights to create custom fields by a system administrator using the **Runtime customization power user** security role. Users without this security role will not be able to create custom fields, but will still be able to see and interact with custom fields added by other users in the system.

### What tables support custom fields?

For performance and technical reasons, only tables that meet the following conditions currently allow custom fields to be added.

- The table must be tagged as one of these groups:

    - Group
    - WorksheetHeader
    - Main
    - Miscellaneous
    - Parameter
    - Reference
    - TransactionHeader

- The table cannot extend another table.
- The table cannot be marked as a system table.
- The table cannot be a temporary table.

### Can I reference custom fields from the developer tools?  

Custom fields can only be managed through the user interface and cannot be referenced by code. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
