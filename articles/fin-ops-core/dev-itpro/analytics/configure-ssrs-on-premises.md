---
title: Configure SQL Server Reporting Services for on-premises deployments
description: This article provides information about configuring SQL Server Reporting Services (SSRS) for an on-premises deployment.
author: faix
ms.date: 01/31/2023
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8
ms.assetid: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---
# Configure SQL Server Reporting Services for on-premises deployments

[!include [banner](../includes/banner.md)]

Use the steps in this article to configure SQL Server Reporting Services (SSRS) for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment.

> [!IMPORTANT]
> Only follow this guide if your environment was deployed using a base deployment older than Application version 10.0.17 (with Platform update 41).

1. Open the Reporting Services Configuration Manager application.
2. Leave the default **Server name**, which should be the name of the current machine, and the **Report Server Instance**, **MSSQLSERVER**.
3. Click **Connect**.

    [![Reporting services configuration connection.](./media/ssrs-config-manager-01.png)](./media/ssrs-config-manager-01.png)

4. Click the **Service Account** tab and verify that the settings match the following graphic.

    > [!NOTE]
    > SQL Server Reporting Services 2019 no longer allows choosing the **Local System** account. Instead you need to use **NETWORK SERVICE** account.

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

14. For SQL Server 2019 only, you need to manually grant **NETWORK SERVICE** the permissions to read the private keys of these certificates.
    - DataEncryption
    - DataSigning
    - ReportingService

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
