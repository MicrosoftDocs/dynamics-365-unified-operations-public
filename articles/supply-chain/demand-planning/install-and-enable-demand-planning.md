# Install and enable Demand Planning

This is a installation guide for Demand planning app for Dynamics 365 Supply Chain Management.

The guide will take you through steps in Power platform admin center to install the Demand planning application in your tenant.

Additional steps are required within the Dynamics 365 Supply Chain Management application to enable connection between the applications.

*Note: The Dynamics 365 Supply Chain Management application and Demand planning application must be installed in the same Tenant to ensure the data can be imported and exported using the built-in Microsoft finance and operation application import and export profiles.*

*[Note: A valid Dynamics 365 license is required to enable Dynamics 365 apps during the environment creation You can install and manage Dynamics 365 apps only in an environment that was created with a database and with Dynamics 365 apps enabled during the environment creation](https://learn.microsoft.com/en-us/power-platform/admin/manage-apps). If the*

## Install Demand planning app:

Sign into the Power Platform admin center.

Select **Resources &gt; Dynamics 365 apps** from the left-side menu.

Select **Demand planning (Preview)** app.

Select **Install** from the top menu bar.

Select an environment, review the packages to be installed, agree to the terms of service,

Select **Install.**

## Enable Demand planning app in Dynamics 365 Supply Chain Management. 

To enable Demand planning in Dynamics 365 Supply Chain Management (D365 SCM), you can follow these steps.

Open the **Feature management workspace** by selecting the appropriate title on the dashboard.

Search for **(Preview) Demand Planning** in Feature name. Read the feature details.

click the **"Enable now"** button to enable the feature.

*Note: When a feature has been turned on, it's still controlled by security. Therefore, the feature will be available only to users who have access to it based on their security role.*

*Note: A new privilege: '*Demand planning informational tile' *has been introduced. This privilege grant users' access to open Demand planning from a button on the dashboard page.*

*This new privilege has also been added to the following roles in the specified duties:*

| *Role name*          | *Duty*                               |
|----------------------|--------------------------------------|
| *Production planner* | *Maintain forecasts*                 |
| *Production planner* | *Maintain firming of planned orders* |
| *Production manager* | *Enable forecast process*            |
| *Production planner* | *Maintain forecast planning*         |
| *Production planner* | *Maintain demand forecasts*          |
| *Sales manager*      | *Maintain demand forecast*           |
| *Production manager* | *Enable the demand planning process* |

*In case you have custom defined roles, you will have to assign the privilege to these.*

*Note: As part of the feature enablement a new system role and user is created. A record is inserted into the Microsoft Entra ID applications enabling data exchange between applications*

For a user to be able to access the Demand planning application, the user must be allowed access to the dataverse environment with the **Demand planning service role** or **System administrator**. If you are the administrator of the environment on power platform admin center, you can add the users needed by selecting **Users** on the needed environment.

![A screenshot of a computer Description automatically generated](media/image3.png)

To enable the Demand planning app button to open the Demand planning application you must provide the applicable URL. This is a generic system parameter.

Navigate to **System administration – Setup – Demand planning app parameters.**

Insert the applicable URL into field **Demand planning app URL.**

Demand planning app is now installed, and you have also enabled it Dynamics 365 Supply Chain Management so data can be exchanged between applications. Demand planning app can be accessed from Dynamics 365 Supply Chain Management.

![](media/image4.png)

*Note: To Import or Export data you must configure the provider Microsoft finance and operation app in Demand planning app.*

For more detailed information, you can refer to the [**Feature Management Overview**](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) on Microsoft Learn. [It provides a comprehensive guide on how to use the Feature management workspace in D365 Finance and Operations](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview)

