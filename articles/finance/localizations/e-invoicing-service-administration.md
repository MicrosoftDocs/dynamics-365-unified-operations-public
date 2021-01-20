# Service administration

This topic provides you information about the components related to the
Electronic invoicing add-on administration, explaining the
elements that need to be configured for the correct functioning
of the service.

## Azure

The Electronic invoicing add-on does not hold any customer information. All data and records that belong to the customers are hold on the customer's storage account associated to the customer Azure subscription, while the digital certificates owned by the customer are also hold on Azure Key vault.

## Microsoft Dynamics 365 Regulatory Configuration Services (RCS)

The Microsoft Dynamics 365 Regulatory Configuration Services (RCS) is the interface for
configuration of the Electronic invoicing add-on. The resources, such as
Environments and Electronic invoicing features are created, maintained,
and hosted in the RCS, and when they are ready, they are published to
the Electronic invoicing add-on service.

For more information about RCS, see [Regulatory Configuration Services (RCS) - Globalization features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-globalization-feature)

### Integration with Electronic invoicing add-on

Before start using RCS for configuring electronic invoices, it must be
configured to allow the communication with Electronic invoicing add-on.

The configuration must be done in **Electronic reporting parameters**
form, on **Electronic invoicing add-on** tab:

#### Service endpoint

It is the URL of the Electronic invoicing add-on:

-   <https://electronicinvoicinglocal.wus2-il100.gateway.test.island.powerapps.com/>

#### Application ID

It is the ID of the Electronic invoicing add-on application. In this
case, the value is fixed:

-   0cdb527f-a8d1-4bf8-9436-b352c68682b2

#### LCS environment ID

It is the ID of your LCS subscription from your organization.

### Service environments

The Service environments are logical partitions created in RCS for
electronic invoicing service. They exist to support the execution of the
electronic invoicing features within service, assuring not only the
management of the governance, granting the permissions to users to
generate electronic invoices through the services, but also allowing the
process of generation of electronic invoices, consuming the customer's
digital certificates stored in the customer's Azure account, and access
the blob storage for holding the customer's transactional data.

Customers can create as many service environments as they want, and they
are independent of each other. And the instances of Finance and Supply
Chain Management can access any of those environments.

#### Service environment status

The Service environments can have up to 3 status:

-   Not published:

    When the environment is just created, but not published yet.

-   Published:

    When the environment was published to electronic invoicing service.

-   Changed:

    When a published environment suffers any changes on some of its
    attributes, but the environment together the updates was not
    published yet.

#### Customer secrets

An important attribute of the service environments are the Customer
secrets. The secrets for the customer digital certificates as well for
the customer storage account must be created in the customer's Azure
subscription. It is through the secrets the Electronic invoicing add-on
consumes the customer digital certificate and accesses the customer
storage account in Azure.  For more information, see [Create Azure
Storage Account and Key
Vault](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-create-azure-storage-account-key-vault).

##### Key vault secret

##### Chain of certificates

##### Storage SAS

#### Users

Each service environment must have listed the users that can connect
from Finance and Supply Chain Management in the Electronic invoicing
add-on.

#### Publish

The Service environments must be Published to the electronic invoicing
service to be used. Only after publishing, the environment can be
accessed by Finance and Supply Chain Management. Even after an update of
any of the environment's attribute, it must be published in order the
changes take effect on the electronic invoicing service.

### Connected applications

The Connected applications are the instances of Finance and Supply Chain
Management you may want to reach through RCS. Besides the application
URL, its tenant, it also contains the credentials to allow RCS to
connect to this environment.

Through the Connected applications, you can configure the part of the
electronic invoicing feature that must be accomplished in Finance and
Supply Chain Management to make the whole electronic invoicing feature
works.

## Finance and Supply Chain Management

### Integration with Electronic invoicing add-on

Before start using Finance and Supply Chain Management for issuing of
electronic invoices through the Electronic invoicing add-on, it must be
configured to allow the communication with the service.

#### Electronic Invoicing add-on integration feature

To enable Finance and Supply Chain Management communicating with
Electronic invoicing add-on, the following feature must be enabled
through Feature management workspace:

-   Electronic Invoicing add-on integration.

#### Service endpoint

The service endpoint is the URL where the Electronic invoicing add-on
can be found. It must be configured in Finance and Supply Chain
Management to allow it communicating with the service for issuing of
electronic invoices.

In the **Organization administration &gt; Setup &gt; Electronic document
parameter** form, on **Submission services** tab, the Electronic
invoicing add-on URL must be entered as:

<https://electronicinvoicinglocal.wus2-il100.gateway.test.island.powerapps.com/>

#### Environments

The Environment name entered in Finance and Supply Chain Management
refers to the name of the environment created in RCS and published into
the Electronic invoicing add-on.

It must be configured in the **Organization administration &gt; Setup
&gt; Electronic document parameter** form, on tab Submission services,
so that every request for issuing electronic invoices contains the
environment where the Electronic invoicing add-on can determine which
electronic invoicing feature must process the request.

