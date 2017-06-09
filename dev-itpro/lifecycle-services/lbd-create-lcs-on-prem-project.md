---
# required metadata

title: Create an on-premise project in Lifecycle Services
description: This topic provides informaton about the process of setting up an on-premise project in Lifecycle Services (LCS).. 
author: kfend
manager: AnnBe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# Create an on-premise project in Lifecycle Services
Lifecycle Services is a required for a customer to be able to deploy and update Dynamics 365 for Operations, On-Premise instance. After purchasing server and user license through Volume Licensing or Dynamics Purchase List flow, customer will receive an email with instructions to log on to Lifecycle Services. After following the instructions <TODO – link to Shelly/Matthews doc>, to create or use an existing Azure Active Directory account, a pre-requisite for logging onto LCS, and completing all the sign-up steps, the customer will be redirected to Lifecycle Services and a Dynamics 365 for Operations, On-Premise implementation project will be provisioned.

 [![On-premise implementation project](./media/lbd-proejcts-01.png)](./media/lbd-proejcts-01.png)

The On-Premise Project has all the tools necessary to implement, maintain and operate a Dynamics 365 for Operations, On-Premise solution. Below is a list of tools available:
 
1.	Methodology - The On-Premise methodology provides best practices to help a customer implement and manage an On-Premise project.
2.	Business Process Modeler - Business Process Modeler is use to capture requirements and do fit gap analysis. 
3.	Cloud Hosted Environments - Cloud Hosted Environments are used for deploying a developer and build topology and do Dev ALM for an on-premise solution. 
4.	Code Upgrade - Tool that’s assists with upgrading code to a newer release. 
5.	Issue Search - Search for KBs published for application and platform issues. 
6.	Localization and Translation - Used to localize and translate assets. 
7.	Support - File and track support incidents. 
8.	Project Users - Add users to a project.
9.	Project Settings - Edit project level settings such as connectors, project name, organization users, license number etc. 
10.	Asset Library - Library for various assets such as packages 
11.	SharePoint Online Library - Connect to an online SharePoint Library.
 
To start implementing Dynamics 365 for Operations, On-Premise, follow the methodology step by step to know how to setup the project, what steps to follow to deploy developer and build environments and then to deploy Sandbox and Production environments. The On-Premise Project has two environment slots, one for Sandbox and another for Production pre-allocated to assist with deployments. These pre-allocated Sandbox and Production environment will be used during the Servicing flow to ensure that packages are tested on Sandbox before applying packages in Production. 
