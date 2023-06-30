---
title: Extend export control sales order functionality
description: This article provides information that is useful for developers who are extending sales order functionality for implementing export controls
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend export control sales order functionality

This article provides information that is useful for developers who are extending sales order functionality for implementing export controls.

<!-- KFM: An introduction is needed to set the context. The following text should maybe be divided into sections. Additional context may be needed to understand what this text is referring to. -->

During confirmation and similar posting steps, the system tracks the history of export control checks. You can view this history from the sales order header by selecting the **Result** button, which will show the details of the check performed at that time. This data is available for reference from reports and other processes in the `COOExportControlSalesTableHistory` table, which also provides helper methods to access common information.

The document level *de minimis* threshold value is *not* computed and will always be zero by default. To provide a computation of document-level *de minimis*, extend the `COOValidateSalesTable::createRequest() API`.

The `SalesLine.QtyOrdered` field is passed for quantity, and the `SalesLine.LineAmount` is passed for the value. No currency conversion is performed on these values. To override and pass different values, extend the `COOValidateSalesTable::createRequest()` method to update the values. The *de minimis* percentage from the associated item is passed for the line without calculation.
