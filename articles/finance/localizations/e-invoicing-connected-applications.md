---
# required metadata

title: Connected applications
description: This topic provides description of setup of Connected applications in Electronic invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]


Connected applications are the instances of Finance and Supply Chain Management that you might want to reach through RCS. 
Through the connected applications, you can configure part of the Globalization feature in Finance and Supply Chain Management to make the whole Electronic invoicing scenario work.

To learn how to set up parameters of the Connected applications, see [Work with Application setup]

When you deploy your Globalization feature, you can publish the setup information, applicable to your Finance and Supply Chain Management applications, directly from RCS to the particular connected application.

Availability of the Finance and Supply Chain Management parameters in RCS gives a big advantage when you have several application environments, like UAT and PROD, and want to keep consistency in setup by deploying the same parameters to different environments of Finance and Supply Chain Management applications.

## Create a connected application
1. On the **Environments setup** page, on the Action Pane, select **Connected applications**.
2. Select **New** to create a connected application.
3. In the **Name** field, enter the name of the application to connect.
4. In the **Type** field, select ***Dynamics 365 Finance***
5. In the **Application** field, enter the URL of the Finance or Supply Chain Management environment to connect.
6. In the **Tenant** field, enter the tenant of the Finance or Supply Chain Management environment.
7. Select **Save**.
8. On the Action Pane, select **Check connectio**n to test the connection with the environment. Then close the page.

## Link connected applications to environments
1. On the **Environments setup** page, select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application.
3. In the **Service environment** field, select a service environment.
4. Select **Save**, and then close the page.
