---
# required metadata
title: [Ratings and Review Configuration - Import or Export Reviews]
description: [A way to import reviews into Dynamics 365 Commerce or export reviews from Dynamics 365 Commerce.]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 08/27/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-10-17
ms.dyn365.ops.version: 10.0.24
---

#Import or export ratings and reviews

Dynamics 365 Commerce offers **[Ratings and Reviews](Ratings and reviews overview - Commerce | Dynamics 365 | Microsoft Docs)** as an omni-channel solution. When you decide to switch over to Dynamics 365 Commerce's Ratings and Reviews solutions you may want to bring your existing Ratings and Reviews data to Dynamics 365 Commerce platform. Additionally you may want to export ratings and reviews data from Dynamics 365 Commerce based on business requirements. This article explains how to import ratings and review into Dynamics 365 Commerce or export from Dynamics 365 Commerce.

##Pre-requisites

You will need the following to proceed:
	1. You have enabled Ratings and Review solution for your E-Commerce site on Dynamics 365 Commerce Platform.  Refer to  [Enable Ratings and Reviews solution] (https://docs.microsoft.com/en-us/dynamics365/commerce/opt-in-ratings-reviews) 
	2. Dynamics 365 Ratings and Reviews Power App Connector to enable Power Automate with either submit reviews or export reviews actions. 
	3. Configure service to service authentication to security call Ratings and Reviews API from outside Dynamics 365 Commerce. Refer to [Configure service to service authentication] (http://url-to-be-created)



##Import reviews

To migrate ratings and reviews data from your existing system using Power Automate  connector you can either create a new Power Automate flow or using an existing flow. In the flow, add the **Dynamics 365 Ratings and Review Connector**, documentation can be found **[here] (http://url-to-be-created)**.  


	1. Select the action for **Submit User Review**
	2. Establish connection with the AAD app information created earlier.  Refer to **[ Configure service to service authentication] (http://url-to-be-created) **
	3. Submit User Review takes a review at a time, so iterate this action using the source reviews as a list to submit bulk reviews. 
	
##Import reviews

To export ratings and reviews data from Dynamics 365 Commerce using Power Automate  connector you can either create a new Power Automate flow or using an existing flow. In the flow, add the **Dynamics 365 Ratings and Review Connector**, documentation can be found **[here] (http://url-to-be-created)**.  


	1. Select the action for **Export All Reviews**
	2. Complete the action. 

![image](https://user-images.githubusercontent.com/42852473/137647111-8f0db51c-6124-4a00-ae7e-dbce94f566fd.png)
