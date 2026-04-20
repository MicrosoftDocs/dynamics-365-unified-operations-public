---
title: Refresh for training purposes
description: Learn about a general-purpose database refresh scenario for Microsoft Dynamics 365 Finance, including prerequisites.
author: LaneSwenka
ms.author: laswenka
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: IT Pro, Developer
ms.search.region: Global
ms.search.validFrom: 2019-01-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.3
---

# Refresh for training purposes

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that you can use as part of data application lifecycle management (DataALM). This tutorial shows how to use the refresh database operation in a training scenario.

In this tutorial, you learn how to:

> [!div class="checklist"]
>
> - Prepare the target environment.
> - Run the refresh.
> - Reconfigure the target environment.
> - Enable selected users.

As an example of this scenario, a customer who already goes live with the application wants to load a recent copy of production transactions into the user acceptance testing (UAT) environment. By using this approach, the customer can support training of new employees and evaluate configuration changes without affecting the live environment.

## Prerequisites

To perform a refresh database operation, you must deploy your production environment or have a minimum of two standard UAT environments.

## Notify users about the pending downtime

Before you start the bulk of the work, notify users of the target environment that the environment is offline for a period. You can notify users either manually via Microsoft Dynamics Lifecycle Services or programmatically by using RESTful application programming interface (API) calls.

### Manually send a broadcast message

To notify users manually through Lifecycle Services, follow these steps:

1. In Lifecycle Services, open the **Environment details** page for the target environment.
1. Select **Maintain** > **Message online users**.
1. Select **Broadcast a new message for downtime**.
1. Select the valid from and valid to times in your local time zone.
1. Select **Post**.

### Programmatically send a broadcast message

Use the following sample code as shown in a console application, or modify it to work with other services that you can call on demand, such as Microsoft Azure Functions. Before this sample code works, set up your application registration as described in [Service endpoints overview](../data-entities/services-home-page.md).

```csharp
[Serializable]
public class SysAddBroadcastMessageDataContract
{
    public SysAddBroadcastMessageRequest request { get; set; }
}
[Serializable]
public class SysAddBroadcastMessageRequest
{
    public DateTime FromDateTime { get; set; }
    public DateTime ToDateTime { get; set; }
}
public class Program
{
    public static AuthenticationResult getResult(AuthenticationContext ctx, string url)
    {
        return ctx.AcquireTokenAsync(url, "YOUR_APP_REGISTRATION_ID", new Uri("YOUR_REPLY_URL"), new PlatformParameters(PromptBehavior.Always)).Result;
    }
    static void Main(string[] args)
    {
        SysAddBroadcastMessageRequest request = new SysAddBroadcastMessageRequest();
        request.FromDateTime = DateTime.UtcNow;
        request.ToDateTime = DateTime.UtcNow.AddHours(12);

        SysAddBroadcastMessageDataContract dc = new SysAddBroadcastMessageDataContract();
        dc.request = request;

        AuthenticationContext ctx = new AuthenticationContext("https://login.microsoftonline.com/YOUR_TENANT.COM");
        AuthenticationResult res = getResult(ctx, "https://YOUR_SANDBOX_UAT.sandbox.operations.dynamics.com");

        HttpClient restfulCli = new HttpClient();
        restfulCli.DefaultRequestHeaders.Clear();
        restfulCli.BaseAddress = new Uri("https://YOUR_SANDBOX_UAT.sandbox.operations.dynamics.com/");
        restfulCli.DefaultRequestHeaders.Add("Authorization", res.CreateAuthorizationHeader());
        restfulCli.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));

        HttpRequestMessage requestMsg = new HttpRequestMessage(HttpMethod.Post, string.Format("api/services/SysBroadcastMessageServices/SysBroadcastMessageService/AddMessage"));
        requestMsg.Content = new StringContent(JsonConvert.SerializeObject(dc));

        HttpResponseMessage responseMsg = restfulCli.SendAsync(requestMsg).Result;
        if(responseMsg.IsSuccessStatusCode)
        {
            Console.WriteLine("Wow I just notified the users programmatically!");
        }
    }
```

Both approaches, manual via Lifecycle Services and programmatic via RESTful API calls, show users that a period of downtime is pending.

:::image type="content" source="media/BroadcastMessage.png" alt-text="Screenshot of a broadcast message of downtime.":::

## Begin the refresh

Depending on the size of your source environment, it might make sense to begin the refresh process immediately. The larger the source database, the longer it takes to copy to your target Azure SQL Database instance. While the copy is in progress, the target environment is still online. The downtime starts after the copy is completed.

You can perform this process manually through Lifecycle Services. For the latest steps, see [Refresh database](database-refresh.md). In a future release of Lifecycle Services, you can also trigger this process through a RESTful API.

## Reconfigure environment specific settings

After the refresh finishes, use the **Sign off** button in Lifecycle Services to close out of the operation. You can then start to configure the environment-specific settings.

First, sign in to the environment by using the admin account that you find on the **Environment details** page in Lifecycle Services. Here are typical areas of reconfiguration. You might require additional reconfiguration, based on your setup and the independent software vendor (ISV) solutions that are installed.

- **System administration** \> **Setup** \> **Batch groups:** Add the various Application Object Server (AOS) instances to the batch server groups that you require.
- **System administration** \> **Setup** \> **Entity Store:** Refresh the various entities that you require for Microsoft Power BI reporting.
- **System administration** \> **Setup** \> **System parameters:** Reconnect the environment to the Lifecycle Services Help configuration for task guides.
- **System administration** \> **Setup** \> **Email** \> **Email parameters:** Enter the Simple Mail Transfer Protocol (SMTP) settings if you use email in your UAT environment.
- **System administration** \> **Inquiries** \> **Batch jobs:** Select the jobs that you want to run in your UAT environment, and update the status to **Waiting**.

To complete this reconfiguration more quickly, build a custom web service endpoint that you can call on demand after the refresh finishes. An example of this type of web service will be added in a future update of this article.

## Open the environment to users

When you configure the system as you require, you can enable selected users to access the environment. By default, all users except the admin and Microsoft service accounts are disabled.

Go to **System administration** \> **Users** \> **Users**, and enable the users that should have access to the UAT environment. If many users must be enabled, you can complete this task more quickly by using the [Microsoft Excel Add-In](../office-integration/use-excel-add-in.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
