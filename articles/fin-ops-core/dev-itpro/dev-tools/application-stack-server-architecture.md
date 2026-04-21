---
title: Application stack and server architecture
description: The application stack is divided into several models - Application Platform, Application Foundation, Test Essentials, and the application suites.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6a5811cc-a551-4e4d-824c-d760460b3223
---

# Application stack and server architecture

[!include [banner](../includes/banner.md)]

The application stack is divided into platform models and application-specific models. The platform models are Application Platform, Application Foundation, and Test Essentials. There are many application-specific models. Some examples are Application Suite, Ledger, Retail, and Case Management.

## Overview

The application stack and server architecture align with three key pillars:

- New client
- Cloud readiness
- New development stack

The application stack is divided into several models: Application Platform, Application Foundation, Test Essentials, and the application suites. This separation enables new application development on the base foundation models, just as the Fleet Management sample application is developed. Note the following important points about the changes in the server architecture:

- The services endpoint on the server is now responsible for returning all form and control metadata and data to the browser-based client. There's no longer any remote procedure call (RPC)-based communication with the server. The form objects still run on the server, and rendering is optimized for browsers and other clients through server and client-side (browser) investments.
- You deploy the server, including the application code base, to an Internet Information Services (IIS) web application. In the cloud, you deploy it to Microsoft Azure infrastructure as a service (IaaS) virtual machines (VMs).
- It's hosted on Azure and is available for access through the Internet. A user can use a combination of clients and credentials to access it. The recommended primary identity provider is OrgID, and the store for the identity is Microsoft Entra ID. The security subsystem uses the same AuthZ semantics for users and roles.
- You must consider two types of clients for access in the cloud: active clients and passive clients.
  - Active clients can programmatically initiate actions based on responses from the server. An active client doesn't rely on HTTP redirects for authentication. A smart or rich client is an example of an active client.
  - Passive clients can't programmatically initiate actions based on responses from the server. A passive client relies on HTTP redirects for authentication. A web browser is an example of a passive client.

    Currently, Access Control Service (ACS) doesn't support a mechanism for non-interactive authentication. Therefore, even when active clients try to authenticate by using ACS, they must use passive client authentication, in which a browser dialog box prompts the user to enter their credentials.
- A completely revamped metadata subsystem incorporates the new compiler and Microsoft Visual Studio–based development model. The model store is represented as a set of folders and XML artifacts that are organized by model. An XML file represents the model elements, such as tables, forms, and classes, and it contains both metadata and source code.

The following diagram shows how the application stack is split into distinct models. It also shows how the key components are stacked in the server.

:::image type="content" source="./media/ArchitectureDrawing1.png" alt-text="Screenshot of the application stack and server architecture diagram." lightbox="./media/ArchitectureDrawing1.png":::

The finance and operations applications use an entry point security model. A form provides read-only access if the menu item used for navigation to that form has only Read Permissions. However, navigation to that same form through another menu item that provides Create Permissions, Delete Permissions, or Update Permissions grants write operations on the form. This behavior simplifies the development experience, because developers can specify the behavior for a form through a given entry point.

## Cloud architecture

The cloud architecture includes services that automate software deployment and provisioning, operational monitoring and reporting, and seamless application lifecycle management. The cloud architecture consists of three main conceptual areas:

- **Microsoft Dynamics Lifecycle Services** – Lifecycle Services is a multitenant shared service that enables a wide range of lifecycle-related capabilities. Capabilities that are specific to this release include software development, customer provisioning, service level agreement (SLA) monitoring, and reporting capabilities.
- **Finance and operations** – You deploy the VM instances through Lifecycle Services to your Azure subscription. Various topologies are available: demo, development/test, and high-availability production topologies.
- **Shared Microsoft services** – A finance and operations application uses several Microsoft services to enable a “One Microsoft” solution where customers can manage a single sign-in, subscription management, and billing relationship with Microsoft across finance and operations applications, Microsoft 365, and other online services.

The architecture uses many features of the Azure platform, such as Microsoft Azure Storage, networking, monitoring, and SQL Azure, to name a few. Shared services put into operation and orchestrate the application lifecycle of the environments for participants. Together, Azure functionality and Lifecycle Services offer a robust cloud service.

## Development environment

The architecture of the development environment resembles the architecture of the cloud instance. It also includes the software development kit (SDK), which consists of the Visual Studio development tools and other components. Source control through Team Foundation Server or Visual Studio Online enables multiple-developer scenarios, where each developer uses a separate development environment. You can compile and generate deployment packages on a development environment and deploy them to cloud instances by using Lifecycle Services. The following diagram shows how the key components interact in a development environment.

:::image type="content" source="./media/dev-environ.png" alt-text="Screenshot of the development architecture showing Visual Studio, local runtime, and cloud deployment.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
