---
# required metadata

title: Security Upgrade Advisor Tool user guide (AX 2012)
description: The Microsoft Dynamics AX Security Upgrade Advisor Tool is intended to help simplify the process of upgrading security settings from earlier versions of Microsoft Dynamics AX to Microsoft Dynamics AX 2012. 
author: kfend
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
# ms.reviewer: 51
ms.search.scope: AX 2012 R3 CU8
# ms.tgt_pltfrm: 
ms.custom: 30061
ms.assetid: fda4d8e9-79a2-4ee2-831e-a90a9df2d980
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: AX 2012 R3 CU8

---

# Security Upgrade Advisor Tool user guide (AX 2012)

[!include[banner](../../includes/banner.md)]


The Microsoft Dynamics AX Security Upgrade Advisor Tool is intended to help simplify the process of upgrading security settings from earlier versions of Microsoft Dynamics AX to Microsoft Dynamics AX 2012. 

| **Note**                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| This is pre-release documentation of a preliminary nature and is subject to change at any time without notice. Microsoft cannot guarantee the accuracy of any information provided herein. |

The Security Upgrade Advisor Tool compares entry points and permissions between systems, and generates a list of matching privileges that can be used for a particular role. The role-to-privilege mapping is based on the user group–to–access right mapping in earlier versions of Microsoft Dynamics AX systems. The tool is designed as an aid for upgrading security settings and is not a one-click solution. Developers are advised to review each suggestion carefully before making any changes. The list of suggestions generated is based on the following criteria:

1.  The entry point name, type, and access right are exactly matched between earlier versions of Microsoft Dynamics AX and Microsoft Dynamics AX 2012.
2.  The entry point name and type are exactly matched. However, for an access right, if an exact match is not found, a similar match suggestion is generated. Any access right that is greater than View in both the earlier versions of Microsoft Dynamics AX and Microsoft Dynamics AX 2012 is considered a potential match.

## Assumptions
Before you use the tool, we assume that you have met the following prerequisites:

-   You are familiar with development environments in earlier versions of Microsoft Dynamics AX and Microsoft Dynamics AX 2012.
-   You are familiar with the security model in earlier versions of Microsoft Dynamics AX and Microsoft Dynamics AX 2012.
-   You have developer privileges in Microsoft Dynamics AX, so that you can run the tool from the Application Object Tree (AOT).
-   You have completed the code upgrade and data upgrade. The Security Upgrade Advisor Tool can be run at any time, but running it after a code upgrade enables artifacts to be carried over from earlier versions of Microsoft Dynamics AX.

## Install the tool
1.  Run **SecurityUpgradeAdvisorTool.msi** to open the **Installation Wizard**.
2.  Accept the License Agreement, and then click **Install**.
3.  Click **Finish** to complete the installation. After the **Installation Wizard** has finished running, the files are available at: x64 systems - %ProgramFiles(x86)%MicrosoftSecurity Upgrade Advisor Toolx32 systems - %ProgramFiles%MicrosoftSecurity Upgrade Advisor Tool

## Before running the tool
Before you run the tool, here are few things that you should consider:

-   Source Control – The tool does not support generating roles and privileges when source control is enabled.
-   Model – Perform all security upgrade tasks in a model. This provides the flexibility to export your newly generated settings to new environments. It also lets you delete the whole setting if you have to clean up and regenerate settings.
-   Testing – The tool generates security artifacts based on security settings from earlier versions of Microsoft Dynamics AX. We recommend that you iteratively review, fine-tune, and test each setting to make sure that the generated settings are the ones intended.

## Running the tool
The following procedures describe the process you should follow when running the Security Upgrade Advisor Tool.

### Export security settings from an environment running an earlier version of Microsoft Dynamics AX

1.  In the environment that is running an earlier version of Microsoft Dynamics AX, import the following XPO: Job\_ExportSecuritySettingsBulk.xpo.
2.  Execute the X++ job ExportSecuritySettingsBuild.
3.  When prompted, enter the name of the file to save.
4.  Export the file to a known location for later retrieval.

### Run the Security Upgrade Wizard in Microsoft Dynamics AX 2012

The outputs of the wizard are custom roles in the AOT, named with a prefix that you specify. No users are assigned to these roles automatically. After roles are generated, you must manually assign roles to each user. Clicking **Next** runs each step of the wizard. Clicking **Cancel** closes the wizard.

1.  Drain the client connections that are connected to the instance of Application Object Server (AOS) that you are working with. For more information, see [Drain users from an AOS](http://technet.microsoft.com/library/d19bd816-cd9e-423a-94c7-aceb946baa30(AX.60).aspx).
2.  In **Administrative Tools** &gt; **Services**, stop the **Microsoft Dynamics AX Object Server 6.0** service.
3.  Use Windows PowerShell or AXUtil to import the model SecurityUpgradeAdvisorTool.axmodel into the Microsoft Dynamics AX 2012 AOT.

        Install-AXModel -File SecurityUpgradeAdvisorTool.axmodel -Details

    For more information, see [How to: Export and Import a Model](http://msdn.microsoft.com/library/c2449a03-7574-4b9d-8518-9005b560209f(AX.60).aspx).

4.  Start the **Microsoft Dynamics AX Object Server 6.0** service.
5.  Open the Security Upgrade Advisor project, and open the **Forms** &gt; **SecurityUpgradeWizard** form. **Important: **Compile the project and synchronize all tables in the object groups **UpgradeAdvisorTool** and **PrivelegeGenerationTool** in the AOT.
6.  Click **Next** to open the **Step 1 Import Settings** page. This step imports the .xml file of security information exported from an earlier version of Microsoft Dynamics AX into temp tables in Microsoft Dynamics AX 2012. This step uses the file generated in the previous section.
7.  Click **Next** to open the **Step 2 Find Privilege Matches** page. This step iterates through the existing security settings, and finds matching entry points and permissions in Microsoft Dynamics AX 2012.
8.  Click **Next** to open the **Step 3 Map User Groups to Custom Roles** page. This step generates new custom role mappings for the privileges that were found.
9.  Click **Next** to open the **Step 4 Export Security Upgrade Suggestions** page. This step exports all the mappings to a temporary table.
10. Click **Next** to open the **Step 5 Security Upgrade Suggestions** page. This page of the wizard displays the suggested security mappings. **Important: ** We strongly recommend that you export the upgrade suggestions for additional analysis.You can copy and paste the data into Microsoft Excel for additional analysis by pressing Ctrl+T. For more information about how to analyze the suggested settings, see the next section.
11. If, during your analysis of the security upgrade suggestions, you notice multiple items that have the **NoMatchingPrivilege** status, you may want to run the Privilege Generation Tool. Click **Generate Privileges**.
12. Click **Next** to open the **Step 6 Specify Custom Role Generation Options** page. In this step, you can specify options for generating roles in the AOT:
    -   Select Include similar matches in the custom role to use privileges that match with **Similar** status, and to add them to the custom role.
    -   In the **Optional prefix for custom role name** field, enter a prefix for the new role. We recommend that you use a prefix that helps you easily identify roles in the AOT later. If your Microsoft Dynamics AX 2009 system had domains, you can prefix the domain name to the role to distinguish between similar user group names in different domains.

13. Click **Finish** to exit the wizard.

When the wizard has finished running, custom roles based on the suggested security mappings are available in the AOT. We strongly recommend that you review the generated custom roles, and follow an iterative testing and refinement process to fine-tune your security settings.

## Analyzing upgrade suggestions
The result generated by step 5 of the Security Upgrade Advisor Tool is a list of all roles, entry points, permissions, and matching privileges. It contains the following columns.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Columns</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span class="ui">Domain</span></td>
<td>The domain names imported from Microsoft Dynamics AX 2009.</td>
</tr>
<tr class="even">
<td><span class="ui">Role</span></td>
<td>The user group names imported from Microsoft Dynamics AX 2009. Data in the column has been formatted to remove any special characters.</td>
</tr>
<tr class="odd">
<td><span class="ui">Privilege</span></td>
<td>The matching privileges in Microsoft Dynamics AX 2012. This column contains values only if the value in the <strong><span class="ui">Status</span></strong> column is <strong><span class="ui">Exact</span></strong> or <strong><span class="ui">Similar</span></strong>.</td>
</tr>
<tr class="even">
<td><span class="ui">Entry Point Name</span></td>
<td>The entry point names imported from Microsoft Dynamics AX 2009.</td>
</tr>
<tr class="odd">
<td><span class="ui">New Entry Point Name</span></td>
<td>If entry points were renamed from earlier versions of Microsoft Dynamics AX to Microsoft Dynamics AX 2012, the script automatically maps privileges based on the new entry point names, and populates this column with the new name.</td>
</tr>
<tr class="even">
<td><span class="ui">Entry Point Type</span></td>
<td>The entry point types.</td>
</tr>
<tr class="odd">
<td><span class="ui">Entry Point Access Rights</span></td>
<td>The matching entry point permissions in Microsoft Dynamics AX 2012. This column contains values only if the value in the <strong><span class="ui">Status</span></strong> column is <strong><span class="ui">Exact</span></strong> or <strong><span class="ui">Similar</span></strong>.</td>
</tr>
<tr class="even">
<td><span class="ui">Entry Point Old Access Rights</span></td>
<td>The entry point rights that were configured in Microsoft Dynamics AX 2009. This column is added for reference.</td>
</tr>
<tr class="odd">
<td><span class="ui">Status</span></td>
<td>The status for each entry point match. The following statuses are generated by the tool:
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><span class="ui">Exact</span></td>
<td>The entry point, type, and access right exactly match a privilege in Microsoft Dynamics AX 2012. The suggested privilege can be used in the specified role for similar security settings in Microsoft Dynamics AX 2012.</td>
</tr>
<tr class="even">
<td><span class="ui">Similar</span></td>
<td>The entry point and type match exactly, but no exact match for an access right was found. However, there is a potential match, because both the old and new access rights have permissions greater than <strong>View</strong>.
<table>
<thead>
<tr class="header">
<th><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The developer and administrator should review these rows, and make sure that the suggested privileges match the intended security outcome.</td>
</tr>
</tbody>
</table></td>
</tr>
<tr class="odd">
<td><span class="ui">NoEntryPoint</span></td>
<td>There were no matching entry point and type between earlier versions of Microsoft Dynamics AX and Microsoft Dynamics AX 2012. A manual entry point mapping must be performed for items that are not found.</td>
</tr>
<tr class="even">
<td><span class="ui">NoMatchingPrivilege</span></td>
<td>Even though an entry point was found in Microsoft Dynamics AX 2012, the access right did not match any criteria. A manual access right mapping might be required, or it may be possible to generate a privilege by using the Privilege Generation Tool.</td>
</tr>
<tr class="odd">
<td><span class="ui">Deprecated</span></td>
<td>The entry point has been removed from Microsoft Dynamics AX 2012.</td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

## Privilege Generation Tool
The Privilege Generation Tool is included as part of the Security Upgrade Advisor Tool. There are many scenarios where custom entry points may not have a privilege and associated access right defined. As a best practice, we recommend that a privilege be associated with an entry point. In cases where a privilege is not predefined, the Privilege Generation Tool can automatically generate privileges during the upgrade process. Use the following procedure to generate privileges for all entry points with a status of **NoMatchingPrivilege**.

1.  From the Security Upgrade Tool, on the **Step 5 Security Upgrade Suggestions page, click Generate Privileges**.–or–Open the Privilege Generation Tool form from the AOT, under **PrivilegeGenerationTool** &gt; **Forms** &gt; SecurityUpgradePrivilegeGenerator.
2.  On the **Step 1: Privilege Generation Wizard** page, click **Next** to start the wizard.
3.  In step 2, specify an optional prefix to add to the names of the generated privileges, and then click **Next**.
4.  Step 3 lists all the privileges that can be generated. Select **Create** for each privilege that you want to generate, and then click **Next**.
5.  After privilege generation is completed, click **Finish** to close the wizard.
6.  In the AOT, verify that the privileges were generated successfully by looking under **Security** &gt; **Privileges**.
7.  Update the AOT to display the new privileges, and then compile them to make sure that they have been generated correctly.
8.  Run the Security Upgrade Advisor Tool again.

| **Important**                                                                                                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If you have the **SysUtilElementsLog** menu item from an earlier version of Microsoft Dynamics AX, it shows compile errors after privileges are generated. The type of the **SysUtilElementsLog** menu item has changed to Display in Microsoft Dynamics AX 2012. **Work Around:** To work around this issue, change the type to **Display**, and reassign the name to the privilege. |

## Frequently asked questions
### Can you automatically generate role definitions from Excel?

No. You cannot modify a spreadsheet in Excel and use those settings to generate roles. However, you can generate custom roles and privileges by using the tool.

### What happens to the custom menu items that were used in the earlier versions of Microsoft Dynamics AX?

When you run this tool on a system that has finished a code upgrade, you find a match for the menu items in the Microsoft Dynamics AX 2012 system. However, there are no privileges for them. You must create new privileges if you believe that they are applicable.

### Does the tool consider other artifacts, such as tables and forms?

No, the tool only considers entry points, such as menu items. In the Microsoft Dynamics AX 2012 security model, privileges are used to maintain access to the artifacts.

### Are the user groups mapped for all the domains?

Yes. The results are for each domain and user group. Based on your organizational structure in Microsoft Dynamics AX 2012, decide which user group/domain combinations you want to create roles for in Microsoft Dynamics AX 2012.

### Are users moved as part of the security upgrade?

No user information is stored or moved. After the roles have been created in Microsoft Dynamics AX 2012, the user role mapping must be created manually.

### Are Record Level Security settings moved as part of the security upgrade?

No Record Level Security (RLS) rules are upgraded. In Microsoft Dynamics AX 2012, there is a new and richer data security mechanism called Extensible Data Security (XDS). We recommend that you create new XDS policies based on your business requirements.

### What are the next steps to complete the security upgrade?

After the Excel spreadsheet with the results is generated, you can use the role generation and privilege generation functionality in the tool to create roles and privileges automatically. Then, test the system by assigning users to those roles, and validating that they have access and the exposed functionality is accurate.



