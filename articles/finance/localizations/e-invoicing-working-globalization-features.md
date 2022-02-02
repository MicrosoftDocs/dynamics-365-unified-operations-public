---
# required metadata

title: Working with Globalization feature components
description: This topic provides overview of the Globalization feature components.
author: dkalyuzh
ms.date: 02/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.custom: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Working with Globalization feature components

[!include [banner](../includes/banner.md)]

The Globalization feature is a set of components that define the rules of data transformation in Electronic reporting configurations. The components are a set of instructions to process electronic documents and communicate them to or from external channels. The components also include the conditions that define when a feature should be executed for the incoming business data.
Zll of the components are dependent on each other. With the Globalization feature, it is easy to create and maintain this dependency, and support lifecycle management and versioning of the set of these components.

## Electronic invoicing feature components 

1. Sign in to your Regulatory configuration service (RCS) account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.

   The Globalization feature has the following components.
	
	- **Version** - This component supports feature lifecycle management. You can use this component to manage the status for different versions of the feature.	
	- **Configurations** - This component lets you manage, view, and edit related Electronic reporting (ER) format and format mapping configurations used in the p rocessing pipelines.
	-  **Setups** - This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.	
	- **Environments** - This component lets users of Globalization services, such as an e-invoicing service, manage the environment where the feature version setup is used and grant authorization to the users who will have access to it.	
	- **Organizations** - This component lets users to share the feature with external organizations.	
	- **Tags** - Allow you to tag features that can be used in Globalization blueprint for the reference 
