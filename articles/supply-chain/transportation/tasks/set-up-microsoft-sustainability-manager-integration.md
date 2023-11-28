This article provides a detailed guide on integrating with Microsoft Sustainability Manager to accurately calculate carbon emissions during rate and route planning in transportation management. By leveraging this integration, transportation planners can make informed decisions, strategically assigning environmentally-friendly transportation service providers to each load.

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:
- You must be running Dynamics 365 Supply Chain Management 10.0.38 version or later.
- You must have valid Microsoft Sustainability Manager subscription.
- The Microsoft Sustainability Manager version must be 2.14.0.355 or later.


## Setup in Power Platform
1. Microsoft Sustainability Manager solution is successfuly installed.
2. Enable inpersonation for FinOps in power platform. Go to **Power Platform Admin Center (PPAC) > Environment > Settings > Features**, Check the [Enable Finance and Operations User Impersonation] checkbox, save the changes.
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/d07324e0-b914-45d3-840e-1de7838a5a7a)


## Setup in Dynamics 365 Supply Chain Management

### Turn on the intergration between Transportation Management and Microsoft Sustainability Manager feature
1.	Go to **System administration > Workspaces > Feature management**. (For more information about how to use the Feature management workspace, see Feature management overview.)
2.	If not already on, turn on the feature that is listed in the following way:
   - **Module**: Transportation management
   - **Feature name**: Integrate Microsoft Sustainability Manager with transportation management


### Set up transportation mode mapping
You need to map **Transportation method in Dynamics 365 SCM** with the value of **Transportation Mode in Microsoft Sustainability Manager** for the carbon emission calculation.

1. Go to **Transportation management -> Setup -> Carriers -> Transportation methods**
2. In the **Transportation Mode in Microsoft Sustainability Manager** field, select value map with Transportation method used in Transportation management. 
> ![Note]: The transportation mode (vehicle type) are taken from EPA's GHG Emission Factors Hub which is used in Microsoft Sustainability Manager's Transportation and distribution calulation model.
> For more information about EPA's GHG Emission Factors Hub, see https://www.epa.gov/climateleadership/ghg-emission-factors-hub
>
3. Select **Save**.

### Validate the connection and enable the integration scenario 

1. Go to **Transportation management -> Setup -> Transportation management parameters**. 
2. Select **Microsoft Cloud for Sustainability integration configuration** tab.
3. Click on **Validate connection** to validate Power platform environment is all set up and ready for the integration.
4. Once validation passed, select a model in field **Model Name** from the drop-down menu.
> [Note:] Below link shows how Microsoft Sustainability Manager process the Scope 3 emission calculation: https://learn.microsoft.com/en-us/industry/sustainability/calculate-scope3#categories-4-and-9-upstream-and-downstream-transportation-and-distribution

5. Activate the toggle for **Enable McFS integration**
6. Select **Save**.
