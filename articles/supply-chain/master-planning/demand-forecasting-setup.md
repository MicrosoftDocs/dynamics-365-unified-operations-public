---
# required metadata

title: Demand forecasting setup
description: This topic describes the setup tasks that you must perform to prepare for demand forecasting.  
author: ChristianRytt
ms.date: 08/09/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanDefaultAlgorithmParameters, ReqDemPlanForecastParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 72653
ms.assetid: c5fa4b09-512d-4349-ac51-cc13da69a160
ms.search.region: global
ms.search.industry: Manufacturing
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

## Demand forecasting parameters

To set up demand forecasting parameters, go to **Master planning \> Setup \> \> Demand forecasting \> Demand forecasting parameters**. Because demand forecasting runs cross-company, the setup is global. This means that the setup applies to all companies.

Demand forecasting generates the forecast in quantities. Therefore, the unit of measure that the quantity should be expressed in must be specified in the **Demand forecast unit** field. The unit of measure must be unique, to help ensure that the aggregation and percentage distribution make sense. For more information about aggregation and percentage distribution, see [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md). For every unit of measure that is used for SKUs that are included in demand forecasting, make sure that there is a conversion rule for the unit of measure and the general forecasting unit of measure. When forecast generation is run, the list of items that don't have a unit of measure conversion is logged, so that you can easily correct the setup.

Demand forecasting can be used to forecast both dependent and independent demand. For example, if only the **Sales order** check box is selected, and if all the items that are considered for demand forecasting are items that are sold, the system calculates independent demand. However, critical subcomponents can be added to item allocation keys and included in demand forecasting. In this case, if the **Production line** check box is selected, a dependent forecast is calculated.

There are three methods for creating a baseline forecast. You can use forecasting models on top of historical data, or you can just copy over the historical data to the forecast. The **Forecast generation strategy** field lets you select between these three methods. To use forecast models, set this field to either *Azure Machine Learning Service* (preferred) or *Azure Machine Learning* (now deprecated).

By selecting **Forecast dimensions** in the left pane of the **Demand forecasting parameters** page, you can also select the set of forecast dimensions to use when the demand forecast is generated. A forecast dimension indicates the level of detail that the forecast is defined for. Company, site, and item allocation key are required forecast dimensions, but you can also generate forecasts at the warehouse, inventory status, customer group, customer account, country/region, state, and item plus all item dimension levels.

At any point, you can add forecast dimensions to the list of dimensions that are used for demand forecasting. You can also remove forecast dimensions from the list. However, manual adjustments are lost if you add or remove a forecast dimension.

Not all items perform in the same manner from a demand forecasting perspective. Similar items can be grouped in one item allocation key, and parameters such as transaction types and forecast method settings can be set per item allocation key. Select **Item allocation keys** in the left pane of the **Demand forecasting parameters** page.

<!--KFM: New material starts here -->

## Set up Azure Machine Learning Service

Demand forecasting is performed in a customer's own Azure subscription while integrated with Dynamics 365 Supply Chain Management. To prepare the subscription for the feature, a series of configuration actions must be done according to the following guide.

### Machine learning workspace

#### Create new workspace

Use the wizard available in Azure portal that creates a new machine learning workspace, few key points to keep in mind:

- Use default settings unless other recommended below
- Make sure that selected region is the same as the region of your instance of Dynamics 365 Supply Chain Management is deployed to otherwise some data might be passing region boundaries, please see[privacy note](#) <!--KFM: link needed --> for the details.
- Use dedicated resources such as resource group, storage account, container registry, keyvault, networking resources, etc. Note that storage account name is needed for configuration on the "Set up Azure Machine Learning Service connection parameters" form.

#### Configure compute resources

Navigate to Studio web URL once the machine learning workspace is created (the link is available on the overview page of the workspace). Then choose Compute navigation menu item. Please create these compute resources:

- Compute instance. It will be used to create the demand forecasting pipeline (can be deleted after pipeline is published). Use default settings.
- Compute cluster. it will be used to generate demand forecast and its settings affect performance and the maximum level of parallelization of the run. Use default settings except those stated below:
  - Name: e2ecpucluster.
  - Virtual machine size: this setting must be adjusted according to the volume of data that will be used as an input to demand forecasting. Max nodes count should not exceed 11 since 1 will be used to trigger the demand forecast generation and max count of nodes to generate actual forecast is 10 (adjusted in the parameters.py file described in the next step). On each node there will be several worker processes executing forecasting script in parallel. The total number of worker processes in your job is \[number of cores a node has\] \* node count. Example, if the compute cluster has type Standard\_D4 (8 cores) and max 11 nodes, then the effective level of parallelism is 80 taken into account node count set to 10 in parameters.py.

#### Create pipelines

Download scripts from [github repository](https://github.com/microsoft/Dynamics-365-Supply-Chain-Management-Demand-Forecasting-With-Azure-Machine-Learning-Service) and upload following files under Notebooks/Users/\[current user\]/src:

- parameters.py
- api\_trigger.py
- run.py
- REntryScript/forecast.r

Review parameters.py and make sure node count is in sync with the created compute cluster. If node count is less than max number of nodes in the cluster – pipeline run might be able to start but will be hanging awaiting for the needed resources.

Then select api\_trigger.py and run it: it will create a pipeline to be triggered through API.

### Active Directory Application

This online service authenticates to the resources dedicated to demand forecasting using service principal thus application should have least privilege needed to generate the forecast.

Create a dedicated application in the tenant's Azure Active Directory – keep default settings. Give it access to the following resources created during step 1 to be able to import/export forecasting data as well as trigger machine learning pipeline runs from Dynamics 365 Supply Chain Management:

- Contributor role to the Machine learning workspace.
- Contributor role to the dedicated Storage account.

Details of this application will be needed for demand forecasting parameters set up: application Id and its secret. The secret must be created explicitly under Certificates & secrets section of the created application.

### Set up Azure Machine Learning Service connection parameters

Follow the steps below to configure Dynamics 365 Supply Chain Management to use resources created earlier in this guide for demand forecast generation:

Navigate to Demand forecasting parameters form and set the fields:

![Azure Machine Learning Service parameters](media/azure-ml-service-parameters.png "Azure Machine Learning Service parameters")

- **Tenant ID** – Azure Tenant ID. The tenant's ID for Azure Active Directory will be used to authenticate access to the Machine Learning Service. Can be found in Azure portal, Active directory overview.
- **Service principal application ID** – The service principal application ID is used to authorize API requests to Azure Machine Learning Service. The ID belongs to the application created during step 2 of the current guide.
- **Service principal secret** – The service principal application secret is used to authenticate the tenant in Azure Active Directory. The secret is the one that was created for the application during step 2 of the current guide.
- **Storage account name** – Azure storage account name. Demand forecasting input and output data will be stored in this storage account. Use an account that is dedicated to demand forecasting. Storage account name was chosen during creation of the Machine learning workspace – step 1.1.
- **Pipeline endpoint address** – Pipeline REST endpoint address. This address is in the Azure Machine Learning workspace after step 1.3 of the configuration is complete. To get pipeline ULR, open Pipelines \> Pipeline endpoints and choose TriggerDemandForecastGeneration, then copy its REST endpoint.

### Using demand forecasting with new Azure Machine Learning Studio

Azure Machine Learning Service needs to be selected as a Forecast generation strategy on the General section of the Demand forecasting parameters form to start using the new way of generating demand forecast. After configuration is done – demand forecast can be generated as with any other strategy.

It is possible to switch to an old Azure Machine Learning strategy at any time until the full removal of the Azure ML Studio (classic) given that there is an existing workspace although the application will keep warning about coming obsoletion which won't affect the forecasting result.

## Setup Azure Machine Learning (Deprecated)

<!--KFM: New material ends here. Add explanation and link for deprecation here -->

To generate the forecast, Supply Chain Management uses a machine learning web service. To connect to the service, you must provide the following information if you sign in to Microsoft Azure Machine Learning Studio (classic):

- Web service application programming interface (API) key
- Web service endpoint URL
- Azure storage account name
- Azure storage account key

> [!NOTE]
> The Azure storage account name and key are required only if you use a custom storage account. If you deploy the on-premises version, you must have a custom storage account on Azure, so that Machine Learning can access the historical data.

To create demand predictions, you can deploy your own service by using Machine Learning Studio or the Supply Chain Management demand forecasting experiments. Instructions for deploying the demand forecasting experiments as a web service are available in Supply Chain Management. On the **Demand forecasting parameters** page, open the **Azure Machine Learning** tab.

## Settings for the demand forecasting machine learning service

To view the parameters that can be configured for the demand forecasting service, go to **Master Planning \> Setup \> Demand forecasting \> Forecasting algorithm parameters**. The **Forecasting algorithm default parameters** page shows the default values for the parameters. You can overwrite these parameters by going to **Master Planning \> Setup \> Demand forecasting \> Demand forecasting parameters**, where you can do the following:

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
