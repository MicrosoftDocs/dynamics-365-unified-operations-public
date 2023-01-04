---
# required metadata

title: Person
description: This article describes the Person entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 12/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Person


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Person entity for Dynamics 365 Human Resources.

Physical name: mshr_dirpersonentity

### Description

This entity provides the personal information for the individual who is the candidate.

## JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_name": "String",
    "mshr_namealias": "String",
    "mshr_knownas": "String",
    "mshr_languageid": "String",
    "mshr_addressbooks": "String",
    "mshr_anniversaryday": Int,
    "mshr_anniversarymonth": Int,
    "mshr_anniversaryyear": Int,
    "mshr_birthday": Int,
    "mshr_birthmonth": Int,
    "mshr_birthyear": Int,
    "mshr_childrennames": "String",
    "mshr_gender": Int,
    "mshr_hobbies": "String",
    "mshr_initials": "String",
    "mshr_maritalstatus": Int,
    "mshr_phoneticfirstname": "String",
    "mshr_phoneticlastname": "String",
    "mshr_phoneticmiddlename": "String",
    "mshr_personalsuffix": "String",
    "mshr_personaltitle": "String",
    "mshr_professionalsuffix": "String",
    "mshr_professionaltitle": "String",
    "mshr_fullprimaryaddress": "String",
    "mshr_addresscity": "String",
    "mshr_addresscountryregionid": "String",
    "mshr_addresscountryregionisocode": "String",
    "mshr_addresscounty": "String",
    "mshr_addressdistrictname": "String",
    "mshr_addresslatitude": Decimal,
    "mshr_addresslocationid": "String",
    "mshr_addresslocationroles": "String",
    "mshr_addresslongitude": Decimal,
    "mshr_addressstate": "String",
    "mshr_addressstreet": "String",
    "mshr_addressvalidfrom": "Date",
    "mshr_addressvalidto": "Date",
    "mshr_addresszipcode": "String",
    "mshr_addressisprivate": Int,
    "mshr_addressdescription": "String",
    "mshr_primarycontactemail": "String",
    "mshr_primarycontactemaildescription": "String",
    "mshr_primarycontactemailisim": Int,
    "mshr_primarycontactemailpurpose": "String",
    "mshr_primarycontactfax": "String",
    "mshr_primarycontactfaxdescription": "String",
    "mshr_primarycontactfaxextension": "String",
    "mshr_primarycontactfaxpurpose": "String",
    "mshr_primarycontactphone": "String",
    "mshr_primarycontactphonedescription": "String",
    "mshr_primarycontactphoneextension": "String",
    "mshr_primarycontactphoneismobile": Int,
    "mshr_primarycontactphonepurpose": "String",
    "mshr_primarycontacttelex": "String",
    "mshr_primarycontacttelexdescription": "String",
    "mshr_primarycontacttelexpurpose": "String",
    "mshr_primarycontacturl": "String",
    "mshr_primarycontacturldescription": "String",
    "mshr_primarycontacturlpurpose": "String",
    "mshr_primarycontactfacebook": "String",
    "mshr_primarycontactfacebookdescription": "String",
    "mshr_primarycontactfacebookisprivate": Int,
    "mshr_primarycontactfacebookpurpose": "String",
    "mshr_primarycontactlinkedin": "String",
    "mshr_primarycontactlinkedindescription": "String",
    "mshr_primarycontactlinkedinisprivate": Int,
    "mshr_primarycontactlinkedinpurpose": "String",
    "mshr_primarycontacttwitter": "String",
    "mshr_primarycontacttwitterdescription": "String",
    "mshr_primarycontacttwitterisprivate": Int,
    "mshr_primarycontacttwitterpurpose": "String",
    "mshr_partytype": "String",
    "mshr_namesequencedisplayas": "String",
    "mshr_firstname": "String",
    "mshr_lastnameprefix": "String",
    "mshr_lastname": "String",
    "mshr_middlename": "String",
    "mshr_electroniclocationid": "String",
    "mshr_dirpersonentityid": "Guid",
    "mshr_addresstimezone": Int
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Entity ID**<br>mshr_dirpersonentityid<br>*GUID* | Read-only<br>Required<br>System-generated | A system-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read-only<br>Required<br>System-generated | A user-readable, system-generated unique identifier for the person.  |
| **Name**<br>mshr_name<br>*String* | Read-only<br>Required | The field value is a concatenation of First Name, Middle Name, Last Name Prefix, and Last Name in the order defined in the **Name Sequence Display As** field. |
| **Name Alias**<br>mshr_namealias<br>*String* | Read/write<br>Optional | A name alias that may be provided for the person. |
| **Known As**<br>mshr_knownas<br>*String* | Read/write<br>Optional | A name that may be used for the person if typically known as another name. |
| **Language ID**<br>mshr_languageid<br>*String* | Read/write<br>Optional | The language ID of the person’s primary language, as defined in ISO 639-1 format. |
| **Address books**<br>mshr_addressbooks<br>*String* | Read/write<br>Optional | Address book to which the person may be assigned. Address books that have been set up for the organization are listed in the mshr_diraddressbooksentity entity. |
| **Anniversary Day**<br>mshr_anniversaryday<br>*Int* | Read/write<br>Optional | The day of the person’s anniversary date. |
| **Anniversary Month**<br>mshr_anniversarymonth<br>*mshr_monthsofyear option set* | Read/write<br>Optional | The month of the person’s anniversary date. |
| **Anniversary Year**<br>mshr_anniversaryyear<br>*Int* | Read/write<br>Optional | The year of the person’s anniversary date. |
| **Birth Day**<br>mshr_birthday<br>*Int* | Read/write<br>Optional | The day of the person’s birthdate. |
| **Birth Month**<br>mshr_birthmonth<br>*mshr_monthsofyear option set* | Read/write<br>Optional | The month of the person’s birthdate. |
| **Birth Year**<br>mshr_birthyear<br>*Int* | Read/write<br>Optional | The year of the person’s birthdate. |
| **Children Names**<br>mshr_childrennames<br>*String* | Read/write<br>Optional | String for the names of the person’s children. There is no required delimitation. |
| **Gender**<br>mshr_gender<br>*mshr_hcmpersongender option set* | Read/write<br>Optional | The person’s gender. |
| **Hobbies**<br>mshr_hobbies<br>*String* | Read/write<br>Optional | The person’s hobbies. |
| **Initials**<br>mshr_initials<br>*String* | Read/write<br>Optional | The initials of the person’s name. |
| **Marital Status**<br>mshr_maritalstatus<br>*mshr_hcmpersonmaritalstatus option set* | Read/write<br>Optional | The person’s marital status. |
| **Phonetic First Name**<br>mshr_phoneticfirstname<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s first name. |
| **Phonetic Last Name**<br>mshr_phoneticlastname<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s last name. |
| **Phonetic Middle Name**<br>mshr_phoneticmiddlename<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s last name. |
| **Personal Suffix**<br>mshr_personalsuffix<br>*String* | Read/write<br>Optional | The person’s personal suffix. Valid values in the mshr_dirnameaffixentity entity where mshr_type is Suffix (200000001). |
| **Personal Title**<br>mshr_personaltitle<br>*String* | Read/write<br>Optional | A personal title for the person. Valid values in the mshr_dirnameaffixentity entity where mshr_type is Title (200000000).
| **Professional Suffix**<br>mshr_professionalsuffix<br>*String* | Read/write<br>Optional | A professional suffix. |
| **Professional Title**<br>mshr_professionaltitle<br>*String* | Read/write<br>Optional | A professional title. |
| **Full Primary Address**<br>mshr_fullprimaryaddress<br>*String* | Read/write<br>Optional | The person’s full primary address, a concatenation of the primary address fields. |
| **Address City**<br>mshr_addresscity<br>*String* | Read/write<br>Optional | The city of the person’s primary address. Set up in mshr_logisticsaddresscityentity entity. |
| **Address Country Region**<br>mshr_addresscountryregionid<br>*String* | Read/write<br>Optional | The country/region of the person’s primary address. Valid values in the mshr_logisticsaddresscountryregionentity entity. |
| **Address Country Region ISO Code**<br>mshr_addresscountryregionisocode<br>*String* | Read/write<br>Optional | The ISO code of the country of the person’s primary address. |
| **Address County**<br>mshr_addresscounty<br>*String* | Read/write<br>Optional | The county of the person’s primary address. Set up in mshr_logisticsaddresscountyentity entity. |
| **Address District Name**<br>mshr_addressdistrictname<br>*String* | Read/write<br>Optional | The district of the person’s primary address. Set up in mshr_logisticsaddressdistrictentity entity. |
| **Address Latitude**<br>mshr_addresslatitude<br>*Decimal* | Read/write<br>Optional | The latitude of the person’s primary address. |
| **Address Location ID**<br>mshr_addresslocationid<br>*String* | Read/write<br>Optional | The unique identifier for the location of the person’s primary address. Valid values in mshr_logisticspostaladdresslocationcdsentity entity. |
| **Address Location Roles**<br>mshr_addresslocationroles<br>*String* | Read/write<br>Optional | The location role of the person’s primary address. Set up in the mshr_logisticslocationrolecdsentity entity. |
| **Address Longitude**<br>mshr_addresslongitude<br>*Decimal* | 	Read/write<br>Optional | The longitude of the person’s primary address. |
| **Address State**<br>mshr_addressstate<br>*String* | Read/write<br>Optional | The state of the person’s primary address. Set up in mshr_logisticsaddressstateentity entity. |
| **Address Street**<br>mshr_addressstreet<br>*String* | Read/write<br>Optional | The street address of the person’s primary address. |
| **Address Valid From**<br>mshr_addressvalidfrom<br>*Date* | Read/write<br>Optional | The date from which the person’s primary address is valid. |
| **Address Valid To**<br>mshr_addressvalidto<br>*Date* | Read/write<br>Optional | The date to which the person’s primary address is valid. |
| **Address Zip Code**<br>mshr_addresszipcode<br>*String* | Read/write<br>Optional | The postal code of the person’s primary address. Set up in mshr_logisticsaddresspostalcodeentity entity. |
| **Address Is Private**<br>mshr_addressisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary address is shared with others in the organization. |
| **Address Description**<br>mshr_addressdescription<br>*String* | Read/write<br>Optional | Description for the person’s primary address. |
| **Primary Contact Email**<br>mshr_primarycontactemail<br>*String* | Read/write<br>Optional | The person’s primary email address. |
| **Primary Contact Email Description**<br>mshr_primarycontactemaildescription<br>*String* | Read/write<br>Optional | A description provided for the primary email address. |
| **Primary Contact Email is IM**<br>mshr_primarycontactemailisim<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary email address is available for instant messages. |
| **Primary Contact Email Purpose**<br>mshr_primarycontactemailpurpose<br>*String* | Read/write<br>Optional | The purpose for the primary email address. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Fax**<br>mshr_primarycontactfax<br>*String* | Read/write<br>Optional | Primary fax number. |
| **Primary Contact Fax Description**<br>mshr_primarycontactfaxdescription<br>*String* | Read/write<br>Optional | Description provided for the primary fax number. |
| **Primary Contact Fax Extension**<br>mshr_primarycontactfaxextension<br>*String* | Read/write<br>Optional | The extension of the primary fax number. |
| **Primary Contact Fax Purpose**<br>mshr_primarycontactfaxpurpose<br>*String* | Read/write<br>Optional | The purpose for the primary fax number. Set up in mshr_logisticslocationroleentity entity.
| **Primary Contact Phone**<br>mshr_primarycontactphone<br>*String* | Read/write<br>Optional | Primary phone number. |
| **Primary Contact Phone Description**<br>mshr_primarycontactphonedescription<br>*String* | Read/write<br>Optional | Description provided for the primary phone number. |
| **Primary Contact Phone Extension**<br>mshr_primarycontactphoneextension<br>*String* | Read/write<br>Optional | The extension of the primary phone number. |
| **Primary Contact Phone Is Mobile**<br>mshr_primarycontactphoneismobile<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary phone number is a mobile phone. |
| **Primary Contact Phone Purpose**<br>mshr_primarycontactphonepurpose<br>*String* | Read/write<br>Optional | The purpose for the primary phone number. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Telex**<br>mshr_primarycontacttelex<br>*String* | Read/write<br>Optional | Primary telex number. |
| **Primary Contact Telex Description**<br>mshr_primarycontacttelexdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary telex number. |
| **Primary Contact Telex Purpose**<br>mshr_primarycontacttelexpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary telex number. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact URL**<br>mshr_primarycontacturl<br>*String* | Read/write<br>Optional | The primary URL. |
| **Primary Contact URL Description**<br>mshr_primarycontacturldescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary URL. |
| **Primary Contact URL Purpose**<br>mshr_primarycontacturldescription<br>*String* | Read/write<br>Optional | The purpose for the person’s primary URL. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Facebook**<br>mshr_primarycontactfacebook<br>*String* | Read/write<br>Optional | Primary Facebook account. Identified by User ID. |
| **Primary Contact Facebook Description**<br>mshr_primarycontactfacebookdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary Facebook account. |
| **Primary Contact Facebook is Private**<br>mshr_primarycontactfacebookisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary Facebook account is visible to other users. |
| **Primary Contact Facebook Purpose**<br>mshr_primarycontactfacebookpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary Facebook account. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact LinkedIn**<br>mshr_primarycontactlinkedin<br>*String* | Read/write<br>Optional | Primary LinkedIn account. Identified by user name. |
| **Primary Contact LinkedIn Description**<br>mshr_primarycontactlinkedindescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary LinkedIn account. |
| **Primary Contact LinkedIn Is Private**<br>mshr_primarycontactlinkedinisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary LinkedIn account information is shared with other users. |
| **Primary Contact LinkedIn Purpose**<br>mshr_primarycontactlinkedinpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary LinkedIn account. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Twitter**<br>mshr_primarycontacttwitter<br>*String* | Read/write<br>Optional | The person’s primary Twitter account. Identified by @username. |
| **Primary Contact Twitter Description**<br>mshr_primarycontacttwitterdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary Twitter account. |
| **Primary Contact Twitter Is Private**<br>mshr_primarycontacttwitterisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary Twitter account information is shared with other users. |
| **Primary Contact Twitter Purpose**<br>mshr_primarycontacttwitterpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary Twitter account. Set up in mshr_logisticslocationroleentity entity. |
| **Party Type**<br>mshr_partytype<br>*String* | Read/write<br>Optional | The party type of the person. Will always be **Person** for candidates. |
| **Name Sequence Display As**<br>mshr_namesequencedisplayas<br>*String* | Read/write<br>Optional | The sequence in which the person’s name properties are concatenated to form the Name (mshr_name) property value. |
| **First Name**<br>mshr_firstname<br>*String* | Read/write<br>Required | The person’s first name. |
| **Middle Name**<br>mshr_middlename<br>*String* | Read/write<br>Optional | The person’s middle name. |
| **Last Name Prefix**<br>mshr_lastnameprefix<br>*String* | Read/write<br>Optional | The prefix of the person’s last name. |
| **Last Name**<br>mshr_lastname<br>*String* | Read/write<br>Optional | The person’s last name. |
| **Electronic Location ID**<br>mshr_electroniclocationid<br>*String* | Read/write<br>Optional | The ID of the person’s electronic location. |
| **Address Time Zone**<br>mshr_addresstimezone<br>*Int* | Read/write<br>Optional | The time zone of the person’s primary address. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
