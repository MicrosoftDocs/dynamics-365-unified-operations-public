Access and security
===================

The **Cost control** workspace is a central point were managers can see
performance of their cost objects. This means that the end users of Cost
accounting can consume Cost accounting data without being cost accountants. For
security reasons, the end users should only be allowed to see the Cost
accounting data that is related to the specific cost objects for which they are
responsible.

There are four unique roles in Cost accounting.

| Role name               | License      |
|-------------------------|--------------|
| Cost accounting manager | Activity     |
| Cost accountant         | Operations   |
| Cost accountant clerk   | Operations   |
| Cost object controller  | Team members |

If a **Cost object controller** role is assigned to an end user, the user can:

-   Access the **Cost control** workspace.

    -   Drill through and have view access to the pages that support the
        drill-through experience.

-   Access the **Cost control** workspace for Microsoft Dynamics 365 for Finance
    and Operations mobile application.

**Note:**

The **Cost object** controller role does control which cost objects the user can
access and see data for. Row-level security is obtained via **Dimension
hierarchies** and **Access list hierarchy**.

Here is an example of a dimension hierarchy.

Dimension hierarchy details

| Dimension hierarchy name | Dimension    | Dimension hierarchy type name      | Access list hierarchy |
|--------------------------|--------------|------------------------------------|-----------------------|
| Organization             | Cost centers | Dimension classification hierarchy | **Yes**               |

You can use the **Users** FastTab in the hierarchy designer to insert one or
several User IDs on each node.

|              | **Users**        | Dimension member ranges |                     |
|--------------|------------------|-------------------------|---------------------|
| Nodes        | User ID          | From dimension member   | To dimension member |
| Organization | Benjamin, Claire |                         |                     |
|              | April            |                         |                     |
|              | Alicia           | CC002                   | CC003               |
|              |                  | CC007                   | CC007               |
|              | Arnie            | CC001                   | CC001               |
|              | David            |                         |                     |
|              | Ellen            | CC005                   | CC005               |
|              | Chris            | CC006                   | CC006               |

>   Admin

>   Finance

>   HR

>   Production

>   Packaging

>   Assembly

**Note:**

Cost accountants should be assigned to the top level of the hierarchy so they
can see all entries in Cost accounting.

Before the **Access list hierarchy** and its security settings can be applied,
the parameter **Enable view access for cost object dimension members** on **Cost
accounting/Setup/Parameters/General** must be set to **Yes**.

The **Access list hierarchy** settings are used to control data displayed in
following areas.

-   **Cost control** workspace (Client)

    -   Data on the pages that are used to drill through

-   **Cost control** workspace (Mobile application)

    -   Balances in cards

-   Microsoft Power BI

    -   Data displayed in Power BI visualizations

    -   Data Power BI visualizations embedded into Microsoft Dynamics 365 for
        Finance and Operations client

**Note:**

Before **Access list hierarchy** can affect data in Power BI, **Access list
hierarchy** and **Row-level security** in Power

BI need to be paired.

Additional links

<https://ax.help.dynamics.com/en/wiki/setting-up-security-for-cost-accounting-content-for-power-bi/>

Please read and learn more about: *Dimension hierarchies*

Why only one role?

User names in demo data?
