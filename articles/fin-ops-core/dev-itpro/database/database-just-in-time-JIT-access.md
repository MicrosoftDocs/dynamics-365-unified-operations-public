---
title: Enable just-in-time database access
description: Learn how to enable database access in a just-in-time (JIT) fashion, including an outline on Microsoft-manage environments and self-service environments.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak

---

# Enable just-in-time database access

[!include [banner](../includes/banner.md)]

This article provides the steps necessary to enable database access by using a just-in-time (JIT) fashion. JIT is useful if you need access to the database for various troubleshooting efforts, running unplanned queries, or data upgrade problem solving. This process is available for both Lifecycle Services managed environments and Power Platform admin center managed environments. For more information about the available environment types, see [Deployment overview](../deployment/cloud-deployment-overview.md).

## Lifecycle Services managed self-service environments

The self-service environment type never had Remote Desktop Protocol (RDP) access or static database accounts. However, you can still access the database.

From the environment details page for your sandbox environment, select **Maintain** > **Enable access**. In the dialog box, add the IP address of your source environment. This firewall entry expires after eight hours or is lost after a database replacement by a database movement operation (whichever comes first). This condition includes operations such as database refresh or database import.

You also need to enter which type of access you require in the **Database Accounts** section. The available options include read or read-write access. Enter a short reason description and then select **Request access**.

:::image type="content" source="media/sql-jit2.png" alt-text="Screenshot of the Request access option.":::

When you refresh the page, the database account is shown with its expiry time.

:::image type="content" source="media/sql-jit3.png" alt-text="Screenshot of the database account shown with the expiry time.":::

You can now use tools like SQL Server Management Studio (SSMS) to connect to the database, by using the accounts from Lifecycle Services and the IP address that you enabled. Lifecycle Services shows the server and database in the following format: **serverName\databaseName**.  To connect in SSMS, you need to append the domain name suffix, such as **serverName.database.windows.net** if you're in Azure public cloud. On the **Options** tab in the SSMS connection window, you also need to explicitly enter the databaseName value in the **Database** field to successfully connect.

> [!NOTE]
> The domain name suffix might be different for Government Community Cloud (GCC).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
