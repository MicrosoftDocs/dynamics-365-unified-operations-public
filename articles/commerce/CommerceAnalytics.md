---
# required metadata

title: Commerce Analytics (Preview)
description: This topic details installation and usage of analytics capability in  Dynamics 365 Commerce. 
author: AamirAllaq
ms.date: 11/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: aamiral
ms.search.validFrom: 2021-11-11
ms.dyn365.ops.version:

---

# Commerce Analytics (Preview)

[!include [banner](includes/banner.md)]

This topic describes functional analytics capability included within Commerce Analytics for Dynamics 365 Commerce as well as installation steps to enable this capability. 

## Commerce Analytics (Preview) system architecture
### Key components
Commerce Analytics is composed of the following key components:

1. Ready to use interactive Power BI reports
2. SQL views in Azure Synapse Analytics
3. Entity & Ontology data in Azure Data Lake
4. Raw data in Azure Data Lake

![image](https://user-images.githubusercontent.com/43016803/141214066-3314d8b8-4644-4f26-a703-b4c838d50aad.png)

### Data flow
#### Step 1: Data generation
Data originates either as transactional or behavioral data from one of the following sources:
1.	Call center associate using Commerce HQ client to process sales orders
2.	Cashier at Point-of-Sale processing sales transactions
3.	Sales created within custom applications using Headless Commerce (Commerce Scale Unit)
4.	E-commerce shopper browsing your E-commerce website 
5.	E-commerce shopper placing an order on your E-commerce website
6.	Data produced by other systems such as Dynamics 365 Connected Spaces

#### Step 2: Ingestion & Pre-processing
Transactional data makes its way to Commerce HQ, either directly (in case of orders captured directly in Commerce HQ client), or via Commerce Scale Unit (in case of Commerce orders captured at POS, E-commerce or custom clients using Headless Commerce). 
Transactional data is then copied over to your data lake as raw data and stored within the Tables folder, via Export to Datalake feature. 
E-commerce web activity data is sent directly to the data lake.
Data produced by other systems such as Dynamics 365 Connected Spaces is also sent to the data lake by other systems directly.

#### Step 3: Transformation & Aggregation
Once raw data is in the data lake, Commerce Analytics service reads the data, transforms & aggregates it, and writes it back to the data lake in the form of logical entities (within Entities folder) and aggregated metrics (within Ontologies folder) 

#### Step 4: Querying
Data in the lake is queried via a T-SQL interface by using Azure Synapse Analytics. This interface includes SQL views which allow for federated querying of data in the lake, either directly using a T-SQL client (for ad-hoc analysis) or through a visualization tool such as Power BI.

#### Step 5: Modeling & Serving
Data queried by Azure Synapse Analytics then makes its way to Power BI’s semantic model. Depending on the type of data, it is either imported in-memory into Power BI on a periodic basis or directly queried at run-time. 
The final stage is for the data to be rendered within Power BI visuals for users to view and interact with. 


## Commerce Analytics functional overview
### 1.	Summary
#### Top level filters
1.	Date Settings
    1.	Year
    2.	Quarter
    3.	Month
    4.	Week
    5.	Day
2.	Channel Settings
    1.	Legal entity
    2.	Channel type
    3.	Customer type
    4.	Sales type
    5.	Channel
    6.	Org hierarchy

3.	Product Settings
    1.	Category hierarchy
    2.	Category

#### a.	Product
1.	Sales
2.	Margin
3.	Returns

#### b.	Customer
1.	Sales
2.	Margin
3.	Returns

#### c.	Channel
1.	Sales
2.	Margin
3.	Returns

### 2.	Sales
1.	By Delivery location
2.	By Channel/Store/Terminal
3.	By Employee
4.	By Date
5.	By Hour
6.	By Product Category

### 3.	Margin
1.	By Delivery location
2.	By Product
3.	By Date

### 4.	Return
1.	Return by amount
    1.	By Store
    2.	By Product
    3.	By Date
2.	Return by transaction
    1.	By Store
    2.	By Product
    3.	By Date

### 5.	Discount
1.	By Store
2.	By Product
3.	By Date
4.	Decomposition
    1.	Legal entity
    2.	Store
    3.	Discount type
    4.	Discount name
    5.	Product

### 6.	Payment
1.	By Channel/Terminal
2.	By Payment method/Type
3.	By Date
4.	Decomposition
    1.	Legal Entity
    2.	Channel type
    3.	Store
    4.	Terminal
    5.	Payment method

### 7.	Customer
1.	Life-time value (LTV)

Life-time value is calculated based on total amount spent by a customer across all Dynamics 365 Commerce sales channels, including Point of Sale, E-commerce, Call center.

3.	Recency

Recency is calculated based on number of days since a customer's last transactional engagement with the organization. At this time, recency does not consider non-transactional engagement signals such as E-commerce browsing activity.

3.	Frequency

Frequency is calculated based on a customer's transactional engagement with the organization. At this time, frequency does not consider non-transactional engagement signals such as E-commerce browsing activity.

4.	Relationship length

Relationship length is calculated based on number of days since the customer record was created in the system. 

5.	Transaction count

### 8.	Comparison
1.	Product comparison By time period
    1.	Sales & Sales difference
    2.	Margin & Margin difference
2.	Customer By time period
    1.	Sales & Sales difference
    2.	Margin & Margin difference

### 9.	Web activity
#### Top level filters

1.	Date range
2.	Channel type
3.	Channel
4.	Category hierarchy

#### a.	Acquisition
1.	Page views
    1.	By Country
    2.	By Product
    3.	By User signed-in status
    4.	By Date
2.	E-commerce orders
3.	Conversion rate
    1.	By Date
4.	Conversion funnel
    1.	Page view by Page type (Home page, Category page, Product details page)
    2.	Add to cart
    3.	Checkout
    4.	Purchase

#### b.	Session
Session is defined as [TBD]
1.	By Country
2.	By Origin (External referrer)
3.	By User Signed-in status
4.	Session count
    1.	By Date
    2.	By Entry page
5.	Order per session
    1.	By Date
6.	Session bounce rate
    Session bounce is defined as a session where the user immediately leaves after visiting your E-commerce website. [TBD]
7.	Clicks per session

#### c.	Visitor
An anonymous visitor on your E-commerce site is determined based on a unique identifier within that specific browser on that specific device. Commerce Analytics does not track anonymous users across different browsers or devices. An anonymous user is identified as a unique visitor for a period of 365 days since the first visit. After 365 days, a new identifier is issued and the visitor is then tracked as a different visitor. 
For visitors who browse your E-commerce site while signed-in, Commerce Analytics is able to provide additional information based on your existing relationship with these users based on purchases such users may have made with your organization, across all Dynamics 365 Commerce sales channels (including Point of Sale, Call center, E-commerce), such as Recency, Relationship Length, Lifetime Value & Frequency

1.	Visitor margin
2.	Visitor average orders
3.	Visitor average sales
4.	E-commerce visitor count
    1.	By Date
    2.	By Location
    
        At this time, Commerce Analytics can only provide country level granularity for location insights for E-commerce visitors. 
    
    3.	By Recency
    
        Recency is calculated based on number of days since a customer's last transactional engagement with the organization. At this time, recency does not consider non-transactional engagement signals such as E-commerce browsing activity.
    
    4.	By Relationship length

        Relationship length is calculated based on [TBD]
    
    5.	By Lifetime value (LTV)

        Life-time value is calculated based on total amount spent by a customer across all Dynamics 365 Commerce sales channels, including Point of Sale, E-commerce, Call center.

    6.	By Frequency
        
        Frequency is calculated based on a customer's transactional engagement with the organization. At this time, frequency does not consider non-transactional engagement     signals such as E-commerce browsing activity.


#### d.	Impression
Impression is defined as each viewing of a Product visual by an E-commerce visitor. For instance, if an E-commerce visitor navigates to Home page of your website and views a Yoga mat product within  a “Top selling” list module, and also views the same Yoga mat product within a “Picks for you” list module, this would count as 2 product impressions. Currently impressions track product views within the following surfaces:
1.	Lists (Recommended, Top selling, Picks for you, Trending, etc.)
2.	Product Details page
3.	Cart module
4.	Search result container
5.	Category search result container
    
Products rendered within Carousel module or within custom visuals is not currently counted within Impressions metric.

Impression report page includes the following metrics
1.	Impression count
    1.	By Page Type & Module
    Page type is the generic page type defined for each page in your E-commerce website. This is defined/configured by [TBD]
    Module type defines the type of E-commerce visual module within which the product is shown.
    You may need to drill down in the Page & Module visual to view impressions by module
    2.	By Product
    3.	By User signed-in status
    4.	By Date
2.	Impression click count

    Impression click is defined as an E-commerce visitor clicking on a product visual, which typically navigates users to the Product Details Page for that product. 
3. Impression click-through rate (CTR)

    Click through rate is defined as the total number of impression clicks divided by the total number of impressions.

## Commerce Analytics (Preview) installation

> [!NOTE]
> **Commerce Analytics (Preview) ** is in preview in the United States, Canada, United Kingdom, Europe, South East Asia, East Asia, Australia, and Japan regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS). Before you can use this feature, see [Configure export to Azure Data Lake](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake)

### <a name="enableCommerceAnalytics"></a> Enable and Configure Commerce Analytics
To enable and configure Commerce Analytics, you will need to follow a series of steps as outlined below. These operations will require you to have permission to create resources in your Azure subscription as well as permission to install add in in your Lifecycle Services (LCS) project. If you don't have the necessary permissions, you will need assistance from someone in your organization with the required permissions.

The steps to enable and configure Commerce Analytics, are as follows:

1. [Join Microsoft Insider Program](#joinInsiderProgram)
2. [Enable and Configure Export to Data Lake](#enableExportToDataLake)
3. [Get Storage Account SAS token](#getSASToken)
4. [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts)
5. [Install and Configure Azure Synapse workspace](#configureAzureSynapse)
6. [Install PowerBI template application](#powerbi) 

### <a name="joinInsiderProgram"></a> Join Microsoft Insider Program
[TODO] TBD Content

### <a name="enableExportToDataLake"></a> Enable and Configure Export to Data Lake
The **Commerce Analytics** feature relies on the **Export to Data Lake** feature for exporting Finance and Operations app data to Azure Data Lake and keep the data fresh. Before you configure the Commerce Analytics feature, enable and configure the Export to Data Lake feature by following the steps outlined in [Configure export to Azure Data Lake](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake). When you configure the Export to Data Lake feature, make note of the following information, as you will need them in the subsequent steps.

1. The key vault secret names storing the application id, application secret. This is outlined in the [Add secrets to the key vault](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake#addsecrets) section in the Configure Export to Data Lake documentation.
2. The storage account name for the Azure Data Lake instance. This is outlined in the [Create a Data Lake Storage (Gen2) account in your subscription](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake#createsubscription) section in the Configure Export to Data Lake documentation.

### <a name="getSASToken"></a> Get Storage Account SAS token
> [!NOTE]
> There is a known limitation of Commerce Analytics Preview, where the Azure Synapse instance will lose access to the Data Lake when the SAS token expires. You should set the maximum expiration date allowed by your organization security policies, when you generate the SAS token. This limitation will be removed in Commerce Analytics General Availability, as we move to a more manageable authentication mechanism between Azure Synapse and Azure Data Lake, such as Managed Service Identity (MSI).

A Shared Access Signature (SAS) token enables external entities to access your storage account, with a specific set of privileges for a finite amount of time. Azure Synapse will use the SAS token to access the underlying data in the Azure Data Lake. The steps to generate a SAS token, are as follows:

1. Navigate to the storage account in Azure Portal, that you created while configuring Export to Data Lake feature, as outlined in the [Create a Data Lake Storage (Gen2) account in your subscription](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake#createsubscription).
2. Click on the `Shared access signature` option on the left options pane, under the storage account.
3. Select the following options on the SAS options page:

    | Option Name | Option Value |
    |-------------|--------------|
    | Allowed services | Select `Blob` |
    | Allowed resource types | Select `Service`, `Container` and `Object` |
    | Allowed permissions | Select `Read`, `Write`, `Delete`, `List`, `Add` and `Create` |
    | Blob versioning permissions | Select `Enables deletion of versions` |
    | Start and expiry date/time | Set an End date and time for the SAS token as appropriate. |
    | Allowed IP addresses | Leave blank |
    | Allowed protocols | Select `HTTPS only` |
    | Preferred routing tier | Select `Basic (default)` |
    | Signing key | Select `key1` or `key2` as appropriate |
4. Click on the `Generate SAS and connection string` button.
5. Copy value from the `SAS token` text box.

### <a name="downloadSynapseDeploymentScripts"></a> Download deployment scripts for Azure Synapse views
In order to create and publish the necessary views in Azure Synapse workspace, you will need to download and execute a set of scripts. The steps to download the scripts, are as follows:

1. The scripts are available in the the [microsoft/Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) Github repo.
2. To download the scripts to your local machine, you can either clone this repo, or download the repo as a zip file.
3. The necessary scripts are under the folder `/Pipeline/CommerceAnalyticsSynapse/`.

### <a name="configureAzureSynapse"></a> Install and Configure Azure Synapse workspace
The steps to install and configure an Azure Synapse instance, are as follows:

1. Install Azure Synapse workspace, in your Azure subscription, by following the steps outlined in [Quickstart: Create a Synapse workspace](https://docs.microsoft.com/en-us/azure/synapse-analytics/quickstart-create-workspace)
2. Open the `SetupSynapse.sql` script file in Notepad, from your local machine folder where you cloned or downloaded the Dynamics365Commerce.Solutions repo, as outlined in the [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts) section. The script file will be under `/Pipeline/CommerceAnalyticsSynapse/` folder. Edit the script to replace the following placeholder texts with values as indicated below:

   | Placeholder Text | Replacement Value |
   |------------------|-------------------|
   | placeholder_storageaccount | Replace with the name for the storage account that you created while configuring Export to Data Lake feature, as outlined in the [Create a Data Lake Storage (Gen2) account in your subscription](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake#createsubscription). |
   | placeholder_container | TODO |
   | placeholder_sastoken | Replace with the SAS token that you copied in the [Get Storage Account SAS token](#getSASToken) section. Make sure to remove the '?' in the beginning of the value. |
   | placeholder_password | Replace with a strong password of your choice. Make note of this password. |
3. Navigate to the new Azure Synapse workspace, in Azure Portal. Click on `Open Synapse Studio` option on the Overview page.
4. Copy the contents of `SetupSynapse.sql` that you updated in step 2. In Synapse Studio on Azure Portal, click on `New` > `SQL script`. Paste the contents into the SQL script editor in Synapse Studio.
5. Ensure that `Use database` is set to **master**. Click on the `Run` button to execute the script.
6. Ensure that the script executes successfully. Successful execution of the script will create the database for Commerce Analytics, credential for accessing the Azure Data Lake and a readonly user, which will be used by PowerBI to connect to the Azure Synapse instance.
7. On your local machine, open a PowerShell prompt in admin mode. Navigate to the folder where you cloned or downloaded the Dynamics365Commerce.Solutions repo, as outlined in the [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts) section.
8. Setup the PowerShell execution policy, by running the following command in the PowerShell window:
   ```powershell
   Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
   ```
9. Install the SQL Server PowerShell module, by running the following command in the PowerShell window:
   ```powershell
   Install-Module sqlserver
   ```
   **Note:** If you already have the SQL Server module installed, you may skip this step.
10. Publish the Azure Synapse views, by running the following command in the PowerShell window:
    ```powershell
    .\PublishSynapseViews.ps1 -serverName SERVER_NAME -password PASSWORD -storageAccount STORAGE_ACCOUNT -containerName CONTAINER_NAME -datarootpath DATA_ROOT_PATH
    ```
    The placeholder values in the command should be replaced as follows:

    | Placeholder Value | Replacement Value |
    |-------------------|-------------------|
    | SERVER_NAME | Replace with the name of the Azure Synapse Serverless SQL endpoint. |
    | PASSWORD | Replace with the password for the sqladminuser. |
    | STORAGE_ACCOUNT | Replace with the name of the Storage Account for the Azure Data Lake. |
    | CONTAINER_NAME | Replace with the name of the container [TODO] |
    | DATA_ROOT_PATH | Replace with the folder name under the container that contains all the data. [TODO] |

    **Note:** You can find the Storage Account name, Container name and the Data Root Path from the Azure Portal, by using the Storage browser on your Azure Data Lake storage account.

11. Ensure that the script executes successfully. Successful execution of the script will create the necessary views for Commerce Analytics, in the Azure Synapse serverless SQL instance.

### <a name="powerbi"></a> Install PowerBI template application
TBD

### <a name="privacy"></a> Privacy
TBD


[!INCLUDE[footer-include](../includes/footer-banner.md)]
