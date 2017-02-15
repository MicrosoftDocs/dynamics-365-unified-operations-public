---
# required metadata

title: Commerce runtime and Retail Server extensibility
description: This article describes various ways that you can extend the commerce runtime (CRT) and Retail Server. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Retail Server controller and add a controller for an entity.
author: josaw1
manager: AnnBe
ms.date: 2016-07-27 23 - 41 - 57
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 104593
ms.assetid: a5f00ab6-ffad-4365-99f7-b119ca5b98a7
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Commerce runtime and Retail Server extensibility

This article describes various ways that you can extend the commerce runtime (CRT) and Retail Server. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Retail Server controller and add a controller for an entity.

Using extension properties on CRT entities
------------------------------------------

One way to add new data to an existing commerce runtime (CRT) entity is to use extension properties. Extension properties are key-value pairs on the entity. By default, these key-value pairs aren't persisted into the database. Extension properties provide the easiest and, it can be argued, the most useful way to extend entities. You should always try to use this pattern first, unless something prevents you from using it. Although you can use polymorphism/inheritance to add simple data members to entities, this approach usually causes more issues than it solves. (Nevertheless, this approach might be required for specific cases.) To add an extension property, you must use this syntax.

    entity.SetProperty("EXTENSION_PROPERTY_ADDED", true);

To enable the property to be read later, you can use this syntax.

    bool? property = (bool?)entity.GetProperty("EXTENSION_PROPERTY_ADDED");

## Using extension properties on CRT entities with persistence
Any extension property that you add to an entity stays in memory for the lifetime of the object. Additionally, the extension property travels across application boundaries. For example, if you add an extension property in Retail Modern POS and then call Retail Server/the CRT, the key-value pair is also available in that process. Additionally, if that entity is sent to Microsoft Dynamics 365 for Operations during a Commerce Data Exchange: Real-time Service (RTS) call, the key-value pair is also available in the Dynamics 365 for Operations process. However, as we mentioned earlier, it isn't persisted by default. If you must persist an extension property, you must do data modeling to help guarantee that you make the right design choices about where the data should reside. You can use a new column in the same table, you can use a new table and a join, or you can use another approach. The recommended approach is to use a new table and a join. This approach fits most requirements well. For this approach, the customizer must learn where all “writes” occur and update the SQL code (stored procedures), and must also learn where all the “reads” occur and update that SQL code (SQL view). The EmailPreference sample provides a good end-to-end example. In that sample, a single SQL view and a single SQL stored procedure are changed via customization. It's important to note that new SQL objects must have the correct role permissions granted. For example, a new table that must be included in Commerce Data Exchange (CDX) synchronization jobs must be granted access by DataSyncUsersRole. For other roles that are available, inspect the main SQL script in the Retail Sdk\\Database folder.

    IF (SELECT OBJECT_ID('ax.RETAILCUSTPREFERENCE')) IS NULL 
    BEGIN
        CREATE TABLE [ax].[RETAILCUSTPREFERENCE](
        // removed . . . 
        ) ON [PRIMARY]
        // removed . . . 
    END
    GO

    -- grant Read/Insert/Update/Delete permission to DataSyncUserRole so CDX can function
    GRANT SELECT ON OBJECT::[ax].[RETAILCUSTPREFERENCE] TO [DataSyncUsersRole]
    GO
    GRANT INSERT ON OBJECT::[ax].[RETAILCUSTPREFERENCE] TO [DataSyncUsersRole]
    GO
    GRANT UPDATE ON OBJECT::[ax].[RETAILCUSTPREFERENCE] TO [DataSyncUsersRole]
    GO
    GRANT DELETE ON OBJECT::[ax].[RETAILCUSTPREFERENCE] TO [DataSyncUsersRole]
    GO

Finally, the SQL update script for your customization must be registered in the Customization.settings file for the Retail software development kit (SDK).

### Using extension properties on CRT request and response types

Like entities, request and response types can be extended.

    request.SetProperty("BoolPropertyName", true);
    response.SetProperty("BoolPropertyName2", true);

    bool? BoolPropertyName = (bool?)request.GetProperty("BoolPropertyName");
    bool? BoolPropertyName2 = (bool?)response.GetProperty("BoolPropertyName2");

### Implementing a new CRT service that handles multiple new requests

It's a typical case to implement a new CRT service. First, you must create new request and response classes.

#### Creating the request and response classes

For serialization to work, the new request type must implement the **\[DataContract\]** and **\[DataMember\]** attributes.

    using System.Runtime.Serialization;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;

    [DataContract]
    public sealed class GetStoreHoursDataRequest : Request
    {
        public GetStoreHoursDataRequest(string storeNumber)
        {
            this.StoreNumber = storeNumber;
        }

        [DataMember]
        public string StoreNumber { get; private set; }
    }

The new response type resembles the request type.

    [DataContract]
    public sealed class GetStoreHoursDataResponse : Response
    {
        public GetStoreHoursDataResponse(PagedResult dayHours)
        {
            this.DayHours = dayHours;
        }

        [DataMember]
        public PagedResult DayHours { get; private set; }
    }

Next, you must create a new CRT service that uses the request and response types.

#### Creating a new CRT service

1.  Implement the new service.

        public class StoreHoursDataService : IRequestHandler

2.  Implement two members of the interface. The **SupportedRequestTypes** member returns a list of all requests that this service can handle. The execute method is the method that the CRT calls for you if a request for this service is run.

        public IEnumerable SupportedRequestTypes
        {
            get
            {
                return new[]
                {
                typeof(GetStoreHoursDataRequest),
                };
            }
        }

        public Response Execute(Request request);

3.  In the commerceRuntime.Config file, update the **composition** section (or the equivalent section) to register this service. Note that you can register single types or all types from an assembly. The CommerceRuntime engine will find all IRequestHandler derived types.
4.  Optional: Use the CommerceRuntime Test Host to do a test run of your service.

### Implementing a new CRT service that handles a single new request

It’s slightly easier to create a single-request service.

    public class CrossLoyaltyCardService : SingleRequestHandler

Registration is done as described in the previous procedure.

### Implementing a new CRT service that overrides the functionality of an existing request

In some cases, the request and response types are sufficient, but the service implementation must be changed. If some new data must be transmitted, you can also extend entity, request, or response objects by using extension properties. In this scenario, you can create the service as described earlier and use the existing IRequestHandler types. Additionally, registration in the commerceRuntime.Config file must precede registration of the service that should be overridden. This registration order is important because of the way that the Managed Extensibility Framework (MEF) loads the extension dynamic-link libraries (DLLs). The types that are higher in the file win.

### Implementing a new CRT entity and using it in new CRT service

Any new entity must be of the **CommerceEntity** type. When you use this type, lots of low-level functionality is automatically handled for you. The following example, which is taken from the StoreHours sample, shows how to create an entity that is bound to the database table. This is the usual case.

    public class StoreDayHours : CommerceEntity
    {
        private const string DayColumn = "DAY";
        private const string OpenTimeColumn = "OPENTIME";
        private const string CloseTimeColumn = "CLOSINGTIME";
        private const string IdColumn = "RECID";

        public StoreDayHours()
            : base("StoreDayHours")
        {
        }

        [DataMember]
        [Column(DayColumn)]
        public int DayOfWeek
        {
            get { return (int)this[DayColumn]; }
            set { this[DayColumn] = value; }
        }

        [DataMember]
        [Column(OpenTimeColumn)]
        public int OpenTime
        {
            get { return (int)this[OpenTimeColumn]; }
            set { this[OpenTimeColumn] = value; }
        }

        [DataMember]
        [Column(CloseTimeColumn)]
        public int CloseTime
        {
            get { return (int)this[CloseTimeColumn]; }
            set { this[CloseTimeColumn] = value; }
        }

        [Key]
        [DataMember]
        [Column(IdColumn)]
        public long Id
        {
            get { return (long)this[IdColumn]; }
            set { this[IdColumn] = value; }
        }
    }

When you want to use the new entity in a service, the process is straightforward. As described earlier, you create a new service as a derived IRequestHandler. Then either use or return the new entity. The following example shows how to read the entity from the database and return it as part of the response.

    private GetStoreHoursDataResponse GetStoreDayHours(GetStoreHoursDataRequest request)
    {
        ThrowIf.Null(request, "request");
        using (DatabaseContext databaseContext = new DatabaseContext(request.RequestContext))
        {
            var query = new SqlPagedQuery(request.QueryResultSettings)
            {
                DatabaseSchema = "crt",
                Select = new ColumnSet("DAY", "OPENTIME", "CLOSINGTIME", "RECID"),
                From = "ISVRETAILSTOREHOURSVIEW",
                Where = "STORENUMBER = @storeNumber",
            };

            query.Parameters["@storeNumber"] = request.StoreNumber;
            return new GetStoreHoursDataResponse(databaseContext.ReadEntity(query));
        }
    }

For the preceding example, the CRT runtime engine automatically makes a query to the channel database via the registered data adapter. It queries a type that has the name **crt.ISVRetailStoreHoursView**, and generates a **where** clause and columns as specified in the code. The customizer is responsible for providing the SQL objects as part of the customization.

### Adding pre-triggers and post-triggers for a specific request

In some cases, some processing must be done before or after a request is handled. There are two hooks that can be used to run additional code. These hooks are called pre-triggers and post-triggers. Follow these steps to create new triggers and associate them with a request.

1.  Create a new trigger class that implements IRequestTrigger.

        public class GetCrossLoyaltyCardRequestTrigger : IRequestTrigger

2.  In the **IRequest.SupportedRequestTypes** property, return the list of requests that this trigger should be run for.

        public IEnumerable SupportedRequestTypes
        {
            get
            {
                return new[] { typeof(GetCrossLoyaltyCardRequest) };
            }
        }

3.  Implement the functions that are called before and after the request.

        void OnExecuted(Request request, Response response);
        void OnExecuting(Request request);

4.  Register the class in the commerceRuntime.Config file.

## Retail Server extensibility scenarios
### Adding a new ODATA action to an existing controller

In the easiest scenario, you must add a new application programming interface (API) for a slightly different use case. To make this scenario work, you can add the new action through inheritance. For any changes to the APIs to Retail Server, you must follow these steps.

1.  Implement the new action or controller.
2.  Override the requirements of the model factory to add the new corresponding metadata.

The following example, which is taken from the Retail SDK, shows how to extend an existing controller so that it has a POST action.

    public class MyCustomersController : CustomersController
    {
        [HttpPost]
        [CommerceAuthorization(AllowedRetailRoles = new string[] { CommerceRoles.Customer, CommerceRoles.Employee })]
        public decimal GetCrossLoyaltyCardDiscountAction(ODataActionParameters parameters)
        {
            if (parameters == null)
            {
                throw new ArgumentNullException("parameters");
            }

            var runtime = CommerceRuntimeManager.CreateRuntime(this.CommercePrincipal);
            string loyaltyCardNumber = (string)parameters["LoyaltyCardNumber"];

            GetCrossLoyaltyCardResponse resp = runtime.Execute(new GetCrossLoyaltyCardRequest(loyaltyCardNumber), null);

            string logMessage = "GetCrossLoyaltyCardAction successfully handled with card number '{0}'. Returned discount '{1}'.";
            RetailLogger.Log.ExtendedInformationalEvent(logMessage, loyaltyCardNumber, resp.Discount.ToString());
            return resp.Discount;
        }
    }

Next, override the model factory.

    [Export(typeof(IEdmModelFactory))]
    [ComVisible(false)]
    public class CustomizedEdmModelFactory : CommerceModelFactory
    {
        protected override void BuildActions()
        {
            base.BuildActions();
            var var1 = CommerceModelFactory.BindEntitySetAction("GetCrossLoyaltyCardDiscountAction");
            var1.Parameter("LoyaltyCardNumber");
            var1.Returns();
        }
    }

Before clients can use this new customization, you must adjust the build system to generate the Retail Server proxy code for the new model factory. This configuration step is done in the build system. Finally, you must adjust the web.config file. You must complete this step in the packaging project for Retail Server in the SDK. If local tests will be done, you can also optionally complete this step on the local development topology machine that is used for testing.

### Adding a new simple controller for an entity

Suppose that you have a simple entity and require a controller to fetch the data. For an example, see the StoreHours sample in the Retail SDK. A new Retail Server controller makes sense, and all the low-level work is done in the CRT (new entity, request, response, and service). To create a new controller, you derive from CommerceController. An example is shown here. The controller name is important and must match the name of the entity.

    [ComVisible(false)]
    public class StoreHoursController : CommerceController
    {
        public override string ControllerName
        {
            get { return "StoreHours"; }
        }

        [HttpPost]
        [CommerceAuthorization(AllowedRetailRoles = new string[] { CommerceRoles.Anonymous, CommerceRoles.Customer, CommerceRoles.Device, CommerceRoles.Employee })]
        public System.Web.OData.PageResult GetStoreDaysByStore(ODataActionParameters parameters)
        {
            if (parameters == null)
            {
                throw new ArgumentNullException("parameters");
            }

            var runtime = CommerceRuntimeManager.CreateRuntime(this.CommercePrincipal);

            QueryResultSettings queryResultSettings = QueryResultSettings.SingleRecord;
            queryResultSettings.Paging = new PagingInfo(10);

            var request = new GetStoreHoursDataRequest((string)parameters["StoreNumber"]) { QueryResultSettings = queryResultSettings };
            PagedResult hours = runtime.Execute(request, null).DayHours;
            return this.ProcessPagedResults(hours);
        }
    }

For new entities, you must also override the factory’s **BuildEntitySets()** method, as shown in the following example.

    [Export(typeof(IEdmModelFactory))]
    [ComVisible(false)]
    public class CustomizedEdmModelFactory : CommerceModelFactory
    {
        protected override void BuildActions()
        {
            base.BuildActions();
            var action = CommerceModelFactory.BindEntitySetAction("GetStoreDaysByStore");
            action.Parameter("StoreNumber");
            action.ReturnsCollectionFromEntitySet("StoreHours");
        }

        protected override void BuildEntitySets()
        {
            base.BuildEntitySets();
            CommerceModelFactory.BuildEntitySet("StoreHours");
        }
    }

### How to call the new retail server API from MPOS/Cloud POS:

Before calling the new retail server API please make sure you have performed the below steps:

1.  Register your new retail server extension in Retail server web.config file:  &lt;add source="assembly" value="**Your assembly name**" /&gt;
2.  Add the new retail server extension in the Customization.settings file. You can find this file in RetailSdk\\BuildTools&lt;RetailServerLibraryPathForProxyGeneration Condition="'$(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;$(SdkReferencesPath)\\**Your assembly name.dll**&lt;/RetailServerLibraryPathForProxyGeneration&gt; &lt;/PropertyGroup&gt;
3.  Drop both the CRT and Retail server extension dlls into the retail server bin folder. If you have any CRT extension releated to the new retail server api then update that information in commerceRuntime configuration file under retail server bin folder.
4.  &lt;add source="assembly" value="**Your assembly name**" /&gt;
5.  Use inetmgr to browse to the retail server metadata and verify whether your entity is exposed in the xml.
6.  Compile and build the mpos/Cloud POS to regenerate the proxy. During compile mpos regenerates all the entities defined in the retail server metadata, so that you can call the new entities using the commerce context like below:

#### Cross loyalty sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.customers().getCrossLoyaltyCardDiscountAction(loyaltyCardNumber);
    return request.execute<number>();

#### Store hours sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.storeHours().getStoreDaysByStore(storeId);
    return request.execute<Commerce.Proxy.Entities.StoreDayHours[]>();

Please refer the retail SDK POS.Extension.CrossloaylySample and POS.Extension.SToreHoursSample sample projects for more details on how to call the new retail server api in mpos.

