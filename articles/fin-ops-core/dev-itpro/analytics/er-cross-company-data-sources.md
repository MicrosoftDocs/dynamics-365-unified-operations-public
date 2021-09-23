---
# required metadata

title: Cross-company data sources in Electronic reporting (ER)
description: This topic explains how you can use cross-company data sources in Electronic reporting (ER).
author: NickSelin
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERModelMappingDesigner, ERFormatMappingLegalEntityFilterTable
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0

---

# Cross-company data sources in Electronic reporting (ER)

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to generate outgoing documents in various formats. When a document is generated, an ER format calls data sources that were configured in a corresponding ER model mapping. To configure access to application tables for record retrieval, you can use ER data sources of the **Table records** type. When the accessing table is a shared table (that is, a table where data is saved without a company identifier), this data source returns all records. When the accessing table is a company-dependent table (that is, a table where data is saved per company), this data source returns only the records that have been saved for the current company (that is, the company context that the ER format is running under).

Every data source of the **Table records** type in a model mapping can be now marked as a cross-company data source. Therefore, you can use data sources of the **Table records** type to access cross-company data in application tables.

If you mark a data source as cross-company, the following behavior occurs:

- For a data source that refers to any shared table except CompanyInfo, the data source returns all records that exist in the referenced table. 
- For a data source that refers to the CompanyInfo table, even though CompanyInfo is a shared table, the data source returns the records that contain the identifier of a company from the defined scope.
- For any company-dependent table, the data source returns the records of the referenced table that contain the identifier of a company from the defined scope.

In the system query dialog box, when the **Ask for query** option is turned on for any data source that is marked as cross-company, you can manually select one or more companies to include on the **Company range** tab.

> [!IMPORTANT]
> Like other filters, the company filter is persisted as a last-used value for queries when you run an ER format. The filter isn't automatically changed if you change the cross-company value for a data source. To use a different cross-company value for another data source, delete the corresponding user-specific selection.

For every data source that is marked as cross-company, you can select the records that you want by using the **FILTER** and **WHERE** functions in ER expressions. The **dataAreaID** field can also be used as a company identifier. Currently, the **dataAreaID** field is limited to the following types of conditions when the **FILTER** function is used:

- Only conditions that have a single **dataAreaID** field comparison are supported.
- Only comparisons that have expressions that don't depend on records list items are allowed.

Therefore, the following expression is valid.

```ER Expression
FILTER (MyTable, MyTable.dataAreaID = $StringUserInputParameter)
While shown below expressions will not pass the validation:
FILTER (MyTable, MyTable.dataAreaID = MyTable2RecordsList.MyField)
FILTER (MyTable, 
    OR(
        MyTable.dataAreaID = $StringUserInputParameter1,
        MyTable.dataAreaID = $StringUserInputParameter2
    )
)
```

By default, the scope includes all companies of the current application. However, it can be restricted. To restrict the scope of cross-company data access for a single ER format, assign a specific organization hierarchy to the format. When a hierarchy is defined for an ER format, only records for legal entities that are presented in the assigned hierarchy are returned, even though the format calls cross-company data sources. When a reference to a hierarchy that no longer exists is defined for an ER format, the default scope is applied, and the format calls cross-company data sources. In this situation, records for all application companies are returned.

Note that when the **Use draft** option is turned on for the assigned to a single ER format organization hierarchy, the legal entities from the draft version of this hierarchy will be used to identify the scope for cross-company data sources. If the draft version does not exist, the legal entities from the last published version of this organization hierarchy will be used for this.

Note that when the **Use draft** option is turned off for the assigned to a single ER format organization hierarchy, the legal entities from the last published version of this organization hierarchy will be used to identify the scope for cross-company data sources. Date effectiveness of organization hierarchies is not supported yet in the ER framework.

The hierarchy can be assigned to a format in a specific page that can be accessed from the ER workspace or by using the **Organization administration \> Electronic reporting \> Legal entity filter for formats** menu item. To access the page, the **Maintain legal entity filters for format** privilege (ERMaintainFormatMappingLegalEntityFilters) must be granted to a user. The scope restriction of hierarchy-based legal entities for the format is applied in addition to the restriction that the user can manually specify in the system query dialog box. The intersection of these restrictions is used when the format is run.

To learn more about this feature, play the task guide, **ER Access records of company dependent tables in cross-company mode**, which is part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process, and can be downloaded from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684). This task guide walks you through the process of configuring an ER model mapping and ER format to access application tables in cross-company mode.

Download the following files to complete the task guide:

- [ER model configuration - CrossCompanyDataAccessModel.xml](https://download.microsoft.com/download/4/2/5/4258f891-7054-4821-aedd-3721ba25fdd5/CrossCompanyDataAccessModel.xml)
- [ER format configuration - CrossCompanyDataAccessFormat.xml](https://download.microsoft.com/download/3/2/1/321deb75-3ba9-4323-99bf-207a52c60b5c/CrossCompanyDataAccessFormat.xml)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
