--- 
title: Set up electronic signatures
description: Learn about how to set up electronic signatures, including an outline on how to enable the electronic signature configuration key.
author: sericks007
ms.author: sericks
ms.topic: how-to
ms.date: 04/15/2025
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysConfiguration, SIGParameters, SIGReasonCode, SIGProcSetup
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up electronic signatures

[!include [banner](../../includes/banner.md)]

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one.

Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, aerospace and defense. They are also necessary for compliance with regulations in 21 CFR Part 11 issued by the Food and Drug Administration (FDA) in the United States.

An electronic signature by itself is not the same as a digital signature. An electronic signature is simply a substitute for a handwritten signature, while a digital signature provides additional security measures. A digital signature can help identify whether another user or process has tampered with the data. A digital signature can also be verified, and this verification cannot be refuted by the owner of the certificate that was used to sign the data.Electronic signatures in finance and operations apps have built-in digital signature functionality.

You can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field. Electronic signatures have built-in digital signature functionality. Each user who signs documents must obtain a valid cryptographic certificate. When a document is signed, the private key associated with that certificate is validated.

## Enable the Electronic signature configuration key

1. Go to **System administration** \> **Setup** \> **License configuration**.
1. In the tree, expand *Administration*.
    - Verify that the **Electronic signature** check box is selected.  
    - If the **Electronic signature** check box is not selected, you must enable maintenance mode. Maintenance mode can be enabled in this environment by running a maintenance job from Lifecycle Services, or by using the Deployment.Setup tool locally.  
1. Close the page.

## Set up electronic signature parameters

### Prerequisites for passphrase constraints (preview)

[!INCLUDE [preview-banner-section](../includes/preview-banner-section.md)]

Most electronic signature features are standard for all current versions of Supply Chain Management. However, passphrase constraints and the ability to require comments have been added more recently. To use these enhancements, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Electronic signature improvements* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Set up the electronic signature parameters

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature parameters**.
1. Select **Edit**.
1. Make the following settings:
    - **Notice** – Enter the notice that signers will see on the **Sign document** form. You can enter any text. Typically, this text tells the user what it means to sign a document electronically, including legal implications. If you want to enter the notice text in additional languages, select the **Translations** button on the Action Pane.
    - **Require comments** – Set to *Yes* if all signers are required to enter a comment when signing.  
    - **Signature timeout** – Enter a timeout period (in seconds). If a signature isn't provided in this time frame, the signing process fails.  
    - **Key expiry** – Enter the number of days a digital key will be valid for from its creation.  
    - **Signature alert recipient** – Select the user who should receive an alert email if signature validation fails. Validation fails if the system determines that the certificate and private key provided by a user show signs of tampering.  
    - **Minimum length** – Enter the required minimum length of the passphrase. We recommend a minimum of 8 characters.  
    - **Minimum alpha** – Enter the required number of alphabetical characters in the passphrase.  
    - **Minimum numerals** – Enter the required number of numeric characters in the passphrase.  
    - **Minimum special** – Enter the required number of special characters in the passphrase. Special characters include: !, @, #, $, %, ^, &, *, (, ), ;, :, ?, <, >, -, +, =, ~.

1. Select **Save**.
1. Close the page.

> [!NOTE]
> All the parameters for the passphrase constraints work in conjunction with the Windows policy requirements. The constraints can be more complex than the Windows policy however, it cannot be less complex. For example, if Windows policy dictates minimum length of 8 characters with couple of numbers and couple of special characters and the Passphrase constraints only requires 6 characters, the password will be rejected when generating the certificate

## Set up reason codes for electronic signatures

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature reason codes**.
1. Select **New**. You must set up reason codes before using electronic signatures. A valid reason code is required when signing a document. A signer selects a reason code to indicate the purpose of an electronic signature. For example, a reason code could be used to indicate legal approval.  
1. In the **Reason code** field, type a value.
1. In the **Description** field, type a value. Enter additional reason codes, if needed.  
1. Select **Save**.
1. Close the page.

## Require electronic signatures for existing processes

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the list, find and select the desired record. Select a process that requires electronic signatures.  
1. Select or clear the **Signature required** check box.
1. Repeat these steps for each process that requires electronic signatures.  
1. Select **Save**.

## Create a custom requirement for electronic signatures

1. Select **New**.
1. Select or clear the Signature required check box.
1. In the **Name** field, enter a name for the process that requires electronic signatures.
1. In the **Table name** field, select the drop-down button to open the lookup.
1. In the list, find and select the table where the data that must be signed is stored.
1. In the list, select the link in the selected row.
1. In the **Field name** field, select the drop-down button to open the lookup.
1. In the list, find and select the field in the table that you want to monitor.
1. In the list, select the link in the selected row.
1. Specify when a signature is required.
    - *Always* – Always require a signature when the data in the field changes.
    - *Only* – Only require a signature under certain conditions. If you select *Only*, you must also select one of the following options: *When a record is inserted*, *When a record is updated*, or *When a record is deleted*.  

1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
