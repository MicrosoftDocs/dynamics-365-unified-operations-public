---
# required metadata

title: Connected applications
description: This topic explains how to set up connected applications in Electronic invoicing.
author: dkalyuzh
ms.date: 02/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Connected applications

[!include [banner](../includes/banner.md)]

Connected applications are the instances of Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management that you might want to reach through Regulatory Configuration Service (RCS). Through the connected applications, you can configure part of your Globalization feature in Finance or Supply Chain Management to make the Electronic invoicing scenario work.

When you deploy your Globalization feature, the setup information that is applicable to your Finance or Supply Chain Management application can be published directly from RCS to the appropriate connected application.

Availability of the Finance or Supply Chain Management parameters in RCS is useful when you have several application environments, such as user acceptance testing (UAT) and production environments, and you want to keep the setup consistent by deploying the same parameters to different environments.

## Create a connected application

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Connected applications**.
4. Select **New** to create a connected application.
5. In the **Name** field, enter the name of the application to connect.
6. In the **Type** field, select **Dynamics 365 Finance**.
7. In the **Application** field, enter the URL of the environment to connect.
8. In the **Tenant** field, enter the tenant of the environment.
9. Select **Save**.
10. On the Action Pane, select **Check connection** to test the connection with the environment. Then close the page.

## Link connected applications to environments

1. On the **Environment setup** page, select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application.
3. In the **Service environment** field, select a service environment.
4. Select **Save**, and then close the page.
