---
title: Dual-write configuration health check
description: This article describes the dual-write configuration health check, including details on the error codes that can result from the health check
author: jaredha
ms.date: 06/06/2023
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: 
ms.search.region: global
ms.author: jaredha
ms.search.validFrom: 2023-06-06
---

# Dual-write configuration health check

[!include [banner](../../includes/banner.md)]

## Overview

This is an overview of the health check, including details on when you would run it and the expected results.

## Running the configuration health check

This section provides step-by-step instructions on how to run the health check.

## Error codes

The following are potential error codes that can result from the configuration health check, indentifying issues in your dual-write configuration.

### Error code DWDVEV1001
**Error Description**: Missing Dataverse APIHub connection, without ConnectionFix support

**How to fix**: If possible relink dualwrite in order to create the APIHub connection again, or reach out to Microsoft support for enabling "AdhocConnectionCreationEnabled" flight for auto connection fix.

### Error code DWFOEV1001
**Error Description**: Missing AX APIHub connection without ConnectionFix support

**How to fix**: If possible relink dualwrite in order to create the APIHub connection again, or reach out to Microsoft support for enabling "AdhocConnectionCreationEnabled" flight for auto connection fix

### Error code DWDVEV1002
**Error Description**: DataVerse deprecated connection is getting used for New Regions

**How to fix**: Reach out to Microsoft support for enabling "UseCDS2Connector" flight in order to use the cds2 connector

### Error code DWDVEV1003
**Error Description**: Company mismatched between DualWrite and Dataverse

**How to fix**: Make sure the dualwrite linked company (legal entity) should be present in Dataverse. Get the mismatch list from the dualwrite UI(in the validation error). If there is a mismatch then either remove the Legalentity mapping for the respective company or relink dualwrite to get the updated legal entity

### Error code DWFOEV1003
**Error Description**: Company mismatched between DualWrite and FO

**How to fix**: Company mismatched between DualWrite and F&O. Make sure the dualwrite linked company (legal entity) should be present in F&O. Get the mismatch list from the dualwrite UI(in the validation error). If there is a mismatch then either remove the Legalentity mapping for the respective company or relink dualwrite to get the updated legal entity

### Error code DWDVEV1004
**Error Description**: Stale DualWrite Configuration present in DV

**How to fix**: Please get the list of entity maps with the dualwrite configuration(from the validation error) and clean it up using these instructions

### Error code DWFOEV1004
**Error Description**: Stale DualWrite Configuration present in F&O

**How to fix**: Please get the list of entity maps with the dualwrite configuration(from the validation error) and clean it up using these instructions

### Error code DWFOEV1005
**Error Description**: Missing AX APIHub connection

**How to fix**: Reach out to Microsoft support for enabling "BypassApiHubConnector" flight. This is a case which adhocconnectioncreation can't fix


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
