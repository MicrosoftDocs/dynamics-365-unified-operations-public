---
title: Health check view for offline readiness (preview)
description: Learn about the health check view for offline readiness feature in Microsoft Dynamics 365 Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: overview 
ms.date: 03/31/2025
ms.reviewer: v-chrgriffin
ms.custom: 
  - bap-template
---

# Health check view for offline readiness (preview)

[!INCLUDE [banner](includes/banner.md)]
[!INCLUDE [banner](includes/preview-banner.md)]

This article provides an overview of the health check view for offline readiness feature in Microsoft Dynamics 365 Commerce. This feature performs various checks to verify the status and readiness of the offline database to help prevent issues and ensure smooth offline switching.

## Key features

The health check view for offline readiness feature provides following the key features.

### Database connection status
- **Database/instance name exists**: Verifies that the connection string is correct and the database instance name exists.
-	**Server is reachable**: Ensures that the server is accessible and the necessary permissions are in place.

### Download session status
- **Data synchronization**: Confirms that data is synchronized.
- **Download success**: Checks that all jobs are successfully downloaded.

### Database information
- **SQL instance name**: Retrieves the SQL instance name from the connection string.
- **Database size**: Provides the current size of the database.
- **Maximum database size**: Displays the maximum allowable size for the database.
-	**Database index compression**: Verifies that database index compression is enabled.
-	**Total and available disk space**: Shows the total and available disk space.

### Current device/User exists
-	**Device and user verification**: Checks if the currently activated device and signed-in employee exist in the offline database.

### Unsuccessful sign-in attempts
- **Number of unresolved sign-in attempts**: Lists the number of unsuccessful sign-in attempts.

## Run the health check operation

You can initiate the health check operation from the current health check page or from the database connection status page. The health check operation is available for all devices with offline capability installed.

When initiated, the health check operation performs the following checks:

- **Database connection status**: Ensures that the connection string is correct and the server is reachable.
-	**Download session status**: Confirms data synchronization and successful downloads.
- **Database information**: Retrieves the SQL instance name, database size, and maximum database size and verifies index compression.
- **Disk space**: Displays total and available disk space.
-	**Device/user verification**: Checks the existence of the activated device and signed-in employee in the offline database.

### View health check results

The results of the health check operation are displayed in a pane on the right side of the point of sale (POS) screen. Each health check operation's status is shown, indicating whether it passed or failed. If a health check fails, the system provides detailed information to help troubleshoot the issue.

:::image type="content" source="dev-itpro/media/offlinehealthchecklearn.jpg" alt-text="Image showing the Available tests page with test results for the Offline database status test.":::


  

