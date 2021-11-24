---
title: Demand forecasting setup
description: This topic describes the setup tasks that you must perform to prepare for demand forecasting.  
author: ChristianRytt
ms.date: 11/23/2021
ms.topic: article
ms.search.form: ReqDemPlanDefaultAlgorithmParameters, ReqDemPlanForecastParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Demand forecasting setup

[!include [banner](../includes/banner.md)]

This topic describes how to set up demand forecasting.  

## Item allocation keys

Item allocation keys establish groups of items. A demand forecast is calculated for an item and its dimensions only if the item is part of an item allocation key. This rule is enforced to group large numbers of items so that demand forecasts can be created more quickly. Forecasts are created based on historical data only.

An item and its dimensions must be part of only one item allocation key if the item allocation key is used during forecast creation.

To create item allocation keys and add a stockkeeping units (SKU) to them:

1. Go to **Master planning \> Setup \> Demand forecasting \> Item allocation keys**.
1. Either select an item allocation key from the list pane to select **New** from the Action Pane to create a new one. Make the following settings in the header for your new or selected key:
    - **Item allocation key** – Enter a unique name for the key.
    - **Name** – Enter a descriptive name for the key.
1. Do one of the following to add or remove items to the selected item allocation key:
    - On the **Item allocation** FastTab, use the **New** and **Delete** buttons on the toolbar to add or remove items as needed. For each row, select the **Item number** and then assign dimension values in the other columns as needed. Select **Display dimensions** on the toolbar to change the set of dimension columns shown in the grid. (The value in the **Percent** column is ignored when generating demand forecasts.)
    - If you want to add a large number of items to the key, select **Assign items** on the Action Pane to open a page where you can find and assign multiple items to the selected key.

> [!IMPORTANT]
> Be careful to include only relevant items in each item allocation key. Unnecessary items might cause increased costs when you use Microsoft Azure Machine Learning.

## Intercompany planning groups

Demand forecasting can generate cross-company forecasts. In Dynamics 365 Supply Chain Management, companies that are planned together are grouped into the same intercompany planning group. To specify, per company, which item allocation keys should be considered for demand forecasting, associate an item allocation key with the intercompany planning group member.

> [!IMPORTANT]
> Planning Optimization does not currently support intercompany planning groups. To do intercompany planning with Planning Optimization, set up master planning batch jobs that include master plans for all of the relevant companies.

To set up your intercompany planning groups:

1. Go to **Master planning \> Setup \> Intercompany planning groups**.
1. Either select a planning key from the list pane to select **New** from the Action Pane to create a new one. Make the following settings in the header for your new or selected group:
    - **Item allocation key** – Enter a unique name for the key.
    - **Description** – Enter a descriptive name for the key.
1. On the **Intercompany planning group members** FastTab, use the toolbar buttons to add rows for each company (legal entity) that should be part of the group. For each row, make the following settings:
    - **Legal entity** – Select the name of a company (legal entity) that is a member of the selected group.
    - **Scheduling sequence** – Assign the order in which each company should be processed (low values are processed first). This can be important when demand for one company affects other companies, in which case the company that supplies the demand should be processed last.
    - **Master plan** – Select the master plan to trigger for the current company.
    - **Automatic copy to static plan** – Select this check box to take the result of the plan and copy it to the static plan.
    - **Automatic copy to dynamic plan** – Select this check box to take the result of the plan and copy it to the dynamic plan.
1. By default, if no item allocation keys are assigned to intercompany planning group members, a demand forecast is calculated for all items that are assigned to all item allocation keys from all companies. Additional filtering options for companies and item allocation keys are available on the **Generate statistical baseline forecast** dialog (**Master planning \> Forecasting ]> Demand forecasting \> Generate statistical baseline forecast**). To specify item allocation keys for a company in the selected intercompany planning group, select the company and then select **Item allocation keys** on the **Intercompany planning group members** FastTab toolbar.

> [!IMPORTANT]
> Be careful to include only relevant item allocation keys in each intercompany planning group. Unnecessary items might cause increased costs when you use Microsoft Azure Machine Learning.

## <a name="parameters"></a>Set up Demand forecasting parameters

Use the **Demand forecasting parameters** page to set up several options that control how demand forecasting will work on your system.

### Open the Demand forecasting parameters page

To set up demand forecasting parameters, go to **Master planning \> Setup \> Demand forecasting \> Demand forecasting parameters**. Because demand forecasting runs cross-company, the setup is global, which means that the setup applies to all legal entities (companies).

### General settings

Use the **General** tab of the **Demand forecasting parameters** page to make general settings for demand forecasting.

#### Demand forecast unit

Demand forecasting generates the forecast in quantities. Therefore, the unit of measure that the quantity should be expressed in must be specified in the **Demand forecast unit** field. This dictates the unit that will be used for all demand forecasts, regardless of the usual inventory units for each product. Using a consistent forecast unit helps ensure that the aggregation and percentage distribution make sense. For more information about aggregation and percentage distribution, see [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md).

For every unit of measure that is used for SKUs that are included in demand forecasting, make sure that there is a conversion rule for the unit of measure and the general forecasting unit of measure you select here. When you generate a forecast generation, the list of items that don't have a unit of measure conversion is logged, so you can easily correct the setup. For more information about units of measure and converting between them, see [Manage units of measure](../pim/tasks/manage-unit-measure.md).

#### Transaction types

Use the settings on the **Transaction types** FastTab to choose which transaction types to use when generating the statistical baseline forecast.

Demand forecasting can be used to forecast both dependent and independent demand. For example, if only **Sales order** is set to *Yes*, and if all the items that are considered for demand forecasting are items that are sold, the system calculates independent demand. However, critical subcomponents can be added to item allocation keys and included in demand forecasting. In this case, if **Production line** is set to *Yes*, a dependent forecast is calculated.

You can override transactions types for one or more specific item allocation keys by going to the **Item allocation keys** tab, which provides similar settings.

#### Choose how to create the baseline forecast

There are three methods for creating a baseline forecast. The **Forecast generation strategy** field lets you select between these three methods. Set it to one of the following values:

- *Copy over historical demand* – Create forecasts simply by copying historical data.
- *Azure Machine Learning Service* – Use a forecast model that runs using the Azure Machine Learning Service. This is the current machine learning solution provided for Azure, so we recommend using it if you want to use a forecast model.
- *Azure Machine Learning* – Use a forecast model that runs using the older Azure Machine Learning Studio (classic), which has now been deprecated. This solution will soon be removed from Azure, so we recommend using *Azure Machine Learning Service* instead if you are setting up demand forecasting for the first time. You should also plan to switch to the new Azure Machine Learning Service as soon as possible if you are currently Azure Machine Learning Studio (classic).

You can override the forecast generation method for one or more specific item allocation keys by going to the **Item allocation keys** tab, which provides similar settings.

#### Override default forecast algorithm parameters globally

Default forecast algorithm parameters and value are assigned using the **Demand forecasting parameters** page (**Master Planning \> Setup \> Demand forecasting \> Demand forecasting parameters**). However, you can override these globally using the **Forecast algorithm parameters** FastTab on the **General** tab of the **Demand forecasting parameters** page. (You can also override them for specific allocation keys using the **Item allocation keys** tab of the **Demand forecasting parameters** page.)

Use the **Add** and **Remove** buttons on the toolbar to establish the required collection of parameter overrides. For each parameter in the list, select a **Name** and then enter an appropriate value in the **Value** field. All of the parameters not listed here will take their values from the settings on the **Demand forecasting parameters** page. For more information about how to use the standard set of parameters and select values for them, see [Default parameters and values for demand forecasting models](#model-parameters).

### Set forecast dimensions

A forecast dimension indicates the level of detail that the forecast is defined for. Company, site, and item allocation key are required forecast dimensions, but you can also generate forecasts at the warehouse, inventory status, customer group, customer account, country/region, state, and/or item plus all item dimension levels. Open the **Forecast dimensions** tab of the **Demand forecasting parameters** page to select the set of forecast dimensions to use when the demand forecast is generated.

At any time, you can add forecast dimensions to the list of dimensions that are used for demand forecasting. You can also remove forecast dimensions from the list. However, manual adjustments are lost if you add or remove a forecast dimension.

### Set up overrides for specific item allocation keys

Not all items perform in the same manner from a demand forecasting perspective. Therefore, you can establish allocation-key-specific overrides for most of the settings established on the **General** tab (other than unit). To set up overrides for a specific item allocation key:

1. Open the **Item allocation keys** tab of the **Demand forecasting parameters** page.
1. In the grid on the left, use the toolbar buttons to add and remove item allocation keys as needed, and then select the allocation key you want to set up overrides for.
1. On the **Transaction types** FastTab, enable the types of transactions you want to use to generate the statistical baseline forecast for products belonging to the selected allocation key. These settings work the same way as they do on the **General** tab, but apply only to the selected item allocation key. All of the settings here (both *Yes* and *No* values) override all of the **Transaction types** settings from the **General** tab.
1. On the **Forecast algorithm parameters** FastTab, select the **Forecast generation strategy** and forecast algorithm parameter overrides for products belonging to the selected allocation key. These settings work the same way as they do on the **General** tab, but apply only to the selected item allocation key. Use the **Add** and **Remove** buttons on the toolbar here to establish the required collection of parameter overrides. For each parameter in the list, select a **Name** and then enter an appropriate value in the **Value** field. For more information about how to use the standard set of parameters and select values for them, see [Default parameters and values for demand forecasting models](#model-parameters).

### Set up the connection to the Azure Machine Learning Service

Use the **Azure Machine Learning Service** tab to set up the connection to Azure Machine Learning Service, which is one of the options for creating the baseline forecast. These settings only have an effect when **Forecast generation strategy** is set to *Azure Machine Learning Service*.

For more information about how to set up Azure Machine Learning Service and then use the settings here to connect to it, see [Set up the Azure Machine Learning Service](#setup-amls).

### Set up the connection to Azure Machine Learning Studio (classic)

> [!IMPORTANT]
> *Azure Machine Learning Studio (classic)* has now been deprecated, so it is no longer possible to create new workspaces for it on Azure. It has been replaced by the *Azure Machine Learning Service*, which provides similar functionality and more. If you aren't already using Azure Machine Learning, then you should use the Azure Machine Learning Service starting now. If you already have a workspace created for Azure Machine Learning Studio (classic), you can continue to use it until the feature is completely removed from Azure, but we recommend updating to the Azure Machine Learning Service as soon as possible. (The application will continually warn you that Azure Machine Learning Studio (classic) has been deprecated, but that won't affect the forecasting result.) For more information about the new Azure Machine Learning Service and how to set it up, see [Set up the Azure Machine Learning Service](#setup-amls). You can freely switch back and forth between using the new and old machine learning solutions with Supply Chain Management for as long as your old Azure Machine Learning Studio (classic) workspace remains available.

If you already have an Azure Machine Learning Studio (classic) workspace available, then you can use it to generate forecasts by connecting it to Supply Chain Management. To do so, go to the **Azure Machine Learning** tab on the **Demand forecasting parameters** page. (These settings only have an effect when **Forecast generation strategy** is set to *Azure Machine Learning*.) Then enter the following details for your Azure Machine Learning workspace:

- Web service application programming interface (API) key
- Web service endpoint URL
- Azure storage account name
- Azure storage account key

> [!NOTE]
> The Azure storage account name and key are required only if you use a custom storage account. If you deploy the on-premises version, you must have a custom storage account on Azure, so that Machine Learning can access the historical data.

## <a name="model-parameters"></a>Default parameters and values for demand forecasting models

When you use machine learning to generate your forecast planning models, you control machine learning options by setting values for *forecasting algorithm parameters*, which are sent from Supply Chain Management to Azure Machine Learning. Use the **Forecasting algorithm parameters** page to control which kinds of values to provide and which values each of them should have.

To set up the default parameters and values used for demand forecasting models, go to **Master Planning \> Setup \> Demand forecasting \> Forecasting algorithm parameters**. A standard set of parameters is provided, each of which has the following fields:

- **Name** – The name for the parameter as used by Azure. Usually you shouldn't change these unless you have customized the experiment in Azure Machine Learning.
- **Description** – A common name for the parameter. This value used to identify the parameter elsewhere in the system (such as on the **Demand forecasting parameters** page).
- **Value** – The default value for each parameter. The value you should enter depends on which parameter you are editing. 
- **Explanation** – A short description of the parameter and how to use it. It typically includes advice about valid values for the **Value** field.

The following parameters are provided by default. (If necessary, you can select **Restore** on the Action Pane to revert to this standard list.)

- **Confidence level percentage** – A confidence interval consists of a range of values that act as good estimates for the demand forecast. A 95% confidence level percentage indicates there is a 5% risk that the future demand falls outside the confidence interval range.
- **Force seasonality** – Specifies whether to force the model to use a certain type of seasonality. Applies to ARIMA and ETS only. Options: *AUTO(default)*, *NONE*, *ADDITIVE*, *MULTIPLICATIVE*.
- **Forecasting model** – Specifies which forecasting model to use. Options: *ARIMA*, *ETS*, *STL*, *ETS+ARIMA*, *ETS+STL*, *ALL*. To select best fit model, use *ALL*.
- **Maximum forecasted value** – Specifies the maximum value to use for predictions. Format: +1E[n] or numeric constant.
- **Minimum forecasted value** – Specifies the minimum value to use for predictions. Format: -1E[n] or numeric constant.
- **Missing value substitution** – Specifies how gaps in historical data are filled. Options: *(numeric value)*, *MEAN*, *PREVIOUS*, *INTERPOLATE LINEAR*, *INTERPOLATE POLYNOMIAL*.
- **Missing value substitution scope** – Specifies whether the value substitution applies only to the date range of each individual granularity attribute, or to the entire dataset. The following options are available for establishing the date range that the system uses when filling in gaps in historical data:

  - *GLOBAL* – The system uses the full range of dates of all granularity attributes.
  - *HISTORY_DATE_RANGE* – The system uses a specific date range defined by the **From date** and **To date** fields on the **Historical horizon** field group in the **Generate statistical baseline forecast** dialog box.
  - *GRANULARITY_ATTRIBUTE* – The system uses the date range of the currently processed granularity attribute.

  > [!NOTE]
  > A granularity attribute is a combination of forecast dimensions against which the forecast is done. You can define forecast dimensions on the **Demand forecasting parameters** page.

- **Seasonality hint** – For seasonal data, provide a hint to the forecasting model to improve forecast accuracy. Format: integer number, representing the number of buckets a demand pattern repeats itself. For example, enter "6" for data that repeats itself every six months.
- **Test set size percentage** – Percentage of historical data to be used as a test set for forecast accuracy calculation.

You can overwrite the values for these parameters by going to **Master Planning \> Setup \> Demand forecasting \> Demand forecasting parameters**, where you can do the following:

- Use the **General** tab to overwrite the parameters globally.
- Use the **Item allocation keys** tab to overwrite the parameters per item allocation key. Parameters that are overwritten for an item allocation key affect only the forecast of items that are associated with that item allocation key.

> [!NOTE]
> You can add or remove parameters in the list on the **Forecasting algorithm parameters** page using the buttons on the Action Pane, but usually shouldn't do so unless you have customized the experiment in Azure Machine Learning.

## <a name="setup-amls"></a>Set up the Azure Machine Learning Service

Supply Chain Management calculates demand forecasts using the *Azure Machine Learning Service*, which you must set up and run on your own Azure subscription. This section describes how to set it up on Azure and then connect it with your Supply Chain Management environment.

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]
<!-- KFM: Preview until 10.0.23 GA -->

### Enable the Azure Machine Learning Service in feature management

Before you can use the Azure Machine Learning Service for demand forecasting, you must turn on a feature in Supply Chain Management to enable the integration. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *Azure Machine Learning Service for demand forecasting*

### <a name="ml-workspace"></a>Set up machine learning on Azure

To enable Azure to process your forecasts using machine learning, you must set up an Azure machine learning workspace for this purpose. You have two options (choose one):

- To set up the workspace by running a script provided by Microsoft, follow the instructions in [Option 1: Run a script to set up your machine learning workspace](#ml-workspace-script) and then skip ahead to [Set up Azure Machine Learning Service connection parameters in Supply Chain Management](#demand-forecast-parameters).
- To set up your workspace manually, which takes a bit longer but gives you more control, follow the instructions in [Option 2: Manually set up your machine learning workspace](#ml-workspace-manual) and then skip ahead to [Set up Azure Machine Learning Service connection parameters in Supply Chain Management](#demand-forecast-parameters).

#### <a name="ml-workspace-script"></a>Option 1: Run a script to automatically set up your machine learning workspace

This section describes how to set up your machine learning workspace using an automated script provided by Microsoft. If you prefer, you can set up all the resources manually by following the instructions provided in [Option 2: Manually set up your machine learning workspace](#ml-workspace-manual), but you do not need to do both.

1. Go to the [Templates for Dynamics 365 Supply Chain Management demand forecasting with Azure Machine Learning](https://github.com/microsoft/Dynamics-365-Supply-Chain-Management-Demand-Forecasting-With-Azure-Machine-Learning-Service) repository on GitHub and download the following files:
    - `quick_setup.ps1`
    - `sampleInput.csv`
    - `src/parameters.py`
    - `src/api_trigger.py`
    - `src/run.py`
    - `src/REntryScript/forecast.R`
1. Open a PowerShell window and run the `quick_setup.ps1` script that you downloaded in step 1. Then following the instructions on your screen. The script will set up the required workspace, storage, default datastore, and compute resources, but you still need to create the required pipelines by following the remaining steps of this procedure. (Pipelines provide a way to start forecasting scripts from Supply Chain Management.)
1. Go to Azure Machine Learning Studio and upload the `sampleInput.csv` file that you downloaded in step 1 to the container called *demplan-azureml* (which was created by the script). This file is needed to publish the pipeline and to generate a test forecast. For instructions, see [Upload a block blob](/azure/storage/blobs/storage-quickstart-blobs-portal#upload-a-block-blob).
1. In Azure Machine Learning Studio, select **Notebooks** from the navigator.
1. Find the following location in the **Files** structure: **Users/\[current user\]/src**.
1. Upload the remaining four files that you downloaded in step 1 to the location you found in the previous step.
1. Select the `api_trigger.py` file that you just uploaded and run it. It will create a pipeline to be triggered through the API.
1. Your workspace is now set up. Skip ahead to [Set up Azure Machine Learning Service connection parameters in Supply Chain Management](#demand-forecast-parameters).

#### <a name="ml-workspace-manual"></a>Option 2: Manually set up your machine learning workspace

This section describes how to set up your machine learning workspace manually. You only need to do this if you decided not to run the automated setup script as described in [Option 1: Run a script to set up your machine learning workspace](#ml-workspace-script).

##### <a name="create-workspace"></a>Step 1: Create a new workspace

Use the following procedure to create a new machine learning workspace.

1. Sign in to your Azure portal.
1. Open the **Machine learning** service.
1. Select **Create** on the toolbar to launch the create wizard.
1. Work through the wizard following the instructions on your screen. Keep the following points in mind as you work:
    - Use default settings unless otherwise recommended in the other points of this list.
    - Be sure to select the geographic region that matches the region where your instance of Supply Chain Management is deployed. Otherwise, some of your data may pass through region boundaries. See also the [privacy notice](#privacy) provided later in this topic.
    - Use dedicated resources such as resource group, storage account, container registry, Azure Key Vault, networking resources, and so on.
    - On the **Set up Azure Machine Learning Service connection parameters** page of the wizard, you must provide a storage account name. Use an account that is dedicated to demand forecasting. Demand forecasting input and output data will be stored in this storage account.

For more information, see [Create the workspace](/azure/machine-learning/quickstart-create-resources#create-the-workspace).

##### <a name="config-storage"></a>Step 2: Configure storage

Use the following procedure to set up your storage.

1. Go to the [Templates for Dynamics 365 Supply Chain Management demand forecasting with Azure Machine Learning](https://github.com/microsoft/Dynamics-365-Supply-Chain-Management-Demand-Forecasting-With-Azure-Machine-Learning-Service) repository on GitHub and download the following file:
    - `sampleInput.csv`
1. Open the storage account that you created in [Step 1: Create a new workspace](#create-workspace).
1. Follow the instructions provided in [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container) to create a container named *demplan-azureml*.
1. Upload the `sampleInput.csv` file that you downloaded in step 1 to the container that you just created. This file is needed to publish the pipeline and to generate a test forecast. For instructions, see [Upload a block blob](/azure/storage/blobs/storage-quickstart-blobs-portal#upload-a-block-blob).

##### Step 3: Configure default datastore

Use the following procedure to set up your default datastore.

1. In Azure Machine Learning Studio, select **Datastores** from the navigator.
1. Create a new datastore of the *Azure Blob Storage* type that points to the *demplan-azureml* blob Storage container that you created in [Step 2: Configure storage](#config-storage). (If the new datastore has an **Authentication type** of *Account key*, provide an account key for the created storage account. For instructions, see [Manage storage account access keys](/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).)
1. Make your new datastore the default datastore by opening its details and selecting **Set as default datastore**.

##### <a name="config-compute-resources"></a>Step 4: Configure compute resources

Set up a compute resource in Azure Machine Learning Studio to run your forecasting generation scripts, as described in the following procedure.

1. Open the details page for the machine learning workspace you created in [Step 1: Create a new workspace](#create-workspace). From here, find your **Studio web URL** and select the link to open it.
1. Select **Compute** on the navigation pane.
1. Open the **Compute instances** tab and select **New** to launch a wizard that will help you create a new compute instance. Follow the instructions on your screen. This will be used to create the demand forecasting pipeline (can be deleted after pipeline is published). Use default settings.
1. Open the **Compute clusters** tab and select **New** to launch a wizard that will help you create a new compute cluster. Follow the instructions on your screen. This will be used to generate demand forecasts. Its settings affect performance and the maximum level of parallelization of the run. Use default settings except those mentioned in the following list:
    - **Name** – Enter *e2ecpucluster*.
    - **Virtual machine size** – Adjust this setting according to the volume of data that you expect to use as an input to demand forecasting. The maximum nodes count should not exceed 11 because one node is needed to trigger the demand forecast generation and the maximum count of nodes that can then be used to generate a forecast is 10. (You will also set the node count in the `parameters.py` file, as described in the next section.) On each node, there will be several worker processes executing forecasting scripts in parallel. The total number of worker processes in your job will be *\[number of cores a node has\] \* node count*. For example, if your compute cluster has type Standard\_D4 (8 cores) and maximum 11 nodes, then the effective level of parallelism is 80, assuming `nodes_count` is set to 10 in `parameters.py`.

##### <a name="create-pipelines"></a>Step 5: Create pipelines

Pipelines provide a way to start forecasting scripts from Supply Chain Management. Use the following procedure to create the required pipelines.

1. Go to the [Templates for Dynamics 365 Supply Chain Management demand forecasting with Azure Machine Learning](https://github.com/microsoft/Dynamics-365-Supply-Chain-Management-Demand-Forecasting-With-Azure-Machine-Learning-Service) repository on GitHub and download the following files:
    - `src/parameters.py`
    - `src/api_trigger.py`
    - `src/run.py`
    - `src/REntryScript/forecast.R`
1. In Azure Machine Learning Studio, select **Notebooks** from the navigator.
1. Find the following location in the **Files** structure: **Users/\[current user\]/src**.
1. Upload the four files that you downloaded in step 1 to the location you found in the previous step.
1. In Azure, open and review the `parameters.py` file that you just uploaded. Make sure the `nodes_count` value specified here is one less than the value you configured for the compute cluster in [Step 4: Configure compute resources](#config-compute-resources). If the `nodes_count` is greater than or equal to number of nodes in the compute cluster, the pipeline run might be able to start but then it will hang while waiting for the needed resources. For more information about the nodes count, see [Step 4: Configure compute resources](#config-compute-resources).
1. Select the `api_trigger.py` file that you just uploaded and run it. It will create a pipeline to be triggered through the API.

### <a name="aad-app"></a>Set up a new Active Directory application

An Active Directory application is needed to authenticate with the resources dedicated to demand forecasting using service principal, so the application should have the lowest level of privilege needed to generate the forecast.

1. Sign in to your Azure portal.
1. Register a new application in the tenant's Azure Active Directory, as described in [Use the portal to create an Azure AD application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal).
1. Follow the instructions on your screen as you work through the wizard. Keep default settings.
1. Give your new Active Directory application access to the following resources (which you created in [Set up machine learning on Azure](#ml-workspace)). For instructions, see [Assign Azure roles using the Azure portal](/azure/role-based-access-control/role-assignments-portal?tabs=current). This will enable the system to import and export forecasting data and to trigger machine learning pipeline runs from Supply Chain Management.
    - Contributor role to the machine learning workspace.
    - Contributor role to the dedicated Storage account.
    - Storage Blob Data Contributor role to the dedicated Storage account
1. Under the **Certificates & secrets** section of the created application, create a secret for it. For instructions, see [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret).
1. Make a note of the application ID and its secret. You will need details of this application later when you set up the **Demand forecasting parameters** in Supply Chain Management.

### <a name="demand-forecast-parameters"></a>Set up Azure Machine Learning Service connection parameters in Supply Chain Management

Use the following procedure to connect your Supply Chain Management environment to the machine learning service you just set up in Azure.

1. Sign in to Supply Chain Management.
1. Go to **Master planning \> Setup \> Demand forecasting \> Demand forecasting parameters**.
1. Open the **General** tab and make sure **Forecast generation strategy** is set to *Azure Machine Learning Service*.
1. Open the **Item allocation keys** tab and make sure **Forecast generation strategy** is set to *Azure Machine Learning Service* for each allocation key that should use the Azure Machine Learning Service for demand forecasting.
1. Open the **Azure Machine Learning Service** tab.

    ![Azure Machine Learning Service parameters](media/azure-ml-service-parameters.png "Azure Machine Learning Service parameters")

1. Make the following settings on the **Azure Machine Learning Service** tab:
    - **Tenant ID** – Enter the ID for your Azure tenant. Supply Chain Management will use this ID to authenticate with the Machine Learning Service. You can find your tenant ID in the Azure portal, on the Azure Active Directory **Overview** page.
    - **Service principal application ID** – Enter the application ID for the application you created in the [Active Directory Application](#aad-app) section of this topic. This value is used to authorize API requests to Azure Machine Learning Service.
    - **Service principal secret** – Enter the service principal application secret for the application you created in the [Active Directory Application](#aad-app) section of this topic. This value is used to acquire the access token for the created security principal to perform authorized operations against Azure Storage and the Azure Machine Language workspace.
    - **Storage account name** – Enter the Azure storage account name that you specified when you ran the setup wizard on your Azure workspace (see also [Set up machine learning on Azure](#ml-workspace)).
    - **Pipeline endpoint address** – Enter the URL of the pipeline REST endpoint for your Azure Machine Learning Service. This is the pipeline you created as the last step when you [Set up machine learning on Azure](#ml-workspace). To get the pipeline URL, sign in to your Azure portal, select **Pipelines** on the navigator and open the **Pipeline** tab. Select the pipeline endpoint named **TriggerDemandForecastGeneration** in the list; then copy the REST endpoint shown.

## <a name="privacy"></a>Privacy notice

When you select Azure Machine Learning Service as your forecast generation strategy, Dynamics 365 Supply Chain Management automatically sends your Customer Data for historical demand such as aggregated quantities, product names and their product dimensions, shipping and receiving locations, customer identifiers as well as forecast parameters to the geographic region where your machine learning workspace and its linked storage account are located, for the purpose of forecasting future demands. Azure Machine Learning Service may be in a different geography than where Dynamics 365 Supply Chain Management is deployed. Some users can control whether this functionality is enabled by selecting the forecast generation strategy on the Demand forecasting parameters form.

## Additional resources

- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)
- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
