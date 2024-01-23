---
title: Globalization Studio workspace features
description: This article explains the features of Globalization Studio workspace
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Globalization Studio workspace features

[!INCLUDE[banner](../../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../../includes/rsc-to-gsw-banner.md)]

You can use Globalization Studio to create a Globalization feature that can be used in Globalization services: Electronic Invoicing and Tax Calculation. Globalization Studio lets you perform these tasks:

- Define related components of a feature.
- Manage the feature lifecycle through a feature's status.

To use a Globalization feature, you must first import it from Dataverse repository and create your own version of it. There are two ways to add Globalization features:

- Add a derived feature that is based on an existing feature that has been published or shared.
- Add a new feature that you've created from scratch.

## Feature component overview

Globalization features have several components:

- **Version**  – This component supports feature lifecycle management and lets users manage the status for different versions of the feature.
- **Configurations**  – This component lets users manage, view, and edit related ER formats and format mappings.
- **Setups**  – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.

For more details on Globalization features setup and usage, see [Electronic Invoicing and Tax Calculation Service](where).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
