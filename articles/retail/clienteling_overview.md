---
# required metadata

title: Clienteling overview
description: This topic provides an overview of new clienteling capabilities available in the retail store application.
author: bebeale
manager: AnnBe
ms.date: 11/01/19
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 260624
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Version 10.0.7

---

# Clienteling overview

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Many retailers, especially high-end specialty retailers, want their sales associates to form long-term relationships with their key customers. The sales associates are expected to know about their customer's likes and dislikes, purchase history, product preferences, and important dates such as anniversary and birthday. Associates need a place to capture and easily find the information when needed. If the information is available in a single view, the associates can easily target the customers that meet certain criteria. For example, they can find all the customers that prefer to shop for Handbags, or find customers for whom an important  event such as birthday or anniversary is approaching. 

## Client book

With Dynamics 365 Retail, retailers can leverage the "client book" functionality which can help their store associates to form long-term relationships with key customers.

The client book includes customer cards which show contact information for the customer along with three additional properties that are determined by the retailer and configured in headquarters. The retailer can decide what the three most important things that the sales associate should know about the customer are. For example, a jewelry retailer might want to include important dates such as anniversary or birthday, because these may be occasions when people buy more jewelry. Similarly, a fashion retailer might want to display the cutomer's preferred shopping interests and brands. 

The client book also enables the sale associates to filter the list to show the customers that meet certain criteria. For example, if a new collection of shoes arrived in the store, and the store associate wants to let customers that like to buy shoes know, the associate can filter the client book to find the relevant customers and then take further action. 

Sales associates can optionally remove customers from their client book for cases when the customer, for any reason, is not considered a key customer and thus should not be closely managed.   

Retailers who do not want to manage customers at the sales associate level and want to manage a list of key customers at the store level can opt to view customers from store client books. Using this option, retailers can view the customers from the client books of all the store associates whose address book matches the address book of the current store. That way, if an associate works in multiple stores of the legal entity, the client book would display the customers from all the stores where the sales associate works. This functionality supports additional capabilities like reassigning customers from one sales associate to another, which is helpful when a sales associate is transferred or leaves the company.

Each store associate can have one client book per legal entity, and they can add one or more customers to their client book. Currently in Retail, a customer can only be added to one client book, but we plan on adding functionality to support adding a customer to multiple client books. 

> [!NOTE]
> Unlike customer search, the client book does not filter customers based on store’s address books. 

## Activities and notes
Using online channels, retailers can understand customer preferences without customers explicitly providing this information. When customers interact with the sales associates in the store, they provide their preference information explicitly, but the information can get lost after the sale is over. This information, if recorded, can help the retailers better understand the customer, and then provide better recommendations and a better overall shopping experience. 

To capture the critical information shared directly by customers, sales associates can not only use the client book attributes, but also use the activities and notes functionality. Retailers can configure the activity types such as information about the store visit, email address, phone number, and appointments. Activities created by the sales associates can be viewed in a timeline format on the point of sale (POS) and by navigating to the **Activities** tab on the **All customers > General** page in headquarters. 

Sales associates can also use notes to capture generic customer information that can be referenced before every interaction. The notes are saved in headquarters and can be viewed on the customer profile or on the customer details page in the call center.

> [!NOTE]
> Currently, all notes and activities are viewable by any sales associates for the legal entity who can view customer details pages. Notes and activities are not restricted to the associate who added the customer to the client book. 

## Integration with Dynamics 365 Customer Insights
By using the Dynamics 365 Customer Insights application, retailers can aggregate their data from various systems by which their customers interact with the retailer’s brand, and use this data to generate a single view of the customer and to derive insights. With the integration of Customer Insights with Retail, retailers can choose one or more measures to display on the customer card if the client book. For example, retailers can use the data in Customer Insights to calculate the "churn probability" for a customer and define the "next best action". If these values are defined as measures, they can be displayed on the customer card, providing crucial information for the sales associate. You can learn more about Customer Insights by reading the [Dynamics 365 Customer Insights](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/overview) documentation, and learn more about measures specifically by reading the [Measures](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/pm-measures) topic.

## Set up clienteling
To enable these new Clienteling capabilities in your environment follow the below steps:
- Navigate to the Feature management workspace and filter the features by “Retail and commerce” module (refer the image “Enable_clienteling” below)

![Enable clienteling from feature management workspace](./media/Enable_clienteling.png "Enable clienteling from feature management workspace"). 

- Navigate to the Number sequence tab under Retail Parameters and assign a number sequence to the “Client book identifier”. This is used by the system to assign a client book ID.
- Create a new attribute group containing the attributes that you want to capture for the customers managed within the client book. Mark the required attributes as “Can be refined” so that the sales associates can filter the client book based on these attributes. Additionally, set the display order for these attributes. This display order will be used to determine which attributes should be displayed on the customer card of the client book. The display order 1 is considered higher than display order 2, so the attribute with display order 1 will be displayed prior to the attribute with display order 2. To know more about the attributes and attribute groups refer the article https://docs.microsoft.com/en-us/dynamics365/retail/attribute-attributegroups-lifecycle

> [!NOTE]
> The Dynamics 365 Customer Insights can also be enabled from the above form, but it requires creation of an Azure Application ID and Secret for authentication purposes. This is covered at the end of this article. If Dynamics 365 Customer Insights is enabled and you choose one or more measures to display on the customer card, then these measures will be displayed first, followed by the client book attribute groups based on the display order. For e.g. if you choose two measures from the Customer Insights, then one client book attribute with the highest display order will be displayed on the customer card.

- Associate the newly created attribute group to the “Client book attribute group” property under “Retail parameters > Clienteling”. Refer the image “Client_book_attributes” below. 
![Select the Client book attribute group](./media/Client%20book%20attributes.png "Select the Client book attribute group"). 

- To capture the activities in POS, you can define the activity types. Navigate to the Retail > Customers > Activity types form. 
Note: The activity types are pulled by the retail server by making a real time call for the first time and then is cached for a few hours. So, if you make a change to the Activity types, either wait for the cache to invalidate or, for non-production environments, restart the Retail server service 
- Add two new buttons to the appropriate POS Screen layout to enable sales associate to view their client book and view the client book for the store i.e. clients from all the client books of the associates that share an address book with the store. These operations are named “View customers in client book” and “View customers from store client books” respectively. You will find three more new operations related to client book which govern which sales associates can Add/Remove/Reassign customers from the client book. These operations are named “Add customer to client book”, “Remove customers from client book” & “Reassign customers to a client book” respectively.
- Run the distribution schedule jobs numbered, 1040, 1150, 1110, and 1090. 
Now, the sales associates can navigate to the customer details page on POS and add customers to their client book, view and capture activities/notes for the customers, and target customers by filtering the client book based on customer and client book attributes (refer the image “Client_book” below).
![Client book](./media/client_book.png "View clientbook")

# Set up for enabling integration of Dynamics 365 Customer Insights with Dynamics 365 Retail
To enable the integration with Dynamics 365 Customer Insights you must ensure you have an active instance of Dynamics 365 Customer Insights in the tenant where the Dynamics 365 Retail is provisioned and you need to have an AAD user account which has an Azure subscription.
Follow the below steps to complete the setup: 
1.	Register an app in Azure portal – This is the Application that will be used to authenticate with the Dynamics 365 Customer Insights. Refer the App registration documentation here: https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app. You also need to generate a secret for this application and note it for later use. You will also need to select expiration duration for the secret. Please take the necessary steps to remember to change the secret before expiration to avoid the integration to stop unexpectedly.
2.	Create an Azure key vault and save the App secret– Refer the Azure Key Vault documentation here: https://docs.microsoft.com/en-us/azure/key-vault/quick-create-portal
3.	Enable access to Key Vault from Dynamics 365 Retail – To enable Dynamics 365 Retail to access the secret from the Azure key vault you need an application ID and secret. This application can be the same application that was created in step 1 or it could be a new application. In other words, you can either use the application created in step 1 for both Azure Key Vault access and Customer Insights service access, or create unique applications for Customer Insights service access and accessing Azure Key Vault. To enable an application to access Azure Key Vault refer the documentation here: https://docs.microsoft.com/en-us/azure-stack/user/azure-stack-key-vault-store-credentials?view=azs-1908#create-a-service-principal
4.	Navigate to the Key Vault parameters form in HQ under System Administration > Setup and provide the required information of the created Key Vault and set the application ID used in step 3 as the Key Vault Client so that the Dynamics 365 Retail can access the secrets in the Key Vault; 
5.	To whitelist the application created in step 1 navigate to the Dynamics 365 Customer Insights application and provide “View” access to the App – Refer the documentation here: https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/pm-permissions
6.	Navigate to the Retail parameters > Clienteling tab and the next steps will be done on this screen:
a.	Set the application ID used in step 1 as the Application ID and choose the name of the Key Vault secret created in step 4 as the Secret name
b.	Set the configuration “Enable Customer Insights” to Yes. If the setup fails for any reason, then an error message will be displayed, and the Enable Customer Insights configuration will be set to No.
c.	You might have multiple environments in Dynamics 365 for Customer Insights e.g. Test, Prod etc. Select the right environment as the “Environment instance ID”
d.	In the Alternate customer ID field you need to select the property of the Dynamics 365 Customer Insights which is mapped to the Customer Account number i.e. customer ID of Dynamics 365 Retail
e.	The remaining three properties are the measures which will be displayed on the Customer card of the client book. You can choose zero or more measures to show on the customer card. As mentioned in the document above, the system first shows these values followed by the attributes of the client book attribute group.


