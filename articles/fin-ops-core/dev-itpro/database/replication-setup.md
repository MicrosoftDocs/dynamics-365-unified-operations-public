---
# required metadata

title: Replication setup
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: sarvanisathish
ms.date: 04/02/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sarvanis
ms.search.validFrom: 2021-04-30
---

# Replication setup

[!include[banner](../includes/banner.md)]

## Prerequisites

-	Source SQLServer should have enabled/installed replication feature.
-	SQL Agent should be running in the source database server.
-	SA Authentication: User should have DB_Owner privilege in Source Database & Target Database. In Source Database, the user should have access to masterDb and sourceDb
-	Update the target firewall by allow-listing the source IP. This can be done via LCS portal and this allows only for 8Hrs. After allow-listing execute this below sp in the target database to have access more than 8 Hrs.

  To reate database-level firewall setting for IP a.b.c.d:
  
  ```sql
  EXECUTE sp_set_database_firewall_rule N'AX 2012 Upgrade', 'a.b.c.d', 'a.b.c.d'; 
  ```


