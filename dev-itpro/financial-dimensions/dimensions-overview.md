---
# required metadata

title: Add dimensions to a Excel template | Microsoft Docs
description: This topic provides information about dimensions, dimensions that have entities, and the dimension controls that are available.
author: twheeloc
manager: AnnBe
ms.date: 2015-10-29 18:19:57
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 11314
ms.assetid: c7a7332b-e852-4ae0-a0cc-8c6dd9f2b102
ms.region: Global
# ms.industry: 
ms.author: rbrow

---

# Add dimensions to a Excel template

This topic provides information about dimensions, dimensions that have entities, and the dimension controls that are available.

The only value that is present on Microsoft Excel templates after installation is the MainAccount. This is the only dimension that all customers will have. To add the dimensions to Microsoft Excel templates you need to complete the following steps:

1.  Add dimensions to the DimensionCombinationEntity or the DimensionSet entity.
2.  Add the dimensions to each template where you want dimensions in separate columns. For more information, see [Create open in Excel experiences](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/office-integration/off101-office-integration-enable-users-to-edit-data-in-excel).
3.  Publish the template.

This topic shows how to modify DimensionCombinationEntity to enable the dimensions in columns for Excel. The same steps can be used to modify the DimensionSet entity. **Note:**  This information is subject to change for each release. Therefore, be sure to check back frequently for the most up-to-date information.

## Add dimensions  Dynamics 365 for Operations (version 1611, build 7.1.1541.3036+, November 2016)
Modifying the **DimensionCombinationEntity** has been greatly simplified in Dynamics 365 for Operations with the release of the Add financial dimensions for OData Addin in Visual Studio. 1. In Microsoft Visual Studio, click **Dynamics 365 **&gt; **Addins** &gt; **Add financial dimensions for Odata**.

![DimWiki1](./media/dimwiki1-300x233.png)

2. Type the name of the Financial dimension in the **Dimension name** column. This should be the exact name of the financial dimension as it is named in Dynamics 365 for Operations. Select the **Model** that has your extensions. It should be above the AppSuite layer.** **Click **Apply**. [![DimWiki2](./media/dimwiki2-300x225.png)](./media/dimwiki2.png)3. Compile the project, and then synchronize it with the database. ![8](./media/8-300x260.png) 4. Your customization is now completed. You can test it in SQL using the following statement.

    select * from DIMENSIONCOMBINATIONENTITY

## Add dimensions  before Dynamics 365 for Operations
To support interactions with dimensions as columns, for example, in the Microsoft Excel integration, you must first create the dimension columns through a customization. 1. Open the Application Explorer in Visual Studio (**View** &gt; **Application Explorer**). 2. Navigate to DimensionCombinationEntity **(AOT** &gt; **Data Model** &gt; **Data Entities**). 3. Right-click on the entity and choose **Customize**. [![5](./media/5-300x187.png)](./media/5.png)4. Open the designer for the entity that you want to modify, in this example **DimensionCombinationEntity**. 5. Create a new private static method that returns a str named **departmentValue**. 6. In this method, you must get the dimension's value from **DimensionAttributeValueCombination**. The final method will look something like this.

     /// <summary>
    /// This method returns the value of Department.
    /// </summary>
    private static str departmentValue()
    {
        Name dimensionName = 'Department';
        str sqlStatement;

        DimensionAttribute dimensionAttribute = DimensionAttribute::findByName(dimensionName);

        if (!dimensionAttribute)
        {
            sqlStatement = SysComputedColumn::returnLiteral('');
        }
        else
        {
            sqlStatement = strFmt('SELECT TOP 1 T1.%1 ', dimensionAttribute.DimensionValueColumnName);
        }

        return sqlStatement;
    }

7. Create a new "string unmapped field" on the entity:

-   Set the **Name** property to the dimension name, **Department**.
-   Set the **Extended Data Type** property to **DimensionValue**.
-   Set the **DataEntityView Method** property to the method that you created earlier (for example, **departmentValue**).
-   Set the **Label** property to the dimension name **Department**.

[![6](./media/6-300x64.png)](./media/6.png)8. Repeat steps 5-7 for each dimension that you want to add, changing the dimension name to the appropriate dimension. 9. Compile the project, and then synchronize it with the database. [![8](./media/8-300x260.png)](./media/8.png)10. Your customization is now completed. You can test it in SQL using the following statement.

    select * from DIMENSIONCOMBINATIONENTITY

 

See also
--------

[Dimension Entry control migration walkthrough](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-migration)

[Dimension Entry control uptake](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-uptake)

[What’s new or changed](https://docs.microsoft.com/en-us/dynamics365/operations/core/organization-administration/whats-new-or-changed-in-dynamics-ax-7)

