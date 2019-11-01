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
> Unlike customer search, the client book does not filter customers based on the store’s address books. 

## Activities and notes
Using online channels, retailers can understand customer preferences without customers explicitly providing this information. But when customers interact with sales associates in the store, they provide their preference information explicitly. That information can get lost after the sale is over, however. If recorded, it could help retailers better understand the customer, and help them provide better recommendations and a better overall shopping experience. 

To capture the critical information shared directly by customers, sales associates can not only use the client book attributes, but also use the activities and notes functionality. Retailers can configure the activity types such as information about the store visit, email address, phone number, and appointments. Activities created by the sales associates can be viewed in a timeline format on the point of sale (POS) and by navigating to the **Activities** tab on the **All customers > General** page in headquarters. 

Sales associates can also use notes to capture generic customer information that can be referenced before every interaction. The notes are saved in headquarters and can be viewed on the customer profile or on the customer details page in the call center.

> [!NOTE]
> Currently, all notes and activities are viewable by any sales associates for the legal entity who can view customer details pages. Notes and activities are not restricted to the associate who added the customer to the client book. 

## Integration with Dynamics 365 Customer Insights
By using the Dynamics 365 Customer Insights application, retailers can aggregate their data from various systems by which their customers interact with the retailer’s brand, and use this data to generate a single view of the customer and to derive insights. With the integration of Customer Insights with Retail, retailers can choose one or more measures to display on the customer card if the client book. For example, retailers can use the data in Customer Insights to calculate the "churn probability" for a customer and define the "next best action". If these values are defined as measures, they can be displayed on the customer card, providing crucial information for the sales associate. You can learn more about Customer Insights by reading the [Dynamics 365 Customer Insights](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/overview) documentation, and learn more about measures specifically by reading the [Measures](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/pm-measures) topic.

## Set up clienteling
To enable the clienteling functionality in your environment, follow the steps below.

1. Go to the **Feature management** workspace and filter the features by “Retail and commerce” module (refer the image below).

![Enable clienteling from feature management workspace](./media/Enable_clienteling.png "Enable clienteling from feature management workspace"). 

2. Enable **Clienteling**. 

3. Go to the **Retail Parameters** page and select the **Number sequence** tab. 

4. Select the **Client book identifier** line, and in the **Number sequence code** field, click the dropdown and choose a number sequence.  The value will be used by the system to assign a client book ID.

5. Click **Save**.

6. Following the instructions in the [Attributes and attribute groups](https://docs.microsoft.com/en-us/dynamics365/retail/attribute-attributegroups-lifecycle) topic, create a new attribute group containing the attributes that you want to capture for customers that are managed within the client book. 
    - Define the required attributes as “Can be refined” so that the sales associates can filter the client book based on these attributes. 
    - Set the display order for these attributes. This display order will be used to determine which attributes should be displayed on the customer card of the client book. Display order 1 is considered higher than display order 2, so the attribute with display order 1 will be displayed prior to the attribute with display order 2. 
  
    > [!NOTE]
    > Dynamics 365 Customer Insights can be enabled from the same page, but it requires the creation of an Azure Application ID and Secret for authentication purposes (the requirements are covered at the end of this topic). If Dynamics 365 Customer Insights is enabled and you choose one or more measures to display on the customer card, these measures you chose will be displayed first, followed by the client book attribute groups based on the display order. For example, if you choose two measures from the Customer Insights, one client book attribute with the highest display order will be displayed on the customer card.

7. On the **Retail parameters** page, on the **Clienteling** tab, click the dropdown in the **Client book attribute group** field and choose the attribute group you just created. (Refer to the image below.) 

![Select the Client book attribute group](./media/Client%20book%20attributes.png "Select the Client book attribute group"). 

8. To capture activities that happen in POS, define the activity types on the **Retail > Customers > Activity types** page. 

    > [!NOTE]
    > Activity types are pulled by the Retail Server making a real-time call for the first time. Once the activities are pulled, they are cached for a few hours. If you make a change to the activity types, either wait for the cache to invalidate, or for non-production environments, restart the Retail Server service.
    
9. Add two new buttons to the appropriate POS screen layout to enable sales associate to view their client book and view the client book for the store (clients from all the client books of the associates that share an address book with the store). These operations are named **View customers in client book** and **View customers from store client books**, respectively. There are three more operations available related to client book that govern which sales associates can add/remove/reassign customers from the client book. These operations are named **Add customer to client book**, **Remove customers from client book**” and **Reassign customers to a client book**.

10. Run the following distribution schedule jobs: 1040, 1150, 1110, and 1090. 

After you've completed the process above, sales associates can navigate to the customer details page on POS and add customers to their client book, view and capture activities and notes for the customers, and target customers by filtering the client book based on customer and client book attributes. (Refer the image below).

![Client book](./media/client_book.png "View clientbook")


## Enable integration of Customer Insights with Retail

To enable the integration of Dynamics 365 Customer Insights with Dynamics 365 Retail, you must ensure you have an active instance of Customer Insights in the tenant where Retail is provisioned. You must also have an AAD user account which has an Azure subscription.

Follow the steps below to set up the integration.

1.	Register an application in Azure portal. This is the application that will be used to authenticate with Customer Insights. Follow the instructions in the [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) topic. 

2. You need to generate a secret for the application. Note the secret someplace safe for later use. Also select the expiration duration for the secret. Take the necessary steps to remember to change the secret before the expiration to prevent having the integration stop unexpectedly.

3.	Create an Azure Key Vault and save the application secret. Follow the instructions in the [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](https://docs.microsoft.com/en-us/azure/key-vault/quick-create-portal) topic.

4.	Enable access to Key Vault from Dynamics 365 Retail. Do do so, you need an app ID and secret. The application can be the same one that was created in step 1 or it can be a new application. (In other words, you can use the application created in step 1 for both Azure Key Vault access and Customer Insights service access, or you can create unique application for each.) Follow the instructions in the [Store service principal credentials in Azure Stack Key Vault](https://docs.microsoft.com/en-us/azure-stack/user/azure-stack-key-vault-store-credentials?view=azs-1908#create-a-service-principal) topic.

5.	Go to **System Administration > Setup > Key Vault parameters** in headquarters and enter the required information for the Key Vault. Then set the application ID used in step 4 as the Key Vault Client so that Retail can access the secrets in the Key Vault.

6.	To whitelist the application created in step 1, go to Customer Insights and provide “View” access to the app. Follow the instructions in the [Permissions](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/pm-permissions) topic.

6.	In Retail, go to the **Retail parameters** page. On the **Clienteling** tab, expand the **Dynamics 365 Customer Insights** section and do the following.

     1. In the **Application ID** field, enter the application ID used in step 1. 
     1. In the **Secret name** field, enter the name of the Key Vault secret created in step 5.
     1. Set **Enable Customer Insights** to **Yes**. If the setup fails for any reason, an error message will be displayed and **Enable Customer Insights** configuration will be set to **No**.
     1.	You may have multiple environments in Customer Insights, for example test, prod, etc. Enter the appropriate environment in the **Environment instance ID** field.
     1. In the **Alternate customer ID** field, enter the property of Customer Insights that is mapped to the customer account number (customer ID of Dynamics 365 Retail).
     1. The remaining three properties are the measures that will be displayed on the customer card of the client book. You can choose zero to three measures to show on the customer card. As mentioned above, the system first shows these values followed by the values of the client book attribute group.


