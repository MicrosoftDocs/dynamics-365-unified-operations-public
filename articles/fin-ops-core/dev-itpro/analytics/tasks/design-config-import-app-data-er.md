--- 
# required metadata 
 
title: Design ER configurations to parse incoming documents
description: This procedure shows how to design Electronic reporting (ER) configurations to parse an incoming electronic document. 
author: NickSelin
manager: AnnBe 
ms.date: 12/12/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---
# Design ER configurations to parse incoming documents

[!include [banner](../../includes/banner.md)]

This procedure shows how to design Electronic reporting (ER) configurations to parse an incoming electronic document. In this procedure, you will import the required ER configurations that have been created for the sample company, Litware, Inc. and use them for parsing incoming electronic documents. To complete the steps in this procedure, you must first complete the procedure, "ER Create a configuration provider and mark it as active."

This procedure is created for users with the assigned role of System administrator or Electronic reporting developer. 

These steps can be completed using any dataset. Before you begin, download and save the files listed in the topic, "Parse incoming documents to update application data" (https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/parse-incoming-electronic-documents). The files are: EFSTA model.xml, EFSTA format.xml, Response1.xml, Response2.xml, Response3.xml, Response4.xml.

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don't see this configuration provider, complete the steps in the procedure, "Create a configuration provider and mark it as active".  
2. Click Reporting configurations.
    * The following scenario will be used to show the capabilities of parsing incoming electronic documents in XML format: ERP application requests data from the web service (such as http://efsta.org/ EFSTA fiscal service) and parses the incoming responses to update application data accordingly. For the most efficient way to parse, a single ER format is used despite the different structure of expected incoming documents in XML format.   

## Import and review ER configurations
Import the ER model configuration that contains the sample data model designed to store the details of the incoming file.  
1. Click Exchange.
2. Click Load from XML file.
    * Click Browse and select the EFSTA model.xml file.  
3. Click OK.
4. In the tree, select 'EFSTA model'.
5. Click Designer.
    * Review the structure of the imported data model. Note that the enumType enumeration is defined to recognize the following types of service responses: to get confirmation about transaction's submission, to get info about last transaction submitted, and to recognize unsupported response types.   
6. In the tree, expand 'Response'.
    * Note that the root item 'Response' is defined to specify what kind of data must be taken from a supported service response to update application data accordingly.   
7. Close the page.
    * You will import the ER format configuration that specifies how the incoming documents will be parsed to store data in the ER data model.   
8. Click Exchange.
9. Click Load from XML file.
    * Click Browse and select the EFSTA format.xml file.  
10. Click OK.
11. In the tree, expand 'EFSTA model'.
12. In the tree, select 'EFSTA model\EFSTA format'.
13. Click Designer.
14. Click Expand/collapse.
    * Note that the CASE format element is used as the root and contains three nested FILE elements, which means that this format has been designed to parse incoming files of several formats.  
15. In the tree, select 'Responses\Transaction completion\TraC'.
    * Note that the response about the submitted transaction starts from the 'TraC' root element.   
16. In the tree, select 'Responses\Last transaction request\Tra'.
    * Note that the response about the last submitted transaction starts from the 'Tra' root element.   
17. In the tree, select 'Responses\Unexpected response\Text'.
    * The third FILE element with nested TEXT element has been added to recognize any other types of responses that differ from mentioned above.   
18. Click Map format to model.
    * This model mapping contains the definition of data flow to store details of the parsed incoming document with using the data model's items.  
19. Click Designer.
20. In the tree, expand 'format'.
21. In the tree, expand 'format\Responses: Case(Responses)'.
    * Review the structure of the 'format' data source. Note that all three response types are offered separately.   
22. In the tree, select 'format\Responses: Case(Responses)\aType'.
    * The data source item 'aType' has been added to indicate the response type and is bound to the data model item 'Type'.  
23. Click the Validations tab.
24. In the tree, select 'Type = format.Responses.aType'.
    * Note that the ER validation has been configured to inform the user about the situation when the response structure does not match the confirmation about transaction's submission or the information about last transaction submitted (unsupported response case).   
25. Close the page.

## Run model mapping of ER format configured for parsing incoming files
You will run the created model mapping for testing purposes to see how the configured ER format will parse incoming service responses. This step uses different XML files to simulate different type of web service responses.   
1. Open the Response1.xml file in an xml reader, such as a web browser. Note that this file contains confirmation details about the completed transaction ('TraC' is the root element).   
2. Click Run.
    * Click Browse and select the Response1.xml file.  
3. Click OK.
    * Review the generated output. Note that the response type has been correctly recognized and parsed (ERModelEnumDataSourceHandler#EFSTA model#enumType#C means transaction completion case).   
    * Open the Response2.xml file in an XML reader. Note that this file contains information about last transaction submitted ('Tra' is the root element).   
4. Click Run.
    * Click Browse and select the Response2.xml file.  
5. Click OK.
    * Review the generated output. Note that the response type has been correctly recognized and parsed (ERModelEnumDataSourceHandler#EFSTA model#enumType#R means system restart case).   
    * Open the Response3.xml file in an XML reader. Note that this file starts from the TraZ root item and that this structure is not configured using ER format.   
6. Click Run.
    * Click Browse and select the Response3.xml file.  
7. Click OK.
    * Review the generated output. Note that the response type has been correctly recognized as not-supported (ERModelEnumDataSourceHandler#EFSTA model#enumType#U). The corresponding message has been placed in the Infolog (according to the ER validation setting), and most of the data model has not been filled in.   
    * Open the Response4.xml file in an XML reader. Note that the structure of this file is almost the same as the successfully parsed Response1.xml, except the sequence of nested elements of the root element 'TraC'.   
8. Click Run.
    * Click Browse and select the Response4.xml file.  
9. Click OK.
    * Review the generated output. Note that the response type has been correctly recognized as not-supported (ERModelEnumDataSourceHandler#EFSTA model#enumType#U)). The corresponding message has been placed in the Infolog, and most of the data model has not been filled in. This is because the current setting of this ER format assumes a certain sequence of nested elements of the root item of the incoming file.   
10. Close the page.
11. In the tree, select 'Responses\Transaction completion\TraC'.
12. In the Parsing order of nested elements field, select 'Any'.
    * Select Any in the 'Parsing order of nested elements' field to allow any sequence of nested elements for this root XML item.  
13. Click Save.
14. Click Map format to model.
15. Click Run.
    * Click Browse and select the Response4.xml file.  
16. Click OK.
    * Review the generated output. Note that the response type has now been properly recognized as equal for Response1.xml file.  

