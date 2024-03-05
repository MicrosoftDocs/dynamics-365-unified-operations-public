---
title: Globalization Studio workspace features (preview)
description: This article explains the features of the Globalization Studio workspace (preview).
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Globalization Studio workspace features (preview)

[!INCLUDE[banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

Globalization Studio lets you create Globalization features that can be used in the following Globalization services: Electronic Invoicing and Tax Calculation. You can perform these tasks:

- Define related components of a feature.
- Manage the feature lifecycle through a feature's status.

To use a Globalization feature, you must first import it from a Dataverse repository and create your own version of it. There are two ways to add Globalization features:

- Add a derived feature that's based on an existing feature that has been published or shared.
- Add a new feature that you created from scratch.

## Feature component overview

Globalization features have several components:

- **Version** – This component supports feature lifecycle management. It lets users manage the status of different versions of the feature.
- **Configurations** – This component lets users manage, view, and edit related Electronic reporting (ER) formats and format mappings.
- **Setups** – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.

For more detailed information about how to set up and use Globalization features, see [Electronic Invoicing and Tax Calculation Service](where should this go).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
