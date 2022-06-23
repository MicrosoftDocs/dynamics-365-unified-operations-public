---
# required metadata

title: Get started with Electronic invoicing for Saudi Arabia
description: This topic provides information that will help you get started with Electronic invoicing for Saudi Arabia.
author: ikondo
ms.date: 11/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Saudi Arabia
# ms.search.industry: 
ms.custom: intro-internal
ms.author: ilyako
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: AX 10.0.21

---

# Get started with Electronic invoicing for Saudi Arabia

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with Electronic invoicing for Saudi Arabia in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. It guides you through the configuration steps that are country/region-dependent in different components of the system. 

### Prerequisites

Before you begin the procedures in this topic, complete the following prerequisites: 

- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](e-invoicing-service-overview.md).
- Sign up for Regulatory Configuration Services (RCS), and set up Electronic invoicing. For more information, see the following topics:

    - [Sign up for and install the Electronic Invoicing service](e-invoicing-sign-up-install.md)
    - [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md)
    - [Install the add-in for microservices in Lifecycle Services](e-invoicing-install-add-in-microservices-lcs.md)
	
- Activate the integration between your Microsoft Dynamics 365 Finance application and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](e-invoicing-activate-setup-integration.md).
- Learn how to create certificates and secrets in Azure Key Vault, and set it up it as described in [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md). 
- In Microsoft Dataverse, configure virtual entities for Finance and Supply Chain Management. For more information, see [Configure Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md).
- Enable the **CustomerPaymentMethodEntity** virtual entity. For more information, see [Enable Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).
- Add the Dataverse endpoint as a connected application in the RCS instance. For more information, see the [Create a connected application](e-invoicing-connected-applications.md) section in the "Get started with Electronic invoicing service administration" topic.
- Import the **Saudi Arabian electronic invoice (SA)** electronic invoicing feature into RCS from the Global repository. For more information, see [Import features from the Global repository](e-invoicing-import-feature-global-repository.md).

## Country-specific configuration for the Saudi Arabian electronic invoice (SA) Electronic invoicing feature

Some of the parameters from the Saudi Arabian electronic invoice (SA) electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. In RCS, in the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing features** page, verify that the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that **PaymentMethodSubstitutionLookup** lookup is selected.
5. In the **Conditions** section, select **Add** to add a condition.
6. In the **Name** column for the new condition, select the method of payment that is defined in the application. Then, in the **Lookup result** column, select a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
7. Add specific conditions for each method of payment that is defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **&#42;Blank&#42;** or **&#42;Not blank&#42;** placeholder value instead of a specific method of payment.

8. On the **Setups** tab, select **Edit** for the selected configuration. 
9. In the **Processing pipeline** section, turn on the **Export result** option for the **Transform document** action.
10. Create certificates for Cryptographic Stamp Identifiers in Azure Key Vault, see [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md) for details.
     > [!NOTE]
     > You need to create Compliance Cryptographic Stamp Identifier (**CCSID**) or Production Cryptographic Stamp Identifier (**PCSID**) depending of your stage of [onboarding](#onboarding) process.
11. In the **Globalization feature** workspace, select the **Environment setup** related link, then the **Service environments** menu and select the environment that will be used for the feature deployment.
12. In “Number Sequence” section, add new record for the number sequence that will be used for submitted electronic invoices counting.
    ![Number Sequence ыуегз](media/emea-sa-einvoice-counter.jpg)
13. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile, select Draft version of the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature. In the **Setups** menu, select the **Sales invoice** feature setup and select **Edit**.
14. On the **Processing pipeline** tab, in **Processing pipeline** section, select the **Get next number sequence value** action. In the **Parameters** section, in the **Value** field, select from the list the number sequence defined on step 12.
15. Complete, publish, and deploy the **Saudi Arabian electronic invoice (SA)** feature to the service environment. For more information, see the [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment) section in the "Get started with Electronic invoicing" topic.
16. Deploy the **Saudi Arabian electronic invoice (SA)** feature to the connected application. For more information, see the [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application) section in the "Get started with Electronic invoicing" topic.

# <a id="onboarding"></a>Electronic invoicing onboarding in Saudi Arabia
Onboarding is mandatory for all taxpayers who are subjects to electronic invoicing in Saudi Arabia. Taxpayers and their software for e-invoicing must be onboarded by Saudi Arabian tax authorities (**ZATCA**). As the result of onboarding process, taxpayers will obtain Cryptographic Stamp Identifiers (**CSID**) which are required for integration with electronic invoicing portal managed by Saudi Arabian Tax authority and further electronic invoices submission.
Onboarding is an essential part of Electronic invoicing configuration. For more information, about onboarding process, see [Electronic invoicing onboarding in Saudi Arabia](e-invoicing-sa-onboarding.md).

## Microcost Dynamics D365 Finance configuration

Add here...

For more details about Microcost Dynamics D365 Finance configuration, see: [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
