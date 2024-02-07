---
title: Extending Copilot capabilities with low-code plugins
description: This article provides a tutorial on creating low-code plugins for Copilot for Finance and Operations using Microsoft Copilot Studio
author: jaredha
ms.author: jaredha
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 2/6/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extending Copilot capabilities with low-code plugins

[!include [banner](../includes/banner.md)]

Microsoft Copilot Studio provides the orchestration of AI capabilities for Copilot in Finance and Operations, which enables a low-code maker experience for customizing the Copilot capabilities. This tutorial walks through an example of adding a plugin to the Copilot in Finance and Operation chatbot in Copilot Studio to add new capabilities to Copilot.

## Scenario
In this scenario we will add the Copilot capability to translate a course description into another language by entering a prompt in the Copilot panel like "Translate the course description into French." The steps provide guidance on creating low-code plugins in Microsoft Copilot Studio and AI translation capabilities of AI Builder.

The following is an overview of the steps of the tutorial:
1. Create a new topic in Microsoft Copilot Studio triggered by a prompt to translate the course description.
2. Create an action that uses a Power Automate flow to get the course description.
3. Create an acton that uses Power Automate and AI Builder to translate the course description text.
4. Create a message response to send the translated text back to the user in the Copilot pane.

### Prerequisites
For this tutorial you must first have enabled Copilot in Finance and Operations in your environment by following the steps outlined in [Enable Copilot capabilities in finance and operations apps](enable-copilot.md).

## Step 1: Create a new topic
In this step you will create a new topic in the **Copilot for finance and oerations apps** chatbot.

1. Open [Microsoft Copilot Studio](https://web.powerva.microsoft.com) in the environment linked to your finance and operations apps.
2. Open the **Copilot for finance and operations apps** Copilot chatbot.
3. On the **Topics & Plugins** tab, select the **Add** drop-down list, and select **Topic** >> **From blank**.
4. On the **Trigger** node, select **Edit** on the **Phrases** card.
5. In the **Enter text** box on the **Phrases** pane, enter "Translate the course description" and hit Enter.

## Step 2: Add questions to determine the course ID and language
In the new topic, add questions Copilot will ask the user to determine the course ID of the course description to translate, and the language into which it will be translated.

> [!NOTE] In a coming release, the current record viewed by the user in finance and operations apps will be available as a variable in Microsoft Copilot Studio, similar to other contextual variables highlighted in [Using application context with Copilot](copilot-application-context.md). Having this available will enable having Copilot know the current record rather than requiring a question to the user to provide the course ID.

1. Select the **(+)** icon below the **Trigger** node, and select **Ask a question**.
2. On the **Question** node, enter the following:
   - **Enter a message**: "What is the course ID for the course description you want to translate?"
   - **Identify**: User's entire response
   - **Save response as**: Select the variable and change the **Variable name** to "CourseID".
3. Below the **Question** node, select the (+) icon and select **Ask a question** to create a second **Question** node.
   - **Enter a message**: "Into what language do you want the description translated?"
   - **Idenfity**: Language
   - **Save response as**: Select the variable and change the **Variable name** to "LanguageChoice".
4. Select **(+)** >> **Variable management** >> **Set a variable value** to create a new node.
   - **Set variable**: Create a new variable with the name **LanguageCode**.
   - **To value**: Select the **Formula** tab and enter the following Power Fx:
     ```powerapps-dot
      Switch(Topic.LanguageChoice,
	      "Italian", "it",
	      "French", "fr",
	      "Spanish", "es",
	      "Russian", "ru",
	      "German", "de",
	      "Japanese", "ja")
     ```
## Step 3: Create an action to get the course description
Create an action in the topic that uses a flow to get the course description.

1. Select **(+)** >> **Call an action** >> **Create a flow**.
2. When Power Automate opens, select **(+)** below the **When Power Virtual Agents calls a flow** node, and select **Add an action**.
3. Select the **When Power Virtual Agents calls a flow** node to open options, and define the parameters:
   - Choose **Text** as the type of user input.
   - Enter "CourseID" for the **Input**.
4. In the **Add an action** pane, search for and select the **List rows** action in the **Microsoft Dataverse** connector.
5. On the **Parameters** tab for the **List rows** options:
   - **Table Name**: Courses V2 (mserp)
     > [!NOTE] If the Courses V2 (mserp) table is not available in your environment, you will need to enable it following the steps outlined in [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md).
   - **Select Columns**: mserp_coursedescription
   - **Filter Rows**: mserp_courseid eq '`CourseID`'
     > [!NOTE] Select the `CourseID` variable by selecting the **Parameters** icon (lightning bolt), allowing you to select data from a previous step.
6. Add an action to compose the course record.
   - Select **(+)** below the **List rows** action, and select **Add an action**.
   - In the **Add an action** pane, search for and select the **Compose** data operation.
   - Use the **Parameters** action on the **Inputs** field to select the **body/value** parameter from the **List rows** action as the input value.
7. Add an action to parse the JSON for the course record.
    - Select **(+)** below the **Compose** action, and select **Add an action**.
    - In the **Add an action** pane, search for and select the **Parse JSON** data operation.
    - In the **Content** parameter of the **Parameters** pane, select the **Outputs** parameter from the **Compose** action.
    - In the **Schema** parameter, enter the following JSON schema:
      ```json
	  {
	    "type": "array",
	    "items": {
	        "type": "object",
	        "properties": {
	            "@@odata.type": {
	                "type": "string"
	            },
	            "@@odata.id": {
	                "type": "string"
	            },
	            "@@odata.editLink": {
	                "type": "string"
	            },
	            "mserp_coursedescription": {
	                "type": "string"
	            },
	            "mserp_hcmcoursev2entityid@odata.type": {
	                "type": "string"
	            },
	            "mserp_hcmcoursev2entityid": {
	                "type": "string"
	            }
	        },
	        "required": [
	            "@@odata.type",
	            "@@odata.id",
	            "@@odata.editLink",
	            "mserp_coursedescription",
	            "mserp_hcmcoursev2entityid@odata.type",
	            "mserp_hcmcoursev2entityid"
	        ]
	     }
	   }
       ```
8. Initialize a variable to be used for the course description that will be the output of the flow.
    - Select **(+)** below the **Parse JSON** action, and select **Add an action**.
    - Search for and select the **Initialize variable** action in the **Variable** group of actions.
    - **Name**: CourseDescription
    - **Type**: String
9. Set the variable to the course description.
    - Select **(+)** below the **Initialize variable** action, and select **Add an action**.
    - Search for and select the **Set variable** action in the **Variable** group of actions.
    - **Name**: CourseDescription
    - **Value**: Select the `Body mserp_coursedescription` parameter from the **Parse JSON** action.
10. Select the flow output to send back to Microsoft Copilot Studio.
    - Select the **Return value(s) to Power Virtual Agents** node.
    - On the **Parameters** tab, select **Add an output** and select **Text** as the type of output.
    - Enter "CourseDescription" for the parameter name.
    - **Enter a value to respond with**: Select the **CourseDescription** variable from the **Variables** parameters.
11. Select the flow name and rename to "Get course description demo".
12. Save the flow.
	<img alt="Create an action using a flow to get the course description" src="../media/Copilot-extensibillity-get-course-description.png" width="70%">
13. Return to Copilot Studio and select **Done** on the **Save and refresh** dialog.
14. Select **(+)** below the **Set variable value** node and select **Call an action**.
15. On the **Select an action** dialog, select the **Get course description demo** action created in flow.
16. On the **Course description demo** action node, select the `Topic.CourseID` variable for the **CourseID (String)** input.

## Step 4: Create an action to translate the course description
Create a new action in the topic that uses a flow and AI Builder to translate the course description retrieved in the previous step.

1. Select **(+)** below the **Get course description demo** action node, and select **Call an action** >> **Create a flow**.
2. In Power Automate, select the **When Power Virtual Agents calls a flow**.
3. On the **Parameters** tab of the options, select **Add an input**.
   - **Input type**: Text
   - **Input**: TextToTranslate
4. Select **Add an input** to add a second input.
   - **Input type**: Text
   - **Input**: LanguageCode
5. Select **(+)** below the **When Power Virtual Agents calls a flow** node of the flow, and select **Add an action**.
6. Search for and select the **Translate text into another language** action in the **AI Builder** connector.
   - **Translate from**: Detect automatically
   - **Text**: Select the `TextToTranslate` variable from the **When Power Virtual Agents calls a flow** step.
   - **Translate To**: Select **Enter custom value**, and select the `LanguageCode` variable from the **When Power Virtual Agents calls a flow** step.
7. Select the value to return to Copilot Studio.
   - Select the **Return value(s) to Power Virtual Agents** node.
   - Add an output with a type of **Text**.
   - Enter "TranslatedText" for the name of the output.
   - In the **Enter a value to respond with** text box, select the **Translated text** variable from the outputs of the **Translate text into another language** action node.
8. Change the flow name to "Translate text demo", and select **Save**.
   <img alt="Create an action using a flow to get the course description" src="../media/Copilot-extensibility-translate-text.png" width="70%">
9. Return to Copilot Studio and select **Done** on the **Save and refresh** dialog.
10. Select **(+)** below the **Course description demo** node and select **Call an action** >> **Translate text demo**.
    - On the **Translate text demo** action node, select the `Topic.CourseDescription` variable for the **TextToTranslate (String)** input.
    - Select the `Topic.LanguageCode` variable for the **LanguageCode (String)** input.
<img alt="Copilot translates a course description into a foreign language" src="../media/Copilot-extensibility-create-actions.png" width="70%">
   
## Step 5: Create a message to return the translated text to Copilot
Add a message node to the chatbot that returns the translated course description output to the Copilot in Finance and Operations.

1. Select **(+)** below the **Translate text demo** action node, and select **Send a message**.
2. In the **Enter a message** text box, select the **Insert variable** action, and select the `Topic.TranslatedText` variable.

## Step 6: Test the new capability in Copilot
1. In Copilot Studio, **Save** the new topic.
2. On the **Publish** tab, select **Publish** to publish your changes to the chatbot.
3. In Finance and Operations, open the **Courses** form (Human Resources >> Courses), and select a course to open the details.
4. Select the **Copilot** icon in the top navigation bar to open the Copilot pane.
5. In the chat panel, enter "Translate the course description into Japanese", and follow the prompt to get a response.
<img alt="Copilot translates a course description into a foreign language" src="../media/Copilot-extensibility-translate-course-description.png" width="70%">
