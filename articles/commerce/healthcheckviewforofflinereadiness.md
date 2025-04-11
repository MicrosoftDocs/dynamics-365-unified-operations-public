---
title: Health check view for offline readiness
description: Learn about Health check view for offline readiness.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 03/31/2025
ms.reviewer: v-chrgriffin
ms.custom: 
  - bap-template
---

# Health check view for offline readiness

This article contains information about the new Health check view for offline readiness. This feature performs various checks to verify the status and readiness of the offline database, helping to prevent issues and ensures smooth offline switching.

## Key Features

**Database Connection Status**
- Check if DB/instance name exists: Verifies that the connection string is correct and the database instance name exists

-	Server is reachable: Ensures that the server is accessible and the necessary permissions are in place

**Download Session Status**
- Data synchronization: Confirms that data is completely synchronized

- Download success: Checks that all jobs have been successfully downloaded

**Database Information**
- SQL Instance Name: Retrieves the SQL instance name from the connection string

- Database Size: Provides the current size of the database

- Max Database Size: Displays the maximum allowable size for the database

-	DB index compression: Verifies that database index compression is enabled

-	Total & Available Disk Space: Shows the total and available disk space

**Current Device/User Exists**
-	Device and user verification: Checks if the currently activated device and logged-on employee exist in the offline 
  database

**Number of unresolved login attempts**
- Lists the number of unsuccessful login attempts.

 ## Healthcheck Operation

The healthcheck operation can be initiated from the current health check page or from the database connection status. The healthcheck operation will be availabe for all devices with offline capability installed.

When initiated, the operation performs the following checks:

- Database Connection Status: Ensures the connection string is correct and the server is reachable

-	Download Session Status: Confirms data synchronization and successful downloads

- Database Information: Retrieves SQL instance name, database size, maximum database size, and verifies index compression

- Disk Space: Displays total and available disk space

-	Device/User Verification: Checks the existence of the activated device and logged-on employee in the offline database

## Healthcheck Results
The results of the healthcheck operation are displayed in a pane on the right side of the POS screen. Each check's status is shown, indicating whether it passed or failed. If a check fails, detailed information is provided to help troubleshoot the issue.




  

