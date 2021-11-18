---
# required metadata

title: Prepare your environment to interoperate with ID-porten and Altinn web services
description: This topic explains how to prepare your environment to interoperate with ID-porten and Altinn web services.
author: liza-golub
ms.date: 11/18/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22

---

# Prepare your environment to interoperate with ID-porten and Altinn web services

After your company [registered integration point](emea-nor-vat-return-integration-point.md) in ID-porten web portal, complete the following tasks. 
These tasks will prepare your Microsoft Dynamics 365 Finance environment to interoperate with ID-porten and Altinn web services to submit VAT returns.

- [Import and set up Electronic reporting (ER) configurations](#er-setup)
- [Set up application-specific parameters for the VAT Declaration format](#application-specific-parameters)
- [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](#em-setup)
- [Set up the VAT registration number of the company that is reporting VAT return](#vat-registration-number)
- [Set up paper format to preview VAT return](#preview-format)
- [Enable VAT return reporting for companies that report as a VAT group in the same system database](#vat-group)
- [Define a sales tax settlement period](#settlement-period)
- [Set up number sequences for Electronic messages functionality](#number-sequences)
- [Set up document management parameters](#document-management-parameters)
- [Set up validation results transformation schema](#transformation-schema)
- [Set up security roles for electronic message processing](#em-security-roles)
- [Set up security roles to interoperate with ID-porten and Altinn web services](#web-security-roles)
- [Set up client ID and client secret of your ID-porten integration point in Finance](#client-credentials)
- [Set up the internet address of ID-porten and Altinn web services](#internet-address)

ID-porten and Altinn web services require that you use TLS 1.2. For more information about how to enable TLS 1.2, see [How to enable TLS 1.2](https://docs.microsoft.com/en-us/mem/configmgr/core/plan-design/security/enable-tls-1-2).

## <a id="er-setup"></a>Import and set up Electronic reporting (ER) configurations

To prepare Finance to generate VAT return format valid for periods starting from January 1, 2022 in Norway and interoperate with ID-porten and Altinn web services, import the following ER configurations.

| Number | ER configuration name | Type | Description |
|--------|-----------------------|------|-------------|
| **1**	|**Tax declaration model**	|**Model**	|**A generic model for different tax declarations.**|
|2	|Tax declaration model mapping	|Model mapping	|A generic model mapping for VAT declarations.|
|3	|VAT Declaration XML (NO)	|Format (exporting)	|A VAT return in XML format for submission to Altinn.|
|4	|VAT Declaration Excel (NO)	|Format (exporting)	|A VAT return in Excel format for preview.|
|5	|Altinn VAT interoperation (NO)	|Format (exporting)	|A format that is used to create a URL path for ID-porten and Altinn web services endpoints.|
|**6**	|E**lectronic Messages framework model**	|**Model**	|**The model for the Electronic messages framework.**|
|7	|Altinn VAT model mapping	|Model mapping (exporting, importing)	|A model mapping that supports interoperation with ID-porten and Altinn web services for Norway.|
|8	|Altinn VAT authorization format (NO)	|Format (exporting)	|The request parameters for the authorization code and access token and building URLs, where the request will be sent.|
|9	|Altinn VAT import Altinn token format (NO)	|Format (importing)	|The ER format that is used to import the access token that is received from Altinn web service into the database.|
|10	|Altinn VAT import feedback status format (NO)	|Format (importing)	|The ER format that is used to import feedback status received from Altinn web service into the database.|
|11	|Altinn VAT import ID-Porten token format (NO)	|Format (importing)	|The ER format that is used to import the access token that is received from ID-porten web service into the database.|
|12	|Altinn VAT import instance format (NO)	|Format (importing)	|The ER format that is used to import the parameters of instance received from Altinn web service into the database.|
|13	|Altinn VAT import validation result format (NO)	|Format (importing)	|The ER format that is used to import the results of VAT return validation received from Altinn web service into the database.|
|14	|Altinn VAT web request headers format (NO)	|Format (exporting)	|A format that is used to create headers for the Hypertext Transfer Protocol over Secure Sockets Layer (HTTPS) request.|

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the number of the KB in the [LCS Issue search portal](https://lcs.dynamics.com/v2)  to learn more about the changes introduced. If the latest configuration version contains references to the objects that aren't available in your Finance version, the import process will be locked for that configuration version. In this case, import the latest version of the configuration that is available for your Finance version.

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the number of the KB in the [LCS Issue search portal](https://lcs.dynamics.com/v2) to learn more about the changes introduced. If the latest configuration version contains references to the objects that aren't available in your Finance version, the import process will be locked for that configuration version. In this case, import the latest version of the configuration that is available for your Finance version.

> [!NOTE]
> After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for the following configurations:
>
> - **Tax declaration model mapping** under **Tax declaration model**
> - **Altinn VAT model mapping** under **Electronic Messages framework model**
>
> ![Setting the Default for model mapping option to Yes for the Tax declaration model mapping configuration.](media/emea-gbr-default-for-model-mapping-parameter.png)

For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
