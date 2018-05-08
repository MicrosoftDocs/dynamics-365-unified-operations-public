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

You can design Electronic reporting (ER) formats to generate outgoing documents in various formats. When a document is generated, data sources that were configured in a corresponding ER model that maps to access application data are called. You can configure access to application tables for record retrieval by using the ER data source type, **Table records**. When the accessing table is a shared table, or a table that saves data without a company identifier, this data source will return all records. When the accessing table is a company dependent table, or a table where data is saved per company, this data source will return the only records that have been saved for the current company, the company under which context this ER format is executing.

Each data source of the **Table records** type in a model mapping can be now marked as cross-company. This means that you can use the **Table records** type data source to access cross-company data in application tables. 
If you choose to mark a data souce as cross-company, the following will apply:

  -	For a data source that refers to any shared table, except for **CompanyInfo**, the data source will return all records that exist in the referred table. 
  -	For a data source that refers to the **CompanyInfo** table, even though the CompanyInfo table is shared, the data source will return the records that contain the identifier of a company from the defined scope.
  -	For any company dependent table, the data source will return the records of the referred table that contain an identifier of a company from the defined scope.

For each data source that is marked as **cross-company**, on the system query dialog form, when the **Ask for query** option is turned on for this data source, you can manually select one or more companies to include on the **Company range** tab.

  >[!IMPORTANT]
  >Similar to other filters, the company filter will be persisted as a last-used value for queries when you run an ER format. The filter will not change automatically if you change the cross-company value for a data source. To use a different cross-company value for another data source, delete the corresponding user-specific selection.
  

For each data source that is marked as **cross-company**, you can select the records that you want by using the **FILTER** and **WHERE** functions in ER expressions. As a company identifier, the **dataAreaID** field can be used for that as well.
At this time, the **dataAreaID** field is limited to the following types of conditions when using the FILTER function: 

  -	Only conditions with a single **dataAreaID** field comparison are supported.
  -	Only comparisons with expressions that do not depend on records list items are allowed.

This means that the folloiwng expression is valid:

      FILTER (MyTable, MyTable.dataAreaID = $StringUserInputParameter)
      While shown below expressions will not pass the validation:
      FILTER (MyTable, MyTable.dataAreaID = MyTable2RecordsList.MyField)
      FILTER (MyTable, 
              OR(
                  MyTable.dataAreaID = $StringUserInputParameter1,
                  MyTable.dataAreaID = $StringUserInputParameter2
                    )
                   )

By default, the scope includes all companies of the current application, but it can be restricted. To restrict the scope of cross-company data access for a single ER format, assign a specific organization hierarchy to the format. When a hierarchy is defined for an ER format, only records for legal entities that are presented in the assigned hierarchy will be returned even though this format calls cross-company data sources. When a reference to a hierarchy that no longer exists is defined for an ER format, the default scope will be applied and the format will call cross-company data sources. In this situation, records for all application companies will be returned. 
The hierarchy can be assigned to a format for a specific form. To access the form, the **Maintain legal entity** filters for format privilege must be granted to a user. The scope restriction of hierarchy-based legal entities’ for the format is applied in addition to the restriction that can be manually specified by the user on the **System query dialog** form. The intersection of these restrictions will be used during the format execution.

To learn more about this feature, play the task guide, ER - Access data tables in cross-company mode (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk through how ER model mapping and ER format can be configured to access application tables in cross-company mode.
Download the following files to complete the task guide.

[ER model configuration] (CrossCompanyDataAccessModel.xml) 

[ER format configuration]	(CrossCompanyDataAccessFormat.xml)

