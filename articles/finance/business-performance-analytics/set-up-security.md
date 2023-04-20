---
# required metadata

title: Set up security for business performance analytics
description: This article explains how to set up security for business performance analytics
author: khaira7
ms.date: 04/20/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DefaultDashboard, UserWorkspaceAdd, UserWorkspaceConfigureWebsite
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2021-04-30
ms.dyn365.ops.version: 10.0.19

---

# Set up security for Business performance analytics

[!include [banner](../includes/banner.md)]


Setting up security in the business performance analytics (BPA) app is a critical step for ensuring the security of your organization’s data. This guide provides an overview of the setup process for role-based security, dimension security, report security and adding users to the application. 
# Admin Role
By default, the first login to the app is given the “BPA admin” role. This role allows the “BPA admin” to access the “Administrator” section of the app to perform actions such as setting up security. The first admin can then assign other users to the “BPA admin” role.
A BPA admin is automatically assigned the “Microsoft report viewer” role and the “All access” dimension group. 
•	The “Microsoft report viewer” role allows a user to view all reports that Microsoft provides in the BPA app. 
•	The “All access” dimension group allows a user to view data for all dimensions, without any filters. 
# Set up Roles
A role defines which reports a user can access. For example, the “Microsoft report viewer” role allows a user to view all reports Microsoft provides with the BPA app. Use roles to organize how BPA app users can access reports. 
# Dimension Security
Dimension security allows administrators to control which data is visible in a report. Setting up dimension security is a two-step process:

1. Set up dimensions to secure: The first step to setting up dimension security is to select the dimensions you want to secure. In public preview, you can select up to five dimensions from your ledger and reporting dimensions. Complete this step carefully. If you attempt to change the selection of dimensions used to secure data later, this may have downstream impacts on the dimension groups you created and, as a result, the users who were assigned those dimension groups. 

2. Set up dimension groups: You may only create dimension groups once you complete step 1. Dimension groups filter report data such that only the filtered dimension values from a given dimension attribute will be visible to a user assigned to said dimension group.  You may assign one or more dimension groups to a user to control what data they see when they open a report. However, you must assign at least one dimension group to a user. Otherwise, they will not be able to see any data in a report. Note: If you assign a lot of dimension groups to a single user, their reports may load slower. 


## Set Up Dimensions to Secure

1.	To set up the dimensions for which you would like to secure access to data, navigate to the “Administration home” page in the BPA app. Alternatively, go to the “Dimensions” page. 
2.	Click “Set up dimensions”. 
3.	Select up to five dimensions for which you would like to secure access to data. If you do not secure a dimension, all users can access the values in that dimension. 
4.	Click “Save” to complete your action. 

## Set Up Dimension Groups
1.	To set up dimension groups, navigate to the “Administration home” page in the BPA app. Click on “Set up dimension groups”. 
2.	Alternatively, go to the “Dimension Groups” page and click on “New”.
3.	A dialog titled “New dimension group” will appear. Name your dimension group (say Test Dimension Group) and click “Next”. 
4.	On the left margin of this dialog, you will see all the dimensions you selected when you completed the “Set up dimensions to secure” step. 
5.	You can select specific dimension values using the “Select specific values” button. This allows you to select the exact dimension value you would like to use in a dimension group.
6.	You may also add a range of dimension values using the “Between” operator. You can add a maximum of 5 ranges. 
7.	Click the “Preview results” button to preview what values will be filtered based on your selections. One by one, you can determine what values for each dimension will be visible to the users assigned this Test Dimension Group. 
8.	If you do not select a dimension value filter for a given dimension, all values will be displayed in the report. However, dimension filters for other dimensions will still be applied. 
9.	Click “Next” after you have made your selection. Once you have repeated this action for all dimensions to be secured, you can review your selections in the “Review” page of the “New dimension group” dialog. 
10.	If satisfied, click “Save” to finish creating the Test Dimension Group.  

>**NOTE:**
The “New dimension group” dialog does not verify if you have selected a valid combination of dimension values. If you have selected an invalid combination of dimension values, the dimension group will filter out all records in reports. Test out the dimension group by opening a report as a user assigned to this dimension group to verify that the dimension value combination set up is valid. 

Within a given dimension group, a record must satisfy all the filter conditions for the data to be visible. Therefore, any conflicting criteria or invalid combinations will result in no data being visible. Consider the following scenarios: 

1.	Conflicting criteria: A user is assigned to only one dimension group, Test Dimension Group, with the following filters: 
Legal Entity: USMF, CNMF
Cost Center: Between 000001 and 000003
Department: 000004
If, in your organization, Cost Center and Department numbers are linked such that Cost Center and Department numbers must match, using the above dimension values will result in no data being available to the user assigned this dimension group. 
2.	Invalid combinations: A user is assigned to only one dimension group, Test Dimension Group, with the following filters: 
Legal Entity: USMF, CNMF
Cost Center: Between 10000 and 20000
Department: 000004
If, in your organization, all Cost Centers have values below 10000, using the range between 10000 and 20000 will result in no data being available to the user assigned this dimension group.
 
If a user is assigned two or more dimension groups, a record must satisfy the filter conditions of at least one of those dimension group for the data to be available to the user in a report. Consider the following scenario: 
A user is assigned to two dimension groups, Test Dimension Group and Group X. 
Test Dimension Group is set up as follows: 
Legal Entity: USMF, CNMF
Cost Center: Between 000001 and 000003
Department: Marketing 01

Group X is set up as follows: 
Legal Entity: USMF
Cost Center: ALL
Department: ALL
The user will be able to see records for legal entities USMF and CNMF. For Legal Entity USMF, the user will be able to see records with all cost centers and all department combinations. For Legal Entity CNMF, the user will be able to see records where Cost Center is between 000001 and 000003 and Department is Marketing 01. 

If a user is assigned an “All access” dimension group or a dimension group with no filters then, the user has full visibility to the data in a report. Consider the following scenario: 
Legal Entity: 
Cost Center: ALL
Department: ALL
No filter was defined for Legal Entity. The “ALL” filter was used for Cost Center and Department. Therefore, the user will be able to see records associated with all combinations of Legal Entity, Cost Center and Department. 

# Set Up Users
Once you have set up the roles and dimension groups, you may start setting up users who will have access to the BPA app. 
1.	To set up users, navigate to the “Administration home” page in the BPA app. Alternatively, go to the “Users” page. 
2.	Click on “Set up user”. Search for the username or email you would like to set up in the BPA app. This search bar searches Dataverse for users. You may only set up one user at a time.
3.	**Note**: If a new user is added to Azure Active directory, it may take up to 30 minutes for this user to become available to be set up as a BPA app user. 
4.	Click “Next”. 
5.	Assign at least one role and one dimension group to the user. You may also make this user a BPA admin by toggling the “App administrator” button to “Yes”. 
6.	Click “Save”.  

# Share BPA app with Users as an Admin
Make sure the users you would like to share the app with are set up as BPA users in the app and their security is appropriately set up. Then, follow these steps: 
1.	On the top left corner of the BPA app, click on the name of the app “Business performance analytics (preview)”. 
2.	A dialog box will open with the list of all “Published Apps”. 
3.	Find the “Business performance analytics (preview)” app tile and click on the three dots.
4.	Click on “Manage Roles”. 
5.	Expand the header named “App URL Suffix” and enter whatever nickname you would like use in the custom URL you share with users of the BPA app. Copy the URL generated and share with users to allow them access to the app.

