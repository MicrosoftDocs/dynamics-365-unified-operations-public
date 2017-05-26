# Cash registers for Sweden
**Setup guide for the POS localization for Sweden**

Using the Microsoft Dynamics POS solution requires some preliminarily settings being maintained in the Retail module of Dynamics363 for Operations.
For the demonstration, training and testing purposes it's possible to use a standard demo data provided by Microsoft. For setting up Retail module from the scratch as well as for making additional settings based on existing dataset you may use this wiki-page: https://docs.microsoft.com/en-us/dynamics365/operations/retail/. 

It explains the most frequently used and important preparation steps. Additional Retail module settings specific for Sweden are described below.
- Set up the Swedish country-context in the current company by updating a primary address in the related Legal entity with 'SWE' country/region code. 
- Maintain VAT settings in accordance with effective legislation requirements. With reference to Dynamics363 for Operations it means to set up the following:
  -	create sales tax codes with an appropriate tax rates,
  -	include sales tax codes in new or existing sales tax groups and item sales tax groups.
- Item sales tax groups should be specified or for released products.
- More information about the sales tax settings: 
https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/indirect-taxes-overview.
 
- Update sales tax parameters for retail stores on the form 'All retail stores'.
- Update POS permissions on the form 'Permission groups' if needed. Additionally here you might limit the number of receipt copies allowed for printing and grant a store manager the permission to skip the fiscal registration of transactions if such registration is currently unavailable.
- Update a POS functionality profile on the form 'Functionality profiles':
  - set Swedish ISO code ('SE').
  - prohibit mixing sales and returns in one receipt,
  - enable a receipt copy registration,
  - pecify parameters of the receipt numbering.
- Make necessary changes in the receipt format on the form ''Receipt profiles. Define the reprint message and custom fields in the receipt layout.
- Setup a fiscal register configuration in xml format. It should contain a mapping of control unit TaxId fields with an appropriate sales tax code from Dynamics363 for Operations.
- Maintain a hardware profile. Set up parameters for integration with a control unit.
