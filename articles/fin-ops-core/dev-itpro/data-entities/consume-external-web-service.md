---
# required metadata

title: Consume external web services
description: This article describes how to consume external web services in finance and operations apps.
author: peakerbl
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Consume external web services

[!include [banner](../includes/banner.md)]

You can consume web services by adding new class libraries. In Microsoft Dynamics AX 2012, you could consume web services from X++ code by adding Microsoft Visual Studio projects as a reference and by using **Aif::CreateServiceClient**. This scenario is supported, but the steps have changed. Application Integration Framework (AIF) is no longer supported.

The following steps show how to consume an external StockQuote service from X++.

Note that the web service URL in this sample is fictional.  There is no known web service at http://www.contoso.net/stockquote.asmx.  To make this code work you will need to adapt it to your specific web service.

1. Create a new Class Library project in Visual Studio, and name it **ExternalServiceLibrary.csproj**.
2. In the Visual Studio project, add a service reference to the external web service: `http://www.contoso.net/stockquote.asmx`.
3. Create a new static class, and wrap the StockQuote service operation as shown in the following example.

    ```xpp
    public static string GetQuote(string s)
    {
        var binding = new System.ServiceModel.BasicHttpBinding();
        var endpointAddress = new EndpointAddress("http://www.contoso.net/stockquote.asmx");
        ServiceLibrary.QuoteReference.StockQuoteSoapClient client = new ServiceLibrary.QuoteReference.StockQuoteSoapClient(binding, endpointAddress);

        //GetQuote is the operation on the StockQuote service
        return client.GetQuote("MSFT");
    }
    ```

4. Build the project. The binary ExternalServiceLibrary.dll is created.
5. Create a new Dynamics project in Visual Studio.
6. Add **ExternalServiceLibrary.dll** as a reference.
7. In the X++ class, you can use the external web services that were referenced in ExternalServiceLibrary.dll.

    ```xpp
    public static void main(Args _args)
    {
        info(ServiceLibrary.StockQuoteClass::GetQuote("MSFT"));
    }
    ```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

