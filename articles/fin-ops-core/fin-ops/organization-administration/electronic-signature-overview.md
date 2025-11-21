---
title: Electronic signatures overview
description: Learn about electronic signatures and understand how they can be used, including an outline on users who require access to electronic signatures.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 11/21/2025
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: SIGParameters, SIGProcSetup, SIGReasonCode
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 98dc6b79-1895-45d8-9dd1-2c8a351b58af
---

# Electronic signatures overview

[!include [banner](../includes/banner.md)]

This article provides an overview of electronic signatures and describes how you can use them.

## What is an electronic signature?

An electronic signature confirms the identity of a person who starts or approves a computing process. In some industries, an electronic signature is as legally binding as a handwritten signature.

Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, and aerospace and defense. They're also required for compliance with regulations in 21 CFR Part 11 that the Food and Drug Administration (FDA) in the United States issued.

> [!NOTE]
> An electronic signature by itself isn't the same as a digital signature. An electronic signature is just a substitute for a handwritten signature, whereas a digital signature provides other security measures. A digital signature can help identify whether another user or process has tampered with the data. A digital signature can also be verified, and this verification can't be refuted by the owner of the certificate that was used to sign the data. As described in the following section, electronic signatures have built-in digital signature functionality.

## Electronic signatures

You can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field.

Electronic signatures have built-in digital signature functionality. Every user who signs documents must obtain a valid cryptographic certificate. When a user signs a document, the private key that is associated with that certificate is validated. The system records electronic signature information in a log to provide an audit trail. To set up electronic signatures, see [Set up electronic signatures](tasks/set-up-electronic-signatures.md).

## Users who require access to electronic signatures

Three kinds of users typically require security access to electronic signatures: electronic signature administrators, signers, and electronic signature auditors.

### Electronic signature administrator

The electronic signature administrator sets up signature requirements, general parameters, and approvers, and receives alerts when signatures can't be verified. By default, a user who belongs to the **Information technology manager** security role has permission to administer electronic signatures.

### Signer

A signer provides electronic signatures for documents and processes that require signatures. By default, a user who belongs to the **System user** security role has permission to sign documents electronically.

> [!NOTE]
> The signer might need extra permissions to access data related to the document or process that they're signing. A user who changes data and then signs for those changes must have permission to change the data. A user who signs on behalf of another user might not need access to the data. An example of this kind of user is a supervisor who signs for an employee's changes.

### Electronic signature auditor

The electronic signature auditor reviews the database log and the signature review log that's available from the database log. By default, a user who belongs to the **Information technology manager** security role has permission to audit electronic signatures.

If you use a role other than **Information technology manager**, make sure that the role is assigned to the following privileges:

- View electronic signature failures
- View database log

## Signing documents electronically

### Get a certificate

Before you sign documents electronically, you must request a certificate.

> [!NOTE]
> Microsoft SQL Server features are used to create certificates and enable electronic signing. You don't need any other certificate or public key infrastructure (PKI).

When you request a certificate, the system creates a public key and a private key for you. You encrypt the private key by using a password that only you know. When you sign a document electronically, you verify your identity by entering the password.

To request a certificate, on the **Options** page, on the **Accounts** tab, select **Get certificate**.

You must enter and confirm the password that you use for signing. The password protects your private key and authorizes the use of your certificate. The database doesn't store this password, and no one else has access to it, not even the administrator.

If you forget the password that connects with your certificate, you must reset the certificate. Resetting the certificate doesn't affect documents that you signed by using the previous certificate. To reset the certificate, on the **Options** page, select **Reset certificate**.

### Sign a document electronically

The **Sign document** page appears when you make a change that requires an electronic signature.

1. On the **Sign document** page, select the **Document** tab to review the changes to the document.
1. On the **Signature** tab, select a reason code.
1. Enter a comment, if a comment is required.
1. If your user ID doesn't appear in the **Signer** field, select it in the list.
1. Enter your location, if this information is required.
1. Select **OK**.

### Sign for another user's changes

Occasionally, you might want a user to sign for another user's changes. For example, a supervisor might be required to sign for changes that an employee makes to a bill of materials (BOM). Use this procedure to designate a user as a signer for another user.

> [!NOTE]
> When one user signs for another user's change, the signature must be provided at the workstation of the user who made the change. The user can't save the change until the signature is provided.

To designate approvers, follow these steps.

1. On the **Options** page, on the **Accounts** tab, select **Designate approver**.
1. In the **Approver user ID** field, select the ID of the user who must sign for another user's changes.
1. In the **Sign for user ID** field, select the ID of the user whose changes must be signed for.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]