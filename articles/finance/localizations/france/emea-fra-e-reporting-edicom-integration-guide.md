---
title: Set up the EDICOM integration for France e-Reporting
description: Learn how to set up the EDICOM integration for France e-Reporting
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 09/28/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2026-04-24
ms.dyn365.ops.version: AX 10.0.48
---

# Set up the EDICOM integration for France e-Reporting

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to install the direct integration between Dynamics 365 Finance and EDICOM for French e-Reporting.

Start with the [e-Reporting article](emea-fra-e-reporting-preparation.md) to understand the overall feature, the reporting scope, and the [report generation flow](emea-fra-e-reporting-experience.md). This guide builds on that setup and doesn't replace the official documentation. Use it as a companion to enable the EDICOM submission channel once your e-Reporting configuration is already in place.

## Privacy notice

When you enable Finance to interoperate with EDICOM for e-Reporting, the system shares customer content with EDICOM to process and submit e-Reports.
This content might include sales, purchase, and payment information, as well as e-Reporting status acknowledgement details. To learn more about the information required for e-Reporting submissions, review [EDICOM's documentation](https://go.microsoft.com/fwlink/?LinkId=2378296). A system administrator can disable the EDICOM interoperation in Finance by going to **Tax** > **Setup** > **Electronic Messages**. Your privacy is important to us. To learn more, read our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a id="prerequisites"></a> Prerequisites

### Application build

Install the application version that includes this feature:

| Finance version | Build |
| --------------- | ----- |
| 10.0.49 | 10.0.2790.**61** |
| 10.0.48 | 10.0.2645.**135** |
| 10.0.47 | 10.0.2527.**212** |

Ensure your environment is on that build (or a later one) before you import the configurations and enable the integration.

### <a id="er-configurations"></a>Electronic reporting (ER) configurations

Import the ER configurations listed in the following table from Microsoft Dataverse. The indicated versions are the minimum required — use the latest available version of each configuration.

| ER configuration | Type | Version |
| --- | --- | --- |
| Electronic Messages framework model | Model | 53 |
| e-Reporting integration model mapping | Model mapping | 53.8 |
| e-Reporting status import (FR) | Import format | 53.4 |
| e-Reporting status confirmation import (FR) | Import format | 53.1 |
| e-Reporting request headers (FR) | JSON format | 53.4 |

For the import procedure, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### <a id="em-setup-package"></a>Electronic messages (EM) setup package

The complete set of **Electronic messages** settings that the integration relies on is delivered in a setup package that's available in the  **Shared asset library** of [Lifecycle Services](https://lcs.dynamics.com/v2): **FR eReporting submission EDICOM EM setup v.1 ID1173584** (or a later version). [Download this package](emea-fra-e-reporting-preparation.md#data-entities) before you start.

### Base France e-reporting setup

Complete the base France e-reporting configuration before you enable the integration.
Follow all of the steps in [How to prepare your Dynamics 365 Finance for French e-Reporting](emea-fra-e-reporting-preparation.md).
The EDICOM integration builds on that setup and only adds the direct submission channel.

## Overview of the EM settings specific to the integration

This section describes the **Electronic messages** settings that are specific to the EDICOM integration.

The settings listed in this section don't represent the full scope of settings required for the EDICOM integration.
They provide only a high-level explanation of what the integration uses.
You can find the complete and authoritative set of settings in the [Electronic messages setup package](#em-setup-package) available on LCS: **FR eReporting submission EDICOM EM setup v.1 ID1170192.zip** (or a later version).
Don't configure the settings manually. Instead, [import this package](emea-fra-e-reporting-preparation.md#data-entities) to apply all of the required settings automatically.

### Message processing actions

The following **Electronic messages processing actions** support the EDICOM integration.

| Action | Type | Description |
| --- | --- | --- |
| **FR-eRep Submit Report** | Executable class (web service) | Submits the generated e-Reporting file directly to EDICOM. |
| **FR-eRep Get Report Status** | Executable class (web service) | Requests the processing status of a previously submitted e-Reporting file from EDICOM. |
| **FR-eRep Import Report Status** | Electronic reporting import | Imports the processing status of a previously submitted e-Reporting file into the electronic message. |
| **FR-eRep Confirm Report Status** | Web service | Imports the confirmation response for a previously received report status. |
| **FR-eRep Import Status Confirmation** | Electronic reporting import | Imports the confirmation response for a previously received report status. |

### Web service settings

The submission and status request actions rely on the following web service settings, which define the EDICOM endpoints:

| Web service setting | Description |
| --- | --- |
| **FR-eRep Report Submission** | Submits e-Reporting files to EDICOM. |
| **FR-eRep Report Status Request** | Requests the status of a submitted e-Reporting file. |
| **FR-eRep Status Confirmation** | Confirms receipt of a previously received e-Reporting status. |

### Executable class settings

The following executable class settings link the submission and status request actions to the classes that call the EDICOM web service:

| Executable class setting | Action type | Class | Description |
| --- | --- | --- | --- |
| **FR-eRep SubmitReport** | Web service | `EReportingSubmitController_FR` | Submits an e-Reporting message (file) to EDICOM. |
| **FR-eRep GetMessageStatus** | Web service | `EReportingStatusController_FR` | Requests the processing status of a submitted e-Reporting file from EDICOM. |

## Install the integration

Before you start, ensure you fulfill all of the [Prerequisites](#prerequisites) — the environment is on a supported application build, the ER configurations are available, the EM setup package is downloaded, and the base France e-reporting setup is completed. Then follow these steps to install and activate the EDICOM integration:

1. **Set up the EDICOM token and configure the web services.** Store the token provided by EDICOM as a secret in your Azure Key Vault.
1. Go to **System administration** > **Setup** > **System parameters**, set the **Use advanced certificate store** option to **Yes** to use Key Vault storage.
1. Go to **System administration** > **Setup** > **Key Vault parameters** and set up the Key Vault parameters.
1. Go to **Tax** > **Setup** > **Electronic messages** > **Web service settings** and select each of the three web services one-by-one: **FR-eRep Report Submission**, **FR-eRep Report Status Request**, and **FR-eRep Status Confirmation**. In each of the three web services, link the Key Vault secret that holds your EDICOM token.
1. Update the constants in the **Internet address** of each web service with the **domain** and **application** information provided by EDICOM as part of your onboarding.

> [!TIP]
> For example, the **FR-eRep Status Confirmation** web service is provided with the <code>https:<wbr>//ipaasgw.edicomgroup.com/api/v1/domain/:domain/application/:application/broker/subscription/confirm</code> internet address in the EM settings package.
>
> Update this Internet address to <code>https:<wbr>//ipaasgw.edicomgroup.com/api/v1/domain/YOUR_DOMAIN_FROM_EDICOM/application/YOUR_APPLICATION_FROM_EDICOM/broker/subscription/confirm</code>.

1. **Attach the validation result converter.** Download the **FR eReporting validation result converter.zip** file from the LCS **Shared asset library** > **Data package** section, and unzip it. Then go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions** and select the **FR-eRep Import Report Status** action. Attach the unzipped **ValidationResult.xslt** file to that action.
1. **Activate the executable classes and provide consent.** Go to **Tax** > **Setup** > **Electronic messages** > **Executable class settings**. For each of the new classes, open **Parameters**, read and acknowledge the consent, and then select **OK**. Without this consent, the integration doesn't work. The system logs the consent. To revoke the consent later, return to the same **Parameters** and select **Cancel**.
