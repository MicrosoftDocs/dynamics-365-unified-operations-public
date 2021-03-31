---
# required metadata

title: Design ER configurations to import data from external CSV files
description: Use this procedure to design Electronic reporting configurations to import data in to a Finance and Operations app from an external file in CSV format.
author: NickSelin
ms.date: 12/12/2017
ms.topic: business-process
ms.prod:
ms.technology:

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang:
ms.reviewer: kfend
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: nselin
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0

---
# Design ER configurations to import data from external CSV files

[!include [banner](../../includes/banner.md)]

Use this procedure to design Electronic reporting (ER) configurations to import data in to the application from an external file in CSV format. In this procedure, you will create the required ER configurations for the sample company, Litware, Inc. To complete these steps, you must first complete the steps in the procedure, "ER Create a configuration provider and mark it as active."

This procedure is created for users with the assigned role of System administrator or Electronic reporting developer. These steps can be completed using the USMF data set.

You must also download and save the following files locally: [Dynamics 365 Finance Electronic Reporting Examples](https://go.microsoft.com/fwlink/?linkid=862266): 1099model.xml, 1099formatcsv.xml, 1099entriescsv.csv.

1. Go to Organization administration > Workspaces > Electronic reporting.
    * You can configure a process to import external files in XML, TXT, or CSV format to tables in the application. First, you must create an abstract data model to represent the imported data, from a business standpoint – an ER data model configuration is created for that. Next, define a structure of the imported file that maps to the designed data model as the way to port data from the file to the abstract data model – an ER format configuration is created for that. Then, the ER data model configuration must be extended with a new model mapping that describes how the data from the imported file and the persisted data from the abstract data model is used to update the application tables or data entities.
    * The following steps show how externally tracked vendors' transactions are imported from the external CSV file for later use in the vendor's settlement for 1099's forms.
    * Verify that the configuration provider for sample company, Litware, Inc. is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the procedure, "Create a configuration provider and mark it as active".
2. Click Reporting configurations.
3. Apply the '1099 Payments model' filter. If you already completed the procedure," ER Create required configurations to import data from an external file for electronic reporting", and the '1099 Payments model' configuration is available in the configuration tree, skip all of the steps in the next sub-task.

## Add a new ER model configuration

1. Instead of creating a new model to support data import, load the 1099model.xml file that you previously downloaded. This file contains the custom data model of vendors' transactions. This data model is already mapped to the necessary data components.
2. Click Exchange.
3. Click Load from XML file.
4. Click Browse and navigate to the 1099model.xml file that you previously downloaded.
5. Click OK.

## Add a new ER format configuration that supports data import

1. In the tree, select '1099 Payments model'.
2. Click Create configuration to open the drop dialog.
3. In the New field, enter 'Format based on data model 1099 Payments model'.
4. Select Yes in the Supports data import field.
5. Press ESC key to close this page.
    * Instead of creating a new ER format to support data import, load the 1099formatcsv.xml file that you previously downloaded. This file contains the required ER format that defines the structure of the incoming CSV file and the mapping of this structure to the data model of the vendors' transactions.
6. Click Exchange.
7. Click Load from XML file.
    * Click Browse and navigate to the 1099formatcsv.xml file that you previously downloaded.
8. Click OK.
9. In the tree, expand '1099 Payments model'.
10. In the tree, select '1099 Payments model\For importing vendors' transactions (CSV)'.

## Review format settings

1. Click Designer.
2. Click Expand/collapse.
3. Toggle 'Show details' on.
    * The designed format represents the expected structure of the external file in CSV format.
4. In the tree, select 'Incoming: File\Root: Sequence'.
    * For the Root element of the type SEQUENCE, the option 'New line - Windows (CR LF)' has been selected in the 'Special characters' field. Based on this setting, each line in the parsing file must be considered as a separate record.
5. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..*`.
    * For the Root\Line element of the type SEQUENCE, the option 'One many' has been selected in the 'Multiplicity' field. Based on this setting, at least one line will be presented in the parsing file.
6. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case`.
    * Note that the Root\Line\Types element of the type CASE has been added as the nested element of the Root\Line sequence. Because this CASE element contains 3 nested sequence elements, this setting assumes that we expect to meet 3 different types of line in the parsing file.
7. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Header: Sequence 1..1`.
    * The Root\Line\Types\Header element of the type SEQUENCE contains the nested STRING element the value of which has been defined as the fixed string value. This sequence will parse the header line of the parsing file.
8. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Record: Sequence 1..1 (,)`.
    * The Root\Line\Types\Record element of the type SEQUENCE, has been configured to parse the transaction lines. Note that the 'Custom delimiter' character option has been configured as a comma. This means that the comma will be used as a fields' separator for this type of line in the parsing file.
    * Note that several nested elements of different data types have been added for the Root\Line\Types\Record element for parsing the transaction's lines as separated fields. Note that the 'Quotation application' option has been configured as 'None'. This means that in the parsing file, all fields of this type will be considered as having no enclosed characters.
9. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Record: Sequence 1..1 (,)\TransactionDate: DateTime`.
    * For example, the Root\Line\Types\Record\TransactionDate element of the type DATETIME has been configured to get the transaction's date and time value from the parsing file in the 'M/d/yyyy' format.
10. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Record: Sequence 1..1 (,)\CountryCode: String 0..1`.
    * Note that Root\Line\Types\Record\CountryCode element of the type STRING has been configured as having the option 'Zero one' in the 'Multiplicity' field. This setting considers the value of the CountryCode field in the parsing line as optional.
11. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Record: Sequence 1..1 (,)\Remark: Sequence 1..1 (,)`.
    * Note that Root\Line\Types\Record\Remark element of the type SEQUENCE has been configured as having the option 'All' in the 'Quotation application' field and double quotes character in the 'Quotation mark' field. It means that all fields of this type of lines in the parsing file (described by the nested elements: Text of the STRING type) will be considered as enclosed in double quotes characters.
12. In the tree, select `Incoming: File\Root: Sequence\Line: Sequence 1..* \Types: Case\Unparsed: Sequence 1..1`.
    * The Root\Line\Types\Unparsed element of the type SEQUENCE has been configured to parse the transaction lines for the structure which does not match the structure described above in the parent CASE element.

## Review the setting of the format mapping to the data model

1. Click Map format to model.
    * The model mapping 'Mapping to model from CSV format' describes the data flow of the data transfer from the incoming CSV file to the data model.
2. Click Designer.
3. In the tree, expand 'format'.
    * Note that the designed format is presented here as a data source component.
4. In the tree, expand 'format\Incoming: File(Incoming)'.
5. In the tree, expand 'format\Incoming: File(Incoming)\Root: Sequence(Root)'.
6. In the tree, expand `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)`.
7. In the tree, expand `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)\Types: Case(Types)`.
8. In the tree, expand `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)\Types: Case(Types)\Record: Sequence 1..1 (,)(Record)`.
9. In the tree, expand `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)\Types: Case(Types)\Record: Sequence 1..1 (,)(Record)\Data`.
10. In the tree, expand `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)\Types: Case(Types)\Record: Sequence 1..1 (,)(Record)\Data\CountryCode: String 0..1 (CountryCode)`.
11. In the tree, select `format\Incoming: File(Incoming)\Root: Sequence(Root)\Line: Sequence 1..* (Line)\Types: Case(Types)\Record: Sequence 1..1 (,)(Record)\Data\TransactionDate: DateTime(TransactionDate)`.
    * Note that the required and optional format elements, such as TransactionDate and CountryCode, look different in the predefined 'format' data source component.
12. In the tree, expand 'Transactions = '$both''.
    * Note that the elements of the format that defines the structure of the imported file are bound to the elements of the data model. Based on these bindings, the content of the imported CSV file will be stored at run-time in the existing data model. Pay attention to the binding of the CountryRegion element. For any transaction element in the incoming file that does not have a country code value specified, the default country code 'USA' will be populated in the data model.
13. Toggle on 'Show details'.
14. Click the Validations tab.
15. Click Search.
16. In the Find field, type 'vend'.
17. Click Find next.
    * This format mapping may contain user-defined logic to validate the accuracy of the imported data from a business standpoint. For example, based on the setting, for any line in the importing file the structure of which does not match neither the structure of the header line nor transaction line, a warning message will be generated in the Info log informing the user about this case, indicating the transaction's sequence number in the file.
18. Close the page.

## Run the format mapping

For testing purposes, execute the format mapping using the 1099entriescsv.csv file that you previously downloaded. The generated output will present data that will be imported from the selected CSV file and populated to the custom data model at real import.

1. Click Run.
    * Click Browse and navigate to the 1099entriescsv.csv file that you previously downloaded.
2. Click OK.
    * Note the warning messages about lines that are not accepted. Line 4 contains the income value that is presented in the non-acceptable format while line 7 does not contain the transaction remark text in double quotes.
    * Review the output in XML format that represents the data that has been imported from the selected file and ported to the data model. Note that all 7 lines of the imported CSV file were processed. The containing fields' titles line 1 were skipped, 4 transactions were properly parsed, and 2 transactions were recognized as not valid.
3. Close the page.
4. Close the page.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]