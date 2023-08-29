---
title: Extend export control sales order functionality
description: This article provides information that's useful for developers who are extending sales order functionality for implementing export controls.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 08/29/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend export control sales order functionality

This article provides information that's useful for developers who are extending sales order functionality for implementing export controls.

During confirmation and similar posting steps, the system tracks the history of export control checks. You can view this history from the sales order header by selecting **Result**. The details of the check that was performed are shown. This data is available for reference from reports and other processes in the `COOExportControlSalesTableHistory` table. This table also provides helper methods for accessing common information.

The document-level *de minimis* threshold value is **not** computed. By default, it's always *0* (zero). To provide a computation of the document-level *de minimis* threshold value, extend the `COOValidateSalesTable::createRequest()` API.

The `SalesLine.QtyOrdered` field is passed for the quantity, and the `SalesLine.LineAmount` field is passed for the value. No currency conversion is performed on these values. To override and pass different values, extend the `COOValidateSalesTable::createRequest()` method to update the values. The *de minimis* percentage from the associated item is passed for the line, without calculation.
