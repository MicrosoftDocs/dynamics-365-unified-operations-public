---
title: Error codes during dual-write sync
description: This article describes error codes for the table map health check.
author: jaredha
ms.date: 03/11/2024
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: jaredha
ms.search.validFrom: 2024-03-11
---

# Error codes during dual-write sync

[!include [banner](../../includes/banner.md)]

This article describes the error codes that can occur during dual-write processing, including both live sync and asynchronous integrations.

| Error code | Message | Detail |
| --- | --- | --- |
| DIPV1000 | Connection validation failed | <p>The error indicates that the Power Apps ApiHub connections used for data integration are not longer valid.</p><p>The error message details will show the actual cause of the validation failure. You should fix the connections as indicated or recreate the connection sets to ensure data integration continues to work. For more information, see [Reset dual-write connections](./reset.md).</p> | 
| DIPV1001 | Exceptions encountered during dual-write project validation | The error indicates that an unknown exception was encountered during dual-write project validation. For assistance in resolving the error, reach out to Microsoft support with the exception details. |
| DIPV1002 | Dual-write only supports mapping between cross-company entities or company-specific entities from both sides | <p>The finance and operations apps entity used in the table map has [Cross-company data sharing](../sysadmin/srs-overview) enabled. Dual-write is not supported for an entity when cross-company data sharing is enabled. See [Limitations](../sysadmin/srs-overview#limitations).</p><p>To resolve this error, either disable cross-company data sharing for the finance and operations apps entity or use a different entity for the table map.</p> |
| DIPV1003 | Integration keys are missing | <p>Integration key constitutes of at least one field to uniquely identify a table record and it's required for dual-write or data integration to work properly between Dataverse and finance and operations apps. The error indicates the Dataverse table used in the table map doesn't have an integration key defined.</p><p>To resolve this error: <ol><li> Open the [Power Apps maker portal](https://make.powerapps.com) of your Dataverse environment</li><li>Open the table defined in the table map</li><li>Define at least one alternate key for the Dataverse table.</li><li>In the Dual-write administration workspace in finance and operations apps, open the table map and select the **Refresh tables** action.</li></ol></p> | 
| DIPV1004 | Integration key field is not bi-directionally mapped | <p>The fields used in the integration key are not all bi-directionally mapped. If a dual-write table map is bi-directionally mapped, meaning that any of the field mappings are bi-directional between finance and operations apps and Dataverse, then ensure that all integration key fields are also bi-directionally mapped to ensure dual-write live sync is able to locate a given record in either finance and operations apps or the Dataverse environment. | 
| DIPV1005 | Missing environment info for dataset | The error indicates that dual-write connection set is either misconfigured or corrupted. To resolve this error, reset the dual-write connection set following the steps outlined in [Reset dual-write connections](./reset.md). | 
| DIPV1006 | Exceptions encountered during project validation | The error indicates that an unknown exception was encountered during dual-write project validation. For assistance in resolving the error, reach out to Microsoft support with the exception details. |
| DIPV1007 | Task has environment which does not exist in the connection set | The error indicates the integration project is either misconfigured or corrupted. To resolve this error, recreate teh data integration project. | 
| DIPV1008 | Data partition is not valid | The organization mapping in the connection set used by the Data Integrator project becomes invalid after the customer deletes or changes the name of the business unit in Dataverse or legal entity in finance and operations apps.</p><p>To resolve this error, either re-add or rename the missing business unit or legal entity, or recreate the connection set and data integration project. |
| DIPV1010 |  |  |
| DIPV1011 |  |  |
| DIPV1012 |  |  |
| DIPV1014 |  |  |
| DIPV1015 |  |  |
| DIPV1016 |  |  |
| DIPV1017 |  |  |
| DIPV1018 |  |  |
| DIPV1019 |  |  |
| DIPV1020 |  |  |
| DIPV1021 |  |  |
| DIPV1022 |  |  |
| DIPV1023 |  |  |
| DIPV1024 |  |  |
| DIPV1025 |  |  |
| DIPV1026 |  |  |
| DIPV1027 |  |  |
| DIPV1028 |  |  |
| DIPV1029 |  |  |
| DIPV1030 |  |  |
| DIPV1031 |  |  |


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
