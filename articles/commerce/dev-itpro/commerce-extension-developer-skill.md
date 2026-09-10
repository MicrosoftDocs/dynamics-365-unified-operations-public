---
title: Commerce extension developer skill (preview)
description: Learn how the Commerce extension developer skill helps developers plan, scaffold, and build Dynamics 365 Commerce extensions with SDK patterns and templates.
author: anvenkat
ms.date: 09/10/2026
ms.topic: overview
audience: Developer
ms.author: anvenkat
ms.reviewer: mirao
ms.search.region: Global
---
# Commerce extension developer skill (preview)

The Commerce extension developer skill is an AI-powered agent skill included with the Dynamics 365 Commerce SDK. It helps developers move from a functional requirement to a buildable Store Commerce extension by using the Commerce SDK's documented patterns, scaffolders, and templates.

You can use the skill from an agent CLI session, such as GitHub Copilot CLI or Claude Code. It provides guidance and generates artifacts, but it doesn't replace developer judgment, code review, testing, or organizational approval.

> [!WARNING]
> This feature is an AI-powered preview feature. Generated responses, code, SQL, project files, and configuration can be inaccurate, incomplete, or inappropriate for your scenario. A qualified developer must review and validate every output before it's built, committed, deployed, or used to modify a system.

## Preview information

- Preview version: Commerce SDK version 9.59.
- End of preview: Commerce SDK version 9.60.
- Functionality, licensing, availability, and data-handling practices can change before general availability, and the preview might never reach general availability.
- The preview is provided for evaluation purposes and isn't covered by production-level support or service-level agreements.

## What the skill helps you do

The skill supports the early implementation stages of a Commerce extension project. Use it to:

- Classify a requirement into the appropriate Commerce extension surface.
- Select documented SDK patterns that fit the requirement.
- Scaffold a solution from SDK templates.
- Apply documented patterns while writing extension code.
- Identify configuration and project wiring that the extension requires.
- Produce a plan for related Headquarters (finance and operations) changes.
- Help install the extension for local testing and troubleshoot issues when it doesn't work as expected.
- Help you reach a buildable solution that you can inspect, test, and refine.

The skill doesn't promise that a generated solution is ready for production use. It helps organize the work and apply first-party guidance consistently, while the developer remains responsible for the final design and implementation.

## Extension surfaces covered by the skill

A Store Commerce customization can span several components. The skill helps classify a requirement across the following extension types:

| Extension type | Typical responsibility | Examples of work the skill can help plan |
| -------------- | ---------------------- | ---------------------------------------- |
| Point of sale (POS) | User interface and client-side retail workflows | Add a POS operation, add a control, respond to a POS event, or connect a user action to a Commerce API. |
| Commerce runtime (CRT) | Business logic executed by the Commerce Runtime | Add a request and response, implement a handler, validate business rules, or extend a Commerce workflow. |
| Hardware station | Integration with supported or custom peripherals | Plan an extension for a device or peripheral interaction and identify the required project structure. |
| Channel database | Data extensions used by Commerce channels | Identify when channel data is required and plan the related schema or data access work. |
| Headquarters (finance and operations) | Authoring and configuration that supports the extension | Produce a plan for required Headquarters changes, configuration, or data distribution. |

A requirement might involve more than one surface. For example, a new POS experience can require a POS extension for the user interaction, a CRT extension for business logic, and Headquarters changes for configuration or data. The skill helps identify those relationships before you begin implementation.

## How the skill works

The skill uses a staged workflow so that a developer can review the design before code is generated.

### Step 1: Describe the functional requirement

Start with the business outcome and the behavior you want to add. Include the user action, the expected result, and any data or business rules that matter.

For example:

```Add a POS button that shows the customer's loyalty tier. The button should be available when a customer is attached to the transaction and should show a message when no customer is attached.```

When you state the requirement this way, it gives the agent enough context to reason about the user experience, the required data, and the likely extension boundaries.

### Step 2: Answer clarifying questions

The skill reviews the requirement and asks clarifying questions when details are missing or ambiguous. Answer these questions before proceeding so that the skill has enough context to classify the extension boundary.

### Step 3: Classify the extension boundary

The skill evaluates the requirement against the Commerce extension surfaces. It can explain whether the work belongs in POS, CRT, hardware station, channel database, Headquarters, or a combination of these areas.

This step is important because placing business logic in the wrong layer can make an extension harder to maintain and can create unnecessary coupling. The skill should explain the proposed boundary and identify questions that still need an answer before implementation.

### Step 4: Select SDK patterns and templates

After classifying the requirement, the skill uses the Commerce SDK content available in the skill bundle. This content includes pattern documentation, templates, and a local scaffolding script. The goal is to guide implementation towards the same structures and conventions used by the SDK instead of starting with an unrelated project layout.

The skill can identify the likely project types, files, handlers, requests, responses, controls, and configuration aspects that are relevant to the requirement. The developer should confirm that the selected pattern matches the SDK version used by the solution.

### Step 5: Scaffold the solution

The skill can use the SDK's scaffolding approach to create the initial solution structure. Scaffolding might include project files, source folders, configuration, and references needed for the selected extension type.

The bundled `scaffold-solution.ps1` script is local-only. It writes files into the workspace and doesn't make network calls. Review the generated file list before continuing, particularly when you're working in an existing solution.

### Step 6: Generate and wire the extension code

After the extension boundary and project structure are established, the skill can generate implementation artifacts based on the selected SDK patterns. Depending on the requirement, this generation can include POS code, CRT requests and handlers, hardware station components, channel database work, and project or configuration changes.

Treat the generated code as a starting point. Verify API names, namespaces, constructor signatures, contracts, request and response types, and version-specific behavior against the official Commerce documentation and the SDK packages referenced by your solution.

### Step 7: Identify Headquarters dependencies

Some extension requirements can't be completed in the Commerce projects alone. They can depend on Headquarters configuration, data entities, distribution, or feature setup.

The skill can produce a plan for required Headquarters changes. This plan is advisory - It doesn't authorize changes to a finance and operations environment. The teams responsible for Headquarters development and configuration should review it.

### Step 8: Build and validate with a developer in the loop

The final output is a buildable solution that a developer can restore, compile, test, and inspect. Run the normal validation steps for your repository and SDK version. Review generated files and diffs, validate security and error handling, and test the extension in an appropriate development environment before you commit or deploy it.

## Prerequisites

Before you use the skill, ensure that you:

- Have an existing Commerce SDK sample or solution that references the Commerce SDK packages.
- Have one of the following agent CLIs installed and signed in:
  - GitHub Copilot CLI: Run `copilot` once to confirm that it launches.
  - Claude Code: Run `claude` once to confirm that it launches.
- Can restore and build the solution with the SDK version used by the repository.
- Understand your organization's policies for sending repository context and prompts to the host AI CLI.

## Set up the skill

### Initialize the skill files in a solution

Run the following commands from the root of an existing solution that references Commerce SDK packages:

```powershell
dotnet restore <Solution>.sln
dotnet msbuild <Solution>.sln /t:InitDev
```

The `InitDev` target copies the skill's knowledge base and entry points (such as `AGENTS.md`, `.github/copilot-instructions.md`, and the agent-specific skill files) into the root of the repository. The marketplace and the plugin it contains aren't copied into the repository; they stay in the restored NuGet package. The two settings files, `.github/copilot/settings.json` and `.claude/settings.json`, point at them by absolute path. Because that path is machine and version-specific, don't commit these two settings files to the source control; add them to `.gitignore` instead.

Run `dotnet msbuild <Solution>.sln /t:InitDev` again after an SDK version update so that the solution receives the updated skill content and the settings files point at the newly restored package. Restoring a new SDK version on its own doesn't refresh the copied files or the settings files.

### Install the skill in GitHub Copilot CLI

From the repository root, install the plugin once:

```bash
copilot plugin install commerce-ext-dev@commerce-sdk-skills
```

The bundled `.github/copilot/settings.json` file registers the marketplace, but you must still install the plugin explicitly. The agent CLI doesn't automatically install a repository-provided plugin.

### Install the skill in Claude Code

Run `claude` from the repository root, enter `/plugin`, and install **commerce-ext-dev** from the **commerce-sdk-skills** marketplace.

## Use the skill

1. Open a terminal at the root of the Commerce SDK solution.
1. Start `copilot` or `claude`.
1. Use `/plugin` to confirm that `commerce-ext-dev` is installed.
1. Describe the extension requirement in functional terms.
1. Review the proposed extension boundary and implementation plan.
1. Approve only the changes you understand and want the agent to make.
1. Review the generated files and configuration changes.
1. Restore, build, and test the solution by using your normal development process.
1. Obtain the required code reviews and approvals before committing or deploying.

For example, you can ask:

```Add a POS button that shows the customer's loyalty tier. Identify the required Commerce extension surfaces, scaffold the solution using the SDK pattern, and explain any Headquarters changes before generating code.```

If a requirement is ambiguous, provide more context such as the target Commerce SDK version, the user flow, whether the behavior must work offline, the required data source, and the environments in which the extension runs.

## Data handling and permissions

The skill is content loaded into the host agent CLI. It consists of pattern documentation, templates, and a local scaffolding script. By itself, the skill doesn't transmit, store, log, retain, or add telemetry for your data, and the local scaffolder makes no external network calls.

The host agent CLI performs AI processing. GitHub Copilot CLI or Claude Code can send prompts, repository context, and skill content to the AI model. The data handling, retention, and privacy terms of that host tool govern this data.

The agent operates with the file-system and command permissions granted to it in the CLI session. Grant only the permissions appropriate for your evaluation and development workflow. Don't provide data classified above the level permitted by your host CLI and organizational policy.

## Limitations

The preview has the following known limitations:

- Generated code, SQL, configuration, and project wiring can be incorrect or incomplete.
- Coverage is limited to documented Store Commerce extension patterns. The skill might handle novel or undocumented scenarios incorrectly or not handle them at all.
- The skill is validated primarily for English language interaction.
- Generated solutions target the SDK version range specified in `repo.props`. A restore or build can fail if your package feed doesn't have that version.
- The skill doesn't remove the need for security review, code review, testing, release management, or operational approval.

## Human review requirements

AI-generated recommendations and artifacts are advisory only. A qualified developer must review, test, and approve each output before:

- Building or packaging it.
- Committing it to source control.
- Deploying it to an environment.
- Using it to modify an existing Commerce or Headquarters system.
- Using it to make a business, financial, security, legal, or regulatory decision.

Pay particular attention to generated code, SQL, project configuration, deployment artifacts, and proposed Headquarters changes.

## Feedback and incident reporting

If the skill produces incorrect, unsafe, or harmful output, report the issue so that the team can investigate and improve the experience. Open an issue in the [Dynamics365Commerce.InStore GitHub repository](https://github.com/microsoft/Dynamics365Commerce.InStore) and include enough non-sensitive information to reproduce the problem.
