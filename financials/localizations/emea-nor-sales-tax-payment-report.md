---
# required metadata

title: Sales tax report for Norway
description: Set up and generate the VAT statement for users in legal entities located in Norway 
author: epodkolz
ms.author: epodkolz
ms.date: 06/16/2017
ms.topic: article
# ms.prod: [If you use ms.prod, don't use ms.service]
# ms.service: [If you use ms.service, don't use ms.prod; dynamics-ax-applications (?); Dynamics365Operations (?)]
# ms.technology: [Required for some ms.prod values; leave blank if ms.service is specified]

# optional metadata

# manager: [You can use this field for your manager or counterparts such as PMs. Format: MSFT alias]
# ms.search.form: [AOT names of the forms related to the topic, separated by comma]
# audience: [Audience group for the topic; Application User]
# ms.devlang: [Development language for the topic]
# ms.reviewer: [Reviewers of the content audience: Attribute to identify audience group; shylaw]
# ms.search.scope: [Which Operations client to show this topic as help for]
# ms.tgt_pltfrm: [Target platform (for example, ios or android).]
# ms.custom: [used by loc for topics migrated from the wiki]
# ms.assetid: [Go get from guidgenerator.com]
# ms.search.region: [Country/region; e.g. Sweden]
# ms.search.industry: [industry; e.g. retail]
# ms.search.validFrom: [date the content is valid from; e.g. 2017-07-01]
# ms.dyn365.ops.version: [Dyn365O version; e.g. Enterprise edition, July 2017 update]
---
# Sales tax report
Set up and generate the VAT statement for users in legal entities located in Norway.

This topic includes country-specific information about VAT statement setup for users in legal entities in Norway. For more information about general VAT reporting, see [VAT reporting](emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the required format for the specific tax authority, you must set up the report layout for the sales tax authorities. 
  - On the **Sales tax authorities page**, in the **General section**, set the **Report layout** to Norwegian report format.
  - Select the same **Sales tax authority** for the **Sales tax settlement period** that you will use for the sales tax codes.

## Set up sales tax reporting codes
The following is an example of how sales tax reporting codes could be set up for VAT statement generation. 
For users in legal entities in Norway, the following sales tax reporting codes could be created and assigned to Sales tax codes:


| Reporting code |                                     Description                                    | Select the reporting code in this field on the Report setup / Report setup - credit note tab on Sales tax codes page  |
|:--------------:|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
|       11       | Total turnover not covered by the VAT Act                                          | Taxable sales or, Tax-free sales, depending on type of sales                                                          |
|       31       | Domestic turnover and withdrawal, and calculated VAT 25 %, basis                   | Taxable sales                                                                                                         |
|       32       | Domestic turnover and withdrawal, and calculated VAT 25 %, calc. tax               | Sales tax payable                                                                                                     |
|       41       | Domestic turnover and withdrawal, and calculated VAT 15%, basis                    | Taxable sales                                                                                                         |
|       42       | Domestic turnover and withdrawal, and calculated VAT 15%, calc. tax                | Sales tax payable                                                                                                     |
|       51       | Domestic turnover and withdrawal, and calculated VAT 10 %, basis                   | Taxable sales                                                                                                         |
|       52       | Domestic turnover and withdrawal, and calculated VAT 10 %, calc. tax               | Sales tax payable                                                                                                     |
|       61       | Zero rated domestic turnover and withdrawal, basis                                 | Taxable sales                                                                                                         |
|       71       | Domestic turnover subject to reverse charge (emission trading and gold), basis     | Taxable import                                                                                                        |
|       72       | Domestic turnover subject to reverse charge (emission trading and gold), calc. tax | Use tax                                                                                                               |
|       81       | Total zero rated turnover due to export of goods and services, basis               | Tax-free sales                                                                                                        |
|       91       | Import of goods, and calculated VAT 25 %, basis                                    | Taxable import                                                                                                        |
|       101      | Import of goods, and calculated VAT 15 %, basis                                    | Taxable import                                                                                                        |
|       102      | Import of goods, and calculated VAT 15 %, calc. tax                                | Use tax                                                                                                               |
|       103      | Offset for the 102                                                                 | Offset use tax                                                                                                        |
|       111      | Import of goods not subject to VAT, basis                                          | Tax-free purchase                                                                                                     |
|       121      | Purchase of intangible services from abroad, and calculated VAT 25 %, basis        | Taxable import                                                                                                        |
|       122      | Purchase of intangible services from abroad, and calculated VAT 25 %, calc. tax    | Use tax                                                                                                               |
|       123      | Offset for the 122                                                                 | Offset use tax                                                                                                        |
|       131      | Domestic purchases subject to reverse charge, and calculated VAT 25 %, basis       | Taxable import                                                                                                        |
|       132      | Domestic purchases subject to reverse charge, and calculated VAT 25 %, calc. tax   | Use tax                                                                                                               |
|       133      | Offset for the 132                                                                 | Offset use tax                                                                                                        |
|       142      | Deductible domestic input VAT, 25 %, calc. tax                                     | Sales tax receivable                                                                                                  |
|       152      | Deductible domestic input VAT, 15 %, calc. tax                                     | Sales tax receivable                                                                                                  |
|       162      | Deductible domestic input VAT, 10 %, calc. tax                                     | Sales tax receivable                                                                                                  |
|       172      | Deductible import VAT, 25 %, calc. tax                                             | Offset use tax, in case not using 93, 123, 133.                                                                       |
|       182      | Deductible import VAT, 15 %, calc. tax                                             | Offset use tax, in case not using 103.                                                                                |


## Set up Sales tax period code
On **Sales tax settlement periods** page, create a list of periods. Set the period codes in **Sales tax period code** according to the submission periods and aligned with the values provided by Tax authorities. Values from this field will be used while generating an XML file.
Example for bi-monthly returns

|             Period             | Sales tax period code |
|------------------------------|:---------------------:|
| 1st period – January/February  |          014          |
| 2nd period – March/April       |          024          |
| 3rd period – May/June          |          034          |
| 4th period – July/August       |          044          |
| 5th period – September/October |          054          |
| 6th period – November/December |          064          |



