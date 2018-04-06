---
# required metadata

title: Submit a service request to the Dynamics Service Engineering team
description: You can submit requests directly to the Dynamics Service Engineering team by using LCS. 
author: manalidongre
manager: AnnBe
ms.date: 03/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 254564
ms.assetid: 43ea0eae-34c8-4f97-8c98-c711844534d9
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Submit a service request to the Dynamics Service Engineering team

[!include[banner](../includes/banner.md)]

Submit a service request to the Dynamics Service Engineering team
=================================================================

A service request is a ticket for the Dynamics Service Engineering (DSE) team to
perform a pre-defined set of tasks on your environments.

>   **Note**: Do not use service requests for product issues. If you encounter a
>   situation that does not fall into any of the tasks described in this
>   article, please file a support ticket. For more information on support
>   tickets, see Find support for Microsoft Dynamics for Finance and Operations

You can submit service requests directly by using Lifecycle Services (LCS). You
can also view which requests have been submitted, executed and cancelled on your
environments.

>   **Note**: Microsoft frequently reviews all incoming service requests. By
>   selecting the correct service request type for your scenario you help DSE to
>   execute the request in a timely manner.

View service requests 
----------------------

There are two ways to view the service requests page.

1.  On the project dashboard, in the **Environments** pane, select **Service
    requests.**

![](media/0dc2b0a14dafe3282a9ea3434bef4ca4.png)

2.  On the LCS menu, click **Support**, and on the **Work items** page, select
    the **Service requests** tab.

![](media/2c537edf3dc67253ff0e24eb30549319.png)

>   By default, the **Service requests** page contains all requests that are
>   currently active or have been denied. You can toggle the filter to show
>   cancelled and finished requests.

![](media/60e34f86525c83ac0985cb652e6b4e3c.png)

>   After you have submitted a request, it will be in **Requested** status.
>   Before the DSE team acts on the request, they may ask for clarification by
>   entering a **Comment**.

>   For example, you might receive a comment from the DSE team if the production
>   environment deployment request is not in the same data center as the data
>   center where your sandbox environments are deployed.

>   Carefully review the comments and provide any required clarifications by
>   entering a comment yourself. To view the details of a specific request, or
>   to submit comments on a service request, click the **ID**.

>   **Note**: If you signed up for LCS Notifications, you will receive an email
>   when the status of a service request changes or a comment has been made.

>   If you submit a service request to DSE to perform an action that is outside
>   of their scope, the service request will be denied with a reason and a
>   suggested action. Common examples of service requests that are denied are
>   discussed later in this article.

Create service requests
-----------------------

There are two ways service requests can be created – **automatically**, when you
request an environment deployment, a package application, or an application
upgrade, and **on demand**, when you enter a request for a database refresh,
point-in-time restore, and other potential needs as described below.

### Create new service requests **automatically** 

-   **Environment deployment** – To set up deployment options and submit a
    request to the DSE team to deploy a new environment, go to the Environments
    pane and click **Configure**.

-   **Package application** – To apply a package to the production environment,
    on the **Environment details** page, click **Maintain** to select the
    package to apply, and then select **Schedule**. For more information, see [Apply updates to a cloud environment](../deployment/apply-deployable-package-system.md).

-   **Upgrade** – To have DSE upgrade one Sandbox: Standard Acceptance Test
    environment or production, go to the **Environment details** page for the
    environment that you are upgrading, select **Maintain**, and then select
    **Upgrade**. For more information, see [Process for moving to the latest
    update of Finance and Operations](../migration-upgrade/upgrade-latest-update.md).

### Create new service requests **on demand**

1.  To create a new service request on demand, go to the **Service requests**
    page and click **Add**.

![](media/2d962c0e943c5582caf07ad5dd68f68c.png)

2.  Select the service request type that you want to create. The options on the
    page are tailored to the specific type of service request that you selected.

-   **Database point-in-time restore request -** Use this request to restore a
    **non-production** database to a specific point in time. For details, see [Request a point-in-time restore](../database/request-point-in-time-restore.md).

>   **Note**:

-   To restore a **production** database during the **cutover phase**, follow
    the process outlined below in the **Other request** section.

-   If you need to restore a **production** database when you are already **live
    in operations**, please submit a **support issue** through LCS.

-   **Database refresh request -** Use this request to refresh a database from
    production to sandbox, or from one sandbox to another sandbox. For details,
    see [Request a sandbox database refresh](../database/database-refresh.md).

>   **Note**:

-   To refresh a database from a sandbox to production during the **cutover
    phase**, follow the process outlined below in the **Other request** section.

-   **Other request -** Use the request type for any of the following actions to
    be performed by the DSE team:

    -   **Database refresh** of your configuration data to **production** during
        the **cutover phase.** For details, see [Copy a Finance and Operations
        database from SQL Server to a production Azure SQL Database environment
        \> Raise a service request to copy database](../database/copy-database-from-sql-server-to-azure-sql#submit-a-service-request-to-copy-the-database).

>   **Note**: please phrase the service request exactly as described in the
>   article

-   **Restore** a **production** database during the **cutover phase** to a
    specific point in time

>   **Note**: please follow the same approach as described above for database
>   refresh to production. However, please word the request as follows:  
>     
>   “**This is a request for a point-in-time restore of production during the
>   cutover phase. Restore point in UTC: \<mm/dd/yyyy hh:mm in UTC\>. I
>   acknowledge that this will overwrite the database currently in
>   production.”**

-   Turn on **maintenance mode** in **production**. For details, see Maintenance
    Mode

-   Define explicit **IP whitelist rules** in **production**

-   Request **Power BI Embedded** to be activated on a Sandbox: Standard
    Acceptance Test environment or production if you get the message “**Power BI
    embedded is not enabled. Please contact your system administrator.**”

>   **Note**: Use the **Other request** exactly as described above. If the
>   request is formulated in a way that is not clear to the DSE team, they will
>   post a comment asking for clarification. If the **Other request** is used
>   for any request that is not listed above, the request will be denied.

>   Common examples of service requests that are denied:

-   You submitted an **Other request** to do the following when it should have
    been a **Support issue**:

    -   **Activate** a new **subscription estimate** after you are live in
        Production or have requested Production

    -   **Reset the Financial reporting data mart** in a release earlier than
        Finance and Operations Financial reporting release 7.2.6.0

    -   Restore a production database after go-live 

    -   If you ran into an **issue** after DSE performed an application upgrade

-   You submitted an **Other request** for an action that you should have
    requested through a different request type, for example, a database refresh
    in a non-production environment

-   You submitted an **Other request** for an action that you should perform
    yourself, for example, a database upgrade on a development environment

>   **Service requests that are created on demand are not explicitly accepted by
>   the DSE team. They will get actioned upon during the specified downtime
>   window unless the DSE team has commented on the request or had to deny the
>   request. Please carefully review the comments in the service request for
>   details.**


Service request types and Service Level Agreements (SLA’s)
----------------------------------------------------------
|    Service   request type              |    Applicable   to environments                                                                         |    Requested   service                                                                                                          |    Lead   time                      |    Down   time                                                                                                             |
|----------------------------------------|---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
|    Environment   deployment            |    Any                                                                                                  |    Environment   deployment                                                                                                     |    SLA: within 2   business days    |                                                                                                                            |
|    Package   application               |    Production                                                                                           |    Deployable package   application                                                                                             |    5 hours                          |    5 hours                                                                                                                 |
|    Upgrade                             |    One Sandbox: Standard   Acceptance Test and Production                                               |    Customer who is live   in production is requesting upgrade to the latest version of Dynamics for   Finance and Operations    |    5 business days                  |    8 hours                                                                                                                 |
|    Database   point-in-time restore    |    Any Tier 2 or higher   sandbox                                                                       |    Database   point-in-time restore                                                                                             |    5 hours                          |    1 hour                                                                                                                  |
|    Database   refresh                  |    From production to   any Tier 2 or higher sandbox;   Between any two Tier   2 or higher sandboxes    |    Database   refresh                                                                                                           |    5 hours                          |    1 hour                                                                                                                  |
|    Other                               |    Production                                                                                           |    Database   point-in-time restore                                                                                             |    5 hours                          |    1 hour                                                                                                                  |
|                                        |    Production                                                                                           |    Database   refresh                                                                                                           |    5 hours                          |    1 hour                                                                                                                  |
|                                        |    Production                                                                                           |    Maintenance mode                                                                                                             |    5 hours                          |    N/A. Customer   communicates on the service request when environment should be taken out of   Maintenance Mode again    |
|                                        |    Production                                                                                           |    IP whitelist rules                                                                                                           |    5 hours                          |    2 hours                                                                                                                 |
|                                        |    Production                                                                                           |    Power BI Embedded                                                                                                            |    5 hours                          |    2 hours                                                                                                                 |
|                                        |    Production                                                                                           |    Special fonts                                                                                                                |    5 hours                          |    2 hours                                                                                                                 |



