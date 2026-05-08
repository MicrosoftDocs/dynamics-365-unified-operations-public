---
title: Configure SQL Server Reporting Services for on-premises deployments
description: Learn about configuring SQL Server Reporting Services (SSRS) for an on-premises deployment, including a step-by-step list that details the configuring process.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.date: 04/09/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8
ms.assetid: 
ms.service: dynamics-365-op
search.app:
  - financeandoperationsonprem-docs
ms.custom: sfi-image-nochange
---

# Configure SQL Server Reporting Services for on-premises deployments

[!include [banner](../includes/banner.md)]

Use the steps in this article to configure SQL Server Reporting Services (SSRS) for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment.

> [!IMPORTANT]
> Only follow this guide if you deployed your environment by using a base deployment older than Application version 10.0.17 (with Platform update 41).

1. Open the Reporting Services Configuration Manager application.
1. Leave the default **Server name**, which should be the name of the current machine, and the **Report Server Instance**, **MSSQLSERVER**.
1. Select **Connect**.

    :::image type="content" source="./media/ssrs-config-manager-01.png" alt-text="Screenshot of the Reporting Services Configuration Manager connection settings.":::

1. Select the **Service Account** tab and verify that the settings match the following graphic.

    > [!NOTE]
    > SQL Server Reporting Services 2019 no longer supports choosing the **Local System** account. Instead, use the **NETWORK SERVICE** account.

    :::image type="content" source="./media/ssrs-config-manager-02.png" alt-text="Screenshot of the Service Account tab in Reporting Services Configuration Manager.":::

1. Select the **Web Service URL** tab and verify that the settings match the following graphic.

    :::image type="content" source="./media/ssrs-config-manager-03.png" alt-text="Screenshot of the Web Service URL tab in Reporting Services Configuration Manager.":::

1. Select the **Database** tab and verify that the **Database Name** and **Credential settings** match the following graphic.

    > [!NOTE]
    > You need to create a new database. To do this, select **Change Database**, and then verify that the new database name is: **DynamicsAxReportServer**.

    :::image type="content" source="./media/ssrs-config-manager-04.png" alt-text="Screenshot of the Database tab in Reporting Services Configuration Manager.":::

1. Select the **Web Portal URL** tab and verify that the settings match the following graphic.

    > [!NOTE]
    > You must select **Apply** to create and properly configure the portal.

    :::image type="content" source="./media/ssrs-config-manager-05.png" alt-text="Screenshot of the Web Portal URL tab in Reporting Services Configuration Manager.":::

    After the portal is configured, the **Web Portal** tab matches the following graphic.

    :::image type="content" source="./media/ssrs-config-manager-06.png" alt-text="Screenshot of the Web Portal tab in Reporting Services Configuration Manager after configuration.":::

1. Select the reports URL to view the SQL Server Reporting Services web portal.
1. When you're in the portal, create a new folder named **Dynamics**.

    :::image type="content" source="./media/ssrs-config-manager-07.png" alt-text="Screenshot of the Dynamics folder created in the SQL Server Reporting Services web portal.":::

1. In the **Reporting Services Configuration Manager**, select the **E-mail Settings** tab and verify that the settings match the following graphic.

    :::image type="content" source="./media/ssrs-config-manager-08.png" alt-text="Screenshot of the E-mail Settings tab in Reporting Services Configuration Manager.":::

1. Select the **Execution Account** tab and verify that the settings match the following graphic.

    :::image type="content" source="./media/ssrs-config-manager-09.png" alt-text="Screenshot of the Execution Account tab in Reporting Services Configuration Manager.":::

    Don't change the default settings on the **Encryption Keys** tab.

    :::image type="content" source="./media/ssrs-config-manager-10.png" alt-text="Screenshot of the Encryption Keys tab in Reporting Services Configuration Manager.":::

1. Select the **Subscription Settings** tab, and verify that the settings match the following graphic.

    :::image type="content" source="./media/ssrs-config-manager-11.png" alt-text="Screenshot of the Subscription Settings tab in Reporting Services Configuration Manager.":::

    Don't change the default settings on the **Scale-out Deployment** tab.

    :::image type="content" source="./media/ssrs-config-manager-12.png" alt-text="Screenshot of the Scale-out Deployment tab in Reporting Services Configuration Manager.":::

    Don't change the default settings on the **Power BI Integration** tab.

    :::image type="content" source="./media/ssrs-config-manager-13.png" alt-text="Screenshot of the Power BI Integration tab in Reporting Services Configuration Manager.":::

1. Select **Exit** to close the **Reporting Services Configuration Manager**.

    :::image type="content" source="./media/ssrs-config-manager-14.png" alt-text="Screenshot of the Exit button to close the Reporting Services Configuration Manager.":::

1. For SQL Server 2019 only, you need to manually grant **NETWORK SERVICE** the permissions to read the private keys of these certificates:
    - DataEncryption
    - DataSigning
    - ReportingService

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
