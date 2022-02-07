---
# required metadata

title: Connected applications
description: This topic provides information about how to set up Connected applications in Electronic invoicing.
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


Connected applications are the instances of Dynamics 365 Finance and Dynamics 365 Supply Chain Management that you might want to reach through the Regulatory Configuration Service (RCS). Through the connected applications, you can configure part of the Globalization feature in Finance or Supply Chain Management to make the Electronic invoicing scenario work.

When you deploy your Globalization feature, you can publish the setup information that's applicable to your Finance or Supply Chain Management applications, directly from RCS to the specific connected application.

Availability of the Finance or Supply Chain Management parameters in RCS provides an advantage when you have several application environments, like UAT and PROD, and want to keep consistency in setup by deploying the same parameters to different environments.

## Create a connected application

1. On the **Environments setup** page, on the Action Pane, select **Connected applications**.
2. Select **New** to create a connected application and in the **Name** field, enter the name of the application to connect.
3. In the **Type** field, select **Dynamics 365 Finance**.
4. In the **Application** field, enter the URL of the environment to connect.
5. In the **Tenant** field, enter the tenant of the environment.
6. Select **Save**.
7. On the Action Pane, select **Check connection** to test the connection with the environment, and then close the page.

## Link connected applications to environments

1. On the **Environments setup** page, select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application.
3. In the **Service environment** field, select a service environment.
4. Select **Save**, and then close the page.
