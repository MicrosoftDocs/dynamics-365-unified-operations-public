---
title: Security enhancements in UK MTD VAT integration (cloud-based deployments only)
description: Learn how to enable the \[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\) feature.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/05/2024
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2025-03-25
ms.dyn365.ops.version: AX 10.0.43
---

# \[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)

To meet security requirements, we are implementing modifications to the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK. 
This enhancement involves the adoption of an Electronic Invoicing service as an intermediary that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs.

This topic explains how to enable the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature in you Finance and what changes to the user experience are introduced with this feature.

## Prerequisites

Prerequisites are essential requirements and foundational elements needed before proceeding with the feature enablement. Ensuring that these conditions are met is critical to achieving optimal functionality and a seamless transition to the more secure integration with external web service. 

### Check system version

The **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature is introduce in **10.0.43** version of Finance.

It is also available in the following lower versions:

<li> <b>10.0.41</b> - 10.0.2015.<b>155</b>
<li> <b>10.0.42</b> - 10.0.2095.<b>77</b>

### Import the required ER configuration updates

To work with the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature the following or higher versions of Electronic Reporting (ER) configurations must be imported in your Finance:

<li> MTD VAT model mapping - version 46.74, under the Electronic Messages framework model
<li> MTD VAT authorization format (UK) - version 46.17, under the Electronic Messages framework model
<li> MTD VAT web request headers format (UK) - version 46.48, under the Electronic Messages framework model
<li> MTD VAT interoperation (UK) - version 31.11, under the Tax declaration model

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Enable the E-Invoicing Add-In

To comply with security requirements, it is essential to enable the **Electronic Invoicing add-in**. This add-in acts as an intermediary, ensuring secure storage and management of credentials required for software authorization within the HMRC APIs. Enabling this functionality is a crucial step in maintaining a secure and compliant integration between Dynamics 365 Finance and the HMRC web service for VAT return submissions.

Learn more about how to [Enable the E-Invoicing Add-In](../global/gs-e-invoicing-set-up-overview.md#install-the-add-in-for-electronic-invoicing-microservices)

## How to enable the feature

## How to proceed once the feature is activated

## Further details
