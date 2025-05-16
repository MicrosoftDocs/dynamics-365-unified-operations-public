--- 
title: Set up electronic signatures
description: Learn how to set up electronic signatures, including how to enable the Electronic signature configuration key.
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

Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, aerospace, and defense. They are also necessary for compliance with regulations that are issued by the United States Food and Drug Administration (FDA) in part 11 of Title 21 of the Code of Federal Regulations (21 CFR Part 11).

Electronic signatures aren't the same as digital signatures. An electronic signature is just a substitute for a handwritten signature, whereas a digital signature provides additional security measures. A digital signature can help identify whether another user or process tampered with the data. A digital signature can also be verified, and this verification can't be refuted by the owner of the certificate that was used to sign the data. Although electronic signatures and digital signatures differ, they can work together. For example, in finance and operations apps, electronic signatures have built-in digital signature functionality.

You can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field. As was mentioned earlier, electronic signatures in finance and operations apps have built-in digital signature functionality. Each user who signs documents must obtain a valid cryptographic certificate. When a document is signed, the private key that is associated with that certificate is validated.

## Enable the Electronic signature configuration key

1. Go to **System administration** \> **Setup** \> **License configuration**.
1. In the tree, expand **Administration**, and verify that the **Electronic signature** checkbox is selected. If the checkbox is cleared, you must enable maintenance mode before you can select it. You can enable maintenance mode in the environment by running a maintenance job from Microsoft Dynamics 365 Lifecycle Services. Alternatively, you can use the Deployment.Setup tool locally. After you select the **Electronic signature** checkbox, turn off maintenance mode.
1. Close the page.

## Set up electronic signature parameters

### Prerequisites for passphrase constraints (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]

Most electronic signature features are standard for all current versions of Microsoft Dynamics 365 Supply Chain Management. However, passphrase constraints and the ability to require comments are recent enhancements. Before you can use them, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Electronic signature improvements* must be turned on in [Feature management](../../get-started/feature-management/feature-management-overview.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Set up the electronic signature parameters

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature parameters**.
1. Select **Edit**.
1. Set the following fields:

    - **Notice** – Enter the notice that is shown to signers on the **Sign document** page. You can enter any text. Typically, this notice informs the user what it means to sign a document electronically, including legal implications. If you want to enter the notice text in more languages, select **Translations** on the Action Pane.
    - **Require comments** – Set this option to *Yes* if all signers must enter a comment when they sign.
    - **Signature timeout** – Enter a timeout period (in seconds). If np signature is provided within this period, the signing process fails.
    - **Key expiry** – Enter the number of days that a digital key remains valid after it's created.
    - **Signature alert recipient** – Select the user who should receive an alert email if signature validation fails. Validation fails if the system determines that the certificate and private key that a user provided show signs of tampering.
    - **Minimum length** – Enter the required minimum length of the passphrase. We recommend a minimum of eight characters.
    - **Minimum alpha** – Enter the required number of alphabetical characters in the passphrase.
    - **Minimum numerals** – Enter the required number of numeric characters in the passphrase.
    - **Minimum special** – Enter the required number of special characters in the passphrase. Special characters include the following symbols:

        - *!* (exclamation point)
        - *@* (at sign)
        - *#* (number sign)
        - *$* (dollar sign)
        - *%* (percent sign)
        - *^* (circumflex accent)
        - *&* (ampersand)
        - *\** (asterisk)
        - *(* (opening parenthesis)
        - *)* (closing parenthesis)
        - *;* (semicolon)
        - *:* (colon)
        - *?* (question mark)
        - *&lt;* (less than sign)
        - *&gt;* (greater than sign)
        - *-* (hyphen)
        - *+* (plus sign)
        - *=* (equal sign)
        - *~* (tilde)

1. Select **Save**.
1. Close the page.

> [!NOTE]
> All the parameters that are related to passphrase constraints work in conjunction with the Windows policy requirements. Although the passphrase constraints can be more complex than the Windows policy, they can't be less complex. For example, the Windows policy might require a minimum length of eight characters, including more than one numeric character and more than one special character. By contrast, the passphrase constraints might just require six characters. In this case, the password is rejected when the certificate is generated.

## Set up reason codes for electronic signatures

Before electronic signatures can be used, you must set up reason codes. A valid reason code is required whenever a document is signed. The reason code indicates the purpose of the electronic signature. For example, a reason code can indicate legal approval.

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature reason codes**.
1. Select **New**.
1. In the **Reason code** field, enter a value.
1. In the **Description** field, enter a value.
1. Repeat these steps to add more reason codes as required.
1. Select **Save**.
1. Close the page.

## Require electronic signatures for existing processes

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the list, find and select the desired record.
1. Select a process that requires electronic signatures.
1. Select or clear the **Signature required** checkbox.
1. Repeat these steps for every other process that requires electronic signatures.
1. Select **Save**.

## Create a custom requirement for electronic signatures

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. Select **New**.
1. Select or clear the **Signature required** check box.
1. In the **Name** field, enter a name for the process that requires electronic signatures.
1. In the **Table name** field, select the dropdown button to open the lookup. Find and select the table that store the data that must be signed. Then select the link in the selected row.
1. In the **Field name** field, select the dropdown button to open the lookup. Find and select the table field that you want to monitor. Then select the link in the selected row.
1. Select one of the following values to specify when a signature is required:

    - *Always* – Always require a signature when the data in the field is changed.
    - *Only* – Require a signature only under certain conditions. If you select *Only*, you must also select one of the following options: *When a record is inserted*, *When a record is updated*, or *When a record is deleted*.

1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
