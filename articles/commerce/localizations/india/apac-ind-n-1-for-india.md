---
title: Support for upgrade and N-1 for India
description: This article provides an overview N-1 support for Microsoft Dynamics 365 Commerce customers in India.
author: anupamar-ms
ms.date: 02/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: India
ms.author: anupamar
ms.search.validFrom: 2018-10-01
ms.custom: 
  - bap-template
---

# Support for upgrade and N-1 for India

[!include [banner](../../../finance/includes/banner.md)]

This article describes the steps needed to set up and use Phased Rollout (N-1) Microsoft Dynamics 365 Commerce components for India. The upgrade procedure and the workflow for N-1 are basically the same as for a general Dynamics 365 Commerce environment. For general information about N-1 installation and usage, see [Upgrade and N-1 support for Retail](../../dev-itpro/overview-upgrade-n-minus1.md).

For upgrade, the following steps are important:

- Both Commerce headquarters and AX 2012 Retail components must support Goods and Services Tax (GST) calculation. See the [Prerequisites](#prerequisites) section for details.
- You must downgrade the GST configuration to use the configuration prepared for Commerce at the AX 2012 channel side.
- Distribution schedule includes more upload and download jobs required to synchronize GST configuration and tax calculation results between headquarters and AX 2012 channels.

## Prerequisites

- Update AX 2013 R3 retail components to GST Update 2, [KB4058327](https://fix.lcs.dynamics.com/Issue/Details?kb=4058327&bugId=3898178&qc=acbe1a0b3f5d9240d56a94a633fa69fbfe4be0cf98587fd05a7807e082210a12), or higher.
- Set up a basic N-1 environment. For more information, see [Phased Rollout (N-1) installation, configuration, and cutover guide](../../dev-itpro/n-1-installation-configuration.md).
- Set up Commerce GST for India in headquarters according to the [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md) guide.

## Periodic procedure to downgrade tax configuration

GST configuration data differs between AX 2012 and Commerce versions. You need to run a special periodic procedure to transform data. To run this procedure, follow these steps:

1. Sign in to headquarters, and go to **Retail and Commerce \> Retail and Commerce IT \> Process tax configuration from N-1**.
1. Select **OK**.

Each time you make and finalize tax configuration changes, run the preceding operation before sending the data to the AX 2012 channel.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
