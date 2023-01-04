---

# required metadata

title: Dynamics 365 Human Resources customer merge overview
description: This article describes the Microsoft Dynamics 365 Human Resources customer merge.
author: twheeloc
ms.date: 01/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# Dynamics 365 Human Resources customer merge 

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Dynamics Human Resources 365 customer merge

As part of the infrastructure merge, all of the Human Resources application capabilities are available in finance and operations environments. Customers can migrate their Human Resources environments by using the migration tooling that is available in Microsoft Dynamics Lifecycle Services. They can also merge their data with their existing finance and operations environment.

Customer merge or consolidation of their Human resources environment with another finance and operations environment isn't required by Microsoft. It's done at the customer's discretion and on the customer's own timeline. During this step, customer moves their data into an existing environment, such as a Finance or Project Operations environment. It's mostly manual and can be done by using Data Management Framework (DMF) data entities.

This page includes resources and information regarding various customer scenarios when merging finance and operations based environments. 

## Custom fields
There's an extensive set of fields out-of-the-box for managing a broad range of business processes. Sometimes there's a need for a company to track additional information. While programmers can be used to add those fields as extensions in developer tools, the custom fields feature allows fields to be added directly from the user interface. This allows you to tailor the application to fit your business. For more information, see [How to create and work with custom fields](../../fin-ops/get-started/user-defined-fields.md). 

### Move custom fields from one environment to another
To move custom fields from one environment to another: 
•	Move the MetadataExtensionTable.
•	Move the tables that contain labels/translations/picklists. These tables are:
  •	SysCustomFieldLabels
  • SysCustomFieldPicklist
  • SysCustomFieldPicklistValues
      o	Open SSMS
      o	Find the AXDB Database
      o	Right-click, select **Tasks**
      o	Click **Generate scripts**
      
      
![Generate scripts.](media/Generate-scripts-1.png)
     
 - Click **Next**
 - Click **Select specific database objects**
 - Extract the **Tables** node and select the “MetaDataExtensionTable” table as shown below:

![Database objects](media/database-objects3.png)

 - Scroll down the tables list and select the following tables:  
  - SysCustomFieldLabels 
  - SysCustomFieldPicklist 
  - SysCustomFieldPicklistValues 
  
  
 - Click **Next**.

![Choose objects](media/choose-objects4.png)

 - Select the highlighted options shown below: 
  - **Save script to a specific location** 
  - **Save to file** 
  - **Unicode text**

 - Click **Advanced**, go to **Types of data to script**. Select the lookup, select **Data only**. Click **Ok**.

![Scripting.](media/set-scripting5.png)

 - Select a file name to save and click **Next**.

![File name](media/file-name6.png)

 - Click **Next**.
 - Click **Finish**.


 - Move the created SQL file to the target environment and open by SQL query editor.

 - Outcomment the lines for “DimensionAttributeValueCombination” and “DimensionAttributeValueSet” and run the script. 
 - This will import the records into the database.

![Import records](media/record-import7.png)

### Copy custom fields metadata in Dataverse

How to copy Dynamics 365 Human Resources custom fields metadata created in Dataverse to another instance of a Dataverse environment.

 - Create a new unmanaged solution
    -   Log into Dynamics 365 Human Resources.
    -   Go to **System administration > Integrations > Dataverse configuration**.
    -   The banner at the top of page provides the name of the Dataverse instance being synced to and a link to the Admin Center. 

![Dataverse instance](media/dataverse-integration8.png)

    -   Make note of the name of the Dataverse instance.
    -   Open a new browser tab and go to the PowerApps Maker portal (https://make.powerapps.com).
    -   In the upper right corner, click on the **Environment** drop-down and find the name of the Dataverse instance.

![Environment drop-down](media/environment-name10.png)


    -   Click **Solutions**.
    -   Click **New solution**.
    -   Enter a name, description and select the **Default publisher**. 
    -   Click **OK**. The new solution will display in the **Solutions** list.

![Solutions list](media/solutions-list11.png)


2.	Add the custom fields created through HR to the new unmanaged solution
    a.   Click on the name of the new solution created in step 1.
    b.   Click **Add existing > Table**.
    c.   Search for the table name where custom fields have been added. 
    d.   Select the table, click **Next**.
    e.   Click **Select objects**, go to the **Fields** tab.
    f.   In the search, find all the fields that end in **_custom**. 
    g.   Select the fields, click **Add**. 
    h.   The table screen should now reflect the number of objects selected. Click **Add** on this dialog.
    i.   The solution screen should now show the name of the table added to the unmanaged solution.
    j.   Repeat the process by clicking Add Existing again until all the custom fields have been added to the new solution.
    k.   Go to the **Solutions** list by clicking the back arrow.
    
    
3.	Export the solution as managed.
    a.   Check the new solution created.
    b.   Click **Next**.
    c.   **Managed** is checked by default. Click **Export** to start the export process.
    d.   Once the export process is completed, click **Download**. The solution should be saved to the browser’s default download folder.

4.	Import managed solution into the other Dataverse environment
    a.   In the Maker portal, in the **Environment** drop-down from step 1 to the destination Dataverse environment.
    a.   In the **Solutions** list, click **Import**.
    a.   Click **Browse**. Locate the exported managed solution from step 3.
    a.   Click **Next**, then click **Import** and wait for the managed solution to be applied to the destination Dataverse environment.







