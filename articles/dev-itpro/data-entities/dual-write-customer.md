---
# required metadata

title: Integrated Customer Master
description: 
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

## Integrated Customer Master

It's common for customer records to be mastered in more than one application. For example, SMB sales motion can bring in commercial customer records through a Dynamics 365 for Sales application and e-Commerce or retail sales can bring in customer records through a Dynamics 365 for Finance and Operations application. Regardless of where the customer record originates, it is integrated behind the scenes beyond application boundaries and infrastructure differences. Integrated customer mastering helps to handle multi-mastering scenarios and provides a comprehensive view of the customer to Dynamics 365 application suite.

## Customer data flow

*Customer* is a well-defined concept in both Finance and Operations and the Common Data Service (CDS). Therefore, the integration of customer data involves harmonizing the customer concept between Finance and Operations and CDS applications. The following diagram shows the customer data flow:

![customer data flow](media/dual-write-customer-data-flow.png)

Customers can be broadly classified into two types - commercial/organizational customers and consumers/end users. These two types of customers are stored and handled differently in Finance and Operations and CDS.

In Finance and Operations, both commercial customers and consumers are mastered in a single table named **CustTable** (CustomerCustomerV3Entity) and they are classified based on the **Type** attribute. (Type=Organization =\> Commercial/organizational customer; Type=Person =\> consumer/end user).The primary contact person information is handled through the **SMMContactPersonEntity** entity.

In CDS, the commercial customers are mastered in **Account** entity and identified as a customer when the **RelationshipType** attribute is set to **Customer**. Both consumer/end user and the contact person are represented as **Contact**. To have a clear separation between a contact person and a consumer/end user, there is a Boolean flag on the **Contact** entity named **Sellable**. When **Sellable** is **True**, the contact is a consumer/end user and can have quotes and orders created for them. When **Sellable** is **False**, the contact is only a primary contact person of a customer.

When a non-sellable contact participates in a quote or order process, the contact is flagged as a sellable contact by setting **Sellable** to **True**. Once a contact becomes a sellable contact, the contact remains as a sellable contact.

## Templates

Customer data includes all information about the customer like customer group, addresses, contact information, payment profile, invoice profile, and loyalty status. A collection of entity maps works together in customer data interaction as shown in the following table.

Finance and Operations    | Customer Engagement Application
--------------------------|---------------------------------
Customer V3               | Account
Customer V3               | Contact
CDS Contacts V2           | Contact
Customer groups           | Msdyn\_customergroups
Customer Payment Method   | Msdyn\_customerpaymentmethods
Loyalty Card              | Msdyn\_loyaltycards
Payment Schedule          | Msdyn\_paymentschedules
Payment Schedule          | Msdyn\_paymentschedulelines
Payment day CDS           | Msdyn\_paymentdays
Payment day lines CDS     | Msdyn\_paymentdaylines
Terms of Payment          | Msdyn\_paymentterms
Name Affixes              | Msdyn\_nameaffixes

## Customer V3 to Account

Synchronizes the commercial and organization customer master information between Finance and Operations and CDS.

![](media/dual-write-account-1.png)

![](media/dual-write-account-2.png)

Source field | Map type | Destination field
---|---|---
CUSTOMERACCOUNT | = | accountnumber
INVOICEADDRESSCITY | = | address2_city
INVOICEADDRESSCOUNTRYREGIONISOCODE | = | address2_country
INVOICEADDRESSCOUNTY | = | address2_county
INVOICEADDRESSLATITUDE | > | address2_latitude
INVOICEADDRESSLONGITUDE | > | address2_longitude
INVOICEADDRESSSTATE | = | address2_stateorprovince
INVOICEADDRESSSTREET | = | address2_line1
INVOICEADDRESSZIPCODE | = | address2_postalcode
CREDITLIMIT | = | creditlimit
DELIVERYADDRESSCITY | = | address1_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | = | address1_country
DELIVERYADDRESSCOUNTY | = | address1_county
DELIVERYADDRESSLATITUDE | > | address1_latitude
DELIVERYADDRESSLONGITUDE | > | address1_longitude
DELIVERYADDRESSZIPCODE | = | address1_postalcode
ORGANIZATIONNAME | = | name
ORGANIZATIONNUMBEROFEMPLOYEES | = | numberofemployees
PRIMARYCONTACTEMAIL | = | emailaddress1
PRIMARYCONTACTFAX | = | fax
PRIMARYCONTACTPHONE | = | telephone1
PRIMARYCONTACTTWITTER | = | primarytwitterid
PRIMARYCONTACTURL | = | websiteurl
SALESCURRENCYCODE | = | transactioncurrencyid.isocurrencycode
SALESMEMO | = | description
CREDITLIMITISMANDATORY | >< | msdyn_creditlimitismandatory
CREDITRATING | = | msdyn_creditrating
CUSTOMERGROUPID | = | msdyn_customergroupid.msdyn_groupid
IDENTIFICATIONNUMBER | = | msdyn_identificationnumber
INVOICEACCOUNT | = | msdyn_billingaccount.accountnumber
INVOICEADDRESS | >< | msdyn_invoiceaddress
ISONETIMECUSTOMER | >< | msdyn_onetimecustomer
ONHOLDSTATUS | >< | msdyn_onholdstatus
PARTYCOUNTRY | = | msdyn_partycountry
PARTYSTATE | = | msdyn_partystateprovince
PAYMENTDAY | = | msdyn_paymentday.msdyn_name
PAYMENTMETHOD | = | msdyn_customerpaymentmethod.msdyn_name
PAYMENTSCHEDULE | = | msdyn_paymentschedule.msdyn_name
PAYMENTTERMS | = | msdyn_paymentterm.msdyn_name
PAYMENTTERMSBASEDAYS | = | msdyn_paymenttermsbasedays
PRIMARYCONTACTFACEBOOK | = | msdyn_primaryfacebookid
PRIMARYCONTACTFAXEXTENSION | = | msdyn_faxextension
PRIMARYCONTACTLINKEDIN | = | msdyn_primarylinkedinid
TAXEXEMPTNUMBER | = | msdyn_taxexemptnumber
VENDORACCOUNT | = | msdyn_vendor.msdyn_vendoraccountnumber
PRIMARYCONTACTEMAILDESCRIPTION | = | msdyn_emailaddress1description
PRIMARYCONTACTFACEBOOKDESCRIPTION | = | msdyn_primaryfacebookdescription
PRIMARYCONTACTFAXDESCRIPTION | = | msdyn_faxdescription
PRIMARYCONTACTLINKEDINDESCRIPTION | = | msdyn_primarylinkedindescrption
PRIMARYCONTACTPHONEDESCRIPTION | = | msdyn_telephone1description
PRIMARYCONTACTPHONEEXTENSION | = | msdyn_telephone1extension
PRIMARYCONTACTTWITTERDESCRIPTION | = | msdyn_primarytwitteriddescription
PRIMARYCONTACTURLDESCRIPTION | = | msdyn_websiteurldescription
LANGUAGEID | << | none
DELIVERYADDRESSSTREET | = | address1_line1
DELIVERYADDRESSSTATE | = | address1_stateorprovince
none | >> | address1_addresstypecode
none | >> | customertypecode
PARTYTYPE | << | none
PARTYNUMBER | = | msdyn_partynumber


## Customer V3 to Contact

Synchronizes consumer and end user customer master data between Finance and Operations and Customer Engagement.

![](media/dual-write-contact-1.png)

![](media/dual-write-contact-2.png)

Source field | Map type | Destination field
---|---|---
none | >> | msdyn_sellable
PARTYTYPE | << | none
PARTYNUMBER | = | msdyn_partynumber
CUSTOMERACCOUNT | = | msdyn_contactpersonid
CUSTOMERGROUPID | = | msdyn_customergroupid.msdyn_groupid
PERSONFIRSTNAME | = | firstname
PERSONLASTNAME | = | lastname
PERSONMIDDLENAME | = | middlename
PERSONPROFESSIONALTITLE | = | jobtitle
PERSONGENDER | >< | gendercode
PERSONMARITALSTATUS | >< | familystatuscode
LANGUAGEID | << | none
ADDRESSCITY | = | address1_city
ADDRESSCOUNTRYREGIONISOCODE | = | address1_country
ADDRESSCOUNTY | = | address1_county
ADDRESSLATITUDE | > | address1_latitude
ADDRESSLONGITUDE | > | address1_longitude
ADDRESSLOCATIONROLES | << | none
ADDRESSSTATE | = | address1_stateorprovince
ADDRESSSTREET | = | address1_line1
ADDRESSZIPCODE | = | address1_postalcode
ADDRESSPOSTBOX | = | address1_postofficebox
none | >> | address1_addresstypecode
INVOICEADDRESSCITY | = | address2_city
INVOICEADDRESSCOUNTRYREGIONISOCODE | = | address2_country
INVOICEADDRESSCOUNTY | = | address2_county
INVOICEADDRESSLATITUDE | > | address2_latitude
INVOICEADDRESSLONGITUDE | > | address2_longitude
INVOICEADDRESSSTATE | = | address2_stateorprovince
INVOICEADDRESSSTREET | = | address2_line1
INVOICEADDRESSZIPCODE | = | address2_postalcode
none | >> | address2_addresstypecode
DELIVERYADDRESSCITY | = | address3_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | = | address3_country
DELIVERYADDRESSCOUNTY | = | address3_county
DELIVERYADDRESSLATITUDE | > | address3_latitude
DELIVERYADDRESSLONGITUDE | >> | address3_longitude
DELIVERYADDRESSSTATE | = | address3_stateorprovince
DELIVERYADDRESSSTREET | = | address3_line1
DELIVERYADDRESSZIPCODE | = | address3_postalcode
none | >> | address3_addresstypecode
PRIMARYCONTACTEMAIL | = | emailaddress1
PRIMARYCONTACTEMAILDESCRIPTION | = | msdyn_emailaddress1description
PRIMARYCONTACTFAX | = | fax
PRIMARYCONTACTFAXDESCRIPTION | = | msdyn_faxdescription
PRIMARYCONTACTFAXEXTENSION | = | msdyn_faxextension
IDENTIFICATIONNUMBER | = | msdyn_identificationnumber
PARTYCOUNTRY | = | msdyn_partycountry
PARTYSTATE | = | msdyn_partystateprovince
PRIMARYCONTACTFACEBOOK | = | msdyn_primaryfacebookid
PRIMARYCONTACTFACEBOOKDESCRIPTION | = | msdyn_primaryfacebookdescription
PRIMARYCONTACTLINKEDIN | = | msdyn_primaryinkedinid
PRIMARYCONTACTLINKEDINDESCRIPTION | = | msdyn_primarylinkedindescrption
PRIMARYCONTACTPHONE | = | telephone1
PRIMARYCONTACTPHONEDESCRIPTION | = | msdyn_telephone1description
PRIMARYCONTACTPHONEEXTENSION | = | msdyn_telephone1extension
PRIMARYCONTACTTWITTER | = | msdyn_primarytwitterid
PRIMARYCONTACTTWITTERDESCRIPTION | = | msdyn_primarytwitteriddescription
PRIMARYCONTACTURL | = | websiteurl
PRIMARYCONTACTURLDESCRIPTION | = | msdyn_websiteurldescription
SALESCURRENCYCODE | = | transactioncurrencyid.isocurrencycode
SALESMEMO | = | description


## Contacts

Synchronizes all primary, secondary, and tertiary contact information for both customers and vendors between Finance and Operations and Customer Engagement.

![](media/dual-write-contacts.png)

Source field | Map type | Destination field
---|---|---
CONTACTPERSONPARTYNUMBER | = | msdyn_partynumber
ASSOCIATEDCONTACTTYPE | << | none
FIRSTNAME | = | firstname
MIDDLENAME | = | middlename
LASTNAME | = | lastname
ASSOCIATEDCONTACTNUMBER | = | msdyn_vendorcontactid.msdyn_vendoraccountnumber
PRIMARYADDRESSCITY | = | address1_city
PRIMARYADDRESSCOUNTRYREGIONID | = | address1_country
PRIMARYADDRESSCOUNTYID | = | address1_county
PRIMARYFAXNUMBER | = | fax
PRIMARYADDRESSSTATEID | = | address1_stateorprovince
PRIMARYADDRESSSTREET | = | address1_line1
PRIMARYADDRESSZIPCODE | = | address1_postalcode
PRIMARYPHONENUMBER | = | telephone1
PRIMARYEMAILADDRESS | = | emailaddress1
EMPLOYMENTDEPARTMENT | = | department
NOTES | = | description
GENDER | >< | gendercode
GOVERNMENTIDENTIFICATIONNUMBER | = | governmentid
PRIMARYURL | = | websiteurl
MARITALSTATUS | >< | familystatuscode
ISRECEIVINGDIRECTMAIL | >< | donotemail
EMPLOYMENTPROFESSION | = | jobtitle
SPOUSENAME | = | spousesname
none | >> | msdyn_contactforvendor
none | >> | msdyn_contactpersonid


## Customer Groups

Synchronizes customer group information between Finance and Operations and Customer Engagement.

![](media/dual-write-customer-groups.png)

Source field | Map type | Destination field
---|---|---
CUSTOMERGROUPID | = | msdyn_groupid
DESCRIPTION | = | msdyn_description
ISSALESTAXINCLUDEDINPRICE | >< | msdyn_issalestaxincludedinprice
PAYMENTTERMID | = | msdyn_paymenttermid.msdyn_name
CLEARINGPERIODPAYMENTTERMNAME | = | msdyn_clearingperiodpaymenttermname.msdyn_name


## Customer Payment Methods

Synchronizes customer payment method information between Finance and Operations and Customer Engagement.

![](media/dual-write-customer-payment-methods.png)

Source field | Map type | Destination field
---|---|---
NAME | = | msdyn_name
ACCOUNTTYPE | >< | msdyn_accounttype
DISCOUNTGRACEPERIODDAYS | = | msdyn_discountgraceperioddays
BRIDGINGPOSTINGENABLED | >< | msdyn_bridgingpostingenabled
ISSEPA | >< | msdyn_issepa
LASTFILENUMBER | = | msdyn_lastfilenumber
LASTFILENUMBERTODAY | = | msdyn_lastfilenumbertoday
DESCRIPTION | = | msdyn_description
PAYMENTTYPE | >< | msdyn_paymenttype
CREATEANDDRAWBILLOFEXCHANGEDURINGINVOICEPOSTING | >< | msdyn_invoiceupdate
PAYMENTSTATUS | >< | msdyn_paymentstatus
SUMBYPERIOD | >< | msdyn_sumbyperiod
ENABLEPOSTDATEDCHECKCLEARINGPOSTING | >< | msdyn_enablepostdatescheckclearingposting
BILLOFEXCHANGEDRAFTTYPE | >< | msdyn_billofexchangedrafttype
DIRECTDEBIT | >< | msdyn_directdebit


## Loyalty Cards

Synchronizes customer loyalty card information between Finance and Operations and Customer Engagement.

![](media/dual-write-loyalty-cards.png)

Source field | Map type | Destination field
---|---|---
CARDNUMBER | = | msdyn_cardnumber
CARDTENDERTYPE | >< | msdyn_cardtendertype
PARTYNUMBER | = | msdyn_partynumber
REPLACEMENTCARDNUMBER | > | msdyn_replacementcardnumber
OMOPERATINGUNITNUMBER | = | msdyn_operatingunitnumber
LOYALTYENROLLMENTDATE | = | msdyn_enrollmentdate



## Payment Schedules

Synchronizes payment schedule reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-payment-schedules.png)

Source field | Map type | Destination field
---|---|---
NAME | = | msdyn_name
DESCRIPTION | = | msdyn_description
ALLOCATIONMETHOD | >< | msdyn_allocationmethod
PAYMENTFREQUENCYUNITS | >< | msdyn_paymentfrequencyunit
PAYMENTFREQUENCY | = | msdyn_paymentfrequency
NUMBEROFPAYMENTS | = | msdyn_numberofpayments
FIXEDPAYMENTAMOUNT | = | msdyn_fixedpaymentamount
MINIMUMPAYMENTAMOUNT | = | msdyn_minimumpaymentamount
SALESTAXALLOCATIONMETHOD | >< | msdyn_salestaxallocationmethod
NOTES | = | msdyn_note


## Payment Schedule Lines

Synchronizes payment schedule lines reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-payment-schedule-lines.png)

Source field | Map type | Destination field
---|---|---
PAYMENTSCHEDULENAME | = | msdyn_paymentschedule.msdyn_name
PAYMENTSCHEDULENAME | > | msdyn_name
LINENUMBER | = | msdyn_linenumber
PERIODSAFTERDUEDATE | = | msdyn_periodsafterduedate
PERCENTORAMOUNT | >< | msdyn_percentoramount
PERCENTORAMOUNTVALUE | = | msdyn_percentoramountvalue


## Payment days

Synchronizes payment days reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-payment-days.png

Source field | Map type | Destination field
---|---|---
NAME | = | msdyn_name
DESCRIPTION | = | msdyn_description


## Payment Day Lines

Synchronizes payment day lines reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-payment-day-lines.png)

Source field | Map type | Destination field
---|---|---
CDSINTEGRATIONKEY | = | msdyn_paymentdaylineid
FREQUENCY | >< | msdyn_frequency
DAYOFWEEK | >< | msdyn_dayofweek
DAYOFMONTH | = | msdyn_dayofmonth
NAME | = | msdyn_paymentday.msdyn_name


## Payment Terms

Synchronizes payment terms (terms of payment) reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-payment-terms.png)

Source field | Map type | Destination field
---|---|---
DESCRIPTION | = | msdyn_description
NAME | = | msdyn_name
NUMBEROFMONTHS | = | msdyn_numberofmonth
CUTOFFDAYOFMONTH | = | msdyn_cutoffdayofmonth
ISCASHPAYMENT | >< | msdyn_iscashpayment
NUMBEROFDAYS | = | msdyn_days
ISCERTIFIEDCOMPANYCHECK | >< | msdyn_iscertifiedcompanycheck
ISDEFAULTPAYMENTTERM | >< | msdyn_isdefaultpaymentterm
CREDITCARDPAYMENTTYPE | >< | msdyn_creditcardpaymenttype
CREDITCARDCREDITCHECKTYPE | >< | msdyn_creditcardcreditchecktype
PAYMENTDAYNAME | = | msdyn_paymentdayname.msdyn_name
PAYMENTMETHODTYPE | >< | msdyn_paymentmethodtype
PAYMENTSCHEDULENAME | = | msdyn_paymentschedulename.msdyn_name


## Name Affixes

Synchronizes name affixes reference data between Finance and Operations and Customer Engagement for both customers and vendors.

![](media/dual-write-name-affixes.png)

Source field | Map type | Destination field
---|---|---
AFFIX | = | msdyn_affix
TYPE | >< | msdyn_affixtype
DESCRIPTION | = | msdyn_description

