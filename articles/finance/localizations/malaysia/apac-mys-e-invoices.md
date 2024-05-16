---
title: Get started with electronic invoicing for Malaysia (preview)
description: This article explains how to get started with electronic invoicing for Malaysia in Microsoft Dynamics 365 Finance (preview).
author: ilikond
ms.date: 05/13/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Malaysia
ms.author: ikondratenko
ms.search.validFrom: 2024-05-09
ms.dyn365.ops.version: AX 10.0.39
---

# Get started with electronic invoicing for Malaysia (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides information to help you get started with electronic invoicing for Malaysia. It guides you through the configuration steps that are country/region-dependent in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

After you configure electronic invoicing, you can generate, digitally sign, and submit the XML files of electronic invoices according to the [regulatory requirements in Malaysia](https://www.hasil.gov.my/en/e-invoice/).

> [!NOTE]
> This functionality is currently in **preview**. During this stage, only the *generation* of electronic invoice XML files is implemented. Further steps, such as digital signing and submission to the authorities, will be added when the functionality becomes **generally available**.

![Diagram of the electronic invoicing workflow in Malaysia.](apac-mys-e-invoice-workflow.jpg)

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an invoicing service that's applicable only to cloud deployments of Finance or Supply Chain Management.

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- The primary address of the legal entity must be in Malaysia.
- Your company must be a registered taxpayer in Malaysia and must have the following registration numbers: Tax Identification Number (TIN), business registration number (BRN), and Sales and Service Tax (SST) number.
- *(Not required for preview)* Obtain **Client ID** and **Client secret** values in the [Inland Revenue Board of Malaysia (IRBN)](https://www.hasil.gov.my/) (Lembaga Hasil Dalam Negeri Malaysia \[LHDN\]). These values serve as credentials that are used to establish a secure connection to the IRBN portal.
- *(Not required for preview)* Obtain a digital signature certificate from one of the [Malaysian certification authorities](https://www.mcmc.gov.my/en/sectors/digital-signature/list-of-licensees). This certificate is used for digital signing of generated electronic invoices.
- Become familiar with electronic invoicing as it's described in [Electronic invoicing overview](../global/gs-e-invoicing-service-overview.md).
- Do the common part of electronic invoicing service configuration as described in [Set up electronic invoicing](../global/gs-e-invoicing-set-up-overview.md).

## Electronic invoicing feature configuration

Some of the parameters from the **(Preview) Malaysian electronic invoicing (MY)** electronic invoicing feature are published with default values. Before you deploy this feature to the service, review the default values, and update them as required, so that they better reflect your business operations.

1. Import the latest version of the **(Preview) Malaysian electronic invoicing (MY)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it. For more information, see [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Configure electronic document parameters

1. Make sure that the country/region-specific Electronic reporting (ER) configurations for the document context and electronic document model mapping that are required for Malaysia are imported. For more information, see [Set up electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

    > [!NOTE]
    > After you import the **(Preview) Malaysian electronic invoicing (MY)** electronic invoicing feature, electronic documents are configured by default. Follow the remaining steps of this procedure if you must make changes.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic document** tab, add records for the **Customer Invoice journal**, **Vendor Invoice journal**, and **Project invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

    ![Screenshot of the setup on the Electronic document tab of the Electronic document parameters page.](apac-mys-e-invoice-documents.jpg)

    > [!NOTE]
    > The setup that's described here lets you issue electronic invoices for the following **posted** source documents:
    >
    > - Customer invoices that are based on sales orders
    > - Free text invoices
    > - Project invoices
    > - Self invoices that are based on vendor invoices from foreign vendors
    > - Credit notes and debit notes for all the previously described invoice types

1. On the **Features** tab, select and enable the **Malaysian electronic invoice** feature.
1. Save your changes, and close the page.

## <a id="NRIC"></a>Configure registration numbers

> [!NOTE]
> When the output files of electronic invoices are generated, registration numbers of the **Enterprise ID (COID)** category are used as BRNs. If the **Enterprise ID (COID)** registration category already exists and has been assigned to a registration type, skip this procedure.

1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **MYS - Malaysia**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

## <a id="SST"></a>Configure SST numbers

To configure an SST number, follow the instructions in [SST registration number](apac-mys-gst.md#gstsst-registration-number).

## Configure electronic document property types

Follow these steps to configure the electronic document property type that's required to define the taxpayer activity code.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**.
1. Select **New** to create an electronic document property type.
1. In the **Type** field, enter **ActivityCode**. You must enter the value exactly as it appears here.
1. On the Action Pane, select **Applicability**.
1. In the **Table name** field, select **CompanyInfo**.
1. Save and close the **Electronic document property type applicability setup** page.
1. Select **New** to create another electronic document property type.
1. In the **Type** field, enter **ActivityDescription**. You must enter the value exactly as it appears here.
1. On the Action Pane, select **Applicability**.
1. In the **Table name** field, select **CompanyInfo**.
1. Save and close the **Electronic document property type applicability setup** page.
1. Save and close the **Electronic document property types** page.

![Screenshot that shows electronic document properties configuration.](apac-mys-e-invoice-properties.jpg)

## Configure legal entity data

### Enter the address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the selected legal entity.

### Enter the registration numbers

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity, and then, on the **Tax registration** FastTab, in the **Tax registration number** field, enter the company's TIN.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the [BRN](#NRIC) registration type that you created earlier.
1. In the **Registration number** field, enter a valid BRN registration number for the selected legal entity. 
1. Select **Add** to create another registration ID.
1. In the **Registration type** field, select the [SST](#SST) registration type that you created earlier.
1. In the **Registration number** field, enter a valid SST registration number for the selected legal entity.

### Enter a business activity code and description

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity, and then, on the Action Pane, select **Electronic document properties**.
1. Select the line where the **Type** field is set to **ActivityCode**.
1. In the **Value** field, enter the taxpayer business activity code.
1. Select the line where the **Type** field is set to **ActivityDescription**.
1. In the **Value** field, enter the taxpayer business activity description.

## Configure customer data

### Enter the address

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.

### Enter the contact person

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer.
1. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered the buyer's contact.

    > [!NOTE]
    > All available contact persons must already be defined for the selected customer. Make sure that the selected contact person has a valid email address. This email address will be used to send generated electronic invoices to the customer.

### Enter the registration numbers

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer, and then, on the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid TIN for the customer.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the [BRN](#NRIC) registration type that you created earlier.
1. In the **Registration number** field, enter a valid BRN registration number for the selected customer. 
1. Select **Add** to create another registration ID.
1. In the **Registration type** field, select the [SST](#SST) registration type that you created earlier.
1. In the **Registration number** field, enter a valid SST registration number for the selected customer.

## Configure funding sources

If business processes assume that **project invoices** are issued, follow these additional configuration steps.

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
1. Create a new project contract, or select an existing project contract.
1. On the **Funding sources** FastTab, create or select a funding source of the **Customer** type, and then select **Details**.
1. On the **Funding source details** page, on the **Other** FastTab, in the **Contact** section, in the **Contact ID** field, select a valid contact person.

    > [!NOTE]
    > All available contact persons must already be defined for the selected customer. Make sure that the selected contact person has a valid email address. This email address will be used to send generated electronic invoices to the customer.

## Configure sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code that you selected in step 2.
1. In the **Value** section, in the **Value** field, enter an external code to use for the selected sales tax code, according to the [required codification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/).
1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**.
1. Define exempt codes used in the event of non-taxable, zero-rated, or exempted operations.

## Configure the application-specific parameters

Make sure that the following ER format configurations are imported:

- Sales invoice (MY)
- Project invoice (MY)
- Self invoice (MY)

Follow these steps to complete the configuration.

1. In the **Globalization Studio** workspace, select the **Electronic reporting** tile, and then select the **Reporting configurations** tile.
1. On the **Configurations** page, select the **Sales invoice (MY)** format configuration.
1. On the **Configurations** menu, in the **Application specific parameters** section, selected **Setup**.
1. In the **Lookups** section, make sure that the **$TaxTypes** lookup is selected.
1. In the **Conditions** section, select **Add** to add a condition.
1. In the **Name** column for the new condition, select the sales tax code that's defined in the application. Then, in the **Lookup result** column, select a tax type code according to the [official list of tax type codes](https://sdk.myinvois.hasil.gov.my/codes/tax-types/).
1. Add specific conditions for each sales tax code that's defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **\*Blank\*** or **\*Not blank\*** placeholder value instead of a specific sales tax code.

1. In the **State** field, select **Completed**. Then select **Save**.
1. Repeat steps 2 through 8 for the **Project invoice (MY)** and **Self invoice (MY)** format configurations, as required.

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. For more information about how to generate electronic invoices, see [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

You can inquire about the results of a submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and selecting the required document type.
