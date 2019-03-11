---
# required metadata

title:  Prepare Finance and Operations for integration with MTD for VAT (United Kingdom)
description: This topic walks you through setting up Microsoft Dynamics 365 Finance and Operations for Making Tax Digital (MTD) for value-added tax (VAT) in the United Kingdom.
author: ShylaThompson
manager: AnnBe
ms.date: 02/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2019-4-30
ms.dyn365.ops.version: 10.0.1

---

# Prepare Finance and Operations for integration with MTD for VAT (United Kingdom)

[!include [banner](../includes/banner.md)]
[!include [preview-banner](../includes/preview-banner.md)]

This topic walks you through setting up Microsoft Dynamics 365 Finance and Operations for Making Tax Digital (MTD) for value-added tax (VAT) in the United Kingdom.

### Making Tax Digital - VAT Statement submission 

On July 13, 2017, the Financial Secretary to the Treasury and Paymaster General in the United Kingdom announced that Making Tax Digital (MTD) for value-added tax (VAT) will take effect on April 1, 2019. 

MTD introduces an obligation for VAT-registered businesses to keep their records digitally (for VAT purposes only) and to provide VAT return information to Her Majesty’s Revenue and Customs (HMRC) through software that is functionally compatible with MTD. Starting April 1, 2019, MTD for VAT will be mandatory for businesses that have turnover which exceeds the VAT registration threshold (currently £85,000). It will remain voluntary for VAT-registered businesses below the VAT threshold until 2020 at the earliest.

VAT returns will have to be submitted to HMRC using software that is compatible with MTD. VAT returns can no longer be submitted by the former method using the HMRC portal. 

VAT returns are filed quarterly or monthly in the UK. The deadline for submitting the return online and paying HMRC is one calendar month and seven days after the end of the VAT period. 

As HMRC states on the official website, the current amendment process will stay in place for VAT: 
- If the net value of the errors on the VAT return is less than £10,000, the company will amend them in the next VAT return. 
- If the net value of the errors exceeds £10,000, the company must complete the VAT 652 form, which is available on the GOV.UK website. 
For more information about MTD for VAT, see Making Tax Digital for VAT: legislation overview.

Software that is compatible with MTD must support the following requirements: 
- Keep the required records in a digital form. 
- Preserve those records in digital form for up to 6 years. 
- Create a VAT return from the digital records that are held in functionally compatible software, and digitally provide this information to HMRC. 
- Provide VAT data to HMRC on a voluntary basis. 
- Receive, via the MTD for VAT application programming interface (API) platform, information from HMRC about a relevant entity’s compliance with obligations under the regulations. 
As HMRC mentions in Making Tax Digital for Business VAT Guide for Vendors, users must sign up for the MTD service for VAT, even if they have already signed up to use the MTD service for income tax. For more information about how to get ready for MTD, see Making Tax Digital: how VAT businesses and other VAT entities can get ready.

To support the MTD for VAT requirements in Dynamics 365 for Finance and Operations the solution is based on Electronic messages functionality which provides a flexible approach of setting up and supporting of reporting processes. The setup package for the UK MTD for VAT covers the following scope of interoperation to let companies in the UK fulfill their VAT obligations:

- **Retrieve VAT obligations** (Mandatory): Users can initiate a request to HMRC to obtain their company’s VAT obligations for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT obligations that is defined in the company’s profile on the HMRC side. VAT obligations contain information about the VAT period, the due date for submission, and the status of the obligation. This information will be reflected in Dynamics 365 for Finance and Operations. 
- **Submit VAT return for period** (Mandatory): The system will collect information about VAT returns. The information collected is based on the Sales tax payment transactions that have been posted in the system via the sales tax settlement process, with respect to the VAT obligations that are registered in the system. After this information is collected a VAT return report in JavaScript Object Notation (JSON) file generated, user will submit the report to HMRC. The HMRC response to the submission will be reflected in Dynamics 365 for Finance and Operations. 
- **Retrieve VAT liabilities** (Optional): Users can initiate a request to HMRC to obtain their company’s VAT liabilities for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT liabilities that is defined in the company’s profile on the HMRC side. This information will be stored in Dynamics 365 for Finance and Operations as an attachment in JSON format to the related electronic message.
- **Retrieve VAT payments** (Optional): Users can initiate a request to HMRC to obtain their company’s VAT payments for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT payments that is defined in the company’s profile on the HMRC side. This information will be stored in Dynamics 365 for Finance and Operations as an attachment in JSON format to the related electronic message.

The setup package for the UK MTD for VAT will not cover the optionally required “View VAT Return” endpoint. Electronic messages functionality allows to set up and support this endpoint.

When a company is signed up for the MTD service for VAT in HMRC, to get Finance and Operations ready to interoperate with HMRC web service for retrieving VAT obligations and submission of VAT returns the following steps should be done in the Finance and Operations:

> [!div class="checklist"]
> * Import and set up Electronic Reporting (ER) configurations
> * Setup application specific parameters
> * Import package of data entities with predefined Electronic messages setup
> * Set up General ledger parameters
> * Define Sales tax settlement period
> * Setup security roles for Electronic messages processing
> * Setup security roles to access token of web application
> * Initialize web application for interoperation with HMRC
> * Obtain Authorization code for Sandbox (for testing purposes only)
> * Obtain Authorization code for Production
> * Get an Access token


## Import and set up Electronic Reporting (ER) configurations

To prepare Dynamics 365 for Finance and Operations to interoperate with MTD for VAT the following ER configuration must be imported:

| **\#** | **ER configuration name**                  | **Type**                             | **Description**     |
|--------|---------------------------------------------|--------------------------------------|--------------------|
| 1      | **Tax declaration model**                   | **Model**                            | Generic model for different tax declarations                                 |
| 2      | Tax declaration model mapping               | Model mapping                        | Generic model mapping for VAT declarations                                   |
| 3      | MTD VAT returns exporting JSON (UK)         | Format (exporting)                   | VAT return in JSON format for submission to MTD HMRC                         |
| 4      | MTD VAT returns exporting EXCEL (UK)        | Format (exporting)                   | VAT 100 report - declaration in Excel format                                 |
| 5      | MTD VAT interoperation (UK)                 | Format (exporting)                   | Format serves to create URL path to HMRC endpoints and to request test user. |
| 6      | MTD VAT importing model mapping (UK)        | Model mapping (importing)            | VAT obligations importing model mapping                                      |
| 7      | MTD VAT obligations importing JSON (UK)     | Format (importing)                   | Retrieved from HMRC VAT obligations importing format                         |
| 8      | **Electronic Messages framework model**     | **Model**                            | Electronic messages (EM) framework model                                                           |
| 9      | MTD VAT model mapping (UK)                  | Model mapping (exporting, importing) | Model mapping to support interoperation for the UK MTD for VAT               |
| 10     | MTD VAT return response importing JSON (UK) | Format (importing)                   | VAT declaration submission response from HMRC import to Electronic messaging |
| 11     | MTD VAT web request headers format (UK)     | Format (exporting)                   | Request header parameters creation for https request                         |
| 12     | MTD VAT authorization format (UK)           | Format (exporting)                   | Request header parameters for authorization code and access token            |
| 13     | MTD VAT import token format (UK)            | Format (importing)                   | Access token from HMRC import to database                                    |

> [!NOTE]
> When all the ER configurations from the table above are imported, select and mark **Default for model mapping** for the following configurations:
> -   Tax declaration model mapping
> -   MTD VAT model mapping (UK)
>
> ![Default for model mapping](media/emea-gbr-default-for-model-mapping-parameter.png)

For more information about how to download Electronic reporting configurations from Lifecycle Services, refer to [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md). 

## Setup application specific parameters

VAT declaration of the United Kingdom includes 9 boxes which must contain values calculated basing on tax transactions depending on a set of criteria like transaction direction, tax code, country code of tax code and tax type (item or service). User can influence on collection of tax transactions supposed for reporting in each box via **Application specific parameters**. For VAT declaration there is a **ReportFieldLookup** parameter for which the following result values are available:

-	VATDue
-	VATDueEC
-	ECSupplies
-	VATReclaimed
-	Other.

For each of these values user can define set of Sales tax codes together with classifier associated with direction of tax transaction and credit note identifier.
Table below provides definition of classifier:

| **Classifier value**       | **Condition**     |
|-----------------|---------------------|
| **PurchaseCreditNote**   | <li> Credit note <li> Tax direction = Sales tax receivable  |
| **Purchase**   | <li> Not credit note <li> Tax direction = Sales tax receivable  |
| **SalesCreditNote**   | <li> Credit note <li> Tax direction = Sales tax payable  |
| **Sales**   | <li> Not credit note <li> Tax direction = Sales tax payable  |
| **PurchaseExemptCreditNote**   | <li> Credit note <li> Tax direction = Tax-free purchase  |
| **PurchaseExempt**   | <li> Not credit note <li> Tax direction = Tax-free purchase  |
| **SalesExemptCreditNote**   | <li> Credit note <li> Tax direction = Tax-free sales  |
| **SaleExempt**   | <li> Not credit note <li> Tax direction = Tax-free sales  |
| **UseTaxCreditNote**   | <li> Credit note <li> Tax direction = Use tax  |
| **UseTax**   | <li> Not credit note <li> Tax direction = Use tax  |
| **PurchaseReverseChargeCreditNote**   | <li> Credit note <li> Tax direction = Sales tax receivable <li> ReverseCharge_W = Yes  |
| **PurchaseReverseCharge**   | <li> Not credit note <li> Tax direction = Sales tax receivable <li> ReverseCharge_W = Yes |
| **SalesReverseChargeCreditNote**   | <li> Credit note <li> Tax direction = Sales tax payable <li> ReverseCharge_W = Yes  |
| **SalesReverseCharge**   | <li> Not credit note <li> Tax direction = Sales tax payable <li> ReverseCharge_W = Yes  |

Before starting to use VAT Declaration JSON (UK) and VAT Declaration Excel (UK) formats it is required to set up **ReportFieldLookup** application specific parameter. Example of this setup can be downloaded from **Shared asset library** of LCS portal. Find “**UK MTD VAT ReportFieldLookup v1.xml**” file on **Data package** folder of Shared asset library and download it.

To setup **ReportFieldLookup**application specific parameters in the system, open **Electronic reporting**, select **VAT Declaration JSON (UK)** format in the configurations’ tree, click **Configurations** > **Application specific parameters** > **Setup** on the Action pane. Select the version of the format you are going to use. If you want to use the example of setup, click **Import** button on the action pane and select previously downloaded file. If you want to define conditions manually, select **ReportFieldLookup** on **Lookups** fast tab and define criteria on **Conditions** fast tab. Example file can also be used as a starting point on setting up of conditions. When setup of condition is completed, change **State** field value to **Completed**, save and close the page.

Important note! It is recommended to setup **Other** value as the last condition in the list. It is not used in **VAT Declaration JSON (UK)** format but must be set up “*Not blank*” for both criteria.

Application specific parameters setup can be easily exported and imported from one version of a report to another as well as from one report to another when both reports have same structure of lookup field(s). Export your setup when it is ready and import it to **VAT Declaration Excel (UK)** format.

## Import a package of data entities that include predefined Electronic messages setup

Setup of Electronic messages functionality for the purposes of MTD for VAT contains many steps, names of some predefined entities are used in the ER configurations. This is why it is important to use a set of predefined values delivered in a package of data entitled for the related tables.

Open [Lifecycle services](https://lcs.dynamics.com/v2) web portal, go to the **Shared asset library** and open **Data package** asset type. Find **UK MTD-VAT setup.zip** in the list of **Data package files** and download it on your computer.

When the **UK MTD-VAT setup.zip** is downloaded, open Finance and Operations, select the company from which you are going to interoperate with HMRC and open **Workspaces** \> **Data management**. You need to import data from the **UK MTD-VAT setup.zip** to the selected company.

To do so, click on **Import** button in **Data management** work space, define **Source data format** as **Package**, and select the **UK MTD-VAT setup.zip** file from your computer by **Upload and add** button, import it:

![Add file](media/emea-gbr-mtd-vat-add-file.png)

For more information, refer to [Data management](../../dev-itpro/data-entities/data-entities-data-packages.md?toc=/fin-and-ops/toc.json).

> [!NOTE]
> Some records in the data entities of the package include link on ER configurations. It is important to have ER configurations imported to Dynamics 365 for Finance and Operations before you start importing of data entities package.

The **UK MTD-VAT setup** package provides setup for two processing which can be used independently:

-   **UK MTD VAT returns** – to interoperate with **production** HMRC web service
-   **UK MTD VAT TEST** – to interoperate with **sandbox** HMRC web service.

The **UK MTD-VAT setup** package provides also setup for two web applications to interoperate with HMRC web services:

-   **Dynamics 365 for Finance and Operations** – to interoperate with **production** HMRC web service
-   **Sandbox HMRC** – to interoperate with **sandbox** HMRC web service

For more information about predefined setup included into data entities in the package for MTD for VAT, refer to [Appendix 1: Electronic messages setup for MTD for VAT](#appendix-1-electronic-messages-setup-for-mtd-for-vat). 

## Set up General ledger parameters

In General ledger parameter the following parameters must be set up:

-   Number sequences
-   VAT statement format mapping

### Number sequences

To work with Electronic messages, related number sequences must be defined. Open **Tax** \> **Setup** \> **General ledger parameters,** select **Number sequences** tab and setup two number sequences:

-   Message
-   Message item.

### VAT statement format mapping

Dynamics 365 for Finance and Operations allows to generate a paper format of the VAT statement in “VAT 100 report” format using **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** page or directly from **Tax** \> **Inquires and reports** \> **Sales tax inquires** \> **Sales tax payments** page for a selected sales tax payment transaction. “VAT 100 report” is generated in SSRS format by using this functionality.

To get the “VAT 100 report” in MS Excel format instead of the SSRS format, a ER format must be defined in **General ledger parameters**. To do so, open **Tax** \> **Setup** \> **General ledger parameters,** select **Sales tax** tab and select “VAT Declaration Excel (UK)” in the **VAT statement format mapping** field in **Tax options** group of fields.

When the **VAT statement format mapping** field is empty, the old SSRS “VAT 100” report will be generated.

Define Sales tax settlement period
----------------------------------

Electronic messages processing defined for MTD for VAT provided in the “UK MTD-VAT setup.zip” is company agnostic and may be implemented to any legal entity in Dynamics 365 for Finance and Operations. Both “UK MTD VAT returns” (for production) and “UK MTD VAT TEST” (for sandbox) Electronic messages processing allows to collect sales tax payment transactions in the Legal entity to generate VAT return in JSON (or MS Excel format) either for production or testing purposes. Collection of sales tax payment transactions is implemented via
**Populate VAT return records** action of “Populate record” type. To collect sales tax payment transactions correctly, **Sales tax settlement period** must be defined for **Populate VAT return records** action. To do so, open **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**, select **Populate VAT return records** action, select **VAT payment** record on **Datasource setup** tab and click **Edit query** button on the Action pane of the tab. Define for **Settlement period** field of the **Sales tax payments** table the Sales tax settlement period in which tax transactions must be reported to HMRC from the selected Legal entity:

![Sales tax inquiry](media/emea-gbr-sales-tax-inquiry.png)

If “**Settlement period**” parameter is not defined, all tax transactions in selected legal entity will be considered for reporting to MTD for VAT.

## Set up security roles for Electronic messages processing

Different groups of users may need to have access to different Electronic messages processing. To restrict access basing on defined in the system **Security groups** to each of both processing (“UK MTD VAT returns”, “UK MTD VAT TEST”) open **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, select “**UK MTD VAT TEST**” processing first and add those security group(s) which must operate with this processing for testing purposes. If no security group is defined for the processing, a system administrator only will be allowed to see the processing in Electronic messages form.

To restrict access for production processing (“UK MTD VAT returns”) open **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, select “**UK MTD VAT returns**” processing and add those security group(s) which must operate with this processing for real-life interoperation with production HMRC environment. If no security group is defined for the processing, a system administrator only will be allowed to see the processing in Electronic messages form.

## Set up security roles to access token of web application

When an access token to each of HMRC web applications (production, sandbox) is retrieved from HMRC, it will be stored in the data base of the system in encrypted format. When a request of any type is going to be addressed to HMRC, the access token must be used. For the security purposes access to the access token must be restricted for only those security groups which must be allowed to address requests to HMRC. When a user outside of the security group is trying to address a request to HMRC, an exception will inform user that he(she) is not allowed to interoperate via selected web application.

To set up **Security groups** which must have access to HMRC’s access token for MTD for VAT, open **Tax** \> **Setup** \> **Electronic messages** \> **Web applications,** select the web application for which you want to define security group(s) and add them on **Security roles** fast tab.

When **Security roles** are not defined for a web application, a system administrator only will be able to interoperate via this web application.

## Initialize web application for interoperation with HMRC

Each web application on HMRC side has three parameters which uniquely identify it:

-   **Client ID** – unique identifier of web application
-   **Client secret** – secret passphrase used to authorize web application
-   **Server token** – secret token used to authorize web application when making requests to any application-restricted endpoint.

These parameters are used during addressing requests to HMRC and must be filled in before you start authorization process for a web application.

For sandbox application these parameters can be obtained manually from **Manage credentials** part of your sandbox application on HMRC portal. Copy and past them into the system via **Tax** \> **Setup** \> **Electronic messages** \> **Web applications** for **Sandbox HMRC** web application in the appropriate fields in the **Authorization parameters** group of fields.

For production application (**Dynamics 365 for Finance and Operations**) these parameters are stored in the system in respect to HMRC’s requirements and must be stored in the encrypted format. To initialize them, open **Tax** \> **Setup** \> **Electronic messages** \> **Executable class settings** page, select **InitProdWebAppl** executable class and click on **Parameters** button on the Action pane. Select **Dynamics 365 for Finance and Operations** in the dialog and click **OK** button. It is important to click OK button here or parameter will not be saved into the data base. When parameter is saved, the executable class must be run. To do so, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages,** click **Run processing** button on the Action pane, select **UK MTD VAT returns** in the Processing field, mark **Choose action** check box, select **Initialize production web
application** **Action** and click **OK** button. Production application credentials will be populated for **Dynamics 365 for Finance and Operations** web application in an encrypted format.

## Obtain Authorization code for Sandbox 

HMRC provides possibility to register as a developer on [“HMRC Developer Hub”](https://developer.service.hmrc.gov.uk/developer/registration) and access to sandbox environment for testing purposes. Being registered as a developer, you may use **UK MTD VAT TEST** processing to try to interoperate with HMRC sandbox environment. For this purpose, you need to get a Test user credentials first:

-   **Used ID** – a name to access HMRC during Authorization code requesting
-   **Password** – a password to access HMRC during Authorization code requesting
-   **VRN** – testing VAT registration number (VRN) which is used during testing interoperation with HMRC’s sandbox.

These three parameters must be used together.

To get these testing credentials, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select **UK MTD VAT TEST** processing and click on **New** button on the Action pane of the **Messages** fast tab. Select **Create test user request** action and click “**OK**”. A new Electronic message will be created. You don’t need to fill in any fields of this electronic message for the purpose of Test user requesting. Click **Generate report** button on the Action pane of the **Messages** fast tab and confirm sending of Test user request to HMRC by **OK** button (**Generate test user request** action is initialized together with **Send test user request** action).

Response from HMRC will be attached to the electronic message as an attachment in JSON format. To open it, select the electronic message and click on **Clip** button in the right top corner of your window. An Attachments window will be open for the selected electronic message. Select the last **TestUserInfo.txt** file and click **Open** button on the Action pane. In the opened file you will find **userID**, **password** and **VRN** fields and their respective values.

Update **Tax exempt number** of the Legal entity you are operating in with obtained **VRN** value from HMRC. Don’t change this number during operation with sandbox web application unless you obtain again a new Test user credentials.

When **Tax exempt number** of the Legal entity you are operating in is updated, proceed with authorization in HMRC. There are two steps to be done before your system is authorized to interoperate with HMRC:

-   Get **Authorization code**
-   Get **Access token**.

To get an **Authorization code,** open **Tax** \> **Setup** \> **Electronic messages** \> **Web applications,** select the web application for which you want to authorize (**Sandbox HMRC**) and click on **Get authorization code** button. Confirm that you want to initialize authorization process by **OK** button. In the **Electronic reporting parameters** form specify **Scope**. The following values are allowed by HMRC:

-   read:vat
-   write:vat
-   read:vat write:vat

It is recommended to type **read:vat write:vat** in this field as the same application must be used for both GET and POST https requests to the web service. Click **OK** button to address the authorization request to HMRC. By **OK** button you will be redirected to HMRC portal for authorization. On **Sign in** page enter values related to **userID** and **password** from response which you received previously on getting of Test user credentials step. Next page will show **Authorization code** granted by HMRC. **Copy** it to the clipboard and proceed with getting an **Access token**. The **Authorization code** is valid only 10 minutes during which you can retrieve Access token. If you didn’t retrieve Access token for 10 minutes and the Authorization code is expired, you may get a new one with the same Test user credentials or get new Test user.

## Obtain Authorization code for Production

When a company is ready to interoperate in real-life with MTD for VAT it must create an **HMRC online account** and link it to the Finance and Operations application inside this account. As a result, the company will be granted with credentials tied to the VAT registration number of this company:

-   **Used ID** – a name to access HMRC during Authorization code requesting
-   **Password** – a password to access HMRC during Authorization code requesting.

Having user credentials, an authorization process can be initialized. There are two steps to be done before your system is ready to interoperate with HMRC:

-   Get **Authorization code**
-   Get **Access token**.

To get an **Authorization code** from HMRC, open **Tax** \> **Setup** \> **Electronic messages** \> **Web applications,** select the web application for which you want to authorize (**Dynamics 365 for Finance and Operations**) and click on **Get authorization code** button. Confirm that you want to initialize authorization process by **OK** button. In **the Electronic report parameters** form specify **Scope**. The following values are allowed by HMRC:

-   read:vat
-   write:vat
-   read:vat write:vat

It is recommended to type **read:vat write:vat** in this field as the same application must be used for both GET and POST https requests to the web service. Click **OK** button to address the authorization request to HMRC. By **OK** button you will be redirected to HMRC portal for authorization. On **Sign in** page enter **Used ID** and **Password** granted by HMRC on creation of the **HMRC online account**. Next page will show **Authorization code**. **Copy** it to the clipboard and proceed with getting of **Access token**. The **Authorization code** is valid only 10 minutes during which you can retrieve Access token. If you didn’t retrieve Access token during 10 minutes and the Authorization code is expired, you may get a new one.

## Getting an Access token

Initialize getting of **Access token** during 10 minutes from the moment an **Authorization code** was generated by HMRC.

Open **Tax** \> **Setup** \> **Electronic messages** \> **Web applications,** select the web application for which you want to authorize (**Sandbox HMRC** – for testing purposes, **Dynamics 365 for Finance and Operations** – for production) and click on **Obtain access token** button on the Action pane of **Web applications** form to request an Access token from HMRC. Past from the clipboard the **Authorization code** copied from the HMRC portal during obtaining of Authorization code and click **OK**. Access token request will be sent to HMRC and an Access token will be automatically saved in Dynamics 365 for Finance and Operations from the HMRC’s response. It is not allowed to review the token from user interface. You can observe validity period of Access token in **Access token will expire in** field. Each Access token is valid during 4 hours from the moment when it was created by HMRC. To receive a new one, you don’t need to renew an Authorization code. For this purpose, you need to Refresh access token.

Each Access token is valid during 4 hours from the moment when it was created by HMRC. To Refresh it, click on **Refresh access token** button on the Action pane of **Web applications** form to manually initiate refreshing of an access token. Refresh Access token request will be sent to HMRC and a new Access token will be automatically saved in the system from the HMRC’s response.

It is not needed to refresh token manually each 4 hours or before you start to interoperate with HMRC. During interoperation with HMRC this refreshing of Access token procedure will be initialized automatically and refreshing of Access token will be hidden from user.

## Retrieving VAT obligations from HMRC

When **Web application** is initialized and authorized, system is ready to interoperate with HMRC.

Open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select either **UK MTD VAT TEST** processing for testing purposes or **UK MTD VAT returns** for real-life interoperation with production HMRC web application. This form presents information about VAT obligations and returns and serves for interoperation with HMRC web service. Click **New** button on **Messages** fast tab, select **Create VAT obligation request** Action and click **OK** button. A new Electronic message will be created in **New obligation request** status. Fill in fields: 

| **Field**       | **Description**     |
|-----------------|---------------------|
| **From date**   | Mandatory field for Electronic message retrieving VAT obligations. Start date of period for which you want to get information about VAT obligations from HMRC. |
| **To date**     | Mandatory field for Electronic message retrieving VAT obligations. End date of period for which you want to get information about VAT obligations from HMRC    |
| **Description** | Optional field for Electronic message retrieving VAT obligations. Type a description for Electronic message. |

**Action log** will save information about user, date and time of the Electronic message creation.

No **Additional fields** are applicable for this type of Electronic message.

Click **Send report** button to initialize retrieving of VAT obligations information from HMRC. Next **Retrieve VAT obligations** Action is automatically defined in the **Run processing** dialog and filled in by the system. Click **OK** button. A request in JSON format will be created and addressed to HMRC web application, response from HMRC will be received and attached to the Electronic message. According to the response, new Electronic messages for VAT return will be created or existing updated.

HMRC identifies uniquely each VAT return period via a **periodKey** parameter. This parameter in stored respectively in Dynamics 365 for Finance and Operation but according HMRC mandatory requirements its value must be hidden from user interface. User must not be allowed to see the **periodKey** value from the system interface.

For storing **periodKey** value in both **UK MTD VAT TEST** and **UK MTD VAT returns** processing, **periodKey** Additional filed is used. It is setup as hidden so that user will not be able to see its value. It is not recommended to change this setup for **periodKey** Additional field to accommodate requirements of HMRC.

Schematically lifecycle of Electronic message processing for VAT obligation retrieving is shown on the diagram:

![Schematic lifecycle of electronic message processing for VAT obligation retrieving](media/mkd-process.png)

The last step of the processing is **Import VAT obligations** action of **Electronic reporting import** type. On this step system defines:

-   if a VAT obligation from the response doesn’t exist in the data base and the status of this VAT obligation in HMRC is **Open**, a new Electronic message in **New VAT return** status will be created.

-   if a VAT obligation from the response doesn’t exist in the data base and the status of this VAT obligation in HMRC is **Fulfilled**, a new Electronic message in **Completed VAT return** status will be created.

-   if a VAT obligation from the response exists in the data base, system verifies and synchronize **Additional fields** values with the information from the response: **HMRC status, Due date, Received date.**

All the actions done with Electronic messages are logged and can be reviewed on the **Log** fast tab.

## Testing “Gov-Test-Scenario” for “Retrieve VAT obligations” endpoint in HMRC’s sandbox

HMRC provides possibility to simulate different scenario of VAT obligations retrieving on sandbox web application. Related information can be found in “Endpoints” paragraph of “VAT” subscription API documentation. For example, “QUARTERLY_NONE_MET” simulates the scenario where the client has quarterly obligations, and none are fulfilled. To try different scenario in sandbox application, open **Workspaces** \> **Electronic reporting** \> **Reporting configurations** and select **MTD VAT web request headers format (UK)** under **Electronic Messages framework model**. Derive new child format configuration under **MTD VAT web request headers format (UK)** and open it in **Designer**. Find **File** \> **JSON Object** \> **Gov-Test-Scenario** property, expand it and select String under it. Define a scenario you want to test as the String value.

For example:

![String value example](media/emea-gbr-format-designer-string.png)

Check that **Gov-Test-Scenario** property is enabled in the format. To do so, switch to **Mapping** tab and check the **Enabled** property value of the **Gov-Test-Scenario** node. It should be either empty or “true”. To change Enabled property value, click on a “pencil” button near it:

![JSON object](media/emea-gbr-format-designer-json-object.png)

Save and complete the format. To let system to use the new format (with **Gov-Test-Scenario** property filled in) instead the parent one on addressing the request to HMRC, open **Tax** \> **Setup** \> **Electronic messages** \> **Web service settings**, select **HMRC sandbox GET** web service and select your new format instead of **MTD VAT web request headers format (UK)** in **Request headers format mapping** field.

Change the **Gov-Test-Scenario** property in the new format for all the scenarios you want to test. Clean up the **Gov-Test-Scenario** property in the format and complete it when you finilize testing.

### Collect data for VAT return

Process of preparation and submission of VAT return for a period is based on **Sales tax payment** transactions posted during [Settle and post sales tax](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/general-ledger/tasks/create-sales-tax-payment) procedure in Dynamics 365 for Finance and Operations. Find more information about Sales tax settlement and reporting in [Sales tax overview](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/general-ledger/indirect-taxes-overview).

Before starting preparation and submission of VAT return to HMRC, complete regular **Settle and post sales tax** procedure for the period you are going to report to HMRC. As a result of this procedure, new **Sales tax payment** transactions will be created. Open **Tax** \> **Inquires and reports** \> **Sales tax inquires** \> **Sales tax payments** and find Sales tax payments are there. You may review the resulting values for each of the Sales tax payment transaction in “VAT 100” report in SSRS or MS Excel format. To know how you can define which format will be used, see [Set up General ledger parameters](#vat-statement-format-mapping) paragraph of this document. To generate “VAT 100” for selected Sales tax payment transaction, click “**Print report**” button on the Action pane.

It is allowed in Dynamics 365 for Finance and Operations to run **Settle and post sales tax** procedure several times for the same period before you submit VAT return to HMRC. All the Sales tax payment transactions will be possible to include to the same VAT return report for a period. System populates transactions for reporting basing on **Sales tax settlement period** defined in “**Populate VAT return records**” action of the processing. See [Define Sales tax settlement period](#define-sales-tax-settlement-period) paragraph of this document to find more information about it.

**Important note!** MTD for VAT allows to do only one submission of VAT return for each reporting period. As HMRC informs on the official web site, the current amend process will stay in place for VAT:

-   To amend a VAT return where the net value of the errors is below £10,000, the company will do this in the next VAT return.
-   To amend a VAT return where the net value of the errors is over £10,000, the company will need to complete the VAT 652 form available on the GOV.UK website.

When **Settle and post sales tax** procedure is completed, start preparing a report for electronic submission. The first step of data preparation is collecting related to the period Sales tax payment transactions. Open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select either **UK MTD VAT TEST** processing for testing purposes or **UK MTD VAT returns** for real-life interoperation with production HMRC web application. Select the Electronic message on **Message** fast tab related to
the period you want to submit VAT return. Don’t update **Start date** and **End date** fields of the record. These values are received from HMRC and will be used as criteria for collecting of Sales tax payment transactions. You may add a description for the Electronic message. Collecting of VAT data is available for Electronic messages in “**New VAT return**” status only. To start collecting, click **Collect data** button on the Action pane of the **Message** fast tab. **Populate VAT return records** Action is predefined in **Run processing** dialog, click **OK** button. As a result of this action, system will populate posted in the **From date** and **To date** period Sales tax payment transactions as **Electronic message items** of the message. Review populated transactions on **Message items** fast tab.

If for some reason a populated Sales tax payment transaction must be excluded from the report, you may delete it or update its status to **Excluded** using **Update status** button on the Action pane of the Message items fast tab. Transactions in **Excluded** status will not be considered for reporting. Status of a transaction may be reverted from **Excluded** back to **Populated** using the same **Update status** button on the Action pane of the Message items fast tab.

You can repeatedly click on **Collect data** button until the Electronic message is moved to the next status. When data is collected, click **Update status** button on the Action pane of Messages fast tab. **Ready to generate VAT return** status is predefined in the **Update status** dialog, click OK to mark the Electronic message as ready for report generation. Linked **Electronic message items** status will be respectively updated to **To be reported**. If for some reason you need to go back to the previous step and continuer
collecting of data of changing Electronic message items status, click on the same **Update status** button on the Action pane of Messages fast tab. Select **New VAT return** in the New status field and click OK.

All the actions with Electronic message are reflected on **Action log** fast tab.

For Electronic message in **Ready to generate VAT return** status a report generation can be initialized. Two options of generation are available:

-   **Preview VAT return** – the file will be generated in MS Excel format, attached to the Electronic message, no statuses will be changed.

-   **Generate file for submission** – the file will be generated in JSON format, attached to the Electronic message, Electronic message status will be updated to **Generated VAT return**, Status of linked Electronic message items will be updated to **Reported**.

### Generate VAT return in MS Excel for preview

To generate a VAT return in “VAT 100” format in MS Excel, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select either **UK MTD VAT TEST** processing for testing purposes or **UK MTD VAT returns** for real-life interoperation with production HMRC web application, select Electronic message record related to the period for which you want to generate a file on **Messages** fast tab and click **Generate report** button on the Action pane of the **Messages** fast tab. **Generate report** button is available for Electronic messages in status:

-   **Ready to generate VAT return** – user changes Electronic message status to this value via **Update status** button.

-   **Error VAT return generation** – if during generation of report an error occurs, the Electronic message status will be changed to **Error VAT return generation**.

-   **Error VAT return submission** – if during submission of the report an error occurs, the Electronic message status will be changed to **Error VAT return submission**. Response with error description is attached to the **Action log**.

Select **Preview VAT return** Action on Run processing dialog and click OK. As a result of **Preview VAT return** Action, the file will be generated in the Microsoft Excel format, attached to the Electronic message, no statuses will be changed. To see the file, select the Electronic message and click on **clip** button in the top right corner of the page on the Action pane. An attachment page for the selected message will be opened. Select the last one (**VAT statement.xlsx**) and click on **Open** button on the Action pane. The file will be opened in Excel.

You may regenerate VAT 100 report several times until you generate the report in JSON format and Electronic message status will be changed to **Generated VAT return**.

### Generate VAT return in JSON

MTD for VAT accepts VAT returns in JSON format only. To generate a VAT return in JSON format, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select either **UK MTD VAT TEST** processing for testing purposes or **UK MTD VAT returns** for real-life interoperation with production HMRC web application, select Electronic message record related to the period for which you want to generate a file on **Messages** fast tab and click **Generate report** button on the Action pane of the **Messages** fast tab. **Generate report** button is available for Electronic messages in status:

-   **Ready to generate VAT return** – user changes Electronic message status to this value via **Update status** button.

-   **Error VAT return generation** – if during generation of report an error occurs, the Electronic message status will be changed to **Error VAT return generation**.

-   **Error VAT return submission** – if during submission of the report an error occurs, the Electronic message status will be changed to “**Error VAT return submission**”. Response with error description is attached to the **Action log**.

Select **Generate file for submission** Action on Run processing dialog and click **OK**. As a result of **Generate file for submission** Action, the file is generated in JSON format, attached to the Electronic message, Electronic message status is updated to **Generated VAT return**, Status of linked Electronic message items are updated to **Reported**. To see the file, select the
Electronic message and click on **clip** button in the top right corner of the page on the Action pane. An attachment page for the selected message will be opened. Select the last one (**VAT_return.json**) and click on **Open** button on the Action pane.

If for some reason you need to regenerate VAT return in JSON format before it is submitted to HMRC, update status of related Electronic message to initial using **Update status** button on the Action pane of Messages fast tab to **New VAT return** or **Ready to generate VAT return** depending on if you need to go back to the data collection step or file generation.

### Submitting VAT returns to HMRC

When VAT return in JSON format is generated and ready to be submitted to HMRC, you may initialize its submission to MTD for VAT web application. The last JSON file attached to Electronic message will be used for submission. To avoid any discrepancy, it is recommended to delete unnecessary JSON files from the attachments of Electronic message to be submited to HMRC. To check and clean up unnecessary attachments, select the Electronic message and click on **clip** button in the top right corner of the page on the Action pane. An attachments page for the selected message will be opened.

To start submission, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select either **UK MTD VAT TEST** processing for testing purposes or **UK MTD VAT returns** for real-life interoperation with production HMRC web application, select Electronic message record related to the period for which you want to submit the VAT return on **Messages** fast tab and click **Send report** button on the Action pane of the **Messages** fast tab. **Send report** button is available for Electronic messages in statuses:

-   **Generated VAT return** – Electronic message status is updated to **Generated VAT return** automatically when VAT return in JSON format is successfully generated and attached to the Electronic message.

-   **Error VAT return submission** – if during submission of the report an error occurs, the Electronic message status will be changed to **Error VAT return submission**. Response with error description will be attached to the **Action log**.

**Submit VAT return** Action is predefined on **Run processing** dialog, click **OK**. System will show a dialog with declaration text which is mandatory required by HMRC. It is not recommended to modify or delete this declaration text in setup of **Submit VAT return** Action, to keep compliancy with requirements of HMRC. By **OK** button on this dialog, user submits VAT information and confirms that the information is true and complete. A false declaration can result in prosecution. VAT return can be submitted to HMRC just once for each period. Make sure you want to submit VAT return before you accept the declaration. If you are not sure that VAT return is ready to be submitted, click Cancel. When you click OK, generated VAT return in JSON format related to the selected Electronic message will be submitted to HMRC. If VAT return is submitted successfully to HMRC status of Electronic message will be updated respectively to **Sent VAT return**, response from HMRC will be attached to the Electronic message.

Next **Import response for VAT return** Action will be run automatically by the system. This Action reflects information from the response in **Processing date** Additional field of the Electronic message, update status of Electronic message to **Completed VAT return** and status of Electronic message items to **Submitted**. If for some reason **Import response for VAT return** Action was not run automatically, it can be manually initialized by **Import response** button on the Action pane of Messages fast tab. **Import response** button is available for Electronic messages in status:

-   **Sent VAT return** – Electronic message status is updated to **Sent VAT return** automatically when VAT return in JSON format is successfully submitted to the Electronic message.

All the actions with Electronic message are reflected on **Action log** FastTab.

### Retrieving VAT liabilities and payments from HMRC

HMRC provides possibility to retrieve information about VAT liabilities and VAT payments. For this purposes MTD for VAT web applications support specific endpoints.

**UK MTD VAT returns** processing includes actions which allow user to retrieve information about VAT liabilities and VAT payments from HMRC.

To retrieve information about VAT payments, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select **UK MTD VAT returns** processing, click **New** button on the Action pane of the Messages fast tab. Select **Create VAT payments request** Action on **Run processing** dialog and click **OK** button. An Electronic message in **New payments request** status will be created. Specify **From date** and **To date** for the Electronic message to define the period for which you want to retrieve VAT payments information from HMRC. Click **Send report** button on the Action pane of Messages fast tab. **Request VAT payments** Action is predefined on Run processing dialog, click **OK** button. Request will be sent to HMRC and response with information about VAT payments will be attached as a file in JSON format to the Electronic message. To see the file, select the Electronic message and click on **clip** button in the top right corner of the page on the Action pane. An attachment page for the selected message will be opened. Select the last one and click on **Open** button on the Action pane.

To retrieve information about VAT liabilities, open **Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic messages**, select **UK MTD VAT returns** processing, click **New** button on the Action pane of the Messages fast tab. Select **Create VAT liabilities request** Action on **Run processing** dialog and click **OK** button. An Electronic message in **New liabilities request** status will be created. Specify **From date** and **To date** for the Electronic message to define the period for which you want to retrieve VAT liabilities information from HMRC. Click **Send report** button on the Action pane of Messages fast tab. **Request VAT liabilities** Action is predefined on Run processing dialog, click **OK** button. Request will be sent to HMRC and response with information about VAT liabilities will be attached as a file in JSON format to the Electronic message. To see the file, select the Electronic message and click on **clip** button in the top right corner of the page on the Action pane. An attachment page for the selected message will be opened. Select the last one and click on **Open** button on the Action pane.

## Security privileges

The following security privileges are available for Electronic messages:

| **Security privilege**           | **Access level description**| **Associated with**       |
|----------------------------------|----------------------------|----------------------------|
| **Maintain electronic messages** | The **Maintain electronic messages** privilege gives full access to the electronic messaging functionality. It allows to set up electronic messaging and execute all the processing.| This privilege is included in the **Maintain sales tax transactions** security duty which in turn is included in the **Accountant** security role. |
| **View electronic messages**     | The **View electronic messages** privilege gives read-only access to the electronic messaging functionality. It allows to view both the electronic messaging settings and messages/items but does not allow to set up or execute anything. | This privilege is included in the **Inquire into sales tax transaction status** security duty which in turn is included in the following security roles: Collections manager, Accounts receivable clerk, Accounts receivable manager, Tax accountant, Accountant, Accounting manager, Accounting supervisor, Sales manager, Accounts payable clerk |
| **Operate electronic messages**  | The **Operate electronic messages privilege** gives access only to the "Electronic messages" and "Electronic message items" forms and allows to execute all the processing which are called from these forms.                              | This privilege is included in the **Operate electronic messages** security duty which in turn included in the only security role **Electronic messages operator**  |

## Appendix 1: Electronic messages setup for MTD for VAT

This appendix provides information about setup of Electronic messages functionality to support both **UK MTD VAT TEST** processing for testing purposes and **UK MTD VAT returns** for real-life interoperation with production HMRC web application. Use this part of the documentation to check whether the Electronic messages functionality setup is correct.

This part includes the most important information about setup but not the full data. It is recommended to use package of data entities with predefined setup of the functionality which includes full data necessary for setup of the processing to interoperate with MTD for VAT.

### Electronic message processing

The following processing are defined to support interoperation with MTD for VAT:

| **Name**               | **Description**                                                                     |
|------------------------|-------------------------------------------------------------------------------------|
| **UK MTD VAT returns** | Process of preparation and submission of VAT returns to HMRC.                       |
| **UK MTD VAT TEST**    | Testing process of preparation and submission of VAT returns to the HMRC’s sandbox. |

Security roles should be additionally defined for both processing to restrict access to them (on record level).

### Web applications

The following Web applications are used by “**UK MTD VAT TEST**” and “**UK MTD VAT returns**” processing:

| **Name**                                    | **Description**                                                            |
|---------------------------------------------|----------------------------------------------------------------------------|
| **Dynamics 365 for Finance and Operations** | HMRC Web application for Microsoft Dynamics 365 for Finance and Operations |
| **Sandbox HMRC**                            | HMRC sandbox for Dynamics 365 for Finance and Operations                   |

Parameters of the web applications:

| **Parameter**                                              | **Value**                            |
|------------------------------------------------------------|--------------------------------------|
| **Base URL for “Dynamics 365 for Finance and Operations”** | https://api.service.hmrc.gov.uk      |
| **Base URL for “Sandbox HMRC”**                            | https://test-api.service.hmrc.gov.uk |
| **Authorization URL path**                                 | /oauth/authorize                     |
| **Token URL path**                                         | /oauth/token                         |
| **Redirect URL**                                           | urn:ietf:wg:oauth:2.0:oob            |
| **Authorization format mapping**                           | MTD VAT authorization format (UK)    |
| **Import token model mapping**                             | MTD VAT import token format (UK)     |

Security roles should be additionally defined for both web applications to restrict access to Access token.

### Web service settings

The following Web services are used by **UK MTD VAT TEST** and **UK MTD VAT returns** processing:

| **Name**            | **Description**                                        | **Web application**                     |
|---------------------|--------------------------------------------------------|-----------------------------------------|
| HMRC GET            | HMRC web-service for GET requests.                     | Dynamics 365 for Finance and Operations |
| HMRC POST           | HMRC web-service for POST requests                     | Dynamics 365 for Finance and Operations |
| HMRC sandbox GET    | Sandbox for testing HMRC web-service for GET requests  | Sandbox HMRC                            |
| HMRC sandbox POST   | Sandbox for testing HMRC web-service for POST requests | Sandbox HMRC                            |
| HMRC TEST USER POST | HMRC web-service to POST test user requests            | Sandbox HMRC                            |

Common parameters for all these web services:

| **Parameter**                     | **Value**                               |
|-----------------------------------|-----------------------------------------|
| **Request type - XML**            | NO                                      |
| **Accept**                        | application/vnd.hmrc.1.0+json           |
| **Content type**                  | application/json                        |
| **Request header format mapping** | MTD VAT web request headers format (UK) |

### Additional fields

The following Additional fields are used by **UK MTD VAT returns** and **UK MTD VAT TEST** processing:

| **Status**          | **Description** |
|---------------------|------------------|
| **Due date**        | The due date for this obligation period. The field cannot be modified by user. |
| **HMRC status**     | Obligation status in HMRC: O = Open, F = Fulfilled. The field cannot be modified by user. |
| **periodKey**       | The ID code for the period that this obligation belongs to. The field cannot be modified by user. This field is hidden and cannot be seen by user. |
| **Processing date** | The time that the message was processed in the HMRC. The field cannot be modified by user. |
| **Received date**   | The date when the obligation is received by HMRC. The field cannot be modified by user. |

### Electronic message item types

Electronic messages setup for both “**UK MTD VAT TEST**” processing for testing purposes and **UK MTD VAT returns** for real-life interoperation with production HMRC web application use one Electronic message item type: **VAT return**.

### Electronic message item statuses

The following Electronic message item statuses are used by **UK MTD VAT TEST** and **UK MTD VAT returns** processing:

| **Status**         | **Description**                                                                                       |
|--------------------|-------------------------------------------------------------------------------------------------------|
| **Populated**      | Populated record from Sales tax payments. Record in this status can be deleted.                       |
| **Excluded**       | The record is excluded from report generation. Record in this status can be deleted.                  |
| **To be reported** | This line will be included to the VAT return for submission. Record in this status cannot be deleted. |
| **Reported**       | The record is included into a VAT declaration file. Record in this status cannot be deleted.          |
| **Sent**           | The record is sent in VAT declaration to HMRC. Record in this status cannot be deleted.               |
| **Submitted**      | The record is submitted to HMRC. Record in this status cannot be deleted.                             |

### Electronic message statuses

The following Electronic message statuses are used by **UK MTD VAT TEST** and **UK MTD VAT returns** processing:

| **Status**                             | **Description**   |
|----------------------------------------|--------------------|
| **New obligation request**             | New electronic message to retrieve VAT obligations. Record in this status can be deleted. |
| **Retrieved VAT obligation**           | VAT obligations request is sent. Record in this status can be deleted. |
| **Error VAT obligations retrieving**   | A technical error occurred on VAT obligations retrieving. Record in this status can be deleted.        |
| **Completed VAT obligations request**  | VAT obligations are successfully retrieved. Record in this status can be deleted. |
| **New VAT return**                     | This Sales tax payment is included for further submission. Record in this status can be deleted.       |
| **Ready to generate VAT return**       | The message is ready to generate VAT return. Record in this status can be deleted.  |
| **Generated VAT return**               | VAT return JSON file is generated and attached to the mess. Record in this status *cannot* be deleted. |
| **Error VAT return generation**        | A technical error occurred on generation of GER report. Record in this status can be deleted.|
| **Sent VAT return**                    | VAT return is sent to HMRC in JSON format. Record in this status *cannot* be deleted.  |
| **Error VAT return submission**        | Error occurred while VAT return submission. Record in this status can be deleted.  |
| **Completed VAT return**               | Completed VAT return. Record in this status *cannot* be deleted.  |
| **New liabilities request**            | New electronic message to request liabilities. Record in this status can be deleted. |
| **Error VAT liabilities request**      | A technical error occurred on VAT liabilities request. Record in this status can be deleted.|
| **Completed VAT liabilities request**  | VAT liabilities are successfully retrieved. Record in this status can be deleted. |
| **New payments request**               | New electronic message to request VAT payments information. Record in this status can be deleted.      |
| **Error VAT payments request**         | A technical error occurred on VAT payments request. Record in this status can be deleted. |
| **Completed VAT payments request**     | Completed VAT payments request. Record in this status can be deleted.  |
| **New test user request**              | New electronic message to request test user. Record in this status can be deleted. |
| **Generated test user request**        | Test user JSON file is generated and attached to the message. Record in this status can be deleted.    |
| **Error test user request generation** | A technical error occurred on generation of test user JSON. Record in this status can be deleted.      |
| **Completed test user request**        | Test user request is sent to HMRC in JSON format. Record in this status can be deleted.  |
| **Error test user request**            | Error occurred while test user request submission. Record in this status can be deleted.  |

### Action populate records

**Populate VAT return records** Action is used by **UK MTD VAT TEST** and **UK MTD VAT returns** processing. Data source setup for the Action:

| **Property**               | **Value**                                                   |
|----------------------------|-------------------------------------------------------------|
| **Name**                   | VAT payment                                                 |
| **Message item type**      | VAT return                                                  |
| **Account type**           | All                                                         |
| **Master table name**      | TaxReportVoucher                                            |
| **Document number field**  | Voucher                                                     |
| **Document date field**    | TransDate                                                   |
| **Document account field** | TaxPeriod                                                   |
| **User query**             | Yes. Define the Settlement period by **Edit query** button. |

### Electronic message actions

The following Electronic message actions are used by **UK MTD VAT TEST** and **UK MTD VAT returns** processing:

| **Name**                                  | **Description**   | **Action type**                     |
|-------------------------------------------|------------------|-------------------------------------|
| **Initialize production web application** | Initialize production UK VAT MTD web application. This action works independently from Electron message. <li> Executable class: "InitProdWebAppl"  | Message execution level             |
| **Create VAT obligation request**         | Create a new message to retrieve VAT obligations. <li> From statuses: No <li> To statuses: New obligation request  | Create message                      |
| **Retrieve VAT obligations**              | VAT obligations retrieval request preparation. <li> From statuses: Error VAT obligations retrieving; New obligation request <li> To statuses: Error VAT obligations retrieving; Retrieved VAT obligation <li> Format mapping for URL path: "MTD VAT interoperation (UK)" <li> Web service: "HMRC GET" <li> File name: "response.json.txt"  | Web service   |
| **Test retrieve VAT obligations**         | Retrieving of VAT obligations from HMRC sandbox. <li> From statuses: Error VAT obligations retrieving; New obligation request <li> To statuses: Error VAT obligations retrieving; Retrieved VAT obligation <li> Format mapping for URL path: "MTD VAT interoperation (UK)" <li> Web service: "HMRC sandbox GET" <li> File name: "response.json.txt"  | Web service   |
| **Import VAT obligations**                | Import response from HMRC with VAT obligations. <li> From statuses: Retrieved VAT obligation <li> To statuses: Completed VAT obligations request <li> Model mapping: "MTD VAT obligations importing JSON (UK)"  | Electronic reporting import         |
| **Populate VAT return records**           | Populate sales tax payment records. <li> From statuses: New VAT return <li> To statuses: No <li> Populates records action: "Populate VAT return records"  | Populate records   |
| **Exclude from reporting**                | Mark Sales tax payment record as Excluded from reporting. This action doesn’t change Electronic messages status.   | User processing                     |
| **Update to initial status**              | Update status of Sales tax payment to initial. This action doesn’t change Electronic messages status. | User processing                     |
| **Ready to generate VAT return**          | Update message status to "Ready to generate". <li> From statuses: New VAT return <li> To statuses: Ready to generate VAT return  | Message level user processing       |
| **Update to initial status VAT return**   | Update status of the message to the initial. <li> From statuses: Generated VAT return; Ready to generate VAT return <li> To statuses: New VAT return; Ready to generate VAT return | Message level user processing       |
| **Preview VAT return**                    | Generate preview file in MS Excel format. <li> From statuses: Error VAT return generation; Error VAT return submission; Ready to generate VAT return <li> To statuses: Error VAT return generation; Ready to generate VAT return <li> Format mapping: "VAT Declaration Excel (UK)" <li> File name: "VAT statement.xlsx" | Electronic reporting export message |
| **Generate file for submission**          | Generate VAT return file in JSON format for submission to HMRC. <li> From statuses: Error VAT return generation; Error VAT return submission; Ready to generate VAT return <li> To statuses: Error VAT return generation; Generated VAT return <li> Format mapping: "VAT Declaration JSON (UK)" <li> File name: "VAT_return.json" | Electronic reporting export message |
| **Submit VAT return**                     | The action submits generated VAT return in JSON format to HMRC. <li> From statuses: Error VAT return submission; Generated VAT return <li> To statuses: Error VAT return submission; Sent VAT return <li> Message item type: "VAT return" <li> Format mapping for URL path: "MTD VAT interoperation (UK)" <li> Web service: "HMRC POST" <li> File name: "response.json"  | Web service   |
| **Test submit VAT return**                | Testing submission of VAT return to HMRC sandbox. <li> From statuses: Error VAT return submission; Generated VAT return <li> To statuses: Error VAT return submission; Sent VAT return <li> Message item type: "VAT return" <li> Format mapping for URL path: "MTD VAT interoperation (UK)" <li> Web service: "HMRC sandbox POST" <li> File name: "response.json"  | Web service                         |
| **Import response for VAT return**        | Importing of a response from HMRC about submitted VAT return. <li> From statuses: Sent VAT return <li> To statuses: Completed VAT return <li> Model mapping: "MTD VAT return response importing JSON (UK)"  | Electronic reporting import         |
| **Create VAT liabilities request**        | Create a new message to request VAT liabilities. <li> From statuses: No <li> To statuses: New liabilities request  | Create message   |
| **Request VAT liabilities**               | Request VAT liabilities. <li>From statuses: Error VAT liabilities request; New liabilities request <li> To statuses: Completed VAT liabilities request; Error VAT liabilities request <li> Format mapping: "MTD VAT interoperation (UK)" <li> Web service: "HMRC GET" <li> File name: "response.json.txt"  | Web service                         |
| **Create VAT payments request**           | Create a new message to request VAT payments. <li> From statuses: No <li> To statuses: New payments request   | Create message                      |
| **Request VAT payments**                  | Request VAT payments. <li> From statuses: Error VAT payments request; New payments request <li> To statuses: Completed VAT payments request; Error VAT payments request <li> Format mapping: "MTD VAT interoperation (UK)" <li> Web service: "HMRC GET" <li> File name: "response.json.txt"  | Web service                         |
| **Create test user request**              | Create a message to request test user. <li> From statuses: No <li> To statuses: New test user request | Create message    |
| **Generate test user request**            | Generate JSON file to request test user. <li> From statuses: Error test user request; New test user request <li> To statuses: Error test user request; Generated test user request <li> Format mapping: "MTD VAT interoperation (UK)" <li> File name: "TestUserRequest.json" | Electronic reporting export message |
| **Send test user request**                | Send JSON request for test user. <li> From statuses: Error test user request; Generated test user request <li> To statuses: Completed test user request; Error test user request <li> Format mapping: "MTD VAT interoperation (UK)" <li> Web service: "HMRC TEST USER POST" <li> File name: "TestUserInfo.txt"  | Web service                         |

### Electronic processing actions

Actions, included to the **UK MTD VAT returns** processing:

| **Name**                                | **Run separately** | **Inseparable sequence** |
|-----------------------------------------|--------------------|--------------------------|
| **Create VAT obligation request**       | Yes                |                          |
| **Retrieve VAT obligations**            | Yes                | Obligation               |
| **Import VAT obligations**              | No                 | Obligation               |
| **Populate VAT return records**         | Yes                |                          |
| **Exclude from reporting**              | Yes                |                          |
| **Update to initial status**            | Yes                |                          |
| **Ready to generate VAT return**        | Yes                |                          |
| **Update to initial status VAT return** | Yes                |                          |
| **Preview VAT return**                  | Yes                |                          |
| **Generate file for submission**        | Yes                |                          |
| **Submit VAT return**                   | Yes                | Submission               |
| **Import response for VAT return**      | No                 | Submission               |
| **Create VAT liabilities request**      | Yes                |                          |
| **Request VAT liabilities**             | Yes                |                          |
| **Create VAT payments request**         | Yes                |                          |
| **Request VAT payments**                | Yes                |                          |

Actions, included to the **UK MTD VAT TEST** processing:

| **Name**                                | **Run separately** | **Inseparable sequence** |
|-----------------------------------------|--------------------|--------------------------|
| **Create test user request**            | Yes                |                          |
| **Generate test user request**          | Yes                | TestUser                 |
| **Send test user request**              | No                 | TestUser                 |
| **Create VAT obligation request**       | Yes                |                          |
| **Test retrieve VAT obligations**       | Yes                | Obligation               |
| **Import VAT obligations**              | No                 | Obligation               |
| **Populate VAT return records**         | Yes                |                          |
| **Exclude from reporting**              | Yes                |                          |
| **Update to initial status**            | Yes                |                          |
| **Ready to generate VAT return**        | Yes                |                          |
| **Update to initial status VAT return** | Yes                |                          |
| **Preview VAT return**                  | Yes                |                          |
| **Generate file for submission**        | Yes                |                          |
| **Test submit VAT return**              | Yes                | Submission               |
| **Import response for VAT return**      | No                 | Submission               |
