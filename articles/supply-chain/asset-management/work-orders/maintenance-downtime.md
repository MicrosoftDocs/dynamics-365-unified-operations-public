---
# required metadata

title: Maintenance downtime
description: This topic describes maintenance downtime in Asset Management.
author: josaw1
manager: tfehr
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Maintenance downtime

[!include [banner](../../includes/banner.md)]


You can create maintenance downtime registrations on the asset that is selected on a work order. This capability is useful if you want to register maintenance downtime on one or more machines in the production area. You first create the maintenance downtime reason codes that you want to use, such as **Breakdown** and **Planned stop**. This step is done on the **Maintenance downtime reason codes** page. You can then create maintenance downtime registrations on the **Maintenance downtime** page and add the relevant maintenance downtime reason codes.

## Create maintenance downtime reason codes

1. Select **Asset management** > **Setup** > **Work orders** > **Maintenance downtime reason codes**.

2. Select **New**.

3. In the **Maintenance downtime reason code** field, enter an ID for the maintenance downtime reason code.

4. In the **Name** field, enter a name.

5. Select the **KPI include** check box if the reason code should be included in calculations of key performance indicators (KPIs) for the asset. In general, planned production stops should not be included in KPI calculations, because they don't affect expected performance.

6. Select **Save**.

The illustration below shows an example of the **Maintenance downtime reason codes** page.

![Figure 1](media/15-work-orders.png)

After you've created the maintenance downtime reason codes that you want to use, you can create maintenance downtime registrations for work orders and assets.


## Create maintenance downtime registrations

1. Click **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Select the work order, and then, on the **Work order** tab, in the **Asset** group, select **Maintenance downtime**.

3. Select **New**.

4. In the **From** and **To** fields, define the date and time interval for the maintenance downtime registration.

>[!NOTE]
>When you leave the **To** field, the duration in hours is automatically inserted in the **Duration** field.

5. In the **maintenance downtime reason code** field, select a reason code.

6. Repeat steps 3 through 5 to add more registrations.

7. Select **Save**.

The illustration below shows an example of maintenance downtime registration.

![Figure 2](media/16-work-orders.png)

The calendar that is used to calculate a maintenance downtime registration depends on your selection in the setup of assets and parameters. If a resource is selected on an asset in the **Resource** field on the **Fixed asset** FastTab of the **All assets** page, the calendar that is set up for the associated resource group is used, as shown in the following illustration.

![Figure 3](media/17-work-orders.png)

If no resource is selected on the asset, the standard calendar that is selected on the **Asset management parameters** page is used, as shown in the following illustration.

![Figure 4](media/18-work-orders.png)

To see an overview of all maintenance downtime registrations, click **Asset management** > **Inquiries** > **Maintenance downtime**.

>[!NOTE]
>All calendars that are used in the **Asset Management** module are set up in **Organization administration** > **Setup** > **Calendars** > **Calendars**.

