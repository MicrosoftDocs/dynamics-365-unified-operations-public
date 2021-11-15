---
# required metadata

title: Commerce analytics (Preview)
description: This topic details installation and usage of the analytics capability in  Dynamics 365 Commerce. 
author: AamirAllaq
ms.date: 11/15/2021
audience: Application user
ms.reviewer: sericks
ms.search.region: Global
ms.author: aamiral
ms.search.validFrom: 2021-11-12

---

# Commerce analytics (Preview)

[!include [banner](includes/banner.md)]

This topic describes and explains how to install Commerce analytics (Preview), the functional analytics capability included in Dynamics 365 Commerce. 

## Commerce analytics (Preview) system architecture
### Key components
Commerce analytics is composed of the following key components:

- Ready to use interactive Power BI reports
- SQL views in Azure Synapse Analytics
- Entity and ontology data in Azure Data Lake
- Raw data in Azure Data Lake

![System architecture of Commerce analytics](media/CommerceAnalytics.png)

### Data flow
#### Step 1: Data generation
Data originates either as transactional or behavioral data from one of the following sources:

- Call center associate using Commerce HQ client to process sales orders
- Cashier at point-of-sale processing sales transactions
- Sales created within custom applications using Headless Commerce (Commerce Scale Unit)
- E-commerce shopper browsing your e-commerce website 
- E-commerce shopper placing an order on your e-commerce website
- Data produced by other systems such as Dynamics 365 Connected Spaces

#### Step 2: Ingestion and pre-processing
Transactional data makes its way to Commerce HQ, either directly (in case of orders captured directly in Commerce HQ client) or via Commerce Scale Unit (in case of Commerce orders captured at POS, e-commerce or custom clients using Headless Commerce). 

Transactional data is then copied over to your data lake as raw data and stored within the Tables folder, via the export to data lake feature. E-commerce web activity data is sent directly to the data lake.

Data produced by other systems such as Dynamics 365 Connected Spaces is also sent to the data lake by other systems directly.

#### Step 3: Transformation and aggregation
Once raw data is in the data lake, the Commerce analytics service reads the data, transforms, aggregates it, and writes it back to the data lake in the form of logical entities (within the Entities folder) and aggregated metrics (within the Ontologies folder). 

#### Step 4: Querying
Data in the lake is queried via a T-SQL interface by using Azure Synapse Analytics. This interface includes SQL views which allow for federated querying of data in the lake, either directly using a T-SQL client (for ad-hoc analysis) or through a visualization tool such as Power BI.

#### Step 5: Modeling and serving
Data queried by Azure Synapse Analytics then makes its way to Power BI’s semantic model. Depending on the type of data, it is either imported in-memory into Power BI on a periodic basis or directly queried at run-time. 

The final stage is for the data to be rendered within Power BI visuals for users to view and interact with. 


## Commerce analytics functional overview
### 1.	Summary
#### Top level filters
1.	Date settings
    1.	Year
    2.	Quarter
    3.	Month
    4.	Week
    5.	Day
2.	Channel settings
    1.	Legal entity
    2.	Channel type
    3.	Customer type
    4.	Sales type
    5.	Channel
    6.	Org hierarchy

3.	Product settings
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
1.	By delivery location
2.	By channel/store/terminal
3.	By employee
4.	By date
5.	By hour
6.	By product category

### 3.	Margin
1.	By delivery location
2.	By product
3.	By date

### 4.	Return
1.	Return by amount
    1.	By store
    2.	By product
    3.	By date
2.	Return by transaction
    1.	By store
    2.	By product
    3.	By date

### 5.	Discount
1.	By store
2.	By product
3.	By date
4.	Decomposition
    1.	Legal entity
    2.	Store
    3.	Discount type
    4.	Discount name
    5.	Product

### 6.	Payment
1.	By channel/terminal
2.	By payment method/type
3.	By date
4.	Decomposition
    1.	Legal entity
    2.	Channel type
    3.	Store
    4.	Terminal
    5.	Payment method

### 7.	Customer
1.	Life-time value (LTV)

Life-time value is calculated based on total amount spent by a customer across all Dynamics 365 Commerce sales channels, including Point of Sale, E-commerce, Call center.

3.	Recency

Recency is calculated based on number of days since a customer's last transactional engagement with the organization. At this time, recency does not consider non-transactional engagement signals such as e-commerce browsing activity.

3.	Frequency

Frequency is calculated based on a customer's transactional engagement with the organization. At this time, frequency does not consider non-transactional engagement signals such as e-commerce browsing activity.

4.	Relationship length

Relationship length is calculated based on number of days since the customer record was created in the system. 

5.	Transaction count

### 8.	Comparison
1.	Product comparison by time period
    1.	Sales and sales difference
    2.	Margin and margin difference
2.	Customer by time period
    1.	Sales and sales difference
    2.	Margin and margin difference

### 9.	Web activity
#### Top-level filters

1.	Date range
2.	Channel type
3.	Channel
4.	Category hierarchy

#### a.	Acquisition
1.	Page views
    1.	By country
    2.	By product
    3.	By user signed-in status
    4.	By date
2.	E-commerce orders
3.	Conversion rate
    1.	By date
4.	Conversion funnel
    1.	Page view by page type (Home page, Category page, Product details page)
    2.	Add to cart
    3.	Checkout
    4.	Purchase

#### b.	Session
Session is defined as an episode of a user's visit to your e-commerce website. A session is considered ended after 30 minutes of inactivity, or after 24 hours of active usage.
1.	By country
2.	By origin (external referrer)
3.	By user signed-in status
4.	Session count
    1.	By date
    2.	By entry page
5.	Order per session
    1.	By date
6.	Session bounce rate
    
Session bounce is defined as a session where the user immediately leaves after visiting your E-commerce website. Learn more about [Bounce rate](https://en.wikipedia.org/wiki/Bounce_rate).

7.	Clicks per session

#### c.	Visitor
An anonymous visitor on your e-commerce site is determined based on a unique identifier within that specific browser on that specific device. Commerce analytics does not track anonymous users across different browsers or devices. An anonymous user using the same browser on the same computer is uniquely indetified across multiple user sessions, until the browser cache data is cleared or typically until a 12 month period, whichever comes first.

For visitors who browse your e-commerce site while signed-in, Commerce analytics is able to provide additional information based on your existing relationship with these users based on purchases such users may have made with your organization, across all Dynamics 365 Commerce sales channels (including Point of Sale, Call center, E-commerce), such as recency, relationship length, lifetime value and frequency.

1.	Visitor margin
2.	Visitor average orders
3.	Visitor average sales
4.	E-commerce visitor count
    1.	By date
    2.	By location
    
        At this time, Commerce analytics can only provide country level granularity for location insights for e-commerce visitors. 
    
    3.	By recency
    
        Recency is calculated based on number of days since a customer's last transactional engagement with the organization. At this time, recency does not consider non-transactional engagement signals such as e-commerce browsing activity.
    
    4.	By Relationship length

        Relationship length is calculated based on number of days since the customer record was created in the system. 
    
    5.	By lifetime value (LTV)

        Life-time value is calculated based on total amount spent by a customer across all Dynamics 365 Commerce sales channels, including Point of Sale, E-commerce, Call center.

    6.	By frequency
        
        Frequency is calculated based on a customer's transactional engagement with the organization. At this time, frequency does not consider non-transactional engagement     signals such as E-commerce browsing activity.


#### d.	Impression
Impression is defined as each viewing of a product visual by an e-commerce visitor. For instance, if an e-commerce visitor navigates to the Home page of your website and views a yoga mat product within a **Top selling** list module, and also views the same yoga mat product within a **Picks for you** list module, this would count as 2 product impressions. Currently impressions track product views within the following surfaces:

1.	Lists (Recommended, Top selling, Picks for you, Trending, etc.)
2.	Cart module
3.	Search result container
4.	Category search result container
    
Products rendered within carousel module or within custom visuals is not currently counted within the Impressions metric.

Impression report page includes the following metrics
1.	Impression count
    1.	By page type and module
    Page type is the generic page type defined for each page in your e-commerce website. Module type defines the type of e-commerce visual module within which the product is shown.
    You may need to drill down in the page and module visual to view impressions by module.
    2.	By product
    3.	By user signed-in status
    4.	By date
2.	Impression click count

    Impression click is defined as an e-commerce visitor clicking on a product visual, which typically navigates users to the Product Details page for that product. 
    
3. Impression click-through rate (CTR)

    Click-through rate is defined as the total number of impression clicks divided by the total number of impressions.

## Commerce analytics (Preview) installation

> [!NOTE]
> Commerce analytics (Preview) is in preview in the United States, Canada, United Kingdom, Europe, South East Asia, East Asia, Australia, and Japan regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS). Before you can use this feature, see [Configure export to Azure Data Lake](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md)

### <a name="enableCommerceAnalytics"></a> Enable and Configure Commerce Analytics (Preview)
To install Commerce Analytics (Preview), you will need permissions to create resources in an Azure subscription and permissions in Lifecycle Service Portal to install add-ins. Complete the steps outlined below: 

1. [Join Insider Program for Commerce Analytics (Preview)](#joinInsiderProgram)
2. [Enable and Configure Export to Data Lake](#enableExportToDataLake)
3. [Enable and Configure Commerce Analytics (Preview) add-in](#enableCommerceAnalyticsAddin)
4. [Generate Storage Account SAS token](#getSASToken)
5. [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts)
6. [Install and Configure Azure Synapse workspace](#configureAzureSynapse)
7. [Install Power BI template app](#powerbi) 

### <a name="joinInsiderProgram"></a> Join Insider Program for Commerce Analytics (Preview)
Sign-up for the [Insider Program for Commerce Analytics (Preview)](https://aka.ms/CommerceAnalyticsInsiderProgram)

### <a name="enableExportToDataLake"></a> Enable and Configure Export to Data Lake
**Commerce Analytics (Preview)** relies on  **Export to Data Lake** for exporting Commerce HQ data to Azure Data Lake and keep the data fresh. Before you configure **Commerce Analytics (Preview)**, enable and configure Export to Data Lake by following the steps outlined in [Configure export to Azure Data Lake](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md). When you configure Export to Data Lake feature, note the following information, which you will need to enter in subsequent steps.

1. <a name="keyVault"></a>The key vault DNS name and the secret names where you store the application id and application secret. This is outlined in [Add secrets to the key vault](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md#addsecrets).
2. The storage account name for the Azure Data Lake instance. This is outlined in [Create a Data Lake Storage (Gen2) account in your subscription](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md#createsubscription).

### <a name="enableCommerceAnalyticsAddin"></a> Enable and Configure Commerce Analytics (Preview) add-in

To install the **Commerce Analytics (Preview)** add-in in LCS, you must be an environment administrator in LCS for the environment that you plan to use.

You will need the following information to configure Commerce Analytics (Preview) add-in. 

|Field| Information source| Example|
|----|----|----|
|Azure AD Tenant ID for your environment| Your Azure AD tenant ID in the Azure portal. Sign in to the **Azure portal** and open the **Azure Active Directory** service. Open the **Properties** page and copy the value in the **Directory ID** field.|72f988bf-0000-0000-00000-2d7cd011db47|
|DNS name of your key vault|Enter the [DNS name](#keyVault) of your key vault.|`https://contosod365datafeedpoc.vault.azure.net/`|
|Secret that contains the Application ID|Enter the [secret name](#keyVault) that stores the application id. This is the same value that you used  when installing **Export to Data Lake** add-in.|app-id|
|Secret that contains the Application secret|Enter the [secret name](#keyVault) that stores the application secret. This is the same value that you used when installing **Export to Data Lake** add-in.|app-secret|

1. Sign in to [Lifecycle Services Portal](https://lcs.dynamics.com/) and navigate to your environment.
2. On the **Environment** page, select the **Environment add-ins** tab.
3. Select **Install a new add-in**, and in the dialog box, select **Commerce Analytics (Preview)**. If **Commerce Analytics (Preview)** isn't listed, make sure you have [joined the Insider Program](#joinInsiderProgram)
4. In the Setup add-in dialog box, enter the required information as outlined in the table above.
5. Accept the terms of the offer by selecting the check box, and then select Install.

The system installs and configures the Commerce Analytics (Preview) for the environment. This operation might take a few minutes. After installation and configuration are completed, **Commerce Analytics (Preview)** should be listed on the Environment page, and the status should be Installed.

### <a name="getSASToken"></a> Generate Storage Account SAS token
> [!NOTE]
> There is a known limitation of Commerce Analytics (Preview), where the Azure Synapse instance will lose access to the Data Lake when the SAS token expires. You should set the maximum expiration date allowed by your organization security policies, when you generate the SAS token.

A Shared Access Signature (SAS) token enables external entities to access your storage account, with a specific set of privileges for a finite amount of time. Azure Synapse will use the SAS token to access the underlying data in Azure Data Lake. To generate a SAS token, complete the below steps:

1. Navigate to the storage account in Azure Portal, which you created while configuring Export to Data Lake, as outlined in [Create a Data Lake Storage (Gen2) account in your subscription](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md#createsubscription).
2. In the left options pane, under the storage account, select `Shared access signature`.
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
5. Copy value from the `SAS token` text box, into a text editor such as Notepad.

### <a name="downloadSynapseDeploymentScripts"></a> Download deployment scripts for Azure Synapse views
In order to create and publish the necessary views in Azure Synapse workspace, you will need to download and execute a set of scripts. Complete the below steps to download the scripts:

1. The scripts are available in the [microsoft/Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) Github repo.
2. To download the scripts to your local machine, you can either clone this repo, or download the repo as a zip file.

### <a name="configureAzureSynapse"></a> Install and Configure Azure Synapse workspace
To install and configure an Azure Synapse workspace, complete the below steps:

1. Install Azure Synapse workspace, in your Azure subscription, by following the steps outlined in [Quickstart: Create a Synapse workspace](/azure/synapse-analytics/quickstart-create-workspace)
2. Open the `SetupSynapse.sql` script file in Notepad, from your local machine folder where you cloned or downloaded the Dynamics365Commerce.Solutions repo, as outlined in  [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts). The script file will be under `/Pipeline/CommerceAnalyticsSynapse/` folder. Edit the script to replace the following placeholder texts with values as shown below:

   | Placeholder Text | Replacement Value |
   |------------------|-------------------|
   | placeholder_storageaccount | Replace with the name for the storage account that you created while configuring Export to Data Lake, as outlined in  [Create a Data Lake Storage (Gen2) account in your subscription](../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md#createsubscription). |
   | <a name="phContainer"></a>placeholder_container | Replace with the name of the storage container that was created in your Azure Data Lake instance, after you successfully installed the Export to Data Lake addin in Lifecycle Services (LCS). You will need to use the Storage Explorer in Azure Portal to browse your storage account, in order to get the container name. |
   | placeholder_sastoken | Replace with the SAS token that you copied in [Get Storage Account SAS token](#getSASToken). Make sure to remove the **'?'** at the beginning of the SAS token value. |
   | <a name="phUserPwd"></a>placeholder_password | Replace with a strong password of your choice. Make a note of this password. This will be set as the password for the new `reportreadonlyuser` account, that will be created by this script. **DO NOT** enter the password of the `sqladminuser` account here.  |
3. Navigate to the new Azure Synapse workspace, in Azure Portal. Click on `Open Synapse Studio` option on the Overview page.
4. Copy the contents of `SetupSynapse.sql` that you updated in Step 2 above. In Synapse Studio on Azure Portal, click on `New` > `SQL script`. Paste the contents into the SQL script editor in Synapse Studio.
5. Ensure that `Use database` is set to **master**. Select `Run` to execute the script.
6. Wait for the script execution to complete. Successful execution of the script will create the database for Commerce Analytics, credential for accessing the Azure Data Lake and a readonly user account, which will be used by PowerBI to connect to the Azure Synapse instance.
7. On your local machine, open PowerShell in admin mode. Navigate to the `/Pipeline/CommerceAnalyticsSynapse/` folder under the folder where you cloned or downloaded the Dynamics365Commerce.Solutions repo, as outlined in  [Download deployment scripts for Azure Synapse views](#downloadSynapseDeploymentScripts).
8. Setup the PowerShell execution policy, by running the following command in the PowerShell window:
   ```powershell
   Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
   ```
9. Install the SQL Server PowerShell module, by running the following command in the PowerShell window:
   ```powershell
   Install-Module sqlserver
   ```
   **Note:** If you already have the SQL Server module installed, you may skip this step. During installation of this module, you may get prompted to install NuGet provider. Press **Y** to proceed with the installation of NuGet provider. Additionally, you may also get prompted that you are installing modules from an untrusted repository. Press **Y** to continue with the installation. Optionally, you may run the `Set-PSRepository` cmdlet, to trust the `PSGallery` repository.
10. Publish the Azure Synapse views, by running the following command in the PowerShell window:
    ```powershell
    .\PublishSynapseViews.ps1 -serverName SERVER_NAME -password PASSWORD -storageAccount STORAGE_ACCOUNT -containerName CONTAINER_NAME -datarootpath DATA_ROOT_PATH
    ```
    The placeholder values in the command should be replaced as follows:

    | Placeholder Value | Replacement Value |
    |-------------------|-------------------|
    | SERVER_NAME | Replace with the name of the Azure Synapse Serverless SQL endpoint. You can get this value from the Azure Synapse workspace Overview page in Azure Portal. |
    | PASSWORD | Replace with the password for the sqladminuser. |
    | STORAGE_ACCOUNT | Replace with the name of the Storage Account for Azure Data Lake. |
    | CONTAINER_NAME | Replace with the name of the container that was created by Export to Data Lake feature. This is the same container that you specified in the [placeholder_container](#phContainer) value above. |
    | DATA_ROOT_PATH | Replace with the folder name under the container that contains all the data. |

    **Note:** You can find the Storage Account name, Container name and the Data Root Path from Azure Portal, by using Azure Storage browser with your Azure Data Lake storage account.

11. Wait for the script to complete. Successful execution of the script will create SQL views in the Azure Synapse serverless SQL instance.

### <a name="powerbi"></a> Install Power BI template app
In order to install the Power BI template app for Commerce Analytics (Preview), complete the steps below:
1. Sign in to [Power BI portal](https://powerbi.microsoft.com/), using your organization id.
2. Install the Commerce Analytics (Preview) Power BI template app, by visiting [https://aka.ms/cdireport-installapp](https://aka.ms/cdireport-installapp). You may see a warning about the app not being listed on AppSource. Click on the `Install` button.
3. If this is the first time you are installing the app, skip to step 5. If you have already installed this app before, you will be presented with the following options to update the app:
   1. Update the workspace and the app.

      This option will update the existing template app, and overwrite your app settings, such as the app instance name, permission configurations, etc.

   2. Update only workspace content without updating the app

      This option will update the existing template app and keep your app settings. This is the **recommended** option for an app update.

   3. Install another copy of the app into a new workspace

      This will create a new copy of the app into a new workspace that will be created for you. The existing workspace will be left intact.
4. Select one of the 3 options, and click on the `Install` button.
5. Open the installed app, by clicking on the `Apps` menu item on the left pane, and then clicking on the app.
6. Next, you will connect the app to your data source. Click on the `Connect` button. If this is not the first time you are installing the app, click on the `Connect your data` link in the yellow info bar.
7. Input the parameter values as follows:

   | Parameter Name | Value |
   |----------------|-------|
   | Server       | Enter the name of the Azure Synapse Serverless SQL endpoint that you created in [Install and Configure Azure Synapse workspace](#configureAzureSynapse) section. You can get this value from the Azure Synapse workspace Overview page in Azure Portal. |
   | Database | Enter the value `CommerceAnalytics`
   | Language | You can select from the dropdown list. This is used for localized product and category names. This value is case sensitive. |
   | Date Range | You can select from the dropdown list. Data for the selected number of months will be imported to the Power BI dataset. The size of the dataset, and the time required to sync will depend on the value that you select. |
   
8. After you have entered the values, click on `Next`. You will be prompted to enter the credentials for connecting to the Azure Synapse SQL database. Enter the values as indicated below:

   | Parameter Name | Value |
   |----------------|-------|
   |Authentication method|Select `Basic`|
   |User name| Enter `reportreadonlyuser`|
   |Password|Enter the value that you replaced the [placeholder_password](#phUserPwd) with in the `SetupSynapse.sql` script. This is the password for the **reportreadonlyuser** account.| 
   
9. Click on `Sign in and connect` button.
10. Wait until the dataset is refreshed successfully. You can navigate to the App workspace, by clicking on the Edit app icon. Once inside the workspace, you can check the refresh status of the dataset. Optionally, you can also set up auto refresh schedules for your dataset from here, as well as manage permissions and rename the app instance.

### <a name="privacy"></a> Privacy
Your privacy is important to us. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
