This article shows how to setup integration with Microsoft Sustainability Manager to calculate carbon emission during the rate and route planning. A transporatation planner can then make decision to assign the most envrionment friendly transporatation service provider to the load.

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:
- You must be running Dynamics 365 Supply Chain Management 10.0.39 version or later.
- You must have valid Microsoft Sustainability Manager subscription.


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
