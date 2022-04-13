---
# required metadata

title: Configure SQL Server Reporting Services for on-premises deployments
description: This topic provides information about configuring SQL Server Reporting Services (SSRS) for an on-premises deployment.
author: PeterRFriis
ms.date: 06/23/2017
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 55651
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: peterfriis
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8

---
# Configure SQL Server Reporting Services for on-premises deployments

[!include [banner](../includes/banner.md)]

Use the steps in this topic to configure SQL Server Reporting Services (SSRS) for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment.

1. Open the Reporting Services Configuration Manager application.
2. Leave the default **Server name**, which should be the name of the current machine, and the **Report Server Instance**, **MSSQLSERVER**.
3. Click **Connect**.

    [![Reporting services configuration connection.](./media/ssrs-config-manager-01.png)](./media/ssrs-config-manager-01.png)

4. Click the **Service Account** tab and verify that the settings match the following graphic.

    [![Service account tab.](./media/ssrs-config-manager-02.png)](./media/ssrs-config-manager-02.png)

5. Click the **Web Service URL** tab and verify that the settings match the following graphic.

    [![Web service URL tab.](./media/ssrs-config-manager-03.png)](./media/ssrs-config-manager-03.png)

6. Click the **Database** tab and verify that the **Database Name** and **Credential settings** match the following graphic.

    > [!NOTE]
    > You will need to create a new database. To do this, click **Change Database**, and then verify that the new database name is: **DynamicsAxReportServer**.

    [![database tab.](./media/ssrs-config-manager-04.png)](./media/ssrs-config-manager-04.png)

7. Click the **Web Portal URL** tab and verify that the settings match the following graphic.

    > [!NOTE]
    > You must click **Apply** to create and properly configure the Portal.

    [![web portal url tab.](./media/ssrs-config-manager-05.png)](./media/ssrs-config-manager-05.png)

    After the Portal is configured, the **Web Portal** tab will match the following graphic.

    [![web portal tab.](./media/ssrs-config-manager-06.png)](./media/ssrs-config-manager-06.png)

8. Click the reports URL to view the SQL Server Reporting Services web portal.
9. When you are in the portal, create a new folder named **Dynamics**.

    [![dynamics folder.](./media/ssrs-config-manager-07.png)](./media/ssrs-config-manager-07.png)

10. In the **Reporting Services Configuration Manager**, click the **E-mail Settings** tab and verify that the settings match the following graphic.

    [![email settings tab.](./media/ssrs-config-manager-08.png)](./media/ssrs-config-manager-08.png)

11. Click the **Execution Account** tab and verify that the settings match the following graphic.

    [![execution account tab.](./media/ssrs-config-manager-09.png)](./media/ssrs-config-manager-09.png)

    Don't change the default settings on the **Encryption Keys** tab.

    [![encryption keys tab.](./media/ssrs-config-manager-10.png)](./media/ssrs-config-manager-10.png)

12. Click the **Subscription Settings** tab, and verify that the settings match the following graphic.

    [![subscription settings tab.](./media/ssrs-config-manager-11.png)](./media/ssrs-config-manager-11.png)

    Don't change the default settings on the **Scale-out Deployment** tab.

    [![scale-out deployment tab.](./media/ssrs-config-manager-12.png)](./media/ssrs-config-manager-12.png)

    Don't change the default settings on the **Power BI Integration** tab.

    [![power bi integration tab.](./media/ssrs-config-manager-13.png)](./media/ssrs-config-manager-13.png)

13. Click **Exit** to close the **Reporting Services Configuration Manager**.

    [![close reporting services configuration manager.](./media/ssrs-config-manager-14.png)](./media/ssrs-config-manager-14.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
