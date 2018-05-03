---
# required metadata

title: Cross-company data sources in Electronic reporting
description: 
author: NickSelin
manager: AnnBe
ms.date: 05/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0

---

# Cross-company data sources in Electronic reporting

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to generate outgoing documents in various formats. When an ER format is running to generate required documents, it calls data sources that were configured in a corresponding ER model mapping to access application data. The existing functionality of the ER framework allows you to configure access to application tables for getting records from them by using the ER data source of the Table records type. When the accessing table is a table in which data is saved without a company identifier (shared table), this ER data source will return all records from this table. When the accessing table is a table in which data is saved per company (company dependent table), this data source will return the only records that have been saved for the current company (a company under which context this ER format is executing).

Recently introduced functionality implemented the cross-company concept for data access in application tables by using ER data sources of the Table records type. Each data source of the Table records type in a model mapping can be now marked as Cross company one. 

  -	If you do this for a data source that refers to any shared table except the CompanyInfo one, such data source will return all records that exist in the referred table (as it previously worked).
  -	If you do this for a data source that refers to the CompanyInfo table, even though the CompanyInfo table is a shared one, such data source will return the only records that contain an identifier of a company from the defined scope.
  -	If you do this for any company dependent table, such data source will return the only records of the referred table that contain an identifier of a company from the defined scope.

For each marked as Cross company data source user can manually select desire companies on the system query dialog form when the Ask for query option is turned on for this data source. The Company range tab can be used for that. Multi-company selection is supported.
Be aware that, like any other filters, the company filter will be persisted as a last used value for such query when you run an ER format. It will not be changed automatically if you changed the Cross company option’s value for a data source. Delete corresponding user-specific selection to start using a new Cross company option’s value of a data source.
For each marked as Cross company data source the list of desired records can be selected by using built-in functions FILTER and WHERE in ER expressions. As a company identifier, the dataAreaID field can be used for that as well.
Note that currently the limited type of conditions with the dataAreaID field are supported for FILTER function: 

  -	only conditions with a single dataAreaID field comparison are supported;
  -	only comparisons with expressions that do not depend on records list items are allowed.

Therefore, the following expression will be valid:

      FILTER (MyTable, MyTable.dataAreaID = $StringUserInputParameter)
      While shown below expressions will not pass the validation:
      FILTER (MyTable, MyTable.dataAreaID = MyTable2RecordsList.MyField)
      FILTER (MyTable, 
              OR(
                  MyTable.dataAreaID = $StringUserInputParameter1,
                  MyTable.dataAreaID = $StringUserInputParameter2
                    )
                   )

By default, the scope includes all companies of the current application. This default scope can be restricted. To restrict the scope of cross-company data access for a single ER format, you can assign for such format a specific Organization hierarchy.

  -	When a hierarchy is defined for an ER format, while this format will call cross-company data sources of the using ER model mapping the only records for legal entities that are presented in the assigned hierarchy will be returned to this format.
  -	When a reference to non-existing any longer hierarchy is defined for an ER format, the default scope will be applied while this format will call cross-company data sources - records for all application companies will be returned in this case. 

Note that when the Use draft option is turned on for the assigned to a single ER format hierarchy, the legal entities from the draft version of this hierarchy will be used to identify the scope for cross-company data sources. If it does not exist, the legal entities from the last published version of this hierarchy will be used for this.
Note that when the Use draft option is turned off for the assigned to a single ER format hierarchy, the legal entities from the last published version of this hierarchy will be used to identify the scope for cross-company data sources. Date effectiveness of hierarchies is not supported yet in the ER framework.
Note that the hierarchy can be assigned to an ER format in a dedicated for that form. To access this form, the Maintain legal entity filters for formats privilege must be grated to a user who is assigned to do this.
Note that the hierarchy based legal entities’ scope restriction for the executing ER format is applied in addition to the restriction that can be manually specified by the user on the system query dialog form. The intersection of these restrictions will be used during the ER format execution.
To learn more about this feature, play the task guide ER Access data tables in cross-company mode (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk through how ER model mapping and ER format can be configured to access application tables in cross-company mode.
Download the following files to complete the task guide mentioned above.

Title	File name
ER model configuration	CrossCompanyDataAccessModel.xml 

ER format configuration	CrossCompanyDataAccessFormat.xml 


