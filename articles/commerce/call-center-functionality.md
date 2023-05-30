---
# required metadata

title: Call center sales functionality
description: This article provides an overview of the call center sales functionality in Dynamics 365 Commerce.
author: josaw1
ms.date: 04/03/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailMCRChannelDetailPage, MCROrderParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: c8ed2ba4-8d06-4d99-9728-2a83e6d95ca9
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Call center sales functionality

[!include [banner](includes/banner.md)]


In Dynamics 365 Commerce, a call center is a type of channel that can be defined in the application. Defining a specific channel for your call center entities allows the system to tie specific data defaults and order processing defaults to sales orders created by a user of the call center channel.

Call center features include advanced price and promotions, catalogs, gift cards, loyalty programs, and coupons. Call center orders are also leveraged by the point of sale (POS) application to support cross-channel order fulfillment scenarios.

It's important to note that while the call center module can be utilized by other industries outside of Commerce, the current release of the call center application hasn't been optimized for use in business-to-business (B2B) order processing scenarios, or scenarios where orders have a large number of sales lines. It's recommended that users who want to utilize the call center features for order processing outside of typical direct-to-consumer transaction processing, take adequate time to test and validate that enabling call center functionality will meet functional and performance needs.

In addition to supporting order creation, the call center module also provides a user-friendly customer service application that makes it easier for users to locate customer accounts and review all of the related customer order data and attributes. The customer service screen is designed to enable a user to quickly access order-related data that will allow them to answer the most common order-related questions received from customers.

This page provides links to relevant documentation related to the setup, configuration, and functional use of the call center features.


## Configure the call center

[Set up call center channels](set-up-order-processing-options.md)

## Configure order processing

[Set up and work with call center fraud alerts](set-up-fraud-alerts.md)

[Configure and work with call center order holds](work-with-order-holds.md)

## Configure payment processing

[Payment methods in call centers](work-with-payments.md)

## Configure delivery modes

[Configure call center delivery modes and charges](configure-call-center-delivery.md)

## Configure direct marketing

[Call center catalogs](call-center-catalogs.md)

[Set up Recency, Frequency, and Monetary (RFM) analysis](set-up-rfm-analysis.md)

## Configure continuity programs

[Set up continuity programs for call centers](set-up-continuity-program.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]