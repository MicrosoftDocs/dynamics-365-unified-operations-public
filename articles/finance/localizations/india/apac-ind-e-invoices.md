---
title: Electronic invoices in India
description: Learn how to set up and submit electronic invoices and e-Way Bill information in India, including an outline on setting up electronic invoices.
author: ilikond
ms.author: ikondratenko
ms.date: 04/30/2026
ms.topic: how-to
ms.reviewer: johnmichalak
ms.custom:
  - bap-template
  - sfi-image-nochange

---

# Electronic invoices in India

An electronic invoice is a legally accepted digital tax receipt document that your organization registers in the Invoice Registration Portal (IRP). The obligation and applicability of using electronic invoices depend on annual turnover. Legislation determines the minimum applicable threshold. Depending on their turnover, some companies might not be able to access IRP directly and must use additional options, such as integration with Goods and Services Tax (GST) Service Providers (GSPs). The registration of an e-Way Bill in IRP is supported as part of electronic invoice registration.

By using Microsoft Dynamics 365 Finance to generate electronic invoices for your organization, you ensure that they're secure, confidential, authentic, and legally acceptable. You also ensure that required standards are applied to them. As an alternative integration option, you can exchange the applicable invoice details through file export and import. For example, you might use this alternative when you expect that the GSP integration will be used.

## Setting up electronic invoices

### Feature activation

1. Go to **System administration** > **Workspaces** > **Feature management**.
1. In the list, find and select the **(India) Electronic invoice under GST** feature.
1. Select **Enable** to activate the feature. For more information about feature management and the available options, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Import Electronic reporting configurations

To prepare Finance to interoperate with the IRP system, import the latest versions of the following Electronic reporting (ER) configurations. For more information, see [(ER) Import configurations from RCS](../../../fin-ops-core/dev-itpro/analytics/tasks/import-configuration-rcs.md).

- Invoice model
- Invoice model mapping (IN)
- GST Invoice format (IN)
- Electronic messages framework model
- eInvoice model mapping
- eInvoice format (IN)
- eInvoice authentication import format (IN)
- eInvoice data import format (IN)

After you import the configurations, set the **Default for model mapping** option to **Yes** for the **eInvoice model mapping** configuration.

> [!NOTE]
> When you import from the Global Repo or Microsoft Dynamics Lifecycle Services (LCS), you just have to import the format configurations. Related model and model mapping configurations are imported automatically. Ensure that you import the latest configuration versions that are available.

### Set up electronic messaging functionality

Electronic messaging (EM) functionality maintains the different processes that are used in electronic reporting and the transmission of different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md). The most important step in the setup of EM functionality for IRP integration is to import the Indian IRP integration setup V5.zip data package. After you successfully import the setup data, almost all the required setup is automatically created. The only remaining setup that you need to do is select parameters for executable classes and set up number sequences for EM. Both those tasks are described later in this topic.

> [!NOTE]
> Apply only the latest data package version that is available in LCS.

#### Import a package of data entities that include a predefined EM setup

The process of setting up the EM functionality to interoperate with the IRP system has multiple steps. Because the names of some predefined entities are used in the ER configurations, use the set of predefined values that are included in a package of data entities for the related tables. Import the ER configurations before you import the data entities.

1. In LCS, go to the Shared asset library, and select **Data package** as the asset type.
1. In the list of data package files, find and download **Indian IRP integration setup V5.zip**.
1. After the file is downloaded, open Finance, and select the company that you want to interoperate with the IRP system.
1. Go to **Workspaces** \> **Data management**.
1. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and select **Refresh entity list**. Wait for confirmation that the refresh is complete. For more information about how to refresh the entity list, see [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
1. Validate that the source data and target data are correctly mapped. For more information, see [Validate that the source data and target data are mapped correctly](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
1. Before you use the data entities to import the data from the package, follow these steps for each data entity in the package:

    1. Sync the mapping of the source data and target data. In the package list, select a data entity, and then, on the Action Pane, select **Modify target mapping**.
    1. Above the grid for the package, select **Generate mapping** to create a mapping from scratch, and then save the mapping.

    For more information about data management, see [Data management overview](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

1. Import data from the Indian IRP integration setup V5.zip file into the selected company. In the **Data management** workspace, select **Import**, specify a group name, select **Add file**, and then, in the drop-down dialog box, set the **Source data format** field to **Package**.
1. Select **Upload and add**, select the **Indian IRP integration setup V5.zip** file on your computer, and upload it.
1. After the data entities are uploaded, on the Action Pane, select **Import**.

You receive a notification in the Action center, or you can manually refresh the page to view the progress of the data import. When the import is completed, the **Execution summary** page shows the results.

After the data entities are imported, the following types of electronic message processing are available. This processing contains most of the setup that is required in your legal entity.

- **OnlineInvoicing** – Indian online invoicing. This processing supports interoperation with the IRP system to submit information about sales invoices, free text invoices, project customer invoices, and transfer orders. IRP responses are parsed to obtain and save the Invoice Registration Number (IRN) and signed QR code.
- **CancelInvoice** – Cancel Indian online invoicing. This processing supports interoperation with the IRP system to cancel previously registered customer invoices.
- **RegisterEWB** – Register e-Way Bill. This processing supports interoperation with the system to submit information that includes e-Way Bill details. As a result of this processing, the e-Way Bill status and other details, such as the e-Way Bill number and date, are updated.
- **CancelEWB** – Cancel e-Way Bill. This processing supports interoperation with the system to cancel previously registered e-Way Bills.

To review the imported processing, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.

#### Set up the integration internet addresses

1. Go to **Tax** \> **Setup** \> **Parameters** \> **Electronic messages** \> **Web service settings**.
1. Define the internet addresses for web services. The addresses that are shown here are testing addresses that are applicable to the sandbox environment.

    - **Authentication:** `https://einv-apisandbox.nic.in/eivital/v1.04/auth`
    - **Generate IRN:** `https://einv-apisandbox.nic.in/eicore/v1.03/Invoice`
    - **Cancel IRN:** `https://einv-apisandbox.nic.in/eicore/v1.03/Invoice/Cancel`
    - **Generate WEB:** `https://einv-apisandbox.nic.in/eiewb/v1.03/ewaybill`
    - **Cancel EWB:** `https://einv-apisandbox.nic.in/ewaybillapi/v1.03/ewayapi`

    > [!NOTE]
    > The National Informatics Centre (NIC) can change internet addresses. Check for actual internet addresses on the official website of the e-Invoice System or other appropriate sources. The official documentation also has information about the available production internet addresses that you should set up.

1. In the **Request** parameters, specify the following set of values for all the preceding web services.

    | Parameter | Value |
    |-----------|-------|
    | Successful response code | 200 |
    | Request method | POST |
    | Content type | Application/json |
    | Request headers format mapping | eInvoice format (IN) |

IRP might limit the number of Internet Protocol (IP) addresses that can access it. To satisfy the requirements, select the **Use proxy server** checkbox, and set up proxy server parameters, such as the proxy server IP address, proxy server port number, and proxy authentication (stored in Azure Key Vault).

#### Set up additional fields

Additional fields are associated with EM items and required for their processing. Include these fields in the electronic message processing of the **OnlineInvoicing** (Indian online invoicing) type that interoperates with the IRP system. Import these fields into the system by using a package of data entities. The system automatically sets values for additional fields when actions run. IRP integration uses only one additional field.

If you didn't import additional fields from the data package, follow these steps:

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**.
1. Select **New**, and enter the **AppKey** and a **Unique ID** that identifies the unique user session.

#### Set up executable class parameters

To finalize the electronic message setup after you import the data package, follow these steps:

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Executable class setting**.
1. Select **Generate EM**.
1. On the Action Pane, select **Parameters**.
1. In the dialog box that appears, set the following values for the parameters of the executable class:

    - **Format mapping:** GST Invoice format (IN)
    - **Message status in case of success:** Generated
    - **Message item status in case of technical error:** Created

### Set up number sequences for electronic messages

To work with the electronic message functionality, you must define related number sequences.

1. Go to **Tax** > **Setup** > **Parameters** > **General ledger parameters**.
1. On the **Number sequences** tab, set up two number sequences:

    - Message
    - Message item

### Set up batch settings for automated processing of interoperation with the IRP system

1. Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing**.
1. Select the processing, such as **OnlineInvoicing** or **CancelInvoice**.
1. On the **Batch** FastTab, select **Create batch**, and then define the required parameters.

### Set up security roles for electronic message processing

Different groups of users might require access to the **OnlineInvoicing** and **CancelInvoice** processing. You can limit access based on security groups that you define in the system.

To limit access to the **OnlineInvoicing** and **CancelInvoice** processing, follow these steps:

1. Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing**.
1. Select the **OnlineInvoicing** or **CancelInvoice** processing, and then add the security groups that must work with the processing. If you don't define a security group for the processing, only a system administrator can see the processing on the **Electronic messages** page.

### Set up certificates and secrets for the IRP system

To interoperate with the IRP system, you must use a security certificate that the operator provides. You must also use all the other secrets that the IRP system provides during the GST Identification Number (GSTIN) registration process. You have two options for storing this sensitive data:

- Key Vault storage
- Local storage (This option isn't recommended for production environments.)

Use Key Vault storage. For more information about how to set up Key Vault, see [Set up the Azure Key Vault Client](../global/setting-up-azure-key-vault-client.md).

> [!NOTE]
> If you follow the recommended setup and use Key Vault, you must upload and define all the secrets you use (including **User name**, **User password**, **Client ID**, **Client secret**, and **Certificate**) in the customer's Key Vault storage before you define the Key Vault parameters.

To enable the use of Key Vault and advanced certificate storage, follow these steps:

1. Go to **System administration** > **Setup** > **System parameters**.
1. Set the **Use advanced certificate store** option to **No** to store sensitive data locally. Set it to **Yes** to use Key Vault storage.
1. If you set the **Use advanced certificate store** option to **Yes**, follow these steps:

    1. Go to **System administration** > **Setup** > **Key Vault parameters** to define the Key Vault parameters.
    1. Create a secret that has a reference to the custom Key Vault storage for each of five required secrets (**User name**, **User password**, **Client ID**, **Client secret**, and **Certificate**).

> [!NOTE]
> Store the .CER certificate in Key Vault as a secret, not as a certificate. Open your .CER file in any text editor, and copy its entire content to a secret value in Key Vault.

### Set up electronic invoice parameters

Use the **Electronic invoice parameters** page to enter the information needed to submit invoices to IRP. You can also provide additional parameter information that controls validations when posting invoices. Here's a list of the available options:

- **Validate before posting** – Enable extra validation against all mandatory information that the electronic invoice must include when posting.
- **Validation format** – The ER format to use for validation against all mandatory elements in the electronic invoice. You can set this option only when you enable the **Validate before posting** option.
- **GSTIN** – Your GSTIN. Use this value for IRP integration.
- **User name** – A reference to the Key Vault secret for your user name that NIC provides. Use this value for IRP integration.
- **User password** – A reference to Key Vault secret for your user password that NIC provides. Use this value for IRP integration.
- **Client ID** – A reference to Key Vault secret for your user client ID that NIC provides. Use this value for IRP integration.
- **Client secret** – A reference to Key Vault secret for your client secret that NIC provides. Use this value for IRP integration.
- **Certificate** – A reference to Key Vault secret for your certificate that NIC provides. Use this value for IRP integration.

### Set up units of measure

For each unit of measure that you use in electronic invoices, follow these steps to match allowed external codes.

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit, such as **ea**, and then select **External codes**.
1. Enter a code for the unit, such as **EInv_IN**, and then enter the external code definition.

    > [!NOTE]
    > Use this code across all units of measure to identify the master data set of units of measure codes that electronic invoicing accepts.

1. Select the external code that you created for the electronic invoicing unit. In the **Value** field, enter a value, such as **NOS**. The external codes are used as international trade units of measure codes that the technical specification recommends.

### Set up HSN codes and products

For more information about how to set up Harmonized System of Nomenclature (HSN) codes, see [Define HSN codes and Service Accounting Codes](apac-ind-GST-hsn-service-accounting-codes.md). The following procedures explain how to set up an HSN code and assign it to a product.

#### Define HSN codes

1. Go to **Tax** > **Setup** > **Sales tax** > **India** > **HSN code**.
1. Create a record.
1. In the **Chapter** field, enter a value.
1. In the **Heading** field, enter a value.
1. In the **Subheading** field, enter a value.
1. In the **Country/region extension** field, enter a value.
1. In the **Statistical suffix** field, enter a value.
1. Save the record, and verify that the **HSN code** field is updated.
1. In the **Description** field, enter a value.
1. Select **Close**.

#### Assign HSN codes to products

1. Go to **Product information management** > **Products** > **Released products**.
1. Select a product, and then select **Edit**.
1. If the product type is **Item**, on the **General** FastTab, select a value in the **HSN code** field.

### Set up tax registration numbers

For more information about how to set up GSTIN master data, see [Create a GSTIN master](apac-ind-GST-create-gstin-master.md). The following steps show only the simplified process of setting up registration numbers that you can use in electronic invoicing.

1. Go to **Tax** > **Setup** > **Sales Tax** > **Enterprise tax registration**.
1. If you don't have any registration numbers of the **GSTIN** type, create a new record. Otherwise, go to step 6.
1. In the **Tax type** field, select **GST**.
1. In the **Registration number type** field, select **Company**.
1. Enter the registration number, and then save the data.
1. On the **eInvoice parameters** FastTab, set the parameters that are used for credentials: **User name**, **User password**, **Client ID**, **Client Secret**, and **Certificate**. Set up these parameters when you expect to use different GSTIN registrations for sending electronic invoices. When you expect to use only a single registration in the company, specify it only on the **Electronic invoices parameters (India)** page.

    > [!NOTE]
    > The **eInvoice parameters** FastTab on the **Enterprise tax registration numbers** page is available only when all the following conditions are met: The **Tax type** field is set to **GST**, the **Type** field is set to **GSTIN**, the **Registration number type** field is set to **Company**, and the user has full access rights to the menu item that opens the **Electronic invoices parameters (India)** page.
    >
    > When you send an electronic invoice for registration in IRP, the system first tries to obtain parameter settings for the seller GSTIN of the electronic invoice from the **Enterprise tax registration numbers** page. If the system doesn't find the settings there, it uses the parameter settings from the **Electronic invoices parameters (India)** page. The global parameters are used only when the GSTIN in those settings is the same as the seller GSTIN of the electronic invoice that is being sent. If the global settings have a different GSTIN, no credentials are found that can be used for communication with IRP, and an error occurs.

1. Create a new record.
1. In the **Tax type** field, select **GST**.
1. In the **Registration number type** field, select **Customer**.
1. Enter the registration number, and then save the data.

### Set up your legal entity

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the **Addresses** tab, select **Add** to create a new address or **Edit** to update an existing primary address.
1. Set or update the **ZIP**, **Street**, **City**, **District**, **State**, and **County** fields.

    > [!NOTE]
    > Assign state codes to states on the **State/province** tab of the **Address setup** page (**Organization administration** > **Setup** > **Addresses** > **Address setup**).

1. Close the **Edit addresses** page.
1. Select **Registration IDs**, and then select your primary address.
1. On the **Manage addresses** page, on the **Tax information** FastTab, select **Add**.
1. Enter a name and a description.
1. In the **GSTIN/GDI/UID** field, select the company registration number that you created.
1. Close the **Manage addresses** page.
1. On the **Legal entities** page, on the **Contact information** FastTab, set the **Primary phone** and **Primary email** fields.

### Set up your customers

1. Go to **Accounts receivable** > **Customers** > **All customers**, and open a customer record.
1. Enter or edit the customer information as required for electronic invoicing.

### Set up tax information

1. On the **Customers** page, on the **Addresses** tab, select **Add** to create a new primary address or **Edit** to update an existing primary address.
1. Set or update the **ZIP**, **Street**, **City**, **District**, **State**, and **County** fields.

    > [!NOTE]
    > Assign state codes to states on the **State/province** tab of the **Address setup** page (**Organization administration** > **Setup** > **Addresses** > **Address setup**).

1. Close the **Edit addresses** page.
1. Select **Registration IDs**, and then select your primary address.
1. On the **Manage addresses** page, on the **Tax information** FastTab, select **Add**.
1. Enter a name and a description.
1. In the **GSTIN/GDI/UID** field, select the customer registration number that you created.
1. Close the **Manage addresses** page.

### Set up contact information

1. On the **Customers** page, select **Contacts** to edit an existing contact or create a new contact.
1. On the **Sales demographics** tab, select an existing primary contact.
1. Expand the **Contact information** FastTab to add the primary phone and primary email.

    > [!NOTE]
    > Customer contact details might not be required for some versions of Finance.

### Enable a customer for electronic invoicing

- On the **Customers** page, on the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes**. The system now marks invoices that are posted for the customer account as ready for electronic invoice processing.

### Set up e-Way Bill types to send electronically

1. On **e-way Bill types**, create a new record or select an existing record.
1. Set the **Can be sent electronically** option to **Yes** to mark the e-way Bill type as applicable for electronic invoice and e-Way Bill integration.

## Working with electronic invoices

EM functionality runs actions that are included in processing groups, based on the status of messages and message items. A periodic batch job can perform the processing, or you can activate it manually.

### Register electronic invoices

When you post an invoice from a sales order, free text invoice, or project invoice proposal for a customer that you enabled for electronic invoices, run EM processing to create an electronic invoice in JavaScript Object Notation (JSON) format and register it in IRP.

1. Go to **Tax** > **Inquiries and reports** > **Electronic messages**.
1. Select the **OnlineInvoicing** processing, and then select **Run processing** to create electronic invoices for all relevant posted documents and send them to IRP.

    > [!NOTE]
    > To send all relevant newly posted documents to IRP at a predefined time interval, select **Run in the background** to set up batch processing.

After the operation completes, you can view information about the number of processed documents in the action log.

Successful completion of invoice registration updates information on the **E-invoice status** page, which you can access from the **Sales invoice journal** or **Project invoice journal** page. The invoice's **Sent electronically** flag is also updated.

You can print the IRN and QR code that you receive on **Tax invoice** reports that are available from the **Sales invoice journal** and **Project invoice journal** pages.

The **Created** electronic invoice status is automatically created. Additionally, the **Create e-invoice status** function (**Accounts receivable** > **Periodic task** > **Create e-invoice status**) enables electronic invoice processing to be reinitiated. It even enables previously posted invoices to be sent. This option doesn't affect electronic invoices that are already sent.

### Cancel electronic invoices

When you register an invoice in IRP, select it for cancellation and run EM processing to cancel it in the IRP system.

1. On the **Sales invoice journal** or **Project invoice journal** page, select the previously registered invoice that you want to cancel.
1. Select **E-Invoice** to open the **e-Invoice status** page.
1. Select **Cancel** to mark the invoice for cancellation.

    > [!NOTE]
    > The status of the invoice is updated to **Cancel**.

1. Go to **Tax** > **Inquiries and reports** > **Electronic messages**.
1. Select the **CancelInvoice** processing, and then select **Run processing** to cancel all electronic invoices that you marked for cancellation.

    > [!NOTE]
    > To send all relevant newly posted documents to IRP at a predefined time interval, select **Run in the background** to set up batch processing.

After the operation completes, you can view information about the number of processed documents in the action log.

If you enable the **Transfer order cancellation** feature in the **Feature management** workspace, you can also cancel a shipment when you cancel a transfer order.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Transfer order history**, and select the shipment that you want to cancel.
1. Select **Cancel**, and confirm the shipment cancellation.

### Inquiry about electronic invoices

To quickly determine which invoices are registered, open the **Sales invoice journal** or **Project invoice journal** page, and then review the status in the **Sent electronically** column.

For detailed information about the status of electronic invoices, open the **e-Invoice** page from the **Sales invoice journal** or **Project invoice journal** page. Review the status information on the **Overview** tab. Electronic invoices can have the following statuses:

- **Created** – The invoice is posted and ready to send to IRP. Run the **OnlineInvoicing** processing to start the registration process.
- **Sent** – The invoice is successfully registered in IRP.
- **Cancel** – The invoice is selected for cancellation. Run the **CancelInvoice** processing to start the cancellation process.
- **Canceled** – The invoice is successfully canceled at IRP.

After successful registration of the invoice on the **Overview** tab, the **Acknowledgement number** and **Acknowledgement date** values appear. On the **Details** tab, you can review the received IRN, signed QR code, and signed invoice.

## e-Way Bill information

### Register an e-Way Bill

When you post an invoice for a customer account that is enabled for electronic invoices, you can add the e-Way Bill details from the **Invoice journal** page. The system sends those details to the service together with the electronic invoice. You can open the e-Way Bill from the **Invoice journal** page by selecting **Invoice** \> **e-Way Bill**.

On the **e-Way Bill** page, provide the following details:

- Tax type
- Direction
- e-Way Bill type
- Mode of transport
- Vehicle Number
- Document Number
- Document date
- Distance
- Transporter ID
- Transporter name
- Vehicle type

After you enter the e-Way Bill for the invoice, its status appears as **Created** on the **E-Invoice** page.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
1. Select **RegisterEWB**, and then select **Run processing**. The system processes the e-Way Bill and sends it to the service. The status of the e-Way Bill updates to **Sent**, and the **E-way bill No** and **E-way bill date** fields update.

### Cancel the e-Way Bill

For e-Way Bills that you already sent, select **Cancel e-Way Bill** and then cancel the electronic invoice. The status updates to **Canceled**.

To review the imported processing, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.

## Alternative integration options (GSP file integration)

This feature enables you to exchange the list of electronic invoices in India by using file integration.

### Prerequisites

- The primary address of the legal entity must be in India.
- Import the following versions or later of ER configurations:

    - GST Export Invoices format (IN).version.104.5
    - GST Import Invoices format (IN).version.104.7

    To import the configurations, go to **Accounts receivable** > **Setup** > **Electronic invoice parameters**. On the **File integration** tab, select the **Export format** and **Import format** configurations.

### File integration for the e-invoice information

To review all electronic invoices that you can export by using file integration, go to **Accounts receivable** > **Invoices** > **e-Invoice**.

To export electronic invoices to a file, select **File Integration/Export to file**. By default, the system generates the file and saves it to your **Download** folder. However, you can set up additional options by using ER destinations. For more information, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

You can also import the file. When you import the file, the system updates the electronic invoice details and status based on the imported file. To import a file, select **File Integration/Import from file**. By default, you can manually select a file in the import dialog box. For information about additional options for setting up the ER source, see [Configure data import from SharePoint](../../../fin-ops-core/dev-itpro/analytics/er-configure-data-import-sharepoint.md).

## FAQ

### Can I clear the selection of a successfully registered invoice that I selected for cancellation?

You can't clear the selection of an invoice after you select it for cancellation on the **e-Invoice status** page. IRP doesn't allow an invoice to be sent again after it's canceled. The only option is to create and post a new invoice.

### Can I specify additional criteria for selecting invoices for electronic processing, such as registration or cancellation?

You can review and modify the queries used for invoice selection by going to **Tax** > **Setup** > **Electronic messages** > **Populate record actions**. Select **Edit query** to open the **System query** page, where you can add or modify query criteria.

### Where can I find detailed information about what went wrong for an invoice that wasn't successfully registered?

You can review the action log by going to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**. The action that failed includes a response code and a response description.

### What formats does India support for electronic invoices?

You can export electronic invoices in a JSON format that contains all the required fields defined in the technical specification. To use a different format or add extra information to the electronic invoice message, use ER to modify the format that Microsoft provides or create a new one. For more information, see [Electronic reporting (ER) overview](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md). After you configure the custom format, select it instead of **GST Invoice format (IN)** in the executable class parameters.

### What integrations does India support for electronic invoice registration?

In a default setup of electronic messages that you import through a data package, you can submit electronic invoices that are generated in JSON format directly to IRP. Because the supported integration option uses electronic messages, you can use it to change configurations and validate the ability to integrate with any GSP of your choice. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

### IRP supports several integration options. Which option should I use to get credentials? Can I use the credentials in a production environment?

The supported integration option is available for companies that can access IRP through direct application programming interface (API) access. Currently, this access is granted only to companies that have annual turnover that exceeds the defined threshold or that are registered in the e-Way Bill portal. Other companies must connect through a GSP. For more information about the process for onboarding and receiving the credentials that are applicable to sandbox and production environments, visit the e-Invoice API developer's portal.

## Known issues

The following table provides a list of known issues and workaround information for each issue.

| Issue | Solution |
|-------|----------|
| The project invoice can't be posted. If you select the **Validate before posting** checkbox, the following validation error occurs when you try to post a project invoice proposal: "Document Details: Document number cannot be empty." | <p>Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup**. Select the company, and then select **Parameters**. Set the **Tax document posting mode** field to **Synchronous**.</p><p></p> |
| When you generate an electronic invoice in EM, the **StateCode_IN** field can't be found in the **LogisticsAddressState** table. | Turn off the **Minimize memory consumption by storing datasets at ER reports runtime** feature in the **Feature management** workspace. |
| An error occurs while the token request is being generated. | <p>Make sure that no setup is missing for the ER configurations, electronic invoice parameters, or Key Vault. If the error contains the following text, the certificate is incorrectly set up: "Function DigitalCertificateManager::findCertificateBySubject has been incorrectly called." Download a certificate from IRP again, and add it to the key vault as a secret by copying the entire file contents. The following illustration shows an example of a correct setup.</p>:::image type="content" source="../media/apac-ind-einvoicesetup.png" alt-text="Screenshot of the item setup page."::: |
| An error occurs while the token response is being imported. The error message indicates that the client ID, client secret, user name, or password isn't valid. | Check Key Vault. The client ID or secret is incorrect. |
| There is a duplicate IRN. | This issue shouldn't occur in a production environment. It occurs when you use the same credentials in different environments, and the same invoice numbers are sent to IRP. Go to **Tax** > **Setup** > **GST reference number sequence group**, and set up a unique number sequence for the Accounts receivable GST invoice. |
| <p>Other types of errors occur. Here are some examples:</p><ul><li>"The field HSN Code must be a string with a minimum length of 6 and a maximum length of 8."</li><li>"Recipient PIN code should be 999999 for Direct Export."</li></ul> | <p>Read the error code, and correct the master data.</p><p>If something is wrong in the customer data or company data, correct it. After you correct the data, select an electronic message that has an error, delete the corresponding EM item, and then run the processing again. A new electronic message is created that has corrected JSON.</p><p>If something is wrong in the transaction data (either the invoice lines or tax transactions), you can't easily correct it. Revert the invoice, fix the master data, and then try to create a new invoice.</p> |
