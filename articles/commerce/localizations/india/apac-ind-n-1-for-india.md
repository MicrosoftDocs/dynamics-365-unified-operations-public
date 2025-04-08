---
title: Support for upgrade and N-1 for India
description: This article provides an overview N-1 support for Commerce customers in India.
author: anupamar-ms
ms.date: 11/26/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: India
ms.author: anupamar
ms.search.validFrom: 2018-10-01
ms.custom: 
  - bap-template
---

# Support for upgrade and N-1 for India

[!include [banner](../../../finance/includes/banner.md)]

This article describes the steps needed to set up and use Phased Rollout (N-1) commerce components for India. The upgrade procedure and the workflow for N-1 are basically the same as for a general Dynamics 365 Commerce environment. For general information about N-1 installation and usage, see [Upgrade and N-1 support for Retail](../../dev-itpro/overview-upgrade-n-minus1.md).

In addition, the following steps are important for upgrade:

- Both Commerce Headquarters and AX 2012 Retail components must support Goods and Services Tax (GST) calculation. See the [Prerequisites](#prerequisites) section for details.
- Downgrade of the GST configuration is required to use the configuration prepared for Commerce at the AX 2012 channel side.
- Distribution schedule includes additional upload and download jobs required to synchronize GST configuration and tax calculation results between Headquarters and AX 2012 channels.

## Prerequisites

- Update AX 2013 R3 retail components to GST Update 2, [KB4058327](https://fix.lcs.dynamics.com/Issue/Details?kb=4058327&bugId=3898178&qc=acbe1a0b3f5d9240d56a94a633fa69fbfe4be0cf98587fd05a7807e082210a12), or higher.
- Set up basic N-1 environment. For more information, refer to [Phased Rollout (N-1) installation, configuration, and cutover guide](../../dev-itpro/n-1-installation-configuration.md).
- Set up Commerce GST for India in Headquarters according to the [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md) guide.

## Periodic procedure to downgrade tax configuration

GST configuration data differs between AX 2012 and Commerce versions. A special periodic procedure should be run to transform data. To run this procedure, do the following:

1. Sign in to Headquarters, and go to **Retail and Commerce \> Retail and Commerce IT \> Process tax configuration from N-1**.
2. Click **OK**.

Each time tax configuration changes are made and finalized the above operation should be run before sending the data to the AX 2012 channel.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
