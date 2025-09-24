---
title: Health check view for offline readiness
description: Learn about the health check view for offline readiness feature in Microsoft Dynamics 365 Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: overview 
ms.date: 04/25/2025
ms.reviewer: v-chrgriffin
ms.custom: 
  - bap-template
---

# Health check view for offline readiness

[!INCLUDE [banner](includes/banner.md)]

This article provides an overview of the health check view for offline readiness feature in Microsoft Dynamics 365 Commerce. This feature performs various checks to verify the status and readiness of the offline database. In this way, it helps prevent issues and ensure smooth offline switching.

## Key features

The health check view for offline readiness feature provides the following key features.

### Database connection status

- **Database/instance name exists**: Verifies that the connection string is correct, and that the database instance name exists.
- **Server is reachable**: Ensures that the server is accessible, and that the necessary permissions are in place.

### Download session status

- **Data synchronization**: Confirms that data is synchronized.
- **Download success**: Checks that all jobs are successfully downloaded.

### Database information

- **SQL Server instance name**: Retrieves the SQL Server instance name from the connection string.
- **Database size**: Provides the current size of the database.
- **Maximum database size**: Displays the maximum allowable size of the database.
- **Database index compression**: Verifies that database index compression is enabled.
- **Total and available disk space**: Shows the total and available disk space.

### Current device/user existence

- **Device and user verification**: Checks whether the currently activated device and signed-in employee exist in the offline database.

### Unsuccessful sign-in attempts

- **Number of unresolved sign-in attempts**: Lists the number of unsuccessful sign-in attempts.

## Run the health check operation

You can initiate the health check operation from either the current health check page or the database connection status page. The health check operation is available for all devices where offline capability is installed.

When the health check operation is initiated, it performs the following checks:

- **Database connection status**: Ensures that the connection string is correct, and that the server is reachable.
- **Download session status**: Confirms data synchronization and successful downloads.
- **Database information**: Retrieves the SQL Server instance name, database size, and maximum database size, and verifies index compression.
- **Disk space**: Displays the total and available disk space.
- **Device/user verification**: Checks for the existence of the activated device and signed-in employee in the offline database.

### View health check results

The results of the health check operation are displayed in a pane on the right side of the point of sale (POS) screen, as shown in the following example image.

:::image type="content" source="dev-itpro/media/offlinehealthchecklearn.jpg" alt-text="Image showing the Available tests page with test results for the Offline database status test.":::

The status of each health check operation is shown, and indicates whether the operation passed or failed. If a health check fails, the system provides detailed information to help you troubleshoot the issue.
