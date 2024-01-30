---
title: Get started with Electronic invoicing for Saudi Arabia - Phase two
description: This article provides information that will help you get started with phase two of Electronic invoicing for Saudi Arabia.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Get started with Electronic invoicing for Saudi Arabia - Phase two

[!include [banner](../../includes/banner.md)]


This article provides information that will help you get started with phase two of Electronic invoicing for Saudi Arabia. This article guides you through the configuration steps that are country/region-dependent in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md).

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites: 

- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](../global/GS-e-invoicing-service-overview.md).
- Do the common part of Electronic Invoicing service configuration as described in [Set up Electronic invoicing](../global/GS-e-invoicing-set-up-overview.md)..
- Import the **Saudi Arabian Zatca submission (SA)** and **Saudi Arabian ZATCA compliance check (SA)** electronic invoicing features from the repository. For more information, see [Import features from the repository](../global/GS-e-invoicing-import-feature-global-repository.md).

## Finance configuration

4. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that **PaymentMethodSubstitutionLookup** lookup is selected.
5. In the **Conditions** section, select **Add** to add a condition.
6. In the **Name** column for the new condition, select the method of payment that is defined in the application. Then, in the **Lookup result** column, select a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
7. Add specific conditions for each method of payment that is defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **\*Blank\*** or **\*Not blank\*** placeholder value instead of a specific method of payment.

8. On the **Setups** tab, select **Edit** for the selected configuration. 
9. In the **Processing pipeline** section, turn on the **Export result** option for the **Transform document** action.
10. In Key Vault, create certificates and secrets for Cryptographic Stamp Identifiers (CSIDs). For more information, see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md).

    > [!NOTE]
    > Depending on your place in the [onboarding](#onboarding) process, create a Compliance CSID (CCSID) or a Production CSID (PCSID).

11. In the **Globalization feature** workspace, select the **Environment setup** related link, and then, on the **Service environments** menu, select the environment to use for the feature deployment.
12. In **Number sequences** section, add a record for the number sequence that should be used to count submitted electronic invoices.

    ![Number sequence setup.](../media/emea-sa-einvoice-counter.jpg)


When tax invoices are cleared, ZATCA generates a QR code that contains the digital signature for that clearance. This QR code must be imported back into Finance, together with other clearance information that the tax authority returns as result of the submission of the tax invoices. To achieve this result, you must configure the response types in Finance. 

Follow these steps to complete the configuration.

1. Make sure that the country/region-specific ER configurations that are required for Saudi Arabia are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters.md)
2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. In the **Electronic document** section, add records for the **Customer Invoice journal**, **Project invoice** and **Fiscal transaction document** table names. 
4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
5. For the **Customer Invoice journal** table name, select **Response types**.
6. Create a response type that has the same name that was defined for the related variable in the corresponding feature setups in RCS. 
7. In the **Submission status** field, select **Pending**.
8. In the **Data entity name** field, select **Sales invoice QR code entity**.
9. In the **Model mapping** field, select **Zatca response data import**.

    ![Response type setup.](../media/emea-sa-einvoice-response.jpg)

For more information about business data configuration and processing in Finance, see [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md).

## Country/region-specific configuration for the Saudi Arabian Zatca submission (SA) Electronic invoicing feature

> [!NOTE]
> The configuration steps in this section are described for **Saudi Arabian Zatca submission (SA)** electronic invoicing feature. This assumes that the [onboarding](#onboarding) process is completed and the Production Cryptographic Stamp Identifier (PCSID) is obtained. If you are in the middle of the onboarding process and only the Compliance Cryptographic Stamp Identifier (CCSID) is received, do the same configuration steps for the **Saudi Arabian ZATCA compliance check (SA)** electronic invoicing feature. 

Some of the parameters from the **Saudi Arabian Zatca submission (SA)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service, review the default values, and update them as required so that they better reflect your business operations.

1. In the **Globalization studio** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing features** page, verify that the **Saudi Arabian Zatca submission (SA)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** menu, select the **Sales invoice** feature setup, and then select **Edit**.
   
   > [!NOTE]
   > Select the **Tax invoice compliance check** feature setup for the electronic invoicing feature, **Saudi Arabian ZATCA compliance check (SA)**.
   
5. On the **Processing pipeline** tab, in the **Processing pipeline** section, select the **Get next number sequence value** action. 
6. In the **Parameters** section, in the **Value** field, select the number sequence that you preliminary created in **Electronic document parameters**.
7. In the **Processing pipeline** section, select **Prepare document for submit for Saudi Arabia Zatca service**, and then follow these steps:

    1. In the **Parameters** section, select the **Invoice counter value** name. 
    2. In the **Value** field, select **Get next number sequence value: Number sequence value**.
    3. Select the **Invoice counter name** name.
    4. In the **Value** field, select **Get next number sequence value: Number sequence name**.

8. In the **Processing pipeline** section, select **Integrate with Saudi Arabia Zatca service**, and then follow these steps:

    1. In the **Parameters** section, select **Web service URL**.
    2. In the **Value** field, enter the URL of the development portal or the production environment that is provided by the Saudi Arabian tax authority (ZATCA).
    3. Select the **API method name** name.
    4. In the **Value** field, select **Invoice clearance** for tax invoices or **Invoice reporting** for simplified invoices.
    5. Select the **Certificate name** name.
    6. In the **Value** field, select **CCSID** or **PCSID**, depending on your place in the [onboarding](#onboarding) process.
    7. Select the **Secret name** name.
    8. In the **Value** field, select **CCSIDSecret** or **PCSIDSecret**, depending on your place in the onboarding process. 

9. Repeat steps 3 through 8 for the **Project invoice** and **Retail simplified invoice** feature setups. 

    > [!NOTE]
    > Repeat steps 3 through 8 for the **Simplified invoice compliance check** and **Retail fiscal document compliance check** feature setups to set up the electronic invoicing feature, **Saudi Arabian ZATCA compliance check (SA)**.
   
10. Complete and deploy the **Saudi Arabian Zatca submission (SA)** feature to the service. For more information, see [Complete and deploy a Globalization feature](../global/GS-e-invoicing-complete-publish-deploy-globalization-feature.md).


## <a id="onboarding"></a>Electronic invoicing onboarding in Saudi Arabia
Onboarding is mandatory for all taxpayers who are subject to electronic invoicing in Saudi Arabia. Taxpayers and their software for e-invoicing must be onboarded ZATCA. As a result of the onboarding process, taxpayers obtain CSIDs, which are required for integration with the electronic invoicing portal that is managed by ZATCA and for further submission of electronic invoices.

Onboarding is an essential part of the Electronic invoicing configuration. For more information about the onboarding process, see [Electronic invoicing onboarding in Saudi Arabia](e-invoicing-sa-onboarding.md).

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

