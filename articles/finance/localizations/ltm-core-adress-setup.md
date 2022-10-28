--- 
title: ltm-core-adress-setup
description: This topic provides information about how to complete address setup´s Latam extension
author: cpicon85 
ms.date: 27/10/2022  
ms.topic: article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
--- 

# Latam Address setup

## **Overview**
For Latam countries you can use Latam extension from the Address setup. Each country has a Tax Identification to identify its taxpayers. For example, in Argentina taxpayers Tax ID is called are identified by the number of CUIT, in Chile by the RUT, etc. This article provides information about how to associate the tax identification ID to each country, state, and county.
## **Prerequisites**
The following prerequisites are recommended to be set up before you can add information to Latam extension 
Country, state, and county standard fields
Latam fiscal register feature

## **Country tab configuration**

On the Address setup page, on the Country/region tab use the LATAM button to select one option from the menu
- LATAM
- Tax application
- Country per Taxpayer Type identification

### LATAM

**Foreign country/region Field:** this field of verification will indicate whether the country  selected is different from the company’s home country. 


> [!NOTE]
> By default the checkbox is on “Yes” option. Is importat to verify that the base country has this unmarked checkbox.

Allowed country/region document types section

**Country document type:** In this field you will be able to select Tax Identification created on Fiscal register feature. 

> [!NOTE] 
> If the field “It is a foreign country” is tilted, only the Tax ID types that are configured as Foreing 
> in Tax ID menu can be selected.

### Tax application  agregar link a tax application document

You can use Tax application option to add the codification provided by the fiscal autorities. 

## **State configuration**
To configure new states, you can select a country option in the Country/Region field, press button Apply Filter and the related states are completed. 
Once the standard fields were completed you will be able to follow the steps:
1. Go to Organization administration > Global address book > Addresses > Address setup.
2. Click the State/province tab.
3. Click LATAM.
4. Click LATAM
5. Click New.
6. In the list, mark the selected row.
7. In the State document type field, enter or select a value.
8. In the list, click the link in the selected row.
9. Click Save.
10. Close the page

By default brings the full fields Country/Region, Description, State and Description.

> [!NOTE] 
> Only those documents that are configured as the State Document type  in the Fiscal register feature can be selected.

Tax application-  agregar link a tax application document

## **County configuration**
In different situations is necessary indicate if the city in which a client or a supplier, or the same company is in a free trade zone.
1.	Go to Organization administration > Global address book > Addresses > Address setup.
2.	Click the County tab.
3.	Click LATAM.
4.	Click LATAM.
5.	Click New.
6.	In the list, mark the selected row.
7.	Select the Free trade zone check box.
8.	Click Save.

By default, brings the full fields Country/Region, Description, State, Description, County and Description.
Tax application-  agregar link a tax application document

