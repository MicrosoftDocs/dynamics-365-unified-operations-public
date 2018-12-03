---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations platform update 23 (December 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operation platform update 23 (December 2018). 
author: tonyafehr
manager: AnnBe
ms.date: 12/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-12-31 
ms.dyn365.ops.version: Platform 23

---
# What's new or changed in Dynamics 365 for Finance and Operations platform update 23 (December 2018)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations platform update 23. This version has a build number of 7.0.XXXX.

### Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

### Platform update 23 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 23, sign in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=) (**not yet available**).

## Legal entity filtering using grid column headers
Starting in Platform update 23, for grids with cross-company queries, users are able to filter the *Legal entity* column using the column drop-down menu, similar to other columns in the grid. For example, if a user is looking at the global transactions for a specific customer, he might want to find the transactions within a small subset of companies. Prior to this feature, he would have had to filter using the Customer range tab on the Advanced filter or sort dialog, or utilize page-specific custom filters.

![Filter by legal entity](media/legalEntityFiltering.png  "Filter by legal entity")

## Export to Excel
In Platform update 22, the Export to Excel feature was improved to allow users to export up to 1 million rows from a grid in Finance and Operations, a substantial increase from the previous 10,000-row limit. 

In Platform udpate 23, we've continued to enhance this feature. After the export completes, users will now receive a notification in the Action center alerting them that the export has finished. The notification includes a link to download the Excel file containing the exported data. The link and notification are accessible for roughly three days after the export completes. 

## Manage access to network printers across legal entities
Access to the new System administration utility is managed by the Carbon Flighting Service. Platform Update 23 includes the **System network printers management** form that System Administrators can use, along with the Document Routing Agent (DRA) to register network printers with Dynamics 365 for Finance and Operations.
After you have enabled the feature, a **Preview** link will appear on the **System ntwork printers** form (**Organization administration** > **Setup** > **Network printers** and click **System network printers**). 
After you register the network printers with the service using the DRA, you will see the configuration information for each legal entity in the organization.

## Enabling index hints in X++ again
Microsoft Dynamics AX 2009 and prior versions supported INDEX HINTS from X++.  However, this was deprecated when Dynamics AX 2012 was released. For more information, see [Deprecated: X++ index hint clause](../../../dynamicsax-2012/appuser-itpro/deprecated-x-index-hint-clause.md)

One of the main reasons this was deprecated was because an ill advised index hit could hurt the queries and little could be done until the query is fixed. Now, after seeing thousands of queries in hundreds of tenants and seeing SQL come up with less optimal plans for some simple queries at times, Finance and Operations has brought back the X++ hints with extra caution.

We have added a new API on common **allowIndexHint** with a default behavior of **False**. This allows developers to opt-in and explicitly enable index hint. The old syntax on the select statement for specifying index hint is reused.
If there is an existing X++ code that specifies index hint, there is no change to the current behavior in Rainier until the new API is invoked. See the following example:

    public void testIndexHintRegularTable()
        {
            SysDataAccessDBLogTestTable tbl1;
            tbl1.allowIndexHint(true);
            select generateonly tbl1 index hint PrimaryKeyIdx where tbl1.description == ''; // Send index hint to SQL server
         ………..

        }

> [!NOTE]
> Index hints should be used sparingly, and only when you can ensure that it causes more benefit than harm. With the new API, knowledgeable power developers are empowered to pass the right hints when needed. Power developers should use this new feature with caution. When in doubt, avoid using index hints.


