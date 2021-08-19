---
# required metadata

title: Checklist for Electronic messages setup for MTD VAT 
description: This topic provides details to check the setup of Electronic messages for MTD VAT.
author: liza-golub
ms.date: 08/18/2021
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
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 07/31/2021
ms.dyn365.ops.version: AX 10.0.22

---

# Checklist for Electronic messages setup for MTD VAT

[!include [banner](../includes/banner.md)]

This topic provides information about how the Electronic messages functionality should be set up so that it supports both the **UK MTD VAT TEST** 
processing for testing purposes, and the **UK MTD VAT returns** processing for real-life interoperation with the production HMRC web application. 
Use this information to determine whether the Electronic messages functionality is set up correctly.

Although this section includes the most important information about the setup, not all of the data is included. 
We recommend that you use a package of data entities that provides a predefined setup of the functionality and includes all the data that is required 
to set up the processing for interoperation with MTD for VAT.

## Electronic message processing

The following types of processing are defined to support interoperation with MTD for VAT.

| Name               | Description |
|--------------------|-------------|
| UK MTD VAT TEST    | The test processing for the preparation and submission of VAT returns to the HMRC sandbox. |
| UK MTD VAT returns | The processing to prepare and submit VAT returns to HMRC. |

> [!IMPORTANT]
> Security roles must be defined for both types of processing to allow access to them at the record level.

## Web applications

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following web applications.

| Name                 | Description |
|----------------------|-------------|
| Dynamics 365 Finance | The HMRC web application for Finance. |
| Sandbox HMRC         | The HMRC sandbox for Finance. |

The following table shows the parameters of the web applications.

| Parameter                               | Value |
|-----------------------------------------|-------|
| Base URL for **Dynamics 365 Finance**   | `https://api.service.hmrc.gov.uk` |
| Base URL for **Sandbox HMRC**           | `https://test-api.service.hmrc.gov.uk` |
| Authorization URL path                  | /oauth/authorize |
| Token URL path                          | /oauth/token |
| Redirect URL                            | urn:ietf:wg:oauth:2.0:oob |
| Authorization format mapping            | MTD VAT authorization format (UK) |
| Import token model mapping              | MTD VAT import token format (UK) that is shown as **MTD VAT token response format to model mapping** in the list |
| Accept                                  | application/vnd.hmrc.1.0+json |
| Content type                            | application/json |

> [!IMPORTANT]
> Security roles must be defined for both web applications to allow access to the access token.

## Web service settings

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following web services.

| Name                | Description                                                              | Web application      |
|---------------------|--------------------------------------------------------------------------|----------------------|
| HMRC GET            | The HMRC web service for GET user requests.                                   | Dynamics 365 Finance |
| HMRC POST           | The HMRC web service for POST user requests.                                  | Dynamics 365 Finance |
| HMRC sandbox GET    | The sandbox that is used to test the HMRC web service for GET user requests.  | Sandbox HMRC         |
| HMRC sandbox POST   | The sandbox that is used to test the HMRC web service for POST user requests. | Sandbox HMRC         |

The following table shows the shared parameters for all these web services.

| Parameter                     | Value |
|-------------------------------|-------|
| Request type – XML            | NO |
| Accept                        | application/vnd.hmrc.1.0+json |
| Content type                  | application/json |
| Request header format mapping | MTD VAT web request headers format (UK) |

The following table shows other request parameters that must be defined for these web services.

| Web service         | Request method | Successful response code |
|---------------------|----------------|--------------------------|
| HMRC GET            | GET            | 200 |
| HMRC POST           | POST           | 201 |
| HMRC sandbox GET    | GET            | 200 |
| HMRC sandbox POST   | POST           | 201 |

## Additional fields

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following additional fields.

> [!NOTE]
> None of these fields can be changed by the user.

| Field           | Description |
|-----------------|-------------|
| Due date        | The due date for the obligation period. |
| HMRC status     | The obligation status in HMRC:<ul><li><strong>O</strong> – Open</li><li><strong>F</strong> – Fulfilled</li></ul> |
| periodKey       | The ID code for the period that the obligation belongs to. This field is hidden and can't be seen. |
| Processing date | The time when the message was processed by HMRC. |
| Received date   | The date when the obligation was received by HMRC. |
| Tax registration number   | The VAT registration number of the company submitting the VAT return. |

## Electronic message item types

The setup of electronic messages for both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing uses one type of electronic message item: **VAT return**.

## Electronic message item statuses

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following electronic message item statuses.

| Status         | Description | Records in this status can be deleted |
|----------------|-------------|---------------------------------------|
| Populated      | The record was filled in from sales tax payments. | Yes |
| Excluded       | The record is excluded from report generation. | Yes |
| To be reported | The line will be included in the VAT return for submission. | No |
| Reported       | The record was included in a VAT declaration file. | No |
| Sent           | The record was sent to HMRC in a VAT declaration. | No |
| Submitted      | The record was submitted to HMRC. | No |

## Electronic message statuses

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following electronic message statuses.

| Status                             | Description | Records in this status can be deleted |
|------------------------------------|-------------|---------------------------------------|
| New obligation request             | A new electronic message has been created to request retrieval of VAT obligations. | Yes |
| Retrieved VAT obligation           | The VAT obligation request has been sent. | Yes |
| Error VAT obligations retrieving   | A technical error occurred during the retrieval of VAT obligations. | Yes |
| Completed VAT obligations request  | VAT obligations have been successfully retrieved. | Yes |
| Error VAT obligations importing    | A technical error occurred during import of VAT obligations. | Yes |
| New VAT return                     | This sales tax payment has been included for further submission. | Yes |
| Ready to generate VAT return       | The message is ready to generate a VAT return. | Yes |
| Generated VAT return               | The VAT return in JSON format has been generated and attached to the message. | No |
| Error VAT return generation        | A technical error occurred when the ER report was generated. | Yes|
| Sent VAT return                    | The VAT return has been sent to HMRC in JSON format. | No |
| Error VAT return submission        | An error occurred during submission of the VAT return. |Yes |
| Completed VAT return               | The VAT return has been completed. | No |
| Error VAT return import response   | A technical error occurred during the import of VAT return response. | Yes |
| New liabilities request            | A new electronic message has been created to request liabilities. | Yes |
| Error VAT liabilities request      | A technical error occurred during the request for VAT liabilities. | Yes |
| Completed VAT liabilities request  | VAT liabilities have been successfully retrieved. | Yes |
| New payments request               | A new electronic message has been created to request VAT payment information. | Yes |
| Error VAT payments request         | A technical error occurred during the request for VAT payments. | Yes |
| Completed VAT payments request     | The request for VAT payments has been completed. | Yes |

## Action populate records

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the **Populate VAT return records** action. The following table shows the setup of the data source for this action.

| Property               | Value |
|------------------------|-------|
| Name                   | VAT payment |
| Message item type      | VAT return |
| Account type           | All |
| Master table name      | TaxReportVoucher |
| Document number field  | Voucher |
| Document date field    | TransDate |
| Document account field | TaxPeriod |
| User query             | Yes |

> [!IMPORTANT]
> Define the settlement period by using the **Edit query** button. For more information, see [Define a sales tax settlement period](emea-gbr-mtd-vat-integration-setup.md#settlement)

## Electronic message actions

Both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing use the following electronic message actions.

| Name                                  | Description | Action type |
|---------------------------------------|-------------|-------------|
| Create VAT obligation request         | Create a message to retrieve VAT obligations.<ul><li><strong>From statuses:</strong> No</li><li><strong>To statuses:</strong> New obligation request</li></ul> | Create message |
| Retrieve VAT obligations              | Prepare the request to retrieve VAT obligations.<ul><li><strong>From statuses:</strong> Error VAT obligations retrieving, New obligation request</li><li><strong>To statuses:</strong> Error VAT obligations retrieving, Retrieved VAT obligation</li><li><strong>Format mapping for URL path:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC GET"</li><li><strong>File name:</strong> "response.json.txt"</li></ul> | Web service |
| Test retrieve VAT obligations         | Retrieve VAT obligations from the HMRC sandbox.<ul><li><strong>From statuses:</strong> Error VAT obligations retrieving, New obligation request</li><li><strong>To statuses:</strong> Error VAT obligations retrieving, Retrieved VAT obligation</li><li><strong>Format mapping for URL path:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC sandbox GET"</li><li><strong>File name:</strong> "response.json.txt"</li></ul> | Web service |
| Import VAT obligations                | Import the response from HMRC that includes VAT obligations.<ul><li><strong>From statuses:</strong> Retrieved VAT obligation, Error VAT obligations importing</li><li><strong>To statuses:</strong> Completed VAT obligations request, Error VAT obligations importing</li><li><strong>Model mapping:</strong> "MTD VAT obligations importing JSON (UK)"</li></ul> | Electronic reporting import |
| Populate VAT return records           | Enter information in sales tax payment records.<ul><li><strong>From statuses:</strong> New VAT return</li><li><strong>To statuses:</strong> No</li><li><strong>Populates records action:</strong> "Populate VAT return records"</li></ul> | Populate records |
| Exclude from reporting                | Mark the sales tax payment record as excluded from reporting. This action doesn't change the electronic message status. | User processing |
| Update to initial status              | Update the status of the sales tax payment to its initial status. This action doesn't change the electronic message status. | User processing |
| Ready to generate VAT return          | Update the status of the message to **Ready to generate**.<ul><li><strong>From statuses:</strong> New VAT return</li><li><strong>To statuses:</strong> Ready to generate VAT return</li></ul> | Message level user processing |
| Update to initial status VAT return   | Update the status of the message to its initial status.<ul><li><strong>From statuses:</strong> Generated VAT return, Ready to generate VAT return, Error VAT return generation, Error VAT return import response. </li><li><strong>To statuses:</strong> New VAT return, Ready to generate VAT return</li></ul> | Message level user processing |
| Preview VAT return                    | Generate a preview file in Excel format.<ul><li><strong>From statuses:</strong> Error VAT return generation, Error VAT return submission, Ready to generate VAT return</li><li><strong>To statuses:</strong> Error VAT return generation, Ready to generate VAT return</li><li><strong>Format mapping:</strong> "VAT Declaration Excel (UK)"</li><li><strong>File name:</strong> "VAT statement.xlsx"</li></ul> | Electronic reporting export message |
| Generate file for submission          | Generate a VAT return file in JSON format for submission to HMRC.<ul><li><strong>From statuses:</strong> Error VAT return generation, Error VAT return submission, Ready to generate VAT return</li><li><strong>To statuses:</strong> Error VAT return generation, Generated VAT return</li><li><strong>Format mapping:</strong> "VAT Declaration JSON (UK)"</li><li><strong>File name:</strong> "VAT_return.json"</li></ul> | Electronic reporting export message |
| Submit VAT return                     | Submit the VAT return in JSON format to HMRC.<ul><li><strong>From statuses:</strong> Error VAT return submission, Generated VAT return</li><li><strong>To statuses:</strong> Error VAT return submission, Sent VAT return</li><li><strong>Message item type:</strong> "VAT return"</li><li><strong>Format mapping for URL path:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC POST"</li><li><strong>File name:</strong> "response.json"</li></ul> | Web service |
| Test submit VAT return                | Test submission of the VAT return to the HMRC sandbox.<ul><li><strong>From statuses:</strong> Error VAT return submission, Generated VAT return</li><li><strong>To statuses:</strong> Error VAT return submission, Sent VAT return</li><li><strong>Message item type:</strong> "VAT return"</li><li><strong>Format mapping for URL path:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC sandbox POST"</li><li><strong>File name:</strong> "response.json"</li></ul> | Web service |
| Import response for VAT return        | Import a response from HMRC about the VAT return that was submitted.<ul><li><strong>From statuses:</strong> Sent VAT return, Error VAT return import response</li><li><strong>To statuses:</strong> Completed VAT return, Error VAT return import response</li><li><strong>Model mapping:</strong> "MTD VAT return response importing JSON (UK)"</li></ul> | Electronic reporting import |
| Create VAT liabilities request        | Create a message to request VAT liabilities.<ul><li><strong>From statuses:</strong> No</li><li><strong>To statuses:</strong> New liabilities request</li></ul> | Create message |
| Request VAT liabilities               | Request VAT liabilities.<ul><li><strong>From statuses:</strong> Error VAT liabilities request, New liabilities request</li><li><strong>To statuses:</strong> Completed VAT liabilities request, Error VAT liabilities request</li><li><strong>Format mapping:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC GET"</li><li><strong>File name:</strong> "response.json.txt"</li></ul> | Web service |
| Create VAT payments request           | Create a message to request VAT payments.<ul><li><strong>From statuses:</strong> No</li><li><strong>To statuses:</strong> New payments request</li></ul> | Create message |
| Request VAT payments                  | Request VAT payments.<ul><li><strong>From statuses:</strong> Error VAT payments request, New payments request</li><li><strong>To statuses:</strong> Completed VAT payments request, Error VAT payments request</li><li><strong>Format mapping:</strong> "MTD VAT interoperation (UK)"</li><li><strong>Web service:</strong> "HMRC GET"</li><li><strong>File name:</strong> "response.json.txt"</li></ul> | Web service |

## Electronic processing actions

The **UK MTD VAT TEST** processing uses the following electronic processing actions.

| Name                                | Run separately | Inseparable sequence |
|-------------------------------------|----------------|----------------------|
| Create VAT obligation request       | Yes            |                      |
| Test retrieve VAT obligations       | Yes            | Obligation           |
| Import VAT obligations              | No             | Obligation           |
| Populate VAT return records         | Yes            |                      |
| Exclude from reporting              | Yes            |                      |
| Update to initial status            | Yes            |                      |
| Ready to generate VAT return        | Yes            |                      |
| Update to initial status VAT return | Yes            |                      |
| Preview VAT return                  | Yes            |                      |
| Generate file for submission        | Yes            |                      |
| Test submit VAT return              | Yes            | Submission           |
| Import response for VAT return      | No             | Submission           |

The **UK MTD VAT returns** processing uses the following electronic processing actions.

| Name                                | Run separately | Inseparable sequence |
|-------------------------------------|----------------|----------------------|
| Create VAT obligation request       | Yes            |                      |
| Retrieve VAT obligations            | Yes            | Obligation           |
| Import VAT obligations              | No             | Obligation           |
| Populate VAT return records         | Yes            |                      |
| Exclude from reporting              | Yes            |                      |
| Update to initial status            | Yes            |                      |
| Ready to generate VAT return        | Yes            |                      |
| Update to initial status VAT return | Yes            |                      |
| Preview VAT return                  | Yes            |                      |
| Generate file for submission        | Yes            |                      |
| Submit VAT return                   | Yes            | Submission           |
| Import response for VAT return      | No             | Submission           |
| Create VAT liabilities request      | Yes            |                      |
| Request VAT liabilities             | Yes            |                      |
| Create VAT payments request         | Yes            |                      |
| Request VAT payments                | Yes            |                      |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
