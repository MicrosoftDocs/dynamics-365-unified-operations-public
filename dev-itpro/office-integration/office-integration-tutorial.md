---
# required metadata

title: Office integration tutorial
description: In this lab, you will use and build Office Integration experiences involving Excel, Word, document management, and email. 
author: ChrisGarty
manager: AnnBe
ms.date: 2015-10-27 16 - 42 - 45
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 10884
ms.assetid: 09fa3569-2f92-46d0-9794-6b4820b6fd8d
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Office integration tutorial

In this lab, you will use and build Office Integration experiences involving Excel, Word, document management, and email. 

Instructor Led Lab ILLAX09: Office integration
----------------------------------------------

*Time: 75 minutes*

## Overview
In this lab, you will use and build Office Integration experiences involving Excel, Word, Document Management, and Email. You will see how Dynamics AX integrates with Excel and Word using data entities as an entry point into the system, how Excel can become a core part of the user experience, and how Excel and Word can be used for adhoc lightweight reporting. You will also see how files can be stored and shared using the Document Management and Email capabilities within Dynamics AX. Initially the lab steps will be small and very detailed in case you are unfamiliar with the use of Dynamics AX or development of Dynamics AX within Visual Studio. In later sections of the lab, the steps will intentionally become bigger and less detailed so the lab becomes easier to read and follow.

## Prerequisites
For this tutorial, you’ll need to access the Microsoft Dynamics AX environment using Remote Desktop, and be provisioned as an administrator on the AX instance. For more information, see [Access Microsoft Dynamics AX Instances](access-instances.md). If you are running Internet Explorer within the Virtual Machine (VM), you will need to enable font and file downloads via Internet Options &gt; Security &gt; Custom Level. Visual Studio 2015 runs within the VM and needs to be run as administrator so that metadata and compilation files can be overwritten. To ensure it runs as administrator, search for it, pin it to the task bar, right click on the task bar shortcut, right click on **Visual Studio 2015**, click on **Properties &gt; Advanced…** then check the **Run as administrator** checkbox. Visual Studio will now run as administrator via a single left click on the task bar shortcut.

## Key Concepts
-   Entities and OData – Use the Microsoft Dynamics Excel Data Connector App (Excel App) to facilitate the reading, creating, updating, and deleting of Dynamics AX records in Excel. The Excel Data Connector App talks to Dynamics AX using OData services that are created for any Entity that is left in the default state of ‘public’ (DataEntity.Public=Yes).
-   Apps for Office framework (aka. Office Web API) – The Excel App is built using the Apps for Office framework and is web-based so that it shares technology with the Dynamics AX Client and will run inside both Excel on-premise and Excel online (O365). The app runs inside Excel in a task pane on the right.
-   Office 2016 is required – The Excel and Word Apps make use of advances in the Apps for Office framework that were introduced in Office 2016, so Office 2016 is required to run the Excel and Word Apps.
-   Authentication – The Excel and Word Apps run in an Internet Explorer (IE) window in Excel and Word. Even if the user is running the Client inside of an IE InPrivate session or inside a different browser like Chrome, IE is still used to run the app inside Excel or Word. Authentication is facilitated by OAuth and the user can select accounts and sign in within the app. IE will initially try to automatically sign the user in, so if you don’t get signed in with the correct user or have trouble signing in, you may need to force a sign out from the app using the sign out link in the user menu in the bottom-right corner of the app. After sign out, right-click on the app surface and attempt to sign in again.
-   Excel App – In addition to facilitating refresh and publish data operations, the Excel App also provides source and field information, lookups, filtering, error messaging, and a design experience to add or remove fields, table columns, or labels from entity data sources.

## Setup
### Load Fleet Data

During this lab we’ll predominantly use forms, entities, and data in the Fleet Management model. First we need to load the Fleet data set.

1.  Navigate to **Fleet Management &gt; Setup &gt; Fleet** **setup**.
2.  Click **Create**.

## Static Export to Excel
### Use: Static Export to Excel

Static Export to Excel provides a quick mechanism to get the data in grids on a form. The standard mechanism for triggering Export to Excel in Dynamics AX is via the **Open in** **Microsoft Office** menu. Static Export to Excel is also available via a right-click context menu on the grid.

1.  In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
2.  Click **Open in** **Microsoft Office &gt; Export to Excel &gt; Customers**.
3.  Download and open the generated workbook.
4.  Note that the columns in the workbook match the columns in the grid.
5.  Mark the first two rows by clicking on the left edge of the row below the “select all” check mark.
6.  Right click on the grid header to get the grid context menu.
7.  Note that both **Export all rows** and **Export marked rows** are available.
8.  Click **Export marked rows**.
9.  Note that the columns in the workbook match the columns in the grid and the rows exported match the marked/selected rows.

### Build: Alter the static Export to Excel experience

A developer has the option of suppressing the static Export to Excel mechanism for a grid or changing the label that is shown in the **Open in** **Microsoft Office** menu.

1.  Open **Visual Studio 2015**. Ensure it is **running as administrator**.
2.  Open **View &gt; Application Explorer (Ctrl+E, Ctrl+E)**.
3.  Navigate to **AOT &gt; User Interface &gt; Forms &gt; FMCustomer**.
4.  Right click on **FMCustomer &gt; Add to new project**.
5.  Double click on the **FMCustomer** form in the Solution Explorer to open the **Designer view**.
6.  Select **FMCustomerDesignTab(Tab)TabPageGrid(TabPage)MainGrid(Grid)**.
7.  In the **Properties** window, find the Export Allowed and Export Label properties.
8.  Set the **Export Label** to “**Fleet Customers**”.
9.  **Save** the form and if asked to “Overwrite or Save As” click **Overwrite**.
10. **Build** the solution (Ctrl+Shift+B).
11. In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
12. Click **Open in Microsoft Office**.
13. Note that the Customers option has changed to **Fleet Customers**.

## Generated Open in Excel experiences
### Use: Generated Open in Excel

Generated Open in Excel options are added to forms automatically by finding data entities that have the same root datasource as the form. The generated workbook will contain a single table datasource that will have the data from that entity loaded. The Open in Excel experiences are listed under the **Open in** **Microsoft Office** menu.

1.  In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
2.  Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers (unfiltered)**.
3.  Download and open the generated workbook. The workbook contains the Excel Data Connector App, a binding to the **Fleet Management Customer** entity, and a pointer to the server it was generated from.
4.  Click **Enable editing** to allow the Excel Data Connector App to load.
5.  Customer data will be read from the OData service on the server and added to the table.
6.  In IE, in the Customer form, click **Edit** (or type F2) and change the email address of one of the customers.
7.  Click **Refresh** in the Excel App.
8.  Note that the changed email address is shown in Excel.
9.  In Excel, change the email address of one of the customers.
10. Click **Publish** in the Excel App.
11. In IE, click **Refresh** (the button is in the top right of the form) or type Shift+F5.
12. Note that the changed email address is shown in the Customer form.
13. In Excel, click the **Settings** button (the button with a gear symbol on it in the bottom-right corner of the Excel App). The Excel App has a settings dialog to allow the user to adjust the settings in the current workbook.
14. Note that the **Server URL** matches the start of the URL shown in IE. Also note that the data refresh and data publish operations are listed here.
15. Click **Cancel** to close the Settings dialog
16. Click the **Message Center** button (the button with a flag symbol on it in the bottom-right corner of the Excel App). The Excel App has a message center dialog to provide the user with information about what is happening within the Excel App.

### Use: Add and remove table columns from an existing table data source in the Excel App

The Excel App has a design experience that allows users to add and edit bindings to entity data sources and labels. To add and remove fields from an existing binding, the user will use the edit experience.

1.  Get a workbook with an existing table data source
    1.  In IE, navigate to Fleet Management &gt; Customers &gt; Customer.
    2.  Click Open in Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers (unfiltered).
    3.  Download and open the generated workbook. The workbook contains the Excel Data Connector App, a binding to the Fleet Management Customer entity, and a pointer to the server it was generated from.
    4.  Click Enable editing to allow the Excel Data Connector App to load.
    5.  Customer data will be read from the OData service on the server and added to the table.

2.  Open the data source for edit
    1.  In Excel, click Design in the Excel App. A list of table and field data sources will be listed.
    2.  Click the Edit button (pencil symbol) next to the existing table data source. The data source details will now be shown.

3.  Remove fields
    1.  In the Selected fields list, double-click on a field. Or click on a field and click Remove. Multiple fields can be selected using Ctrl+Click or Ctrl+A.

4.  Add fields
    1.  In the Available fields list, double-click on a field. Or click on a field and click Add. Multiple fields can be selected using Ctrl+Click or Ctrl+A.

5.  Change field order
    1.  In the Selected fields list, click on a field and click Up or Down.

6.  Change field label
    1.  In the Selected fields list, click on a field and click into the Column label textbox below the list. The label can be changed to a static string or can be changed to a label identifier that will be translated to the active language (e.g. @SYS129977).

7.  Apply data source field changes
    1.  Click Update to return to the data source list.
    2.  Click Refresh to ensure that any new fields are filled with data.

### Build: Change an automatically generated Open in Excel experience

The automatic generated Open in Excel experiences created for entities have a single table binding. The list of fields added into that table binding is defined by the AutoReport field group if it contains fields, otherwise the key and mandatory fields for the entity will be automatically added. The order of fields in the AutoReport group determines the order of fields in the table binding.

1.  Open **Visual Studio 2015**. Ensure it is running as administrator.
2.  Open **View &gt; Application Explorer (Ctrl+E, Ctrl+E)**.
3.  Navigate to **AOT &gt; Data Model &gt; Data Entities &gt; FMCustomerEntity**.
4.  Right click on **FMCustomerEntity &gt; Add to project**.
5.  Expand **FMCustomerEntity &gt; Field Groups &gt; AutoReport**.
6.  Swap the order of the **First name** and **Last name** fields by clicking on the **Last name** field and moving it up (Alt+UpArrow).
7.  **Save** the entity and if asked to “Overwrite or Save As” click Overwrite.
8.  **Build** the solution (Ctrl+Shift+B).
9.  In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
10. Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers**.
11. Open the generated workbook.
12. Click **Enable editing** to allow the Excel Data Connector App to load.
13. Note that the **Last name** column is before the **First name** column.

### Use: Open in Excel Online

The Excel App is currently not working in Excel Online because of a bug that we helped identify. A fix is in the process of being moved to production and should be in place in the next few weeks. The Excel App is built using a new Apps for Office framework that provides a JavaScript-based web API for apps to communicate with the Office applications. The biggest advantage of using this new framework is that apps can run inside Excel on-premise (Win32), Excel Online (Office 365), Excel on the iPad, and other Excel apps in the future.

1.  Navigate to **Fleet Management &gt; Customers &gt; Customer**.
2.  Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers**.
3.  Click SharePoint
4.  Browse to a desired SharePoint folder
5.  Click Save. The default behavior is to open the file after save.
6.  Note that the workbook opens in Excel Online. In Excel Online, the capabilities of the Excel App like refresh, publish, and the design experience should work the same as in Excel on-premise.

## Template Open in Excel experiences
### Use: Template Open in Excel

Similar to the generated Open in Excel options, template options are added to forms automatically by finding templates that have the same first datasource as the root datasource in the form. A workbook template can have multiple datasources, as well as unbound content. The Open in Excel experiences are listed under the **Open in** **Microsoft Office** menu. The Excel workbook designer form provides an easy way to get a generated Open in Excel experience for an entity as well as providing a mechanism to get a blank workbook containing just the Excel App and a pointer to the server.

1.  In IE, navigate to **Common &gt; Common &gt; Office integration &gt; Excel workbook designer**.
2.  Select the **FleetCustomer** entity.
3.  Add all available fields so they are in the selected fields list.
4.  Click **Create workbook**.
5.  Open the generated workbook. The workbook contains the Excel Data Connector App, a binding to the **Fleet Management Customer** entity, and a pointer to the server it was generated from.
6.  Click **Enable editing** to allow the Excel Data Connector App to load.
7.  Customer data will be read from the OData service on the server and added to the table.
8.  Insert a blank row above the table and add “Fleet Customers” text as a title.
9.  Rename the sheet to “FleetCustomers”.
10. Now reorder some of the fields in the table. Click **Design** to open the design experience.
11. Next to the **FleetCustomer** data source there are buttons to edit and delete. Click **Edit** to see the fields list.
12. Select fields and move them around as needed. Set the order for the first three fields to **FirstName**, **LastName**, and **DriverLicense**.
13. Click **Update**. Note that the field order changed.
14. Click **Done**.
15. Click the **Settings** (gear) button.
16. Click **Clear binding data** so the workbook contains no bound data.
17. Click **OK**.
18. Save the workbook as **FleetCustomersBasic.xlsx**.
19. In IE, navigate to **Common &gt; Common &gt; Office integration &gt; Document templates**.
20. Click **New**.
21. Browse to locate the file you just saved.
22. Click Ok to add the template. The template will be added as a line in the templates table.
23. On the **FleetCustomersBasic** row, deselect the **Apply current record filter** checkbox so an unfiltered list of customers is loaded after the template is opened.
24. Adjust the **Template display name** to “Fleet Customers Basic”.
25. Navigate to **Fleet Management &gt; Customers &gt; Customer**.
26. Click **Open in** **Microsoft Office**.
27. Note that “**Fleet Customers Basic**” is now an option under the Open in Excel section. Click that option.
28. Open the generated workbook.
29. Click **Enable editing** to allow the Excel Data Connector App to load.
30. Customer data will be read from the OData service on the server and added to the table binding you created.

### Build: Register a template as a system defined template

Templates that are registered as a system defined template are loaded at deployment. This is useful for ISVs and partners that want to package templates with other model artifacts.

1.  Open **Visual Studio 2015** with the previously created Dynamics AX project with the model set to Fleet Management, or create a new one.
2.  Right click on the project &gt; **Add &gt; New item…**
3.  Select the **Resource** item type.
4.  Set the name as **FleetCustomersBasicTemplate**.
5.  Ensure that the **FleetCustomersBasic.xlsx** file is closed.
6.  Click **Add**.
7.  Select the **FleetCustomersBasic.xlsx** file. Note that the resource is added to the project.
8.  Open **View &gt; Application Explorer (Ctrl+E, Ctrl+E)**.
9.  Navigate to **AOT &gt; Classes &gt; Code &gt; FMTemplateRegistrations**.
10. Right click on **FMTemplateRegistrations &gt; Add to project**.
11. **Open FMTemplateRegistrations**. The FMTemplateRegistrations.xpp code file should be shown.
12. Copy one of the existing lines and change it to provide the template name, resource name, description, display name and the “Apply current record filter” and “List in Open in Office menu” values. The display name is the text that shows as an Open in Excel option and the description is shown when hovering over that item. The display name and description can be labels or just static strings.
13. The code should look something like this: this.addTemplate(OfficeAppApplicationType::Excel, resourceStr(FleetCustomersBasicTemplate), resourceStr(FleetCustomersBasicTemplate), "Template for fleet customers", "Fleet customers basic", NoYes::No, NoYes::Yes);.
14. **Save** the code and if asked to “Overwrite or Save As” click Overwrite.
15. **Build** the solution (Ctrl+Shift+B).
16. Now verify that the change was successful. In IE, navigate to **Common &gt; Common &gt; Office integration &gt; Document templates**.
17. Click **Reload system templates**.
18. Click **Yes** to confirm that you want to reload the system templates.
19. Verify that the new system-defined template is loaded with a template name of “FleetCustomersBasicTemplate”.

### Use: Journal Entry in Excel experience powered by a template

1.  In IE, navigate to **General ledger &gt; Journal entries &gt; General journals**
2.  Make sure that you are in company **USMF**
3.  Create a new journal by clicking New
4.  Set **Name** to **GenJrn**
5.  Click **Open lines in Excel**
6.  Open the generated workbook and enable editing (if needed)
7.  Note that header fields are populated
8.  **Enter a new line** with MainAccount set to 110110. Enter a description, a currency, and a debit amount
9.  Note that lookups are provided for the company and currency fields since this entity has those relationships defined
10. Click **Publish**
11. Note that the line is refreshed with the current date and debit amount of 0
12. In IE, click **Lines**
13. Note that line entered in Excel is shown

## Lookups in Excel experiences
### Use: Lookups in the Excel App

To facilitate data entry, the Excel App provides lookups and data assistance. Date fields provide a date picker, enumeration (enum) fields provide a enum list, and relationships provide a relationship lookup.

1.  In IE, navigate to **Fleet Management &gt; Rentals &gt; Rental**.
2.  Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Rentals**.
3.  Open the generated workbook.
4.  Click **Enable editing** to allow the Excel Data Connector App to load and read in data.
5.  Click on a **Drivers license** value.
6.  Note that a **relationship lookup** is now shown inside the Excel App showing a list of customers. This is the first generation of relationship lookup so no filtering or sorting is supported.
7.  Click on one of the other customers in the lookup and note that the **Drivers license** value changes. Because this is part of the key, click on the original **Drivers license** value to reset it. Note that the **Drivers license**, **First name**, and **Last name** fields make a multi-part key, but the Excel App doesn’t immediately change all parts of the multi-part key.
8.  Click on a **Start date** value.
9.  Note that a **date picker** is now shown inside the Excel App.
10. Click on another day to change the Start date.
11. Click **Design** and edit the FleetRental data source to **add the Status field** as a column in the table binding.
12. Once added, click on a **Status** value.
13. Note that a **enum list** is now shown inside the Excel App.
14. With focus in the status column, move up and down the list of rentals to see how quickly the enum list changes to reflect the current value. The enum list is shown in full so that the user can quickly see all the available values.
15. Click on a different **Status** value to see how an enum value can be changed with a single click.

### Build: Create a relationship lookup

When relationships exist between entities, then a relationship lookup is shown. Let’s create a new relationship lookup for Fleet Customers.

1.  Open **Visual Studio 2015** with the previously created Dynamics AX project with the model set to Fleet Management, or create a new one.
2.  Open **View &gt; Application Explorer (Ctrl+E, Ctrl+E)**.
3.  Navigate to **AOT &gt; Data Model &gt; Tables &gt; FMCustGroup**.
4.  Right click to **Open designer**.
5.  Right click on **FMCustGroup** in the designer &gt; **Addins &gt; Create data entity**.
6.  Artifacts will be added to the project.
7.  Open the designer view for **FMCustGroupEntity**.
8.  In the property sheet for **FMCustGroupEntity**, set **Public Collection Name** to **FleetCustomerGroups** and set **Public Entity Name** to **FleetCustomerGroup**.
9.  Add the **CustGroup** and **Description** fields to the **AutoLookup** field group.
10. If **FMCustomerEntity** is not already in the project, then add it.
11. Open the designer view for **FMCustomerEntity**.
12. Right click on **Relations &gt;** **New &gt; Relation**.
13. On the new relation set Name to CustomerGroup, Cardinality to ZeroMore, RelatedDataEntity to FMCustGroupEntity, RelatedDataEntityCardinality to ZeroOne, RelationshipType to Association, Role to CustomerGroupSource, RelatedDataEntityRole to CustomerGroupTarget.
14. **Build** the solution (Ctrl+Shift+B).
15. Now verify that the change was successful. In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
16. Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers**.
17. Open the generated workbook.
18. Click on a **Customer group** value.
19. **Change** a Customer group value for a customer.
20. **Publish** the change.
21. Change the value back and publish that change.

### Build: Create a custom lookup

Custom lookups can be created to show data options when an enum or relationship is not sufficient. The key example is when data needs to be retrieved from an external service and presented in real-time. Let’s add a simple custom lookup for country...

1.  Open **Visual Studio 2015** with the previously created Dynamics AX project with the model set to Fleet Management, or create a new one.
2.  Open the designer view for **FMCustomerEntity.**
3.  Right click on **Methods &gt;** **New Method**.
4.  Add the lookup\_Country code from below.
5.  **Save** the code and if asked to “Overwrite or Save As” click Overwrite.
6.  **Build** the solution (Ctrl+Shift+B).
7.  Now verify that the change was successful. In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
8.  Click **Open in** **Microsoft Office &gt; Open in Excel &gt; Fleet Management Customers**.
9.  Open the generated workbook.
10. Click on a **Country** value.
11. **Change** a Country value for a customer.
12. **Publish** the change.
13. Change the value back and publish that change.

public class FMCustomerEntity extends common { \[SysODataActionAttribute("FMCustomerEntityCountryCustomLookup", false), //Name in $metadata SysODataCollectionAttribute("\_fields", Types::String), //Types in context SysODataFieldLookupAttribute("Country")\] //Name of field public static str lookup\_Country(Array \_fields) { OfficeAppCustomLookupListResult result = new OfficeAppCustomLookupListResult(); result.items().value(1, "US"); result.items().value(2, "AU"); result.items().value(3, "FR"); result.items().value(4, "GR"); result.items().value(5, "NZ"); return result.serialize(); } }

## Export to Word experiences
### Use: Export to Word

Export to Word experiences can be used for lightweight reporting. Export to Word experiences are powered by pre-built templates. The Export to Word experiences are listed under the **Open in** **Microsoft Office** menu. Let's look at an example experience that has been created for Fleet Management Customers.

1.  In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
2.  Click **Open in** **Microsoft Office &gt; Export to Word &gt; Customer information Fleet Management Customers (unfiltered)**.
3.  Download and open the generated document. The document data from the currently selected record.

### Build: Create a Word template

The Microsoft Dynamics App for Office can be run in Word to enable the creation of templates that are subsequently used for document generation.

1.  Add a trusted catalog pointing at the file share containing the Microsoft Dynamics App manifest
    1.  In Word, click **File &gt; Options**
    2.  Click **Trust Center &gt; Trust Center Settings…**
    3.  Click **Trusted Add-in Catalogs**
    4.  In the **Catalog URL** field, put the file share location of the manifest
    5.  Click **Add catalog**
    6.  Click **OK**
    7.  Click **OK**
    8.  Restart Word

2.  Add the Microsoft Dynamics App into a document
    1.  In Word, click **Insert &gt; My Add-ins &gt; Shared Folder &gt; Microsoft Dynamics**
    2.  Click **Insert**
    3.  In the app, click **Add server information**
    4.  Enter the start of the URL (protocol + hostname) into the Server URL field e.g. "<https://topo00dfa4stbobaos.cloudax.test.dynamics.com>"
    5.  Click OK
    6.  Click Yes to apply the settings change and reload the app

3.  Sign into the app
    1.  Click **Sign In**. The Azure Active Directory sign in screen should provide a list of credentials. If an error is encountered, force a sign out (using the sign out link in the bottom right corner of the app) and sign in again.
    2.  Select the appropriate account or click **Use another account**.
    3.  Enter the credentials for that Dynamics AX environment and click **Sign in**.

4.  Load the template designer applet
    1.  After sign in, click Load applets
    2.  Check the Template Designer
    3.  Click OK
    4.  Click Yes to confirm
    5.  Click OK to exit the settings page. The latest Dynamics AX OData metadata will now be loaded.

5.  Either, add a fields data source
    1.  In the app, click Design
    2.  Click **Add fields**.
    3.  Select FleetCustomer
    4.  Click Next to go to the field selection page
    5.  In the document, add a title and/or some blank lines at the top of the document
    6.  In the app, in the Available fields list, select the **FirstName** field
    7.  Click Add label to add a content control referencing the "First name" label
    8.  In the document, click once to put focus into the document, then click again to put focus at the end of the label, then press right arrow until outside the content control (the control box disappears).
    9.  Add a separator like " - " or " : "
    10. In the app, click Add value to add a content control referencing the "FirstName" field
    11. Repeat the process for the **LastName** field label and value
    12. Continue adding fields as desired.

6.  Or, add a table data source
    1.  In the app, click Design
    2.  Click **Add table**.
    3.  Select FleetCustomer
    4.  Click Next to go to the field selection page
    5.  In the document, add a title and/or some blank lines at the top of the document
    6.  In the app, in the Available fields list, add the **FirstName**, **LastName**, and **City** fields
    7.  Click **Done**

7.  Save the template
    1.  In Word, save the document somewhere

### Build: Create a Word template and use it for document generation

Once a Word template has been built then it can be uploaded to create an Export to Word experience.

1.  Upload a template
    1.  In Dynamics AX, navigate to **Common &gt; Common &gt; Office integration &gt; Document templates**. Alternately, search for the page.
    2.  Click New
    3.  Click Browse
    4.  Use the file explorer dialog to select a previously created template and click **Open**
    5.  Note that the **Root data entity** is obtained from the template and displayed near the bottom of the dialog
    6.  Click OK.
    7.  Scroll down in the list of templates to confirm that the template was added
    8.  Optionally, if the template should not be filtered to the user's current record, uncheck Apply current record filter.
    9.  Optionally, if the template should not be filtered to the user's current company, uncheck Apply company filter.

2.  Use the uploaded template via document generation
    1.  Navigate to a form sharing the same root datasource as the template's root data entity. For FleetCustomer (FMCustomerEntity) that is Fleet Management &gt; Customers &gt; Customer.
    2.  Click **Open in Microsoft Office &gt; Export to Word** and click on the template
    3.  Download and open the generated document

## Document Management and SharePoint
### Use: Add a SharePoint document type

The Document Management subsystem can be used to attach files to records. Most non-executable file types are supported as attachments. A document preview is provided for Office document files and PDFs. Document Types are created by administrators to indicate where attachments should be stored. When an administrator uses SharePoint as the storage location then they need to provide a specific folder that the files should be placed in. Security of that SharePoint folder is a separate administration responsibility.

1.  In IE, navigate to **Organization administration &gt; Document management &gt; Document management parameters**
2.  Click **SharePoint**
3.  Ensure the **Default SharePoint server** field is set to a default value for the tenant e.g. "contosoax7.sharepoint.com"
4.  Click **Test SharePoint connection**
5.  Note successful connection
6.  Click **Save**
7.  Navigate to **Organization administration &gt; Document management &gt; Document types**.
8.  Click **New**.
9.  Set **Type** to **SharePointDoc**
10. Set **Name** to **SharePointDoc**
11. Set** Location** to **SharePoint**
12. Click the edit button (pencil symbol) next to the **SharePoint Address** field.
13. On the left side of the dialog, select a site. For the contosoax7 tenant, use **ContosoAX Team Site.**
14. On the right side of the dialog, select a folder. For the contosoax7 tenant, use **ContosoAX Team Site &gt; Documents &gt; OfficeIntegration &gt; Attachments.**
15. Click **OK**.
16. Click **Save**.
17. Click the browse button (globe symbol) next to the **SharePoint Address** field.
18. Note that a browser tab is opened showing the selected folder.
19. Using Windows Explorer, create a new Word document in the Documents folder with a few words in it.
20. In IE, navigate to **Fleet Management &gt; Customers &gt; Customer**.
21. With focus on the first customer, click the **Attach** button (paperclip symbol) in the top right corner of the form.
22. Click **New &gt; SharePointDoc**.
23. Click **Browse** and select the Word document.
24. Expand the **Preview** FastTab to see a preview of the Word document.
25. Expand the **Attachment **FastTab to see the **File location** of the Word document.
26. In IE, use the previously opened tab showing the SharePoint folder to double-check that the file has been placed appropriately.

## Email
### Use: Send mail via a local mail client

Email workflows enabled via the SysEmail framework can generate an email message (EML file) containing attachments for sending via Outlook or another email client.

1.  In IE, navigate to **Accounts receivable &gt; Customers &gt; All customers**.
2.  Select **US-008 Sparrow Retail**.
3.  Click **Collect &gt; Customer balances &gt; Collections** to open the Collections form.
4.  Click **Communicate &gt; Email &gt; Statements to contact**.
5.  Click **Ok** to accept the default values in the drop dialog.
6.  If prompted about the mail option to use, uncheck “Do not ask again” (this option can be altered via the user options form), select **Use an email app, such as Outlook**, and click **OK**.
7.  If you are running IE on your laptop, **open the generated email** (.eml) file. If you are running IE within the VM, copy the generated email (.eml) file out to your laptop and open it.
8.  Note the email address in the **To** field and the generated workbook **attachment**.

### Use: Send mail via SMTP

Email workflows enabled via the SysEmail framework can also be authored in a simple email dialog and then sent via SMTP.

1.  In IE, navigate to **System administration &gt; Setup &gt; Email &gt; Email parameters**
2.  Click **SMTP settings**
3.  Set the **Outgoing mail server** to the desired SMTP server:
    1.  [Office 365 production](https://support.office.com/en-us/article/Outlook-settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c) (including \*.onmicrosoft.com accounts): smtp.office365.com (Find via outlook.office.com &gt; Settings &gt; Mail &gt; POP and IMAP)
    2.  Outlook/Hotmail: smtp-mail.outlook.com

4.  Set the **username** and **password** to an appropriate email account and password
5.  Leave **SSLRequired toggled on** and leave **SMTP port number** as 587
6.  Click **Save**
7.  In IE, navigate to **Accounts receivable &gt; Customers &gt; All customers**.
8.  Select **US-008 Sparrow Retail**.
9.  Click **Collect &gt; Customer balances &gt; Collections** to open the Collections form.
10. Click **Communicate &gt; Email &gt; Statements to contact**.
11. Click **Ok** to accept the default values in the drop dialog.
12. If prompted about the mail option to use, select **Use the Microsoft Dynamics AX email client**, and click **OK**.
13. Change the **To** address to your email address to receive the test message
14. Enter a **Subject** and **Body**
15. Click **Send**.
16. In 1-5 minutes the email should be delivered.
17. Note that the mail will appear to be sent **From** the email account set on the Email parameters form. If the email account listed in the Email parameters form is given permissions to "**Send As**" (or "Send email from this mailbox") the **FROM** address used in the **Send email** dialog, then the emails will start appearing to come from that address.
    1.  Send As permissions can be configured on the Office 365 admin center (portal.office.com/Admin) &gt;  Users &gt; Active users &gt; User &gt; Edit mailbox permissions &gt; Send email from this mailbox ([Office 365 Help on Send email from another user's mailbox](https://support.office.com/en-us/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E)).
    2.  Send As permission for each user email account in the client, needs to be given to the email account setup in the Email parameters form, before emails can be sent by users.
    3.  Additional information: [How to set up an application to send email using Office 365](https://technet.microsoft.com/en-us/library/dn554323(v=exchg.150).aspx)

18. Note that if an email is sent directly from the server without user interaction, then it will be sent via batch process and the **Email distributor batch** process must be started
    1.  Navigate to **System administration &gt; Periodic tasks &gt; Email processing &gt; Batch**
    2.  Toggle **Batch processing to on**



See also
--------

[Office integration in Dynamics AX](office-integration.md)

[Office Integration Troubleshooting](office-integration-troubleshooting.md)

