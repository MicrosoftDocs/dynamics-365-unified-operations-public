---
# required metadata

title: Set up e-Invoicing 
description: This topic provides information about how to set up the e-Invoicing service in Dynamics 365 Finance and Dynamics 365 Supply chain management.
author: gionoder
manager: AnnBe
ms.date: 06/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Set up e-Invoicing 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


The e-Invoicing feature setup is the process of creating the necessary configuration through the Regulatory Configuration Services (RCS) environment and publishing to the e-Invoicing service server. The setup enables you to create the configurable rules that allow the e-Invoicing services to communicate and exchange data, under secure protocol over the internet, with a 3rd party entity through web services.

The configurability relies on the Electronic Report (ER) format configuration as the mean of building content that is sent and received through digital files, and on the orchestration of communication actions to send requests and receive responses from 3rd party web services, without the need to write code.

## Overview

The figure below shows the main components of an e-Invoicing feature:

![Overview e-Invoicing feature](media/e-Invoicing-services-feature-setup-Overview-e-Invoicing-feature.png)

The e-Invoicing feature is the generic name of the resource that is configured and published for consumption of e-invoicing service server. The e-Invoicing feature setup combines, among others, the usage of ER configuration formats to create configurable export and import files, and Actions and Actions flows, which allows the creation of configurable rules to send request, import response and parsing of the response contents.

Because of variation of invoice formats and Action flows, the e-Invoicing feature setup may vary across different countries or business needs. 

## Set up the e-Invoicing feature

The setup process must be completed in your RCS environment. Complete the following steps to create a new e-Invoicing feature.

1. Log in into your RCS environment.
2. Go to **Globalization features workspace** and select **Features \> e-invoicing** tile.
3. In RCS, on the **e-Invoicing features** page, select **Import** to import the ER data model configuration from the Global Repository.
4. Select **+Add** to create a new e-Invoicing feature. You can create the feature from the scratch or derive it from an existing one.

![Select Add e-Invoicing feature](media/e-Invoicing-services-feature-setup-Select-Add-e-Invoicing-feature.png)

> [!NOTE]
> When you create a new e-Invoicing feature, the e-Invoicing feature has a version, and its default status is setup to **Draft**.

### Configurations

Configurations hold the ER format configurations that are necessary for transformations and to create the files that will be exchanged during the communication with 3rd party web service. An e-Invoicing feature can have as many ER file format configurations as necessary and will depend on the integration technical specification given by the web service provider.

To add ER formats to the e-Invoicing feature:

1. On the **e-Invoicing Features** page, select **Configurations**.
2. Select **+Add** to add ER file format configurations for the e-Invoicing feature.

![Select Add e-Invoicing feature configurations](media/e-Invoicing-services-feature-setup-Select-Add-e-Invoicing-feature-Configurations.png)

> [!NOTE]
> When you create an e-Invoicing feature from scratch, you must manually add all the ER file format configurations. When you create a derived feature from an existing e-Invoicing feature, the ER file format configurations are automatically created, inherited from the original e-invoicing feature.

3. Select **Edit** to edit the ER file format configuration through the **Format designer** page.

![Select Edit e-Invoicing feature configurations](media/e-Invoicing-services-feature-setup-Select-Edit-e-Invoicing-feature-Configurations.png)

> [!NOTE]
> While you are editing the format, the Configuration version status is setup to **Draft.**

Use the **Format designer** page to change the file format configuration. For more details, see [Create electronic document configurations](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-configuration).

![ER format designer](media/e-Invoicing-services-feature-setup-ER-Format-designer.png)

### Setups

Feature setups encapsulate the rules for communication and security with a 3rd party web service. An e-invoicing feature can have as many **Feature setups** as necessary based on the business rule you want to accomplish.

Complete the following steps to add Feature setups to the e-invoicing feature.

1. On **the e-Invoicing** Features page, on the **Setups** tab, select **Add** to add Feature setups to the e-invoicing feature.

![Select Add e-Invoicing feature setups](media/e-Invoicing-services-feature-setup-Select-Add-e-Invoicing-feature-Setups.png)

> [!NOTE]
> When you create an e-invoicing feature from scratch, you must add manually the Feature setups that you need. When you create a derived feature from an existing e-invoicing feature, all Feature setups are automatically created because they are inherited from the original e-invoicing feature.

2. Select **Edit** to edit the Feature version setup.

![Select Edit e-Invoicing feature setups](media/e-Invoicing-services-feature-setup-Select-Edit-e-Invoicing-feature-Setups.png)

In the Feature version setup, you can configure the actions, applicability rules, and variables.

![View Actions-Applicability rules-Variables ](media/e-Invoicing-services-feature-setup-View-Actions-Applicability-Rules-Variables.png)

### Actions

Actions are a predefined list of operations, that are executed in sequential order. These actions represent the breakdown of steps needed to accomplish the full execution of the e-Invoicing feature. The actions can encapsulate in the same e-invoicing feature the communication in both directions, sending a request for a destination and receiving a response and parsing its contents.

Each action contains a predefined list of parameters that are required for the action to perform its purpose. Additionally, some parameters may be optionally provided.

**Actions field group**

1. On the **Feature versions setup** page, on the **Actions** tab, select **New** or **Delete** button to manage the creation of actions.
2. Select **Up** or **Down** to move the actions along the sequence order. The actions are executed from top to bottom as shown at grid of actions.

![Manage Actions](media/e-Invoicing-services-feature-setup-Manage-Actions.png)

| **Field**    | **Description**                                                                                                                                                                                                                                                                                 |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Action       | There are nine predefined actions:                                                                                                                                                                                                                                                              |
| Action name  | The name of the action and its execution order.                                                                                                                                                                                                                                                 |
| Description  | Description                                                                                                                                                                                                                                                                                     |
| Enable retry | Enable repeating the action                                                                                                                                                                                                                                                                     |
| Retry action | In the case of retrying, the **Retry** action is the action from where to begin the retrying, finishing on the current action (inclusive retrying). For the actions who have those parameters, the minimum and maximum amounts of retrying are given by minimum and maximum back off parameters |

The following actions are included in the **Actions** field group: 

- Sign the document
- FileStoreActionName
- Use the MS Power AutomateTransform document
- Process the response
- Call the REST web service
- Call the Mexican PAC service
- Call the Brazilian SEFAZ service
- Call the Italian SDI service

**Parameters field group**

![View Actions parameters](media/e-Invoicing-services-feature-setup-View-Actions-Parameters.png)

| **Field**   | **Description**                  |
|-------------|----------------------------------|
| Name        | A predefined list of parameters. |
| Description | A description of the parameters. |
| Value       | The value of the parameters.     |

**List of parameters by action**

Action: Sign document

| **Parameter**                         | **Description**                                                                                                                                                      |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input file                            | Input xml file with a document that needs to be signed with an electronic signature.                                                                                 |
| Certificate name                      | Name of the certificate in storage.                                                                                                                                  |
| Signature type                        | Type of signature to use.                                                                                                                                            |
| Signature method name                 | Name of the signature method which is used to generate an electronic signature.                                                                                      |
| Digest method name                    | The digest method which is used to generate a digest string in the digital signature.                                                                                |
| Canonicalization method name          | The canonicalization method used to calculate the signature hash.                                                                                                    |
| Reference attribute name              | The attribute name that indicates where to insert the reference ID in the signature element.                                                                         |
| Name of element to sign               | Specifies the name of the xml element inside document which needs to be signed with an electronic signature. If not specified, the root of the document is signed.   |
| Name of element to insert signature   | The name of the xml element where we need to insert a generated digital signature. If this is not specified, the signature will be inserted in root of the document. |
| XLST file with digest transform       | XLST file that contains digest transformation rules to generate the digest string for an electronic signature.                                                       |
| Path to insert digest string          | Specifies the path in \<elementName\>.\<Attribute.Path\> format to locate where the generated digest string needs to be inserted.                                    |
| Certificate number location           | Specifies the name of the element and attribute where the certificate number should be put.                                                                          |
| Location of certificate data          | Specifies the name of the element and attribute to where certificate data (base64) needs to be inserted.                                                             |
| Certificate number is in ASCII format | Specifies if the number of the certificate is encoded in ASCII.                                                                                                      |

Action: FileStoreActionName

| **Parameter** | **Description**          |
|---------------|--------------------------|
| Input file    | The input file to store. |

Action: Transform document

| **Parameter**                   | **Description**                                                                     |
|---------------------------------|-------------------------------------------------------------------------------------|
| Input file                      | The source file provides the action with the data to be executed.                   |
| Direction                       | The direction describes if the import or export format will be used.                |
| Configuration id                | The configuration ID describes the format which will be executed.                   |
| Configuration version           | The configuration version may be specified. Otherwise, the latest one will be used. |
| Configuration integration point | The source file provides data to the reporting runtime.                             |

Action: Process response

| **Parameter**                | **Description**                                 |
|------------------------------|-------------------------------------------------|
| Input file                   | Response to analyze.                            |
| Reporting configuration list | List of configurations used to parse responses. |

Action: Call REST web service

| **Parameter**               | **Description**                                                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Web service URL             | The URL address to send request.                                                                                                  |
| Web request timeout         | The maximum amount of time (in milliseconds) to wait for a web service response.                                                  |
| Request operation type      | HTTP Request operation type (GET, POST, DELETE etc).                                                                              |
| Certificate names           | Certificate names.                                                                                                                |
| Response body encoding      | Expected encoding of http response body (to decode it properly).                                                                  |
| HTTP request content type   | Http request content-type header input.                                                                                           |
| HTTP request content body   | Http request body (can be empty).                                                                                                 |
| HTTP parameter query values | Parameter query values to fill the URL with variable parameters.                                                                  |
| Request route               | The route path for HTTP request. The variable parameters can be written in {paramName} notation. For example, "api/{id}/submit"). |
| Route parameter list        | The route parameters in key-value notation to insert variables into the route.                                                    |
| Custom HTTP headers         | The custom HTTP headers to put into the request.                                                                                  |
| HTTP request cookies        | A list of cookies in the key-value notation to put into the http cookies header request.                                          |
| Security protocol           | The security protocol to use for the http request to communicate with the server (TLS1.2 using by default).                       |

Action: Call Mexican PAC service

| **Parameter**            | **Description**                                                                                                                                                                              |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input file               | The file with xml data that will be sent to the web service as a method input parameter.                                                                                                     |
| URL address              | The web service address (endpoint).                                                                                                                                                          |
| Web method (action) name | The name of the web method (action) which must be executed.                                                                                                                                  |
| Certificates             | The certificate chain needed for client authentication on the web service. The client certificate should be the last in the chain. The root and intermediate certificates should come first. |
| Web request timeout      | The maximum amount of time (in milliseconds) to wait for a web service response.                                                                                                             |
| Retry interval           | The time interval between attempts to call and receive a response from the web service. If nothing is specified, no retry attempts will be made after the first call fails.                  |
| Retry count              | The maximum retry count of attempts to call and retrieve a response from the web service.                                                                                                    |
| Retry till               | The maximum time (in milliseconds) until which retry calls can continue.                                                                                                                     |
| Minimum back off         | The minimum back off rate for exponential calculation of retry intervals.                                                                                                                    |
| Maximum back off         | The maximum back off rate for exponential calculation of retry intervals.                                                                                                                    |
| Security protocol        | The security protocol to use for HTTP request to communicate with the server (TLS1.2 using by default).                                                                                      |

Action: Call Brazilian SEFAZ service

| **Parameter**            | **Description**                                                                                                                                                                              |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input file               | File with xml data that will be sent to the web service as a method input parameter.                                                                                                         |
| URL address              | Web service address (endpoint).                                                                                                                                                              |
| Web method (action) name | The name of the web method (action) which must be executed.                                                                                                                                  |
| Certificates             | The certificate chain needed for client authentication on the web service. The client certificate should be the last in the chain. The root and intermediate certificates should come first. |
| Web request timeout      | The maximum amount of time (in milliseconds) to wait for a web service response.                                                                                                             |
| Retry interval           | The time interval between attempts to call and receive a response from the web service. If nothing is specified, no retry attempts will be made after the first call fails.                  |
| Retry count              | The maximum retry count of attempts to call and retrieve a response from the web service.                                                                                                    |
| Retry till               | The maximum time (in milliseconds) until which retry calls can continue.                                                                                                                     |
| Minimum back off         | The minimum back off rate for exponential calculation of retry intervals.                                                                                                                    |
| Maximum back off         | The maximum back off rate for exponential calculation of retry intervals.                                                                                                                    |
| Security protocol        | The security protocol to use for HTTP request to communicate with the server (TLS1.2 using by default).                                                                                      |

Action: Call Italian SDI service

| **Parameter**            | **Description**                                                                                                                                                                                    |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input file               | File with xml data that will be sent to the web service as a method input parameter.                                                                                                               |
| URL address              | Web service address (endpoint).                                                                                                                                                                    |
| Web method (action) name | The name of the web method (action) that must be executed.                                                                                                                                         |
| Certificates             | A certificate chain that is needed for client authentication on the web service. The client certificate should be the last in the chain. The root and intermediate certificates should come first. |
| Web request timeout      | The maximum amount of time (in milliseconds) to wait for web service response.                                                                                                                     |
| Retry interval           | The time interval between attempts to call and receive a response from the web service. If nothing is specified, no retry attempts will be made after the first call fails.                        |
| Retry count              | The maximum retry count of attempts to call and retrieve a response from the web service.                                                                                                          |
| Retry till               | The maximum time (in milliseconds) until which retry calls can continue.                                                                                                                           |
| Minimum back off         | The minimum back off rate for exponential calculation of retry intervals.                                                                                                                          |
| Maximum back off         | The maximum back off rate for exponential calculation of retry intervals.                                                                                                                          |
| Security protocol        | Security protocol to use for HTTP requests to communicate with the server (TLS1.2 using by default).                                                                                               |

## Applicability rules

Applicability rules allow you to create logical rules that determine the usage context for the feature setup. After the e-Invoicing feature is deployed to the service, these rules will be used for comparison against the context received with a business document sent for processing to execute actions from applicable feature setup.

### Set up the Applicability rule field group

1. On the **Feature version setup** page, on **Applicability rules** tab, select **New** to add an applicability rule.

![Manage Actions applicability rules](media/e-Invoicing-services-feature-setup-Manage-Actions-Applicability-rules.png)

2. Select the clauses in the grid to be grouped.
3. Select **Group clause**.

![Manage applicability rules group clause](media/e-Invoicing-services-feature-setup-Manage-Applicability-rules-Group-clause.png)

> [!NOTE]
> When clauses are grouped, a new column is added to the grid. This column contains the logic operation for the grouped clauses.

![Manage applicability rules group criterias](media/e-Invoicing-services-feature-setup-Manage-Applicability-rules-Group-criterias.png)

3. To ungroup a clause, select the grouped clauses you want to ungroup and then select **Ungroup clause**.

![Manage applicability rules ungroup criterias](media/e-Invoicing-services-feature-setup-Manage-Applicability-rules-UnGroup-criterias.png)

> [!NOTE]
> When you ungroup a clause, always start from the inner most level of grouping.

| **Field**     | **Description**                  |
|---------------|----------------------------------|
| And/or        | The logic operators.             |
| Field         | The field to construct the rule. |
| Operator type | The type of operator:            |
| Value         | The criteria for the rule.       |

- Equal
- Not equal
- Greater than/Less than
- Greater than or equal to/Less than or equal to
- Contains
- Begin with

## Variables

Variables can be created and then used as the input value for a parameter of a certain action or to exchange information between e-Invoicing services and the client, resulting from the execution of a certain action as part of the flow of submissions.

**Set up Variables** field group

1. On the **Feature version setup** page, select the **Variable** tab.
2. Select **New** or **Delete** to manage the variables.

![Manage variables](media/e-Invoicing-services-feature-setup-Manage-Variables.png)

| **Field**   | **Description**                                                                   |
|-------------|-----------------------------------------------------------------------------------|
| Name        | The name of variable.                                                             |
| Description | A brief description of the variable.                                              |
| Type        | The type of variable:                                                             |
| Data type   | The variable data type:                                                           |
| Value       | The value of the variable or the name of the action which populates the variable. |

- Constant - The content of the variable is fixed.
- From client - The content of the variable is acquired from the Microsoft Dynamics 365 client during the execution of submission process.
- To client - The content of the variable made available for import by Microsoft Dynamics 365 client during the execution of submission process.
- Boolean
- Date
- Number
- UUID
- String
- File

**Validate feature setup**

On the **Feature version setup** page, select **Validate** to validate the feature version setup.

![Select validate button](media/e-Invoicing-services-feature-setup-Select-Validate-Button.png)

> [!NOTE]
> The validation checks the consistency of the entire configuration. For example, if a certain parameter for an action is mandatory but its value is kept empty, the validation checks catch this inconsistency and you will receive a warning.

#E Environments

An e-Invoicing feature must have an e-Invoicing environment associated with and enabled for it. The e-Invoicing environments must be previously created and published through the configuration of Globalization features from the RCS for your organization.

To enable the e-Invoice environment to an e-Invoicing feature complete the following steps.

1. On the **E-Invoicing Features** page, select the **Environments** tab.
2. Select **Enable** to add an e-Invoicing environment and in the **Effective from** field, enter the date on which it becomes effective.

![Select Enable e-Invoicing feature environment](media/e-Invoicing-services-feature-setup-Select-Enable-e-Invoicing-feature-Environment.png)

## Organizations

The e-invoicing features can be shared across multiple organizations.

To share the e-invoicing feature:

1. On the **e-Invoicing Features** page, on the **Organizations** tab, select **Share with** to add an organization to share.
2. Select **Unshare** to undo the sharing.

## Versions

The Versions controls the e-invoicing feature life cycle by managing its status. You can either create a new version of an existing e-Invoicing feature, or when all configurations are done for a given e-Invoicing feature, you can change its status to Complete, and then to Publish.

If you want to create a new version:

1. On the **e-Invoicing Features** page, select an e-Invoicing feature on the left grid of the page.
2. On **Versions** tab, select **New** to add a new version of the e-Invoicing feature.

Or if you want to manage the e-invoicing feature life cycle:

1. On the **e-Invoicing Features** page, select an e-Invoicing feature on the left grid of the page.
2. On **Versions** tab, select **Change status** to change the status from **Draft** to **Complete**.
3. It will be prompted a dialog form where you must confirm you want to complete the e-Invoicing feature and all its components. Select **Yes**, if want to confirm, or **No** to dismiss.

> [!NOTE]
> When you select Yes, the status of Configuration versions, as one of its components, is automatically changed from **Draft** to **Completed**.

4. Select **Change status** to change the status from **Complete** to **Publish**.
5. It will be prompted a dialog form where you must confirm you want to Publish the e-Invoicing feature and all its components to the Global repository. Select **Yes**, if want to confirm, or **No** to dismiss.

> [!NOTE]
> When you select **Yes**, the status of configuration versions, as one of its components, is automatically changed from **Completed** to **Shared.**

