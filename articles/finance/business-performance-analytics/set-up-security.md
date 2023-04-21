---
# required metadata

title: Set up security for business performance analytics
description: This article explains how to set up security for business performance analytics
author: jkhaira7
ms.author: jkhaira
ms.reviewer: twheeloc 
ms.date: 04/20/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:
---

# Set up security for business performance analytics

[!include [banner](../includes/banner.md)]


Setting up security in the business performance analytics app is a critical step for ensuring the security of your organization’s data. This article provides an overview of the setup process for role-based, dimension, report security and adding users to the application. 

## Admin Role
The first login to the app is given the **BPA admin** role. This role allows the user to access the **Administrator** section of business performance analytics to set up security. The admin is automatically assigned the **Microsoft report viewer** role and the **All access** dimension group. 
•	The **Microsoft report viewer** role allows a user to view all reports that Microsoft provides in business performance analytics. 
•	The **All access** dimension group allows a user to view data for all dimensions, without any filters. 

## Set up roles
A role defines which reports a user can access. Use roles to organize how business performance analytics users can access reports. 

## Dimension security
Dimension security allows administrators to control which data is visible in a report. Setting up dimension security is a two-step process:

1. Set up dimensions: Select the dimensions you want to secure. In public preview, you can select up to five dimensions from the ledger and reporting dimensions. If this selection of dimensions is updated, this may have impact on the dimension groups created and the users who were assigned those dimension groups. 

2. Set up dimension groups: You may only create dimension groups after step one is complete. Dimension groups filter report data so only the filtered dimension values from a given dimension attribute are visible to users assigned to that dimension group. You may assign one or more dimension groups to a user to control what data is visable on a report. There has to be at least one dimension group assigned to a user.  

>[!Note]
>If you assign a lot of dimension groups to a single user, the user's reports may load slower. 


## Set up dimensions 
To set up the dimensions to secure access to data, follow these steps:

1.	Go to the **Administration** page in business performance analytics or go to the **Dimensions** page. 
2.	Click **Set up dimensions**. 
3.	Select up to five dimensions to secure access to data. If you don't secure a dimension, all users can access the values in that dimension. 
4.	Click **Save**. 

## Set up dimension groups
To set up dimension groups, follow these steps:
1.	Go to the **Administration** page in business performance analytics. 
2.	Click **Set up dimension groups**.

or 
go to the **Dimension groups** page and click **New**.

3.	Enter a name for the dimension group. Click **Next**.
You will see the selected dimensions when the **Set up dimensions to secure** step is completed.
4. Click **Select specific values** to select the exact dimension values to use in a dimension group.
5. Add a range of dimension values using a **Between** operator. You can add a maximum of 5 ranges. 
6. Click **Preview results** to preview the values will be filtered based on your selections. You can determine what values for each dimension will be visible to the users assigned this dimension group.
7. If you don't select a dimension value filter for a given dimension, all values will be displayed in the report. Dimension filters for other dimensions will still be applied.
8. Click **Next** after you have made your selections for all dimensions to be secured. You can review the selections on the **Review** page of the **New dimension group** dialog. 
9. Click **Save** to create the dimension group.  

>[!NOTE:]
>Creating a new dimension group process doesn't confirm if a valid combination of dimension values have been selected. If you have selected an invalid combination of dimension values, the dimension group will filter out all records in reports. Test the dimension group by opening a report as a user assigned to this dimension group to verify that the dimension value combination is valid. 

Within a given dimension group, a record must satisfy all the filter conditions for the data to be visible. Any conflicting criteria or invalid combinations will not display data. 

### Example  

A user is assigned to only one dimension group, Test dimension group, with the following filters: 
Legal entity: USMF and CNMF
Cost center: Between 000001 and 000003
Department: 000004
If the Cost center and Department numbers are linked so the Cost center and Department numbers must match, using the above dimension values will result in no data being available to the user assigned this dimension group. 

Invalid combinations: A user is assigned to only one dimension group, Test dimension group, with the following filters: 
Legal entity: USMF and CNMF
Cost center: Between 10000 and 20000
Department: 000004
If all cost centers have values below 10000, using the range between 10000 and 20000 will result in no data being available to the user assigned this dimension group.
 
If a user is assigned two or more dimension groups, a record must satisfy the filter conditions of at least one of those dimension group for the data to be available to the user in a report. For example:
A user is assigned to two dimension groups: Test dimension group and Group x. 
Test dimension group: 
Legal entity: USMF, CNMF
Cost center: Between 000001 and 000003
Department: Marketing 01

Group x: 
Legal entity: USMF
Cost center: ALL
Department: ALL
The user will be able to see records for legal entities USMF and CNMF. For Legal entity USMF, the user will see all cost centers and all department combinations. For Legal entity CNMF, the user will see records where the cost center is between 000001 and 000003 and department is Marketing 01. 

If a user is assigned an **All access** dimension group or a dimension group with no filters, the user has full visibility to the data in a report. For example:

Legal entity: 
Cost center: All
Department: All
No filter was defined for Legal entity. The **All** filter was used for Cost center and Department. The user will see records with all combinations of Legal entity, Cost center and Department. 

### Set up users
After you have set up the roles and dimension groups, you can set up users to have access to business performance analytics.

To set up users: 
1.	Go to the **Administration** or **Users** page in business performance analytics.  
2.	Click **Set up user**. Search for the username or email to set up in business performance analytics. This search bar searches Dataverse for users. You may only set up one user at a time.

>[!Note]
>If a new user is added to Azure Active directory, it may take some time for this user to become available. 

3.	Click **Next**. 
5.	Assign at least one role and one dimension group to the user. To make this user a BPA admin, select **App administrator**. 
6.	Click **Save**.  

### Share business performance analytics with users 
Confirm that the users you would like to share the app with are set up as business performance analytics users in the app and their security is set up. 
Follow these steps: 
1.	On the top left corner of the business performance analytics, click **Business performance analytics (preview)**. 
2.	A dialog box will open with a **Published apps** list. 
3.	Find **Business performance analytics (preview)**. Click on the three dots.
4.	Click **Manage roles**. 
5.	Expand **App URL suffix**. Enter a name to use in the custom URL you share with users of the BPA app. 
6.	Copy the URL generated and share with users to allow them access to the app.

