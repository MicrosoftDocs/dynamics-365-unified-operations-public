---
# required metadata

title: Set up an alternate dataflow for recommendations
description: This article describes how to configure an environment using an alternate dataflow to provide data to the recommendations service. 
author: bebeale
ms.date: 07/26/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Set up an alternate dataflow for recommendations

[!include [banner](includes/banner.md)]

This article describes how to configure an environment using an alternate dataflow to provide data to the recommendations service. 

![Overview of how the alternate dataflow will fit into the environment](media/alternate-flow.png)

## Assumptions

- This document assumes you have already enabled the recommendations service for your environment. For more information, see [Enable product recommendations](enable-product-recommendations.md).
- When working with files and folders in the Microsoft Azure Data Lake storage account:
    - You can use either the Azure web portal interface or the the Azure Storage Explorer application.
    - The starting points for working with files and folders is in the container named **dynamics365-financeandoperations** that is located under the folder that is named to match your environment URL. 
    - If your sandbox environment name is **MyUAT**, then the environment base URL would be `myuat.sandbox.operations.dynamics.com`. 
    - If you have more than one environment connected to the same storage account, each environment will have its own root folder.

## Prerequisites

The following prerequisites must be met to implement the alternate dataflow approach.

### Set up Microsoft Power Platform

For instructions on setting up Microsoft Power Platform, see [Enable the Microsoft Power Platform integration](../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).

### Install the Export to Data Lake add-in

To install the Export to Data Lake add-in, follow the instructions in [Install Export to Azure Data Lake add-in](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md).

> [!NOTE]
> Make notes of these values. They will be needed later during the configuration steps.

### Configure tables to export in Dynamics 365

Table syncing from Dynamics 365 to Azure Date Lake Store is managed in the **Export to Data Lake** form. The form doesn't currently have a menu item so a user must be in the **System Administrator** security role to open it. 

To configure tables to export in Dynamics 365, follow these steps.

1. To open the form, add the string `?mi=DataFeedsDefinitionWorkspace` to the environment's base URL, as shown in the following example: 

    `https://<environment-URL>/?mi=DataFeedsDefinitionWorkspace`

1.	Open the **Export to Data Lake** form and copy the list of tables [from *Table 1* in the Appendix](set-up-alternate-data-flow.md#appendix) of this document.
2.	On the **System Name** column, expand the filter options drop-down list. 
3.	Choose ```is one of``` for the filter type and place your cursor in the text box and paste in the table list.
4.	At the bottom of the filter drop-down list, select **Apply** .
5.	Select all rows in the grid, then select **Activate**

> [!NOTE]
> Ensure that all rows update to the status of **Running** before proceeding to the next step. Troubleshoot and resolve any errors before proceeding.


### Create a Synapse Workspace if you don't already have one

Follow the QuickStart guide here: [Quickstart: create a Synapse workspace](/azure/synapse-analytics/quickstart-create-workspace)

To keep your Azure resources organized, it's advised to put the ADLS storage account and synapse workspace together in a resource group in Azure.
You can reuse the storage account you created when you installed the Export to Data Lake Add-in.

## Create a Database in Synapse for Recommendations Data Processing

Using the CDM Utility Console Application (CDMUtil_ConsoleApp) creates a database in your Synapse workspace and populates it from the CDM tables manifest in your data lake. It's recommended to use the CMD Utility in a development environment with your database (in case there are any extensions). 

> [!NOTE] 
> The steps below assume no extension data is added to the RetailSales cube.

### Steps

1. Follow the steps and download the CDMUtilConsoleApp.zip file from the [Dynamics-365-FastTrack-Implementation-Assets GitHub](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution#2-cdmutil-console-app).
2. Extract the zip into a local folder.
3. Open ```CDMUtil_ConsoleApp.dll.config``` file in a text editor and update these values.
   1. Set the Tenant ID (azure tenant id).
   2. Set the Access key (access key to storage account for data lake).
       1. In the Azure portal, open the storage account. In the menu on the left side of the page, select **Access keys**. 
       2. Click Show keys on the top of the page.
       3. Click on the copy icon for one of the two key fields and paste it into the config file between the double quotes.
   3. Set the ```ManifestURL``` to the URL of your ```Tables.manifest.cdm.json``` file in ADLS
       1. In the Azure portal, browse the file, click on the 3 dots on the right side of the view and click Properties. The first property in the overview tab is the URL. Copy it and paste it into the config file between the double quotes.
   4. Set the ```TargetDbConnectionString``` to the connection string for the Built-in serverless SQL pool of your Synapse workspace.
       1. In the Synapse workspace open the Manage tab: 
          1. Select SQL pools in the submenu. 
          2. Select the name **Built-in** to view its properties.
          3. In the properties dialog box, select the ADO.NET connection type you want to use and then copy the connection string value and paste it into the config file between the double quotes. 
      > [!NOTE]
      > The user must have permission to create databases. For ease of use you might want to use the builtin admin login ```sqladminuser```.
  5. Next, Uncomment the ```ProcessEntities``` node and set it to **true**.
      1. ```<add key="ProcessEntities" value ="true"/>```
  6. Save and close the ```CDMUtil_ConsoleApp.dll.config``` file.
  7. Copy in ```EntityList.json``` to the ```/Manifest``` directory
  8. In a command prompt window run ```cdmutil_consoleapp.exe```.

> [!NOTE]
> When reviewing the output there should be 35 Entities/Views and at least 75 tables and no errors.

## Prepare the Data Lake RetailSales Aggregate Measurements directory

### Back up your current RetailSales cube data from the Data Lake

The easiest way to do this is to rename the RetailSales folder in the data lake. 
Rename it to ```RetailSales-backup```, or something similar. This preserves the existing data in case troubleshooting is required later.

#### The RetailSales cube folder is here: 

```
<storage-account>
  /dynamics365-financeandoperations
    /<environment-url> (example: myuat.sandbox.operations.dynamics.com)
      /AggregateMeasurements
        /RetailSales
```

### Create a New RetailSales folder and upload the model file

In the data lake:

1.	Create a new empty folder named RetailSales.
2.	Upload the model.json file to the directory.

## Create a Pipeline to Copy the RetailSales Cube Data

The pipeline will read the RetailSales cube views and export the data to csv files in the data lake.

### Steps

1.	Select the integrate tab in the Synapse workspace.
1.	Click the ```+``` icon and select import from pipeline template.
1.	Download and Select the [ExportRetailSalesCubeViews.zip file](https://aka.ms/reco-alternate-dataflow-files).
1.	Select your SQL database linked service.
1.	Select your storage account linked service.
1.	Open the **CopyData** task and change the folder property to be the `<environment_name>/...`.

### Test execution of the pipeline

It's recommended to test the pipeline using only one view. The **RetailSales_RetailMediaTemplateView** view works well as it usually contains fewer than 10 rows.

## Schedule the pipeline to run on a recurring schedule

Every time the pipeline runs, Azure consumption occurs. It's recommended to schedule executions at intervals of 48 hours or longer. You can always execute the pipeline manually if you need to sync data immediately. 
 
## Appendix

### Table list for syncing from Dynamics 365 to ADLS

This list of tables is a subset of all tables needed for the whole RetailSales cube. Only 15 of the views in the RetailSales cube are used by the Recommendations Service and the list of tables needed was filtered accordingly.

#### Retail Sales Cube Table

|Table 1|
| --- |
|BICalendarOffsets <br>
BIDateDimension <br>
BIDateDimensionValue <br>
Catalog <br>
CatalogProduct <br>
CatalogProductCategory <br>
CustInvoiceJour <br>
CustInvoiceTrans <br>
CustTable <br>
DataArea <br>
DimensionAttributeValueCombination <br>
DimensionAttributeValueSet <br>
DirPartyTable <br>
EcoResCategory <br>
EcoResCategoryHierarchy <br>
EcoResCategoryHierarchyRole <br>
EcoResColor <br>
EcoResConfiguration <br>
EcoResProduct <br>
EcoResProductCategory <br>
EcoResProductTranslation <br>
EcoResSize <br>
EcoResStyle <br>
HcmWorker <br>
InventDim <br>
InventDimCombination <br>
InventItemGroup <br>
InventItemGroupItem<br>
InventItemSetupSupplyType<br>
InventTable<br>
InventTrans<br>
LogisticsAddressCountryRegion<br>
LogisticsAddressCountryRegionTranslation<br>
LogisticsLocation<br>
LogisticsPostalAddress<br>
OMHIERARCHYPURPOSE<br>
RetailAssortmentLookup<br>
RetailAssortmentLookupChannelGroup<br>
RetailChannelProfile<br>
RetailChannelProfileProperty<br>
RetailChannelTable<br>
RetailChannelTableExt<br>
RetailConnDatabaseProfile<br>
RetailCustInvoiceJourTable<br>
RetailCustTable<br>
RetailMediaTemplate<br>
RetailOfflineProfile<br>
RetailPeriodicDiscount<br>
RetailRecoListConfigurationParameters<br>
RetailSalesTaxOverrideGroup<br>
RetailSharedParameters<br>
RetailSpecialCategoryMember<br>
RetailTenderTypeCardTable<br>
RetailTenderTypeTable<br>
RetailTerminalTable<br>
RetailTmpProductMedia<br>
RetailTransactionDiscountTrans<br>
RetailTransactionPaymentTrans<br>
RetailTransactionPaymentTransExt<br>
RetailTransactionSalesTrans<br>
RetailTransactionSalesTransExt<br>
RetailTransactionTable<br>
SalesLine<br>
SalesTable<br>
SystemParameters<br>
RETAILCATALOGINTERNALORG <br>
RETAILGROUPMEMBERLINE<br>
RETAILINTERNALORGANIZATION<br>
RETAILSPECIALCATEGORYPRODUCT<br>
RETAILPRODUCTCATEGORY<br>
ECORESCONFIGURATION<br>
DIMENSIONATTRIBUTE<br>
DIMENSIONATTRIBUTEVALUESET<br>
DIMENSIONHIERARCHY<br>
DIMENSIONHIERARCHYINTEGRATION <br>
DIMENSIONHIERARCHYLEVEL <br>
DIMENSIONPARAMETER <br>
OMExplodedOrganizationSecurityGraph |

### View list for parameter to pass into the Synapse Pipeline

This is a comma separated list of RetailSales cube views. This is the list of views the pipeline will perform a ‘select’ operation on and copy the results to the data lake. 

> [NOTE]
> The Pipeline parameter must be a list of view names separated by a coma with no spaces or line feeds.

```
RetailSales_RetailAssortmentRulesView,RetailSales_RetailChannelNavigationHierarchiesView,RetailSales_RetailChannelNavigationHierarchyCatalogProductsView,RetailSales_RetailChannelNavigationHierarchyCategoryNodesView,RetailSales_RetailChannelNavigationHierarchyCategoryProductsView,RetailSales_RetailMediaBaseUrlChannelView,RetailSales_RetailMediaRelativeUrlProductView,RetailSales_RetailMediaTemplateView,RetailSales_RetailOptOutCustomersView,RetailSales_RetailProductCategory,RetailSales_RetailProductTransaction,RetailSales_RetailProductVariantDimensionsView,RetailSales_RetailRecoListConfigurationParametersView,RetailSales_RetailRecoListsSharedParametersView,RetailSales_RetailEcoResProductTranslation|
```

### Environment specific fixes

#### [RETAILCHANNELVIEW]

This view has a hardcoded integer in it that represents a ‘retail channel’ type of organization.  
The actual value of the type can change from environment to environment or at least from tenant to tenant.

```
CREATE OR ALTER   VIEW [dbo].[RETAILCHANNELVIEW]
AS
SELECT T1.RECID AS RECID1,
       T1.STOREAREA AS STOREAREA,
       T1.OMOPERATINGUNITID AS OMOPERATINGUNITID,
       T1.DEFAULTCUSTACCOUNT AS DEFAULTCUSTOMER,
       T1.RETAILCHANNELID AS RETAILCHANNELID,
       T1.CHANNELTYPE AS CHANNELTYPE,
       T1.PARTITION AS PARTITION,
       T1.RECID AS RECID,
       T2.OMOPERATINGUNITNUMBER AS OMOPERATINGUNITNUMBER,
       T3.NAME AS NAME
FROM   dbo.RETAILCHANNELTABLE AS T1 CROSS JOIN dbo.DIRPARTYTABLE AS T2 CROSS JOIN dbo.DIRPARTYTABLE AS T3
WHERE  ((((T1.OMOPERATINGUNITID = T2.RECID)
          )
         AND ((T2.RECID = T3.RECID)
              ))
        AND T2.INSTANCERELATIONTYPE IN (8363));
```
To fix this use SSMS attached to the synapse database.
1.	In Dynamics 365, look up the **ChannelID** for your online channel.
2.	Run this query and copy the value from the first column, ```INSTANCERELATIONTYPE```, and paste it into ```the view definition```

```
select INSTANCERELATIONTYPE, NAME, NAMEALIAS, * from dbo.DIRPARTYTABLE where RECID IN (select OMOPERATINGUNITID from dbo.RETAILCHANNELTABLE where RETAILCHANNELID = <channelID>)
```

### Troubleshooting

#### Pipeline task fails

There should be 15 pipeline task executions for CopyData. If any of them fail, you will need to validate that all the dependent SQL objects exist and the queries execute. To get to all the dependencies, it is easiest to use SSMS to connect to the database.  You can then right click on a view and select Generate CREATE as to a new window’
Example error message text includes: 
- Error: Failure happened on 'Source' side
- Error handling external file: 'Max errors count.   
- /RetailSales/RetailSales_xxxxxx

##### Example scenario

As an example, let’s consider the RetailSales_RetailProductCategory task fails with an error ‘max errors count’
1.	Using the ```EntityList.json``` file, open it in a text editor (Visual studio code is good for this).
2.	Find the view definition for``` RetailSales_RetailProductCategory```


```
CREATE  VIEW [dbo].[RetailSales_RetailProductCategory] AS SELECT 0 AS ROW_UNIQUEKEY ,CATEGORY AS CATEGORYID ,PRODUCT AS PRODUCTID ,PRODUCTNAME ,CATEGORYNAME ,PARENTCATEGORY AS PARENTCATEGORYID ,PARTITION ,RECID FROM RetailProductCategoryView
```

3.	This view depends on only 1 other view: ```RetailProductCategoryView```
4.	Find the view definition for ```RetailProductCategoryView```.


```
CREATE VIEW [DBO].[RETAILPRODUCTCATEGORYVIEW] AS SELECT T1.CATEGORY AS CATEGORY, T1.PRODUCT AS PRODUCT, T1.PARTITION AS PARTITION, T1.RECID AS RECID, T2.PRODUCTNAME AS PRODUCTNAME, T2.PARTITION AS PARTITION#2, T3.NAME AS CATEGORYNAME, T3.PARENTCATEGORY AS PARENTCATEGORY, T3.PARTITION AS PARTITION#3 FROM RETAILPRODUCTCATEGORY T1 CROSS JOIN ECORESPRODUCTTRANSLATIONS T2 CROSS JOIN RETAILCATEGORYEXPANDED T3 WHERE((( T1.PRODUCT = T2.PRODUCT) AND ( T1.PARTITION = T2.PARTITION)) AND (( T1.CATEGORY = T3.RECID) AND ( T1.PARTITION = T3.PARTITION)))

```

5.	This view depends on 3 other views: ```RETAILPRODUCTCATEGORY```, ```ECORESPRODUCTTRANSLATIONS```, ```RETAILCATEGORYEXPANDED```
6.	Find the definitions for each of these views and list their dependencies.  Continue this until you find all the dependent views.
7.	In this example here is the whole list in dependency tree order. There are 13 views that need to be validated.

- RetailSales_RetailProductCategory
   - RetailProductCategoryView
      - RETAILPRODUCTCATEGORY
         - ECORESPRODUCTCATEGORY
         - ECORESCATEGORYHIERARCHYROLE
         - RETAILSPECIALCATEGORYPRODUCT
            - ECORESPRODUCT
            - RETAILGROUPMEMBERLINE
            - RETAILSPECIALCATEGORYMEMBER
      - ECORESPRODUCTTRANSLATIONS
         - ECORESPRODUCT
         - ECORESPRODUCTTRANSLATION
         - SYSTEMPARAMETERS
      - RETAILCATEGORYEXPANDED
         - ECORESCATEGORY
         - ECORESCATEGORYHIERARCHYROLE


8.	Now a quick copy and paste using excel you can create 13 select count(*) from <view_name> statements.  Run these in SSMS with results to text and you can scroll through the results to see if any of the views failed. The initial error suggests that at least one of them will

 ```
select count(*) from	RetailProductCategoryView
select count(*) from	RETAILPRODUCTCATEGORY
select count(*) from	ECORESPRODUCTCATEGORY
select count(*) from	ECORESCATEGORYHIERARCHYROLE
select count(*) from	RETAILSPECIALCATEGORYPRODUCT
select count(*) from	ECORESPRODUCT
select count(*) from	RETAILGROUPMEMBERLINE
select count(*) from	RETAILSPECIALCATEGORYMEMBER
select count(*) from	ECORESPRODUCTTRANSLATIONS
select count(*) from	ECORESPRODUCTTRANSLATION
select count(*) from	SYSTEMPARAMETERS
select count(*) from	RETAILCATEGORYEXPANDED
select count(*) from	ECORESCATEGORY
```

9.	A technique to validate what you are looking at, you can create  a root dependent view to generate the view definition in SSMS and verify there is a data lake file column named ```r.filepath```. That indicates the view you are looking at is reading data from the data lake.



## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Opt out of personalized recommendations](personalization-gdpr.md)

[Add product recommendations on POS](product.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)




[!INCLUDE[footer-include](../includes/footer-banner.md)]
