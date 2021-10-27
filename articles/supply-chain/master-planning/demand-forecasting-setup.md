---
title: Demand forecasting setup
description: This topic describes the setup tasks that you must perform to prepare for demand forecasting.  
author: ChristianRytt
ms.date: 08/09/2021
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

This topic describes the setup tasks that you must perform to prepare for demand forecasting.  

The setup tasks include setting up the following data and parameters.

## Item allocation keys

A demand forecast is calculated for an item and its dimensions only if the item is part of an item allocation key. This rule is enforced to group large numbers of items, so that demand forecasts can be created more quickly. The item allocation key percentage is ignored when demand forecasts are generated. Forecasts are created based on historical data only.

An item and its dimensions must be part of only one item allocation key if the item allocation key is used during forecast creation.

To add a stock keeping unit (SKU) to an item allocation key, go to **Master planning \> Setup \> Demand forecasting \> Item allocation keys**. Use the **Assign items** page to assign an item to an allocation key.

## Intercompany planning groups

Demand forecasting generates cross-company forecasts. In Dynamics 365 Supply Chain Management, companies that are planned together are grouped into one intercompany planning group. To specify, per company, which item allocation keys should be considered for demand forecasting, associate an item allocation key with the intercompany planning group member by going to **Master planning \> Setup \> Intercompany planning groups**.

By default, if no item allocation keys are assigned to intercompany planning group members, a demand forecast is calculated for all items that are assigned to all item allocation keys from all companies. Additional filtering options for companies and item allocation keys are available on the **Generate statistical baseline forecast** page.

Review the number of items that are forecasted. Unnecessary items might cause increased costs when you use Microsoft Azure Machine Learning.

## <a name="parameters"></a>Demand forecasting parameters

To set up demand forecasting parameters, go to **Master planning \> Setup \> Demand forecasting \> Demand forecasting parameters**. Because demand forecasting runs cross-company, the setup is global, which means that the setup applies to all legal entities (companies).

Demand forecasting generates the forecast in quantities. Therefore, the unit of measure that the quantity should be expressed in must be specified in the **Demand forecast unit** field. The unit of measure must be unique, to help ensure that the aggregation and percentage distribution make sense. For more information about aggregation and percentage distribution, see [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md). For every unit of measure that is used for SKUs that are included in demand forecasting, make sure that there is a conversion rule for the unit of measure and the general forecasting unit of measure. When forecast generation is run, the list of items that don't have a unit of measure conversion is logged, so you can easily correct the setup.

Demand forecasting can be used to forecast both dependent and independent demand. For example, if only **Sales order** is set to *Yes*, and if all the items that are considered for demand forecasting are items that are sold, the system calculates independent demand. However, critical subcomponents can be added to item allocation keys and included in demand forecasting. In this case, if **Production line** is set to *Yes*, a dependent forecast is calculated.

There are three methods for creating a baseline forecast. The **Forecast generation strategy** field lets you select between these three methods. Set it to one of the following values:
    - *Copy over historical demand* – Create forecasts simply by copying historical data.
    - *Azure Machine Learning Service* – Use a forecast model that runs using the new machine learning service for Azure. This is the current machine learning solution provided for Azure, so we recommend using it if you want to use a forecast model.
    - *Azure Machine Learning* – Use a forecast model that runs using the old (now deprecated) machine learning solution for Azure. This solution will soon be removed from Azure, so we recommend using *Azure Machine Learning Service* instead if you are setting up demand forecasting for the first time. You should also plan to switch to the new service soon if you are currently using the older solution.

<!--KFM: We should describe the purpose of the grid on the **Forecast algorithm parameters** FastTab. -->

Open the **Forecast dimensions** tab of the **Demand forecasting parameters** page to select the set of forecast dimensions to use when the demand forecast is generated. A forecast dimension indicates the level of detail that the forecast is defined for. Company, site, and item allocation key are required forecast dimensions, but you can also generate forecasts at the warehouse, inventory status, customer group, customer account, country/region, state, and item plus all item dimension levels.

At any time, you can add forecast dimensions to the list of dimensions that are used for demand forecasting. You can also remove forecast dimensions from the list. However, manual adjustments are lost if you add or remove a forecast dimension.

Not all items perform in the same manner from a demand forecasting perspective. Similar items can be grouped in one item allocation key, and parameters such as transaction types and forecast method settings can be set per item allocation key. Open **Item allocation keys** of the **Demand forecasting parameters** page. <!--KFM: And then what should we do?-->

<!--KFM: New material starts here -->

## Set up and connect Azure Machine Learning Service

Supply Chain Management calculates demand forecasts using the Azure Machine Learning Service, which you must set up and run on your own Azure subscription. This section describes how to set it up on Azure and then connect it with your Supply Chain Management environment.

<!--KFM: Mention the deprecation of the previous ML solution, and point out that this is the new version everyone should use from now on.  -->

### Enable the Azure Machine Learning Service in feature management

<!--KFM: Is this feature in preview? Starting with which version of SCM?  Do we now consider this feature to be required to use all of the features described in this topic? -->

Before you can use the Azure Machine Learning Service for demand forecasting, you must turn on a feature to enable the integration. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *Azure Machine Learning Service for demand forecasting* <!--KFM: Not available in the current build. Is this name correct? -->


### <a name="ml-workspace"></a>Set up your machine learning workspace on Azure

<!--KFM: Briefly describe what a machine learning workspace is and why we need one. -->

#### Step 1: Create a new workspace

Use the following procedure to create a new machine learning workspace.

1. Sign in to your Azure portal.
1. <!--KFM: Describe how to find and run the wizard. Tell what the wizard is called. Give a link to related Azure documentation if possible.-->
1. Work through the wizard following the instructions on your screen. Keep the following points in mind as you work:
    - Use default settings unless otherwise recommended in the other points of this list.
    - Be sure to select the geographic region that matches the region where your instance of Supply Chain Management is deployed. Otherwise, some of your data may pass through region boundaries. For details, see this [privacy note](#) <!--KFM: link needed -->.
    - Use dedicated resources such as resource group, storage account, container registry, Azure Key Vault, networking resources, and so on.
    - On the **Set up Azure Machine Learning Service connection parameters** page of the wizard, you must provide a storage account name. Use an account that is dedicated to demand forecasting. Demand forecasting input and output data will be stored in this storage account.

#### Step 2: Configure compute resources

<!--KFM: Briefly introduce what we are about to do here and why. -->

1. Sign in to your Azure portal.
1. <!--KFM: Describe more clearly how to get to the right page in Azure. Original text was: "Navigate to Studio web URL once the machine learning workspace is created (the link is available on the overview page of the workspace). " --> 
1. Select **Compute** on the navigation pane.
1. Use the **Compute** page to create the following compute resources: <!--KFM: We should either provide details about how to do this, or give a link to Azure documentation. -->
    - **Compute instance** – This will be used to create the demand forecasting pipeline (can be deleted after pipeline is published). Use default settings. <!--KFM: Is this a filed/setting name? How do I do these things? This should maybe have its own step. -->
    - **Compute cluster** – This will will be used to generate demand forecasts. Its settings affect performance and the maximum level of parallelization of the run. Use default settings except those mentioned in the following list: <!--KFM: Is this a filed/setting name? How do I do these things? This should maybe have its own step. -->
        - **Name** – Enter *e2ecpucluster*.
        - **Virtual machine size** – Adjust this setting according to the volume of data that you expect to use as an input to demand forecasting. The maximum nodes count should not exceed 11 because one node is needed to trigger the demand forecast generation and the maximum count of nodes that can then be used to generate a forecast is 10. (You will also set the node count in the `parameters.py` file, as described in the next section.) On each node, there will be several worker processes executing forecasting script in parallel. The total number of worker processes in your job will be *\[number of cores a node has\] \* node count*. For example, if your compute cluster has type Standard\_D4 (8 cores) and maximum 11 nodes, then the effective level of parallelism is 80, assuming `nodes_count` is set to 10 in `parameters.py`. <!--KFM: Why would the customer choose anything other than the max here? -->

#### Step 3: Create pipelines

<!--KFM: Briefly describe what a pipeline is and why we need one. -->

1. Download [these scripts from GitHub](https://github.com/microsoft/Dynamics-365-Supply-Chain-Management-Demand-Forecasting-With-Azure-Machine-Learning-Service).
1. <!--KFM: Provide full details of where to sign in and how to navigate to the right page/tab -->
1. On the **Notebooks** page, find the following location in the **Files** structure: **Users/\[current user\]/src**. <!--KFM: Does it matter which user we choose here? Any restrictions at all? -->
1. Upload the following files (which you downloaded in step 1) to the location you found in the previous step:
    - `parameters.py`
    - `api_trigger.py`
    - `run.py`
    - `REntryScript/forecast.r`
1. In Azure, open and review the `parameters.py` file that you just uploaded. Make sure the `nodes_count` value specified here is in sync with the created compute cluster <!-- KFM: What does "in sync" mean? The same? Greater than or equal to? -->. If the node count is less than maximum number of nodes in the cluster, the pipeline run might be able to start but then it will hang while waiting for the needed resources.
1. Select the `api_trigger.py` file that you just uploaded and run it. It will create a pipeline to be triggered through the API.

### <a name="aad-app"></a>Set up a new Active Directory application

A Active Directory application is needed authenticate to the resources dedicated to demand forecasting using service principal thus application should have least privilege needed to generate the forecast. <!--KFM: This sentence isn't clear. Please revise. -->

1. Sign in to your Azure portal.
1. Create a dedicated application in the tenant's Azure Active Directory <!--KFM: Either explain how to do this or provide a link to Azure documentation. -->
1. Follow the instructions on your screen as you work through the wizard. Keep default settings. <!--KFM: Is this a wizard? (I assumed so...) -->
1. Give your new Active Directory application access to the following resources (which you created created in [Set up your machine learning workspace on Azure](#ml-workspace)). <!--KFM: Either explain how to do this or provide a link to Azure documentation. --> This will enable the system to import and export forecasting data as well as trigger machine learning pipeline runs from Supply Chain Management.
    - Contributor role to the machine learning workspace.
    - Contributor role to the dedicated Storage account.
1. You will need details of this application later when you set up the **Demand forecasting parameters** in Supply Chain Management. Make a note of its application Id and its secret <!--KFM: Provide exact fields values and describe how to find them. -->. The secret must be created explicitly under the **Certificates & secrets** section of the created application <!--KFM: Do you mean the user needs to do this now? If so, add new steps with instructions and/or link to Azure documentation -->.

### Set up Azure Machine Learning Service connection parameters in Supply Chain Management

Use the following procedure to connect your Supply Chain Management environment to the machine learning service you just set up in Azure.

1. Sign in to Supply Chain Management.
1. Go to **Master planning \> Setup \> Demand forecasting \> Demand forecasting parameters**.
1. Open the **Azure Machine Learning Service** tab.

    ![Azure Machine Learning Service parameters](media/azure-ml-service-parameters.png "Azure Machine Learning Service parameters")

1. Make the following settings on the **Azure Machine Learning Service** tab:
    - **Tenant ID** – Enter the Azure Active Directory ID for your Azure tenant. Supply Chain Management will use this ID to authenticate with the Machine Learning Service. You can find your Azure Active Directory ID in Azure portal, Active directory overview. <!-- KFM: Provide more specific navigation. -->
    - **Service principal application ID** – Enter the application ID for the application you created in the [Active Directory Application](#aad-app) section of this topic. This value is used to authorize API requests to Azure Machine Learning Service.
    - **Service principal secret** – Enter the service principal application secret for the application you created in the [Active Directory Application](#aad-app) section of this topic. This value is used to authenticate the tenant in Azure Active Directory.
    - **Storage account name** – Enter the Azure storage account name that you specified when you ran the setup wizard on your Azure workspace (see also [Set up your machine learning workspace on Azure](#ml-workspace)).
    - **Pipeline endpoint address** – Enter the URL of the pipeline REST endpoint for your Azure Machine Learning Service. This is the pipeline you created as the last step when you [set up your machine learning workspace on Azure](#ml-workspace). To get pipeline URL, sign in to your Azure portal, go to **Pipelines \> Pipeline endpoints**, and choose **TriggerDemandForecastGeneration** <!-- KFM: Is this really the right label? -->; then copy the REST endpoint shown <!-- KFM: Can we describe this more accurately? -->.

### Set up Demand forecasting parameters in Supply Chain Management

Use the following procedure to configure Supply Chain Management to use the Azure Machine Learning Service for demand forecasting.

1. Sign in to Supply Chain Management.
1. Go to **Master planning \> Setup \> Demand forecasting \> Demand forecasting parameters**.
1. On the **General** tab, expand the **Forecast algorithm parameters** FastTab and set **Forecast generation strategy** to *Azure Machine Learning Service*.
1. Make other relevant configuration settings as described in [Demand forecasting parameters](#parameters).

You will be able to revert to an older **Forecast generation strategy** at any time until Azure ML Studio (classic) is fully removed from Azure <!-- KFM: Is this the correct product name? We need to be careful to always use the exact correct name of each of the very similar sounding Azure ML products. --> provided you already have an existing workspace. The application will continually warn you that Azure ML Studio (classic) has been deprecated, but that won't affect the forecasting result.

## Setup Azure Machine Learning (Deprecated)

<!--KFM: Add explanation that this product has been deprecated, so the reader should instead work through the previous section. Clearly contrast this with the new ML product and be careful to use the exact, official names for each product. -->

To generate the forecast, Supply Chain Management uses a machine learning web service. To connect to the service, you must provide the following information if you sign in to Microsoft Azure Machine Learning Studio (classic):

- Web service application programming interface (API) key
- Web service endpoint URL
- Azure storage account name
- Azure storage account key

> [!NOTE]
> The Azure storage account name and key are required only if you use a custom storage account. If you deploy the on-premises version, you must have a custom storage account on Azure, so that Machine Learning can access the historical data.

To create demand predictions, you can deploy your own service by using Machine Learning Studio or the Supply Chain Management demand forecasting experiments. Instructions for deploying the demand forecasting experiments as a web service are available in Supply Chain Management. On the **Demand forecasting parameters** page, open the **Azure Machine Learning** tab. <!-- KFM: We should explain what each of these settings does and mention whether they have any effect on the newer ML service. -->

## Settings for the demand forecasting machine learning service

<!-- KFM: Does this section apply for both the new and old Azure ML features? Or just the old one? Why are we describing the **Demand forecasting parameters** in two different sections of this topic? Maybe these should be combined. -->

To view the parameters that can be configured for the demand forecasting service, go to **Master Planning \> Setup \> Demand forecasting \> Forecasting algorithm parameters** to open the **Forecasting algorithm default parameters** page, which shows the default values for the parameters. You can overwrite these parameters by going to **Master Planning \> Setup \> Demand forecasting \> Demand forecasting parameters**, where you can do the following:

- Use the **General** tab to overwrite the parameters globally.
- Use the **Item allocation keys** tab to overwrite the parameters per item allocation key. Parameters that are overwritten for an item allocation key affect only the forecast of items that are associated with that item allocation key.

### Forecast algorithm parameters

On the **Item allocation keys** tab of the **Demand forecasting parameters** page, you can use the **Forecast algorithm parameters** FastTab to assign forecast algorithm parameters for the item allocation key currently selected in the grid on the left. Use the **Add** and **Remove** buttons on the toolbar to establish the required collection of parameters. For each parameter in the list, select one of the following values in the **Name** field and then enter an appropriate value in the **Value** field:

- **Confidence level percentage** – A confidence interval consists of a range of values that act as good estimates for the demand forecast. A 95% confidence level percentage indicates there is a 5% risk that the future demand falls outside the confidence interval range.
- **Force seasonality** – Specifies whether to force the model to use a certain type of seasonality. Applies to ARIMA and ETS only. Options: AUTO(default), NONE, ADDITIVE, MULTIPLICATIVE.
- **Forecasting model** – Options: ARIMA, ETS, STL, ETS+ARIMA, ETS+STL, ALL. To select best fit model, use **ALL**.
- **Maximum forecasted value** – Specifies the maximum value to use for predictions. Format: +1E[n] or numeric constant.
- **Minimum forecasted value** – Specifies the minimum value to use for predictions. Format: -1E[n] or numeric constant.
- **Missing value substitution** – Specifies how gaps in historical data are filled. Options: numeric value, MEAN, PREVIOUS, INTERPOLATE LINEAR, INTERPOLATE POLYNOMIAL.
- **Missing value substitution scope** – Specifies whether the value substitution applies only to the date range of each individual granularity attribute, or to the entire dataset. The following options are available for establishing the date range that the system uses when filling in gaps in historical data:

  - GLOBAL – The system uses the full range of dates of all granularity attributes.
  - HISTORY_DATE_RANGE – The system uses a specific date range defined by the **From date** and **To date** fields on the **Historical horizon** field group in the **Generate statistical baseline forecast** dialog box.
  - GRANULARITY_ATTRIBUTE – The system uses the date range of the currently processed granularity attribute.

  > [!NOTE]
  > A granularity attribute is a combination of forecast dimensions against which the forecast is done. You can define forecast dimensions on the **Demand forecasting parameters** page.

- **Seasonality hint** – For seasonal data, provide a hint to the forecasting model to improve forecast accuracy. Format: integer number, representing the number of buckets a demand pattern repeats itself. For example, enter "6" for data that repeats itself every 6 months.
- **Test set size percentage** – Percentage of historical data to be used as a test set for forecast accuracy calculation.

## Additional resources

- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)
- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
