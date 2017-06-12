---
# required metadata

title: Cash registers for Sweden
description: Overview of the cash register functionality available for Sweden 
author: epopov
manager: vastrup
ms.date: 07/1/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
# ms.search.scope: [Which Operations client to show this topic as help for]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.assetid: [Go get from guidgenerator.com]
ms.search.region: Sweden
ms.search.industry: retail
ms.author: epopov
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---
# Cash registers for Sweden

This topic provides an overvew of the cash register functionality available for Sweden in Microsoft Dynamics 365 for Retail, and guidelines on setting up the functionality. The functionality includes the following parts:

1. Common POS features that are made available to customers in all countries/regions, such as an option to prohibit mixing sales and returns in one retail receipt;

2. Sweden-specific features, such as additional counters in daily POS reports;

3. A sample for integration of Dynamics 365 Retail POS with Sweden-specific fiscal devices named control units.

## Common POS features

Please refer to [Microsoft Dynamics 365 for Retail documentation](../index.md) to learn common  POS features available to customers in all countries/regions.

A few additional common POS features implemented for Sweden but made available to customers in all countries/regions include:

1. An option to prohibit mixing sales and returns in one retail receipt

    In order to prohibit mixing sales and returns in one retail receipt, set the POS functionality profile parameter **Prohibit mixing sales and returns in one receipt** to **Yes**. When the parameter is enabled, Cloud POS/Modern POS will not allow creating a transaction containing both positive and negative lines.

2. An option to print text fields in receipt with large-sized font. This option may be used to print the copy indication in a receipt copy with large characters

    You can use the Receipt format designer parameter **Font size** to specify that the large (~double) font size should be used for a tag in a receipt format. 

3. An option to register printing of receipt copies in the POS audit event log

    You can enable the registration of printing of receipt copies, as well as other POS audit events, via the **Audit** parameter in the POS functionality profile. The audit events are registered in the Channel DB and in the Dynamics 365 for Retail Headquarters, and can be viewed on the **Audit events** page.

4. A POS permission to restrict printing of a receipt copy more than once

    When the POS audit is enabled, the POS permission **Allow printing receipt copies** controls the possibility to print receipt copies, including the option to prohibit printing a copy of a receipt more than once. 

## Sweden-specific POS features

Sweden-specific POS features are enabled in POS when the POS functionality profile parameter **ISO code** is set to **SE**. The features include:

1. Additional counters in daily POS reports, such as X- and Z-reports. These counters include:

    - Receipt copy count and total amount;
    
    - Value added tax amouns per tax rate;

    - Counts of items and services sold;

    - Total sales excluding and including VAT;

    - Grand total sales, returns; and net.

2. The channel report Electronic journal (Sweden) that lists continuous use events in the POS, including sales, returns, receipt copies, drawer openings, price overrides, etc. **NOTE**: the report cannot be exported and/or printed. The functionality to export and/or print the Electronic journal (Sweden) report will be made available later.

## Integration of Dynamics 365 Retail POS with control units

Microsoft Dynamics 365 for Retail includes a sample for integration of POS with Sweden-specific fiscal devices named control units. The example is implemented as a source code of POS, HW station and Commerce Run-Time extensions, and is available in Retail SDK. The sample includes the following capabilitities:

  - Sales, returns, receipt copies are registered in the control unit connected to the HW station paired with the POS;
  
  - The control code and control unit serial number for a registered transaction (further referred to as "fiscal data") are captured from the control unit and saved in the transaction;
  
  - Custom fields for control code and control unit serial number may be added to a receipt format to print the fiscal data for the transaction in a receipt;

  - The fiscal data for a transaction is printed in the channel report **Electronic journal (Sweden)**.   

**NOTE**: customer orders are not supported by the integration. A sample for the control unit integration for customer orders will be available later.

You can find more information about the control unit integration sample in the [sample deployment guide](../dev-itpro/retail-sdk/retail-sdk-control-unit-sample.md).

## Setup guide for the POS localization for Sweden

Using the Microsoft Dynamics POS solution requires some preliminarily settings being maintained in the Retail module of Dynamics365 for Operations.
For the demonstration, training and testing purposes it's possible to use a standard demo data provided by Microsoft. For setting up Retail module from the scratch as well as for making additional settings based on existing dataset you may use this wiki-page: https://docs.microsoft.com/en-us/dynamics365/operations/retail/. 

It explains the most frequently used and the most important preparation steps. Additional Retail module settings specific for Sweden are described below.
- Set up the Swedish country-context in the current company by updating a primary address in the related Legal entity with 'SWE' country/region code. 
- Maintain VAT settings in accordance with effective legislation requirements. Regarding Dynamics365 for Operations it means to set up the following:
  -	create sales tax codes with an appropriate tax rates,
  -	include sales tax codes in new or existing sales tax groups and item sales tax groups.

Item sales tax groups should be specified  for released products.
More information about the sales tax settings: 
https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/indirect-taxes-overview.
 
- Update a retail store details on the form 'All retail stores'. Update sales tax parameters, fill 'Tax identification number (TIN)' with a company identity number (The Swedish organization number of the dealer).
Field 'Store name' should include the company name.
- Update POS permissions on the form 'Permission groups' if needed. Additionally, here you might limit the number of receipt copies allowed for printing and grant a store manager the permission to skip the fiscal registration of transactions if such registration is currently unavailable.
- Update a POS functionality profile on the form 'Functionality profiles':
  - set Swedish ISO code ('SE').
  - prohibit mixing sales and returns in one receipt,
  - enable a receipt copy registration,
  - specify parameters of the receipt numbering.
- Make necessary changes in the receipt format on the form ''Receipt profiles:
  - set up Language texts and Custom fields,
  - define the reprint message and custom fields in the receipt layout,
  - add fields to display tax amounts per tax rate.
- Setup a fiscal register configuration in xml format. It should contain a mapping of control unit TaxId fields with an appropriate sales tax code from Dynamics365 for Operations. You can use the example below to create your own configuration:

    <?xml version="1.0" encoding="utf-8"?>
    	<configuration>
    	  <configSections>
    	    <section name="UnitConfiguration" type="Microsoft.Dynamics.Retail.FiscalRegistrationServices.CleanCashFiscalRegister.UnitConfiguration, Microsoft.Dynamics.Retail.FiscalRegistrationServices.CleanCashFiscalRegister" />
    	  </configSections>
    	  <UnitConfiguration>
    	    <!--Setting up mapping between VAT codes in POS and control unit that contain VAT rates.-->
    	    <TaxMapping>
    	      <Tax taxCode="stc1" controlUnitTaxId="1" />
    	      <Tax taxCode="stc2" controlUnitTaxId="2" />
    	    </TaxMapping>
    	  </UnitConfiguration>
    </configuration> 
       
Note: stc1, stc2 - sales tax codes with a different tax rate; substitute them with sales tax codes from your dataset.

- Maintain a hardware profile:
Maintain a hardware profile:
  - set up parameters for integration with a control unit, select the fiscal register configuration created before; 
  - specify default options for receipt printing.


5. Create and assign a fiscal register configuration in Retail Headquarters:

    - Run Dynamics 365 for Retail Headquarters.

    - Open *Retail > Channel setup > POS setup > POS profiles > Fiscal register configurations*

    - Create a new fiscal register configuration record, set the name and the description of the configuration.

    - Fill in the configuration content. For this sample, a configuration is an XML file that establishes the mapping between sales tax codes and control unit's VAT groups. You can map up to four sales tax codes. An example configuration can be found below. It is also possible to export a sample configuration by selecting *Export sample configuration* in the action pane.

        ``` xml
        <UnitConfiguration>
            <TaxMapping>
                <Tax taxCode="VAT10" controlUnitTaxId="1"/>
                <Tax taxCode="VAT20" controlUnitTaxId="2"/>
            </TaxMapping>
        </UnitConfiguration>
        ```
    
    - Open *Retail > Channel setup > POS setup > POS profiles > Hardware profiles*

    - Select the hardware profile of the HW station, which the fiscal register is connected to, and set the following fields on the Fisacl register fast-tab:

        - Select Third-party driver in the Fiscal register field;

        - Select the name of the newly created fiscal register configuration in the Configuration field.

