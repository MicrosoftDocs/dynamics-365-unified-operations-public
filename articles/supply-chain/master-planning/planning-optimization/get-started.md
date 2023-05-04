---
title: Get started with master planning
description: This article explains how to start to use master planning functionality in Dynamics 365 Supply Chain Management. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
ms.topic: how-to
ms.date: 01/27/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Get started with master planning

[!include [banner](../../includes/banner.md)]

Master planning in Supply Chain Management is provided by an external service called the Planning Optimization Add-in for Dynamics 365 Supply Chain Management. This article explains how to obtain and set up that service.

## Availability

Planning Optimization is currently available in the following Azure geographies: United States, Canada, Brazil, Europe, France, United Kingdom, Norway, Switzerland, Australia, Asia Pacific, Japan, and India. If you try to install the add-in from another geographic region, then LCS will show a message that this geographic isn't supported. For more information about Azure geographies and the related regions, see [Azure geographies](https://azure.microsoft.com/global-infrastructure/geographies/#geographies).

> [!NOTE]
> Planning Optimization doesn't support on-premises deployments of Dynamics 365 Supply Chain Management.

## Licensing

If you can run master planning by using your current license, you don't have to buy an additional license to start to use Planning Optimization.

## <a name="install-enable-po"></a>Install and enable Planning Optimization

To use Planning Optimization, you must make sure your system has all of the prerequisites in place and then enable its license key and install the Planning Optimization Add-in for Dynamics 365 Supply Chain Management.

### Prerequisites

Before you install the Planning Optimization Add-in, the following prerequisites must be in place:

- You must be running Supply Chain Management on an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation won't complete and you'll need to cancel the installation.

- Your system must be set up for Power Platform integration. For more information, see [Microsoft Power Platform integration with finance and operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

- You must sign in to your Power Platform environment using an account with administrator privileges and an access mode of *Read-Write*. If you get an error message regarding missing user permissions while installing the Planning Optimization Add-in, follow these steps:
    1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. Open the environment where you want to install the add-in.
    1. Go to **Settings \> Users** and select your user account from the list to see its details.
    1. From your user details page, select the **Client Access License (CAL) information** link.
    1. On the **Client Access License (CAL) information** page, make sure that **Access Mode** is set to *Read-Write*.
  
    For more information about licenses and access modes for the Power Platform, see [Create a Power Platform admin account](/power-platform/admin/global-service-administrators-can-administer-without-license#create-a-power-platform-admin-account).

### Enable the Planning Optimization license

To use Planning Optimization, you must enable its configuration key. To do so:

1. Put your system into maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, select the check box for **Planning Optimization**.
1. Turn off maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

### Install the Planning Optimization Add-in

You must install the add-in from your LCS project and then turn on the Planning Optimization functionality from the Supply Chain Management user interface.

To install the Planning Optimization Add-in:

1. Sign in to LCS, and open the desired environment.
1. Go to **Full details**.
1. Scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Planning Optimization**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that Planning Optimization is installing.
1. After a few minutes, **Installing** should change to **Installed** (you may need to refresh the page). When installed, you're ready to activate Planning Optimization in Dynamics 365 Supply Chain Management.

The main purpose of installing the Planning Optimization add-in is to connect the service and the environment. Therefore, you must install the add-in separately on each environment where you'll use Planning Optimization, regardless of any code moved between the environments.

## Turn on Planning Optimization for your environment

After you've installed the Planning Optimization Add-in for your environment, you must enable it in Supply Chain Management before you can start using it.

### Enable Planning Optimization for your environment

To configure your system to use the Planning Optimization Add-in for master planning, follow these steps:

1. Sign in to Supply Chain Management.
1. Go to **Master planning** \> **Setup** \> **Planning Optimization parameters**.
1. Open the **General** tab.
1. Check the **Connection status**. It will show one of the values listed in the following table.

    | Connection status | Description | Can Planning Optimization be used? |
    |---|---|---|
    | Connected | A connection has been established between the Planning Optimization service and Supply Chain Management. | Yes |
    | Enabling connection | A request to turn on the connection to the Planning Optimization service is currently in progress. | No |
    | Disconnected | There's no connection to the Planning Optimization service. The connection can be turned on from LCS, as described earlier in this article. | No |
    | Disabling connection | A request to turn off the connection to the Planning Optimization service is currently in progress. | No |
    | Getting status | The system is waiting for status information from the Planning Optimization service. | No |

1. If the **Connection stats** is *Connected*, then you're ready to enable Planning Optimization. Use the **Use Planning Optimization** option to choose which planning engine is used for master planning. Select one of the following options:

    - *Yes* – Planning Optimization is used for master planning for all companies (unless overridden for one or more specific companies).
    - *No* – The deprecated master planning engine is used for master planning for all companies.

> [!NOTE]
> If existing planning batch jobs that were created for the deprecated master planning engine are triggered while the **Use Planning Optimization** option is set to *Yes*, those jobs will fail.

### <a name="exclude-po"></a>Continue to use deprecated master planning for some companies

Starting with Supply Chain Management version 10.0.32, it's possible allow some companies (legal entities) to run Planning Optimization while others continue to use the [deprecated master planning engine](../deprecated-master-planning-overview.md) until they are ready to be migrated, but you must obtain a special exception from Microsoft to do so (see also [Migration to Planning Optimization for master planning](../new-master-planning-engine.md)).

Follow these steps to set a company to use the deprecated master planning engine on an environment that is otherwise enabled to use Planning Optimization:

1. Use the company picker to choose the company (legal entity) that you want to set up.
1. Go to **Master planning \> Setup \> Planning Optimization parameters**.
1. Open the **Company information** tab.
1. Set **Exclude company from running Planning Optimization** to one of the following values
    - *Yes* – Use the deprecated master planning engine for this company.
    - *No* – Use Planning Optimization for this company.
1. Select **Save** on the Action Pane.
1. Repeat this procedure for each company you want to set up.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
