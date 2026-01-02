---
title: Work with NFS-e Service Invoices
description: Learn about the steps to set up and generate Brazilian NFS-e Service Invoices
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.date: 01/02/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 01/02/2026
ms.custom: 
  - bap-template
---

# NFS-e Service Invoices

[!include [banner](../../includes/banner.md)]

This article describes how to set up and work with Brazilian NFS-e Service Invoices.

The functionality uses Electronic Reporting. To set up and configure the feature, follow these steps:

## Prerequisites for Generating NFS-e XML in Dynamics 365 Finance

> [!IMPORTANT]
> Submission and digital signature of NFS-e (both for São Paulo and Federal) is out of scope. A customization or third-party solution will be required to submit and sign the NFS-e XML. 

This article outlines the key setup steps required before you can generate an **NFS-e** (Nota Fiscal de Serviço Eletrônica - **both for São Paulo and Federal**) XML in Microsoft Dynamics 365 Finance. Each section 
below covers a specific prerequisite, with navigation paths and field names to help you configure the system correctly. These steps apply to both end users and IT admins responsible for the Brazilian service invoice process.

First of all, the Brazil reformed tax feature must be enabled according to [Set up Brazil reformed tax](brazil-reform-setup.md).

### Environment Identification (Testing vs. Production)

**Purpose**: Ensure the system knows whether to issue NFS-e in test mode or live mode.
- **Navigation**: Go to **Organization administration > Organizations > Fiscal establishments > Fiscal establishments**.
- **Field**: On the **Fiscal establishment** form, find the field **Environment** under the **NFS-e** FastTab.
- **Action**: Set **NFS-e Environment** to **Testing** (homologation) for test scenarios, or **Production** for real invoices.

### NBS and Operation Indicator Codes

**Purpose**: Provide the classification codes needed for NFS-e.
- **NBS Codes**: Nomenclatura Brasileira de Serviços codes classify the type of service provided (similar to a service item code). Ensure all required NBS codes are available in the system.
- **Operation Indicator Codes**: These codes indicate the nature of the service operation (e.g., within city, outside city, or abroad). Make sure the valid operation indicator values are present.

**Navigation to Code Tables**: Open the forms to maintain these codes:
- **NBS Codes: Inventory management > Setup > Fiscal information > NBS codes**. Here you can **Add** or verify entries (each with a code and description).
- **Operation Indicator Codes: Inventory management > Setup > Fiscal information > Operation indicator codes**. Ensure the list of operation indicators and descriptions is up to date.

By populating these lookup tables, users will be able to select the correct NBS and operation indicator values on transactions.

### NBS and Operation Indicator codes

Once the code tables are set up, use those codes in the following areas of Dynamics 365 Finance:

- **Released Products**: Go to **Product information management > Products > Released products**. Open each service product and on its details (under the **Fiscal information** FastTab), set the **NBS Code** field to the appropriate service code. (The field is visible for products of type “Service.”) If available, also set the default **Operation Indicator** for the product.
- **Sales Orders**: For service sales, navigate to **Accounts receivable > Orders > All sales orders** and open the order. On each service line, under **Line details > Fiscal information** tab, verify that **NBS Code** is filled (it should default from the product). Also select the **Operation Indicator Code** if it did not default or if it needs to be changed for this order (for example, choose the code for “service out of municipality” if applicable).
- **Free Text Invoices (FTI)**: Go to **Accounts receivable > Invoices > All free text invoices**. When creating a service invoice here, enter the **NBS Code** and **Operation Indicator Code** on the invoice line (these fields appear under the **Fiscal information invoice line** tab). Since FTIs aren’t linked to a product’s defaults, you must input these codes manually on each service line.
- **Fiscal Documents**: After posting a service invoice (from a sales order or FTI), open **Accounts receivable > Fiscal documents > All fiscal documents**, and find the generated fiscal document record. On the fiscal document form, confirm that **NBS Code** and **Operation Indicator Code** fields are populated (in the grid of **Fiscal document lines**). These values flow from the transaction; ensure they are correct because the NFS-e XML will use them.

Setting the NBS and operation indicator in all these places guarantees the NFS-e XML will include the correct service classification and operation context. Missing or incorrect codes could lead to NFS-e generation errors.

### Reason for Not Providing NIF

**Purpose**: Explain why a **Foreigner ID is not present**, if applicable.
 
If the customer or service recipient does **not** have a Brazilian tax identification number (a scenario with foreign customers), you must specify a reason:
- **Field**: **Reason for not providing NIF** (NIF = Taxpayer Identification Number). 
- **Where to find it**: On the Customers or Sales invoice header form, locate the **R**eason for not providing Foreign ID** field (on a **Fiscal information** FastTab). This field is enabled when the customer’s Foreign ID is blank.
- **Action**: Select the appropriate reason code from the dropdown (e.g., “Foreign customer - No Foreigner ID”).

By doing this, the NFS-e XML will include a code explaining the absence of the tax ID. If this field is left empty while the customer has no Foreigner ID, the NFS-e likely will be rejected for missing required information.
    
### Domestic vs. Non-Domestic Service Location

**Purpose**: Indicate if the service was provided outside Brazil, which affects tax applicability.
- **Group of Fields: LOCATION OF SERVICE PROVISION**.
- **Location**: You can find this option on the service invoice screen or the fiscal document. For example, on a sales order header, check the **Fiscal information** FastTab for a checkbox **Foreign** (by default = No), a field indicates if the service is provided abroad.
- **Action**:
  - If the service was performed **outside Brazil**, mark this field (Yes/Checked). If the service was performed within Brazil (domestic), leave it unmarked (No). The default is typically domestic, so only change
it for export of services.
  - **Domestic**: specify the state where the service was performed.
  - **Foreign**: select the country where the service was provisioned.

This setting tells the system and the NFS-e XML whether ISS (municipal service tax) is applicable. A non-domestic (export) service might be exempt from ISS, so correctly flagging it ensures compliance.

### Approximate Tax Percentage Values (Federal NFS-e Format)

**Purpose**: Provide required tax burden distribution percentages for the national (federal) NFS-e layout.

When using the **Federal standard NFS-e format**, you must enter three percentage values that roughly break down the taxes for the service:
- **Approximate % of federal taxes** – estimated portion of total tax that is federal.
- **Approximate % of state taxes** – estimated portion of total tax that is state.
- **Approximate % of municipal taxes** – estimated portion of total tax that is municipal.

**Where to enter**: These fields appear on the **Released product details form** under the **Fiscal information** FastTab in the **NFS-E TAX BURDEN** group - for cities using the national layout.
**Action**: Enter values in each field so that they total 100%. For example, if only municipal ISS applies, you might input 0%, 0%, and 100%. If federal PIS/COFINS taxes apply, you might split it (e.g., 10% federal, 0% state, 90% municipal). Below is a summary of these fields. Make sure all three fields are filled (use 0% where a level doesn’t apply). This information will be included in the Federal NFS-e XML to meet the reporting requirements of the federal layout.

By completing the above configurations, your Dynamics 365 Finance environment will meet the prerequisites for NFS-e generation. With the environment correctly set, code tables populated, fields filled on products and documents, and required indicators provided, you can proceed to generate NFS-e XML files that comply with the Brazilian electronic service invoice standards.

## Electronic Reporting configuration files

Find configuration files for NFS-e e-invoicing in two locations (for more information, see [Set up Brazil reformed tax](brazil-reform-setup.md)).

### Download list

Configuration files for NFS-e:
- Fiscal documents
- Fiscal documents mapping
- NFS-e Federal format
- NFS-e São Paulo format

## Import the configuration files for e-invoicing

After you download the files, import the configuration files into the system.
    
### Import the configuration files for e-invoicing

To import e-invoicing configuration files, follow these steps:

1. Go to **Workspaces** \> **Electronic reporting**.
1. Select the **Reporting configurations** tile.
1. On **Configurations**, select **Exchange**.
1. Select **Load from XML file**.
1. Select a file by selecting **Browse**.
1. Upload all configuration files, and then go to step 7.

> [!NOTE]
> Upload the model and model mapping configuration files first and then the formats:
> 1. Fiscal documents
> 1. Fiscal documents mapping
> 1. NFS-e Federal format
> 1. NFS-e São Paulo format

7. Go to **Organization administration** \> **Setup** \> **Brazilian parameters**.
8. Select the **Electronic reporting** tab.
9. Select **NfeServices** in the **Type** field, and select **Fiscal documents mapping** in the **Model Mapping** field.
10. Go to **Organization administration** \> **Organizations** \> **Fiscal establishments** \> **Fiscal document types**.
11. Select **NFS-e Federal** or **NFS-e São Paulo** format in the **Export format mapping** field.

## Generate NFS-e service electronic invoices
After you complete all the required configuration steps, you can generate electronic invoices for posted invoices by going to **Accounts receivable > Periodic tasks > NFS-e export**.


## Related set up information

- **Brazil tax reform setup**: Learn about the steps to set up Brazilian tax reform in [Set up Brazil reformed tax](brazil-reform-setup.md)  
- **Import configuration**: Learn more about importing the configuration files in the video [Brazil tax reform : Import configuration](https://learn-video.azurefd.net/vod/player?id=379f59fe-54cf-40f4-af7e-3fe7c09cc082)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
