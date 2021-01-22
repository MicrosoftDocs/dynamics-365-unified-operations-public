# Configuration of Electronic invoicing in RCS

This topic provides you information about the configuration capabilities
of Electronic invoicing add-on.

The most important configuration pillar is allowing you fulfill business
and regulatory requirements of electronic invoices without need of
coding. The configuration capabilities involve either meet file
formatting requirements, as well fulfill communication requirements, in
the scenarios where the electronic invoices need to be sent or submitted
to an external party, over the internet, through web services.

## Electronic reporting

The Electronic reporting supports the Electronic invoicing add-on.

The data model, data model mapping and formats are configurable
components that are created and maintained through Electronic reporting
and utilized along Electronic invoicing add-on, while the Format
designer, from Electronic reporting, is the tool for creating and
maintaining file formats, utilized in the configuration of electronic
invoicing features.

For more information, see [Electronic reporting (ER)
overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting?toc=/dynamics365/finance/toc.json)

## Electronic invoicing features

Electronic invoicing feature, within the Electronic invoicing add-on, is
the element responsible for transforming the electronic document data,
sent by Finance and Supply Chain Management, into electronic invoices,
since the scenarios where the requirement is simply the generation of
the invoice as a digital media, until the scenarios where the
requirement is the submitting the electronic invoice for a digital
approval granted by an external party, through web services, hosted by
the own government tax authority, or by a party accredited by the tax
authority.

### Electronic invoicing feature availability

The availability of electronic invoicing features varies according to
the country/regions. While some are generally available, others are in
preview:

#### Generally available features:

| Country/Region    | Business document                        |
|-------------------|------------------------------------------|
| Egypt             | Sales and Project invoices               |

#### Preview features:

| Country/Region    | Business document                        |
|-------------------|------------------------------------------|
| Austria           | Sales and Project invoices               |
| Belgium           | Sales and Project invoices               |
| Brazil            | Fiscal document model 55 (NF-e)          |
|                   | Service fiscal document ABRASF (NFS-e)   |
|                   | Service fiscal document São Paulo city   |
| Denmark           | Sales and Project invoices               |
| Estonia           | Sales and Project invoices               |
| Finland           | Sales and Project invoices               |
| France            | Sales and Project invoices               |
| Germany           | Sales and Project invoices               |
| Italy             | Sales and Project invoices               |
| Mexico            | CFDI invoice                             |
| Netherlands       | Sales and Project invoices               |
| Norway            | Sales and Project invoices               |
| Spain             | Sales and Project invoices               |
| Europe            | PEPPOL Sales and Project invoices        |

### Electronic invoicing feature configurable components

Electronic invoicing features are composed by the following groups of
configurable components:

-   Formats:

    They allow configuring the "what" the Electronic invoicing add-on
    must generate during the processing of an electronic invoicing
    feature, that transforms the electronic document that was submitted
    by Finance and Supply Chain Management, into electronic invoices.

-   Actions:

    They allow configuring the "how" the Electronic invoicing add-on
    must generate during the processing of an electronic invoicing
    feature, that transform the electronic document that was submitted
    by Finance and Supply Chain Management, into electronic invoices.

-   Applicability rules:

    They allow configuring the "context" the Electronic invoicing add-on
    must consider for processing of an electronic invoicing feature.

-   Variables:

    They allow configuring the variables that can be used to support the
    construction of the configuration logic, they can work as input of
    values for accomplishing a specific action, or for exchanging of
    values between the Finance and Supply Chain Management client and
    the Electronic invoicing add-on.

-   Electronic document model mapping:

    They allow configuring the Electronic reporting model mapping, which
    defines the data mapping of the abstract invoice that Finance and
    Supply Chain Management integrates to Electronic invoicing add-on,
    when the submission of electronic documents is performed.

-   Invoice context model:

    They allow configuring the Electronic reporting invoice context
    model, which allows defining what is the context of the electronic
    invoicing feature.

-   Response types

    They allow configuring the "what" the Electronic invoicing add-on
    must update back in the Finance and Supply Chain Management client
    as the result of the processing of the electronic invoice.

### Formats

### …

### Actions

| Action                                        | Description                                                 | Availability                |
|-----------------------------------------------|-------------------------------------------------------------|-----------------------------|
| Transform document                            | Generates a file following a given ER format configuration  | Preview                     |
| Transform document from OData source          |                                                             | Preview                     |
| Sign xml document                             | Applies a digital signature in the XML file                 | Preview                     |
| Sign json document for Egyptian Tax Authority | Applies a digital signature in a JSON file                  | Preview                     |
| Egyptian Tax Authority REST client            | Submits an e-invoice to Egyptian tax authority web service  | Preview                     |
| Call Brazilian SEFAZ Service                  | Submits an e-invoice to Brazilian tax authority web service | Preview                     |
| Call Mexican PAC Service                      | Submits an e-invoice to PAC web services                    | Preview                     |
| Process response                              | Analyze the web service response                            | Preview                     |
| Use MS Power Automate                         |                                                             | Preview                     |
| File store action name                        |                                                             | Preview                     |

### Applicability rules

### Variables

### Electronic document model mapping

### Invoice context model

### Response types

## Configuration providers

The Configuration providers are the providers from where you get the
Electronic invoicing features, as well their Electronic reporting
components, such as model mapping, format configuration, context model,
and so on.

When the Configuration provider publishes an electronic invoicing
feature, and any of its Electronic reporting components, it does by
publishing in the Global repository associated to it, from where other
organizations can download.

Before starting the configuration of Electronic invoicing features
through RCS, you must configure your own organization as a configuration
provider. Thus, make sure the configuration providers are configured in
Electronic reporting module. For information about how to set a provider
to **Active**, see [Create configuration providers and mark them as
active](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11).

## Listing Electronic invoicing features in Global repository

You can browse all available electronic invoicing features available in
the Global repository for a given Configuration provider, by
synchronizing your RCS. After you synchronize, the list of available
electronic invoicing features is refreshed and you can discover the
features to use listed by Configuration provider.

## Importing Electronic invoicing feature

You can only use or configure Electronic invoicing features imported to
the instance of your organization in RCS.

If you choose using some of the electronic invoicing feature published
by some of the Configuration providers, the importation of Electronic
invoicing features is the first step, because it creates a local copy of
the selected electronic invoicing feature, as well all its Electronic
reporting components, from which you can either start using, configure
or customize.

## Creating Electronic invoicing feature

The Electronic invoicing features can be either created from scratch, as
well it can be created deriving from another Electronic invoicing
feature.

When it is created by deriving, it inherits all configurations from the
original Electronic invoicing feature, while when it is created from the
scratch, it requires manually addition of the Electronic reporting
components such as Feature version configurations, as well other
configurations, such as Feature version setup and Application setup.

## Electronic invoicing feature version

The electronic invoicing features are versioned, when a new version is
created, the version number is automatically incremented, and it is
possible to define an effective from date.

The feature version follows a life cycle up to 3 status:

-   Draft:

    When the feature version is on Draft status, it is possible to edit
    the configuration attributes of the feature version, as well editing
    any of its artifacts, such as file format configurations.

-   Complete:

    When the feature version is on Complete status, means the feature
    version has been published into the Global repository associated to
    your organization. At this point, it is not allowed editing neither
    the feature version, nor none of its Electronic reporting
    components.

-   Published:

    When the feature version is on Published status, means the feature
    version has been published into the Electronic invoicing add-on. At
    this point, it is not allowed editing neither the feature version,
    nor none of its Electronic reporting components.

### Feature configurations

The Feature configurations holds all Electronic reporting format
configurations the electronic invoicing feature uses. All the electronic
files the electronic invoicing feature manipulates along the processing
come from the format configurations added to this section of the
electronic invoicing feature.

It is also through Feature configuration you have access to the Format
designer, the Electronic reporting tool used to create the format
configurations.

### Feature setup

Used in combination with the Feature configurations, each Feature setup
encapsulates a set of Actions, Applicability rules and Variables that
provides an expected behavior for the Electronic invoicing feature to
fulfill a specific requirement of the electronic invoice.

### Application setup

The Application setup must be associated to a Connected application
previously created.

Through Application setup, you can configure the part of the electronic
invoicing feature that must be accomplished in Finance and Supply Chain
Management. At least 3 configurable components are mandatory,
independent of the electronic invoicing feature:

-   Table name:

    It is the entity in Finance and Supply Chain Management that holds
    the posted invoices, and over which the electronic invoicing feature
    is based.

-   Context:

    It is the name of the invoice context model configured through
    Electronic reporting.

-   Business document mapping:

    It is the name of the invoice mapping model configured through
    Electronic reporting.

Important: the configuration entered under application setup can be
viewed in Finance and Supply Chain Management on **Organization
administration &gt; Setup &gt; Electronic document parameter** form,
**Electronic document** tab, after running Deploy command, with option
to deploy to connected application.

### Deploy

The Deploy is the command executed in RCS that effectively publishes the
Electronic invoicing feature version. It can have up to targets:

-   Service environment:

    When the target of the deploy is the Service environment, the
    Electronic invoicing feature version is published into the Service
    environment. After that, the Electronic invoicing add-on is ready to
    receive the submissions of electronic documents sent by Finance and
    Supply Chain Management and process accordingly.

-   Connected application:

    When the target of the deploy is the Connected application, the
    configuration given by the Application setup is written in the
    Finance and Supply Chain Management instance that was previously
    associated to it.

Only Electronic invoicing feature versions with status Completed can be
deployed, either to a service environment as well to a connected
application.

### Undeploy

The Undeploy is the command executed in RCS that removes a specific
Electronic invoicing feature version from a Service environment in
Electronic invoicing add-on.

Important: the Undeploy works only for Service environments, removing
Electronic invoicing feature versions. It does not remove the feature
version from the Connected applications.

### Rebase

When an Electronic invoicing feature is created derived from another
Electronic invoicing feature imported from a Configuration provider, the
Rebase action updates the derived Electronic invoicing feature with the
updates introduced in the original Electronic invoicing feature.

## Additional resources
- [Issuing of electronic invoices in Finance and Supply Chain Management](e-invoicing-issuing-electronic-invoices-in-finance-and-supply-chain-management.md)
