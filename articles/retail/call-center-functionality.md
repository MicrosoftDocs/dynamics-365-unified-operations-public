---
# required metadata

title: Call center functionality
description: This topic provides an overview of the call center sales functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 04/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailMCRChannelDetailPage, MCROrderParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16361
ms.assetid: c8ed2ba4-8d06-4d99-9728-2a83e6d95ca9
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Call center 

[!include[banner](includes/banner.md)]

In Dynamics 365 for Retail, a Call Center is a type of Retail channel that can be defined in the application. Defining a specific channel for your call center entities allows the system to tie some specific data defaults and order processing defaults to sales orders created by a user of the call center channel.

The call center feature in Dynamics 365 for Retail utilizes Retail features of Dynamics 365 such as advanced retail price and promotions, catalogs, gift cards, loyalty programs, and coupons. Call Center orders are also leveraged by our POS application to support cross-channel order fulfillment scenarios.

It's important to note that while the call center module can be utilized by other industries outside of Retail, the current release of the Dynamics 365 for Retail call center application hasn't been optimized for use in Business to Business (B to B) order processing scenarios, or scenarios where orders have a large amount of sales lines. It's recommended that users who wish to utilize the call center features for order processing outside of normal Direct to Consumer (B to C or Direct) transaction processing take adequate time to test and validate that enabling call center functionality will meet functional and performance needs.

In addition to supporting the order creation side, the call center module also provides a user-friendly customer service application that better allows users to locate customer accounts and review all of the related customer order data and attributes through a single workbench. The customer service screen is designed to enable a user to quickly access order related data that will allow them to answer the most common order related questions received from customers.

This landing page provides links to relevant documentation and videos related to the setup, configuration and functional use of the call center features of Dynamics 365 for Retail.

> [!NOTE]
> We're working on updating the call center documentation. Check back, as we'll continue to update this page as new or updated topics are published.

## Configure the Call Center
[Call Center Setup](set-up-order-processing-options.md)

## Configure Order Processing Features
[Fraud Holds](set-up-fraud-alerts.md)
[Manual Order Holds](work-with-order-holds.md)

## Configure Payment Processing
[Payment Methods](work-with-payments.md)

## Configure Direct Marketing Features
[Catalogs and Source Codes](call-center-catalogs.md)
[RFM Scoring](set-up-rfm-analysis.md)

## Configure Continuity Programs
[Continuity Program Setup](set-up-continuity-program.md)

