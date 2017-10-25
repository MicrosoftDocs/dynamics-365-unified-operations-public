---
# required metadata

title: Office integration tutorial
description: In this tutorial, you will use and build Office integration experiences that involve Excel, Word, Document Management, and email. 
author: ChrisGarty
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 10884
ms.assetid: 65fb607a-58e4-4800-81b5-6058acb003cb
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Office integration tutorial

[!include[banner](../includes/banner.md)]


In this tutorial, you will use and build Office integration experiences that involve Excel, Word, Document Management, and email. 

Overview
--------

In this tutorial, you will use and build Microsoft Office integration experiences that involve Microsoft Excel, Microsoft Word, the Document Management subsystem, and email. You will see how Excel and Word use data entities as an entry point into the system, how Excel can become a core part of the user experience, and how Excel and Word can be used for ad-hoc lightweight reporting. You will also see how files can be stored and shared by using the Document Management and email capabilities.

## Prerequisites
For this tutorial, you must access the environment by using Remote Desktop, and you must be provisioned as an administrator on the instance. For more information, see [Access development instances](..\dev-tools\access-instances.md). If you're running Internet Explorer on the virtual machine (VM), you must enable font and file downloads at **Internet Options** &gt; **Security** &gt; **Custom Level**. Microsoft Visual Studio 2015 runs on the VM, and it must run as an administrator so that metadata and compilation files can be overwritten. To make sure that Visual Studio runs as an administrator, search for the program, and pin it to the taskbar. Then right-click the shortcut on the taskbar, right-click **Visual Studio 2015**, click **Properties** &gt; **Advanced**, and select the **Run as administrator** check box. Visual Studio will now run as an administrator via a single left click of the taskbar shortcut.

## Key concepts
-   **Entities and OData** – You will use the Microsoft Dynamics Excel Data Connector App (Excel App) to create, read, update, and delete. The connector uses OData services that are created for any entity that is left in the default state of "public" (**DataEntity.Public**=**Yes**).
-   **Apps for Office** – The Excel App is built by using the Apps for Office framework (which is also known as the Office Web API). The Excel App is web-based, and therefore shares technology with the client and will run inside both on-premises Excel instances and Microsoft Excel Online (Microsoft Office 365). The app runs inside Excel in a task pane.
-   **Microsoft Office 2016** – The Excel and Word Apps use advances in the Apps for Office framework that were introduced in Office 2016. Therefore, Office 2016 is required in order to run the Excel and Word Apps.
-   **Authentication** – The Excel and Word Apps run in an Internet Explorer window inside Excel and Word. Even if the user is running the client in an InPrivate Browsing session in Internet Explorer, or in a different browser, such as Chrome, Internet Explorer is still used to run the app inside Excel or Word. Authentication is facilitated by OAuth, and the user can select accounts and sign in within the app. Internet Explorer will first try to automatically sign the user in. Therefore, if you aren't signed in as the correct user, or if you have trouble signing in, you might have to force a sign-out from the app by using the sign-out link on the user menu in the lower-right corner of the app. After sign-out, right-click in the app, and try to sign in again.
-   **Excel App** – In addition to facilitating refresh and publish data operations, the Excel App also provides source and field information, lookups, filtering, error messaging, and a design experience for adding or removing fields, table columns, or labels from entity data sources.

## Setup
### Load the Fleet data set

During this tutorial, we will mainly use forms, entities, and data in the Fleet Management model. Therefore, we must first load the Fleet data set.

1.  Navigate to **Fleet Management** &gt; **Setup** &gt; **Fleet** **setup**.
2.  Click **Create**.

## Static Export to Excel experiences
### Static Export to Excel

Static Export to Excel provides a quick mechanism for getting data into grids on a page. The standard mechanism for triggering Export to Excel is the **Open in** **Microsoft Office** menu. Static Export to Excel is also available via a shortcut menu on the grid.

1.  In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
2.  Click **Open in** **Microsoft Office** &gt; **Export to Excel** &gt; **Customers**.
3.  Download and open the workbook that is generated. Note that the columns in the workbook match the columns in the grid.
4.  Select ("mark") the first two rows by clicking in the left edge of the row, below the "Select all" check mark.
5.  Right-click the grid header to open the shortcut menu. Note that both **Export all rows** and **Export marked rows** are available as commands.
6.  Click **Export marked rows**. Note that the columns in the workbook match the columns in the grid, and that the rows that are exported match the rows that you marked.

### Modify the static Export to Excel experience

You can suppress the static Export to Excel mechanism for a grid or change the label that appears on the **Open in** **Microsoft Office** menu.

1.  Start Visual Studio 2015. Make sure that it's running as an administrator.
2.  Click **View** &gt; **Application Explorer** (or press Ctrl+E, Ctrl+E).
3.  Navigate to **AOT** &gt; **User Interface** &gt; **Forms** &gt; **FMCustomer**.
4.  Right-click **FMCustomer**, and then click **Add to new project**.
5.  In Solution Explorer, double-click the **FMCustomer** form to open the designer view.
6.  Select **FMCustomerDesignTab(Tab)TabPageGrid(TabPage)MainGrid(Grid)**.
7.  In the **Properties** window, find the **Export Label** property.
8.  Set the **Export Label** property to **Fleet Customers**.
9.  Save the form. If you're asked whether you want to overwrite the existing form or save it as a new form, click **Overwrite**.
10. Build the solution (press Ctrl+Shift+B).
11. In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
12. Click **Open in Microsoft Office**. Note that the **Customers** option has changed to **Fleet Customers**.

## Generated Open in Excel experiences
### Generated Open in Excel

Generated Open in Excel options are automatically added to forms when the system finds data entities that have the same root data source as the form. The workbook that is generated will contain a single table data source where the data from that entity is loaded. The Open in Excel experiences are listed on the **Open in** **Microsoft Office** menu. (When an entity has the same root data source as a form, it's added as an option in the **Open in Excel** section of the **Open in Microsoft Office** menu. This option is referred to as a “generated” option.)

1.  In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
2.  Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers (unfiltered)**.
3.  Download and open the workbook that is generated. This workbook contains the Excel Data Connector App, a binding to the **Fleet Management Customer** entity, and a pointer to the server that the workbook was generated from.
4.  Click **Enable editing** to enable the Excel Data Connector App to load. Customer data is read from the OData service on the server and added to the table.
5.  In Internet Explorer, on the **Customer** page, click **Edit** (or press F2), and change the email address of one of the customers.
6.  In the Excel App, click **Refresh**. Note that the new email address is shown in Excel.
7.  In Excel, change the email address of one of the customers.
8.  In the Excel App, click **Publish**.
9.  In Internet Explorer, click **Refresh** in the upper right of the page (or press Shift+F5). Note that the new email address is shown on the **Customer** page.
10. In Excel, click the **Settings** (gear) button in the lower-right corner of the Excel App. You can use the dialog box that appears to adjust the settings in the current workbook. Note that the **Server URL** value matches the start of the URL that is shown in Internet Explorer. Also note that the data refresh and data publish operations are listed.
11. Click **Cancel** to close the **Settings** dialog box.
12. Click the **Message Center** (flag) button in the lower-right corner of the Excel App. The message center dialog box that appears provides information about what is occurring in the Excel App.

### Add and remove table columns from an existing table data source in the Excel App

The Excel App has a design experience that lets users add and edit bindings to entity data sources and labels. To add and remove fields from an existing binding, you use the edit experience that is outlined in the following steps.

1.  Get a workbook that has an existing table data source:
    1.  In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
    2.  Click **Open in Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers (unfiltered)**.
    3.  Download and open the workbook that is generated. This workbook contains the Excel Data Connector App, a binding to the Fleet Management Customer entity, and a pointer to the server that the workbook was generated from.
    4.  Click **Enable editing** to enable the Excel Data Connector App to load. Customer data is read from the OData service on the server and added to the table.

2.  Open the data source for editing:
    1.  In Excel, in the Excel App, click **Design**. A list of table and field data sources appears.
    2.  Click the **Edit** (pencil) button next to the existing table data source. The data source details are shown.

3.  Remove fields. In the **Selected** list, double-click a field. Alternatively, click a field, and then click **Remove**. To select multiple fields, keep the Ctrl key held down while you click them. To select all fields, press Ctrl+A.
4.  Add fields. In the **Available** list, double-click a field. Alternatively, click a field, and then click **Add**. To select multiple fields, keep the Ctrl key held down while you click them. To select all fields, press Ctrl+A.
5.  Change the field order. In the **Selected** list, click a field, and then click **Up** or **Down**.
6.  Change a field label. In the **Selected** list, click a field, and then click in the **Column label** field below the list. You can change the label to either a static string or a label identifier that will be translated to the active language (for example, **@SYS129977**).
7.  Apply the changes that you made to data source fields:
    1.  Click **Update** to return to the data source list.
    2.  Click **Refresh** to make sure that any new fields are filled with data.

### Change an automatically generated Open in Excel experience

The automatically generated Open in Excel experiences that are created for entities have a single table binding. The list of fields that are added to that table binding is defined by the **AutoReport** field group if the table binding contains fields. Otherwise, the key and mandatory fields for the entity are automatically added. The order of fields in the **AutoReport** group determines the order of fields in the table binding.

1.  Start Visual Studio 2015. Make sure that it's running as an administrator.
2.  Click **View** &gt; **Application Explorer** (or press Ctrl+E, Ctrl+E).
3.  Navigate to **AOT** &gt; **Data Model** &gt; **Data Entities** &gt; **FMCustomerEntity**.
4.  Right-click **FMCustomerEntity**, and then click **Add to project**.
5.  Expand **FMCustomerEntity** &gt; **Field Groups** &gt; **AutoReport**.
6.  Reverse the order of the **First name** and **Last name** fields by clicking the **Last name** field and moving it up (press Alt+Up arrow key).
7.  Save the entity. If you're asked whether you want to overwrite the existing entity or save it as a new entity, click **Overwrite**.
8.  Build the solution (press Ctrl+Shift+B).
9.  In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
10. Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.
11. Open the workbook that is generated.
12. Click **Enable editing** to enable the Excel Data Connector App to load. Note that the **Last name** column appears before the **First name** column.

### Open in Excel Online

The Excel App is built by using a new Apps for Office framework. This framework provides a JavaScript-based web application programming interface (API) that enables apps to communicate with Office applications. The biggest advantage of this new framework is that apps can run in on-premises Excel instances (Win32), Excel Online (Office 365), and Excel on the Apple iPad. They will also be able to run in other Excel apps in the future.

1.  Navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
2.  Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.
3.  Click **SharePoint**.
4.  Browse to the desired Microsoft SharePoint folder.
5.  Click **Save**. The default behavior is to open the file after it's saved. Note that the workbook opens in Excel Online. In Excel Online, capabilities of the Excel App, such as refresh and publish, and the design experience, should work just as they work in on-premises Excel instances.

## Template Open in Excel experiences
### Template Open in Excel

Template options resemble the generated Open in Excel options. They are automatically added to forms when the system finds templates that have the same first data source as the root data source in the form. A workbook template can have multiple data sources. It can also have unbound content. The Open in Excel experiences are listed on the **Open in** **Microsoft Office** menu. The **Excel workbook designer** page provides an easy way to get a generated Open in Excel experience for an entity. It also provides a mechanism getting a blank workbook that contains just the Excel App and a pointer to the server.

1.  In Internet Explorer, navigate to **Common** &gt; **Common** &gt; **Office integration** &gt; **Excel workbook designer**.
2.  Select the **FleetCustomer** entity.
3.  Add all fields in the list of available fields to the list of selected fields.
4.  Click **Create workbook**.
5.  Open the workbook that is generated. This workbook contains the Excel Data Connector App, a binding to the **Fleet Management Customer** entity, and a pointer to the server that the workbook was generated from.
6.  Click **Enable editing** to enable the Excel Data Connector App to load. Customer data is read from the OData service on the server and added to the table.
7.  Insert a blank row above the table, and enter **Fleet Customers** as the title.
8.  Rename the worksheet **FleetCustomers**.
9.  Rearrange some of the fields in the table. Click **Design** to open the design experience.
10. Next to the **FleetCustomer** data source, there are buttons for editing and deleting the data source. Click **Edit** to see the field list.
11. Select fields, and move them as you require. Set the order for the first three fields to **FirstName**, **LastName**, and **DriverLicense**.
12. Click **Update**. Note that the field order is changed.
13. Click **Done**.
14. Click the **Settings** (gear) button.
15. Click **Clear binding data** so that the workbook contains no bound data.
16. Click **OK**.
17. Save the workbook as **FleetCustomersBasic.xlsx**.
18. In Internet Explorer, navigate to **Common** &gt; **Common** &gt; **Office integration** &gt; **Document templates**.
19. Click **New**.
20. Browse to the file that you just saved.
21. Click **OK**. The template is added as a line in the templates table.
22. In the **FleetCustomersBasic** row, clear the **Apply current record filter** check box, so that an unfiltered list of customers will be loaded after the template is opened.
23. Change the **Template display name** value to **Fleet Customers Basic**.
24. Navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
25. Click **Open in** **Microsoft Office**. Note that **Fleet Customers Basic** is now an option in the **Open in Excel** section. Click that option.
26. Open the workbook that is generated.
27. Click **Enable editing** to enable the Excel Data Connector App to load. Customer data is read from the OData service on the server and added to the table binding that you created.

### Register a template as a system-defined template

Templates that are registered as system-defined templates are loaded at deployment. This behavior is useful for independent software vendors (ISVs) and partners that want to package templates together with other model artifacts.

1.  Start Visual Studio 2015 by opening the previously created project where the model is set to **Fleet Management**, or create a new project.
2.  Right-click the project, and then click **Add** &gt; **New item**.
3.  Select the **Resource** item type.
4.  Set the name to **FleetCustomersBasicTemplate**.
5.  Make sure that the FleetCustomersBasic.xlsx file is closed.
6.  Click **Add**.
7.  Select the **FleetCustomersBasic.xlsx** file. Note that the resource is added to the project.
8.  Click **View** &gt; **Application Explorer** (or press Ctrl+E, Ctrl+E).
9.  Navigate to **AOT** &gt; **Classes** &gt; **Code** &gt; **FMTemplateRegistrations**.
10. Right-click **FMTemplateRegistrations**, and then click **Add to project**.
11. Open **FMTemplateRegistrations**. The FMTemplateRegistrations.xpp code file should be shown.
12. Copy one of the existing lines, and change it by providing the template name, resource name, description, display name, and **Apply current record filter** and **List in Open in Office menu** values. The display name is the text that appears as an Open in Excel option. The description appears when the user holds the pointer over that item. The display name and description can be either labels or static strings. The code should resemble the following example.

        this.addTemplate(
            OfficeAppApplicationType::Excel, 
            resourceStr(FleetCustomersBasicTemplate), 
            resourceStr(FleetCustomersBasicTemplate), 
            "Template for fleet customers", "Fleet customers basic", NoYes::No, NoYes::Yes);

13. Save the code. If you're asked whether you want to overwrite the existing code or save it as a new file, click **Overwrite**.
14. Build the solution (press Ctrl+Shift+B).
15. Verify that the change was successful. In Internet Explorer, navigate to **Common** &gt; **Common** &gt; **Office integration** &gt; **Document templates**.
16. Click **Reload system templates**.
17. Click **Yes** to confirm that you want to reload the system templates.
18. Verify that the new system-defined template is loaded, and that the template name is **FleetCustomersBasicTemplate**.

### Journal Entry in Excel experience powered by a template

1.  In Internet Explorer, navigate to **General ledger** &gt; **Journal entries** &gt; **General journals**.
2.  Make sure that you're in company **USMF**.
3.  Create a new journal by clicking **New**.
4.  Set the name to **GenJrn**.
5.  Click **Open lines in Excel**.
6.  Open the workbook that is generated, and enable editing as required. Note that header fields are filled with data.
7.  Enter a new line, and set the **MainAccount** field to **110110**. Enter a description, a currency, and a debit amount. Note that lookups are provided for the company and currency fields, because those relationships are defined for this entity.
8.  Click **Publish**. Note that the line is updated with the current date and a debit amount of 0 (zero).
9.  In Internet Explorer, click **Lines**. Note that line that you entered in Excel is shown.

## Lookups in Excel experiences
### Lookups in the Excel App

To facilitate data entry, the Excel App provides lookups and data assistance. Date fields provide a date picker, enumeration (enum) fields provide an enum list, and relationships provide a relationship lookup.

1.  In Internet Explorer, navigate to **Fleet Management** &gt; **Rentals** &gt; **Rental**.
2.  Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Rentals**.
3.  Open the workbook that is generated.
4.  Click **Enable editing** to enable the Excel Data Connector App to load and read in data.
5.  Click a **Drivers license** value. Note that a relationship lookup now appears in the Excel App and shows a list of customers. Because relationship lookups are in their first generation, no filtering or sorting is currently supported.
6.  Click another customer in the lookup, and note that the **Drivers license** value changes. Because this field is part of the key, click the original **Drivers license** value to reset it. Note that the **Drivers license**, **First name**, and **Last name** fields form a multi-part key, but the Excel App doesn’t immediately change all parts of the multi-part key.
7.  Click a **Start date** value. Note that a date picker now appears in the Excel App.
8.  Click another date to change the **Start date** value.
9.  Click **Design**, and edit the FleetRental data source by adding the **Status** field as a column in the table binding.
10. When you've finished adding the **Status** column, click a **Status** value. Note that an enum list now appears in the Excel App.
11. While focus is in the **Status** column, move up and down the list of rentals to see how quickly the enum list changes to reflect the current value. The whole enum list is shown, so that the user can quickly see all the available values.
12. Click a different **Status** value to see how an enum value can be changed by using a single click.

### Create a relationship lookup

When relationships exist between entities, a relationship lookup is shown.

1.  Start Visual Studio 2015 by opening the previously created project where the model is set to **Fleet Management**, or create a new project.
2.  Click **View** &gt; **Application Explorer** (or press Ctrl+E, Ctrl+E).
3.  Navigate to **AOT** &gt; **Data Model** &gt; **Tables** &gt; **FMCustGroup**.
4.  Right-click, and then click **Open designer**.
5.  In the designer, right-click **FMCustGroup**, and then click **Addins** &gt; **Create data entity**. Artifacts are added to the project.
6.  Open the designer view for **FMCustGroupEntity**.
7.  In the property sheet for **FMCustGroupEntity**, set **Public Collection Name** to **FleetCustomerGroups** and **Public Entity Name** to **FleetCustomerGroup**.
8.  Add the **CustGroup** and **Description** fields to the **AutoLookup** field group.
9.  If **FMCustomerEntity** isn't already in the project, add it.
10. Open the designer view for **FMCustomerEntity**.
11. Right-click **Relations**, and then click **New** &gt; **Relation**.
12. On the new relation, set **Name** to **CustomerGroup**, **Cardinality** to **ZeroMore**, **RelatedDataEntity** to **FMCustGroupEntity**, **RelatedDataEntityCardinality** to **ZeroOne**, **RelationshipType** to **Association**, **Role** to **CustomerGroupSource**, and **RelatedDataEntityRole** to **CustomerGroupTarget**.
13. Build the solution (press Ctrl+Shift+B).
14. Verify that the change was successful. In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
15. Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.
16. Open the workbook that is generated.
17. Click a **Customer group** value.
18. Change the **Customer group** value for a customer.
19. Publish the change.
20. Change the value back, and publish that change.

### Create a custom lookup

You can create custom lookups to show data options when an enum or relationship isn't sufficient. The main use case is when data must be retrieved from an external service and presented in real time.

1.  Start Visual Studio 2015 by opening the previously created project where the model is set to **Fleet Management**, or create a new project.
2.  Open the designer view for **FMCustomerEntity**.
3.  Right-click **Methods**, and then click **New Method**.
4.  Add the **lookup\_Country** code from the following example.

        public class FMCustomerEntity extends common
        {
            [SysODataActionAttribute("FMCustomerEntityCountryCustomLookup", false), //Name in $metadata
            SysODataCollectionAttribute("_fields", Types::String), //Types in context
            SysODataFieldLookupAttribute("Country")] //Name of field
            public static str lookup_Country(Array _fields)
            {
                OfficeAppCustomLookupListResult result = new OfficeAppCustomLookupListResult();

                result.items().value(1, "US");
                result.items().value(2, "AU");
                result.items().value(3, "FR");
                result.items().value(4, "GR");
                result.items().value(5, "NZ");
            
                return result.serialize();
            }
        }

5.  Save the code. If you're asked whether you want to overwrite the existing code or save is as a new file, click **Overwrite**.
6.  Build the solution (press Ctrl+Shift+B).
7.  Verify that the change was successful. In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
8.  Click **Open in** **Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.
9.  Open the workbook that is generated.
10. Click a **Country** value.
11. Change the **Country** value for a customer.
12. Publish the change.
13. Change the value back, and publish that change.

## Export to Word experiences
### Export to Word

Export to Word experiences can be used for lightweight reporting. They are powered by pre-built templates. The Export to Word experiences are listed on the **Open in** **Microsoft Office** menu. Let's look at an example experience that has been created for Fleet Management Customers.

1.  In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
2.  Click **Open in** **Microsoft Office** &gt; **Export to Word** &gt; **Customer information Fleet Management Customers (unfiltered)**.
3.  Download and open the document that is generated. The document contains data from the record that is currently selected.

### Create a Word template

The Microsoft Dynamics App for Office can be run in Word to enable the creation of templates that can then be used for document generation.

1.  Add a trusted catalog that points to the file share that contains the Microsoft Dynamics App manifest:
    1.  In Word, click **File** &gt; **Options**.
    2.  Click **Trust Center** &gt; **Trust Center Settings**.
    3.  Click **Trusted Add-in Catalogs**.
    4.  In the **Catalog URL** field, enter the file share location of the manifest.
    5.  Click **Add catalog**.
    6.  Click **OK**.
    7.  Click **OK**.
    8.  Restart Word.

2.  Add the Microsoft Dynamics App to a document:
    1.  In Word, click **Insert** &gt; **My Add-ins** &gt; **Shared Folder** &gt; **Microsoft Dynamics**.
    2.  Click **Insert**.
    3.  In the app, click **Add server information**.
    4.  In the **Server URL** field, enter the start of the URL (protocol + hostname). For example, enter **https://topo00dfa4stbobaos.cloudax.test.dynamics.com**.
    5.  Click **OK**.
    6.  Click **Yes** to apply the settings change and reload the app.

3.  Sign in to the app:
    1.  Click **Sign In**. The Azure Active Directory sign-in screen should provide a list of credentials. If you encounter an error, force a sign-out (by using the sign-out link in the lower-right corner of the app), and then sign in again.
    2.  Select the appropriate account, or click **Use another account**.
    3.  Enter the credentials for that environment, and then click **Sign in**.

4.  Load the template designer applet:
    1.  After sign-in, click **Load applets**.
    2.  Select **Template Designer**.
    3.  Click **OK.**
    4.  Click **Yes** to confirm.
    5.  Click **OK** to close the settings page. The latest OData metadata is loaded.

5.  Follow one of these steps:
    -   Add a fields data source:
        1.  In the app, click **Design**.
        2.  Click **Add fields**.
        3.  Select **FleetCustomer**.
        4.  Click **Next** to go to the field selection page.
        5.  In the document, add a title and/or some blank lines at the top of the document.
        6.  In the app, in the **Available** list, select the **FirstName** field.
        7.  Click **Add label** to add a content control that references the "First name" label.
        8.  In the document, click to put focus into the document, click again to put focus at the end of the label, and then press the Right arrow key until the cursor is outside the content control (the control box will disappear).
        9.  Add a separator, such as space+hyphen+space (" - ") or space+colon+space (" : ").
        10. In the app, click **Add value** to add a content control that references the **FirstName** field.
        11. Repeat the process for the **LastName** field label and value.
        12. Continue to add fields as desired.
    -   Add a table data source:
        1.  In the app, click **Design**.
        2.  Click **Add table**.
        3.  Select **FleetCustomer**.
        4.  Click **Next** to go to the field selection page.
        5.  In the document, add a title and/or some blank lines at the top of the document.
        6.  In the app, in the **Available fields** list, add the **FirstName**, **LastName**, and **City** fields.
        7.  Click **Done**.

6.  In Word, save the template document.

### Create a Word template and use it for document generation

After you've built a Word template, you can upload it to create an Export to Word experience.

1.  Upload a template:
    1.  Navigate to **Common** &gt; **Common** &gt; **Office integration** &gt; **Document templates**. Alternatively, search for the page.
    2.  Click **New**.
    3.  Click **Browse**.
    4.  In the dialog box, select a previously created template, and then click **Open**. Note that the Root data entity is obtained from the template and appears near the bottom of the dialog box.
    5.  Click **OK**.
    6.  Scroll down the list of templates to confirm that the template was added.
    7.  Optional: If the template should not be filtered to the user's current record, clear the **Apply current record filter** check box.
    8.  Optional: If the template should not be filtered to the user's current company, clear the **Apply company filter** check box.

2.  Use the uploaded template for document generation:
    1.  Navigate to a page that shares the same root data source as the template's root data entity. For **FleetCustomer** (**FMCustomerEntity**), that page is **Fleet Management** &gt; **Customers** &gt; **Customer**.
    2.  Click **Open in Microsoft Office** &gt; **Export to Word**, and click the template.
    3.  Download and open the document that is generated.

## Document Management and SharePoint experiences
### Add a SharePoint document type

The Document Management subsystem can be used to attach files to records. Most non-executable file types are supported as attachments. A document preview is provided for Office document files and PDFs. Administrators create document types to indicate where attachments should be stored. When administrators use SharePoint as the storage location, they must provide a specific folder that the files should be put in. Security of that SharePoint folder is a separate administration responsibility.

1.  In Internet Explorer, navigate to **Organization administration** &gt; **Document management** &gt; **Document management parameters**.
2.  Click **SharePoint**.
3.  Make sure that the **Default SharePoint server** field is set to a default value for the tenant, such as **contosoax7.sharepoint.com**.
4.  Click **Test SharePoint connection**. Note a successful connection.
5.  Click **Save**.
6.  Navigate to **Organization administration** &gt; **Document management** &gt; **Document types**.
7.  Click **New**.
8.  Set **Type** to **SharePointDoc**.
9.  Set **Name** to **SharePointDoc**.
10. Set **Location** to **SharePoint**.
11. Click the **Edit** (pencil) button next to the **SharePoint Address** field.
12. On the left side of the dialog box, select a site. For the contosoax7 tenant, select **ContosoAX Team Site**.
13. On the right side of the dialog box, select a folder. For the contosoax7 tenant, select **ContosoAX Team Site** &gt; **Documents** &gt; **OfficeIntegration** &gt; **Attachments**.
14. Click **OK**.
15. Click **Save**.
16. Click the **Browse** (globe) button next to the **SharePoint Address** field. Note that a new browser tab that shows the selected folder appears.
17. Use Windows Explorer to create a Word document in the Documents folder, and enter a few words in the document.
18. In Internet Explorer, navigate to **Fleet Management** &gt; **Customers** &gt; **Customer**.
19. Put focus on the first customer, and then click the **Attach** (paperclip) button in the upper-right corner of the page.
20. Click **New** &gt; **SharePointDoc**.
21. Click **Browse**, and select the Word document that you created.
22. Expand the **Preview** FastTab to see a preview of the Word document.
23. Expand the **Attachment** FastTab to see the file location of the Word document.
24. In Internet Explorer, use the previously opened tab that shows the SharePoint folder to double-check that the file has been placed appropriately.

## Email experiences
### Send mail via a local mail client

Email workflows that are enabled via the SysEmail framework can generate email messages (.eml files) that contain attachments. You can then send these messages via Microsoft Outlook or another email client.

1.  In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
2.  Select **US-008 Sparrow Retail**.
3.  Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
4.  Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
5.  Click **OK** to accept the default values in the dialog box.
6.  If you're prompted for the mail option to use, clear the **Do not ask again** check box (you can change this option from the user options page), select **Use an email app, such as Outlook**, and then click **OK**.
7.  If you're running Internet Explorer on your laptop, open the email (.eml) file that is generated. If you're running Internet Explorer on the VM, copy the file to your laptop, and open it there.
8.  Note the email address in the **To** field and the generated workbook attachment.

### Send mail via SMTP

Email workflows that are enabled via the SysEmail framework can also be created in a simple email dialog box and then sent via Simple Mail Transfer Protocol (SMTP).

1.  In Internet Explorer, navigate to **System administration** &gt; **Setup** &gt; **Email** &gt; **Email parameters**.
2.  Click **SMTP settings**.
3.  Set the **Outgoing mail server** to the desired SMTP server:
    -   For [Office 365 production](https://support.office.com/en-us/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including \*.onmicrosoft.com accounts): smtp.office365.com (Find this setting via outlook.office.com, at **Settings** &gt; **Mail** &gt; **POP and IMAP**.)
    -   For Outlook/Hotmail: smtp-mail.outlook.com

4.  Set the user name and password to an appropriate email account and password.
5.  Leave **SSLRequired** turned on, and leave **SMTP port number** set to **587**.
6.  Click **Save**.
7.  In Internet Explorer, navigate to **Accounts receivable** &gt; **Customers** &gt; **All customers**.
8.  Select **US-008 Sparrow Retail**.
9.  Click **Collect** &gt; **Customer balances** &gt; **Collections** to open the **Collections** page.
10. Click **Communicate** &gt; **Email** &gt; **Statements to contact**.
11. Click **OK** to accept the default values in the dialog box.
12. If you're prompted for the mail option to use, select **Use the Microsoft Dynamics 365 for Finance and Operations email client**, and then click **OK**.
13. To receive the test message, change the To address to your email address.
14. Enter a subject and body for the message.
15. Click **Send**. The message should be delivered in one to five minutes. Note that the message will appear to be sent from the email account that is set on the **Email parameters** page. If that email account is given "Send As" (or "Send email from this mailbox") permissions for the From address that is used in the **Send email** dialog box, messages will appear to come from that address.
    -   You can configure "Send As" permissions in the Office 365 admin center (portal.office.com/Admin), at **Users** &gt; **Active users** &gt; **User** &gt; **Edit mailbox permissions** &gt; **Send email from this mailbox**. For more information, see [Enable sending email from another user's mailbox in Office 365](https://support.office.com/en-us/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E).
    -   Before users can send email messages, "Send As" permissions for each user email account in the client must be given to the email account that is set on the **Email parameters** page. For more information, see [How to set up a multifunction device or application to send email using Office 365](https://technet.microsoft.com/en-us/library/dn554323(v=exchg.150).aspx).

16. Email that is sent directly from the server, without user interaction, is sent via a batch process and requires that the **Email distributor batch** process be started. Follow these steps to start the process:
    1.  Navigate to **System administration** &gt; **Periodic tasks** &gt; **Email processing** &gt; **Batch**.
    2.  Turn on **Batch processing**.



See also
--------

[Office integration](office-integration.md)

[Office Integration Troubleshooting](office-integration-troubleshooting.md)



