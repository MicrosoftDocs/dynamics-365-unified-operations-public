---
# required metadata

title: Work with Globalization features overview
description: This topic provides overview of Globalization features.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Work with Globalization features overview

[!include [banner](../includes/banner.md)]


Globalization feature is a set of components that in combination define the rules of data transformation (Electronic reporting configurations), set of instructions on processing electronic documents, and communicating them to or from external channels (Processing pipeline with Actions), conditions that define when this feature should be executed for the incoming business data (Applicability rules).
All these components are dependent on each other. With Globalization feature it is easy to create and maintain this dependency, as well as support lifecycle management and versioning of the set of these components.


## Electronic Invoicing feature components 

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.


	Globalization features have several components:
	- **Version**
		
		This component supports feature lifecycle management and lets users manage the status for different versions of the feature.
		
	- **Configurations**
	
		This component lets users manage, view, and edit related Electronic reporting (ER) format and format mapping configurations used in the Processing pipelines.
		
	-  **Setups**
	
		This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.
		
	- **Environments**
	
		This component lets users of Globalization services, such as an e-invoicing service, manage the environment where the feature version setup is used and grant authorization to the users who will have access to it.
		
	- **Organizations**
	
		This component lets users to share the feature with external organizations.
		
	- **Tags**
	
		Allow you to tag features that can be used in Globalization blueprint for the reference 
