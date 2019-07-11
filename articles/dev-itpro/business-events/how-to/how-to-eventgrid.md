---
# required metadata

title: Consume business events with Azure Event Grid
description: This topics provides information about the business events that are available for consumption in Azure Event Grid via the Finance and Operations connector.
author: ibenbouzid
manager: AnnBe
ms.date: 07/11/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: imbenbou
ms.search.validFrom: Platform update 27
ms.dyn365.ops.version: 2019-6-30 

---
# Consume business events with Azure Event Grid

This topic provides steps to help you configure an
Azure Event Grid endpoint with Dynamics 365 Finance and Operation and
consume a business event form Azure Event Grid.

## Scenario overview
Security best practices recommend storing connection strings outside of
applications, but in a Key Vault drive and giving applications the
right access to the key vault keys, secrets or certificates.

This has many benefits, first, if someone gets access to the application
database he will not be able to get the 3rd party connection string. Second,
maintainability becomes easier as there is only one place where we need to
update connection strings especially when multiple applications access the same
resources.

The procedures you'll need to complete include:

1.   Create a new Event Grid Topic
2.   Create a new Key Vault to store Event Grid key
3.   Register an Azure App with permissions to access the key vault on behalf of
    Finqnde and Operations.
4.   Configure Finance and Operations endpoint’s parameters
5.   Consume your business event.

Procedure 1: Create a new Event Grid Topic
=========================================

1.  Log into the Azure Portal.

2.  Select **All services \> Integration \> Event Grid Topics**.

3.  Click **Add** to create a new Event Grid Topic, then fill in the
    parameters and click **Create**. You can create a new resource group
    as a container for your lab or use an existing one.


4.  Once deployment is complete, select you newly created event grid. Click
    **Overview**, and then note the topic endpoint value. You will need this value
    later in Finance and Operations.

    <img src="../../media/BEF-Howto-EventGrid-03.png" width="70%">

5.  Back on the property blade select **Access keys** and copy the **Key 1**
    value. You will need this value later when configuring the key vault.

    <img src="../../media/BEF-Howto-EventGrid-04.png" width="70%">

Procedure 2: Create a Key Vault
==============================

For this procedure, you will have to create a key vault to store the key you
copied above. A key vault is a secure drive used to store keys, secrets, and
certificates. Instead of storing the connection string in Finance and Operations, it is more common
and secure to store it in a key vault then register a new application with Azure
active directory that will have the right to retrieve the secret form the key
vault on behalf of Finance and Operations.

1.  Select **All services \> Security \> Key vaults**


2.  Create a new key vault within your resource group and default
    parameters.

    <img src="../../media/BEF-Howto-Keyvault-02.png" width="50%">

2.  Select **Overview** and copy the key vault URL **DNS Name** and save it
    for later use.

    <img src="../../media/BEF-Howto-Keyvault-03.png" width="70%">

3.  Then select new **BE-key vault \> Secrets \> Generate/Import**, choose a
    new name for your secret and copy the Event Grid Topic key you saved
    earlier on in procedure 1.

    <img src="../../media/BEF-Howto-Keyvault-04.png" width="70%">

4.  Click **Create**.

Procedure 3: Register a new Application
======================================

For this procedure, you will register a new application with Azure AD and give
read and retrieve access to key vault secrets. Then this application will be
used by Finance and Operations to retrieve event grid secrets.

1.  Select **All services \> Security \> Azure Active Directory**.

2.  Select **App registrations (preview) \> New registration**, and then type a new
    name for your application.

3.  Click **Register**.

4.  Select the new application, and then **Certificates & secrets\> New client
    secret**. Type a name for your secret, and set it so it never expires. Click  **Add**.

   <img src="../../media/BEF-Howto-Keyvault-07.png" width="50%">

5.  Copy your new secret for later use. Secrets are visible only once, if
    you forget to copy it you will need to delete it and create a new one.

   <img src="../../media/BEF-Howto-Keyvault-08.png" width="70%">

6.  Select **Overview** and copy your application ID and save it for later
    use.

    <img src="../../media/BEF-Howto-Keyvault-09.png" width="70%">

7.  Then go back to the previously created key vault by selecting **All services
    \> Security \> Key vaults**.

8.  Select your key vault then click **Access policies \> Add new**

9.  Select your new registered application in the **Principal** area of the page.
    Selcted **Get** and **List** secret permissions to retrieve key vault
    secrets.

    <img src="../../media/BEF-Howto-Keyvault-12.png" width="50%">

10.  **Save** your new access policy.

Procedure 4: Configure a Business Events Endpoint in F&O
=======================================================

1.  Log into Finance and Operations.

2.  Go to **System Administration \> Setup \> System Parameters**.

3.  Click the **Business Events** tab.

4.  Click **Business Events**.

5.  Click **Endpoints**.

6.  Click **New**.

7.  Select **Azure Event Grid**.
   
8.  Click **Next**.

9.  Provide the necessary parameters values.

    <img src="../../media/BEF-Howto-EventGrid-06.png" width="50%">

10.  Then click **OK**.

Procedure 5: Consuming a Business Event
======================================

The business scenario is to send an email whenever a free text invoice has been
posted for the USMF company. The message needs to contain details such as the customer
account number, customer name, and the total of the invoice.


1.  Activate the free text invoice posted business event for USMF.

 
2.  Once you activate a business event with a new endpoint, Finance and Operations sends a test
    message to verify that the configuration was right and to cash the
    connection. In order to verify that the test message has been received,
    navigate to Azure and select your **Event Grid Topic \> Metrics**.

3.  Verify that the **Published Events** metric and **Unmatched Events** are
    both showing a value of at least 1. If this is not the case, wait for the
    batch job to pick up your message.

    <img src="../../media/BEF-Howto-EventGrid-08.png" width="70%">

4.  If the above is fine, then we will create a new Logic Apps to subscribe to
    our Event Grid Topic. Select **All services\> Integration\> Logic Apps**.


5.  Then create a new logic app in your resource group.

    <img src="../../media/BEF-Howto-EventGrid-10.png" width="50%">

6.  Once your logic apps resource has been created, choose the option to create a
    **Blank Logic Apps**.

7.  Then search for **Event Grid** and select **When a resource
    event occurs (preview)** trigger.

    <img src="../../media/BEF-Howto-EventGrid-11.png" width="50%">

8.  Select your subscription, the resource type
    **Microsoft.EventGrid.Topics** and the event grid topic name you created
    in procedure 1.

    <img src="../../media/BEF-Howto-EventGrid-12.png" width="50%">

9.  Select the **New Step** button to add a new action.

10. Search for **Parse Json** data operation. This step is needed to be able
    to parse our message with the schema of our data contract provided by Finance and Operations.


11. Select the content field of **Parse Json** action then a side bar will
    appear and give you option form the previous trigger. You need to select the
    **Data object** field of Event Grid message which contains the payload
    transmitted by Finance and Operations.

    <img src="../../media/BEF-Howto-EventGrid-14.png" width="50%">

12. Now we need to type in the schema of the contract received from Finance and Operations.
    However, Finance and Operations provides only a sample payload instead. Hence, we can use Logic
    Apps capability to generate a schema from a payload. Go to Finance and Operations and
    select your event in the catalog and click the **Download schema**
    link. This will download a text file. Open the text file and copy
    the content.


13. Go back to Logic Apps and click the **Use sample payload to generate
    schema** link. Then paste the text file content and click
    **Done**.

    <img src="../../media/BEF-Howto-EventGrid-16.png" width="70%">

14. Depending on the quality of your sample payload, your generator will note
    recognize an Integer from a real especially if the real is provided as a
    whole number in the sample payload. Review your generated schema and check
    if you need to change an “integer” filed into “number”. (In Json a “number”
    data type means real).

    <img src="../../media/BEF-Howto-EventGrid-17.png" width="100%">

15. Choose another final action like to send an email to notify with
    customer payment details. Search for **send email** action, then log in
    to your Office 365 account.
   
16. Fill in the message with the required fields.


17.  Save your logic apps.

18. Then final step is to trigger the business event by posting a customer payment
    then check whether the logic app runs and whether you receive an
    email with customer payment details.
