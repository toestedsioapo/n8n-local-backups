n8n Automation Engine & Workflow Backups

A centralized production repository hosting local workflows, AI integrations, and background automation systems built on **n8n**. This ecosystem serves as an operational backbone—streamlining document parsing, scheduling intelligence, event briefings, and background data replication pipelines.



Core Automation Ecosystem

| Workflow File | Infrastructure Stack | Architectural Focus & Purpose |
| :--- | :--- | :--- |
| **`meeting-prep-briefing.json`** | n8n, Google Calendar, Gmail, Gemini AI, Slack | **Executive Intelligence:** Monitors calendars 45–60 mins ahead, pulls corresponding attendee email threads, appends contextual web search data via Gemini LLM, and dispatches unified contextual executive summaries to Slack. |
| **`expense-receipt-logging.json`** | n8n, Gmail, Gemini AI, Google Drive | **Document Parsing System:** Listens for document/receipt attachments via Gmail webhooks, routes binaries via Base64 encodings to Google Drive, and executes deterministic entity extraction through an optimized Gemini Vision/Text schema. |
| **`backup-n8n-workflows-to-github.json`** | n8n, GitHub API, File System | **CI/CD Configuration:** Automated background cron engine tracking local changes, stripping structural credential states, formatting names dynamically, and pushing version-controlled JSON arrays directly into Git. |
| **`flight-finder.json`** | n8n, Web Scraping / APIs, Email | **Asynchronous Monitoring:** Scrapes Google Flights configuration matrixes sequentially to flag real-time price reductions, running data transformations against defined destination trip bounds. |
| **`inbox-triage-daily-briefing.json`** | n8n, IMAP/Gmail, LLM Classifier, Slack | **Information Architecture:** Triages raw inbound communications, filters repetitive spam payloads, evaluates message urgency vectors, and pipes organized daily briefings directly into targeted messaging rooms. |
| **`new-contact-crm-lite-updater.json`** | n8n, Webhooks, CRM Platform / Databases | **Data Pipeline Integrity:** Listens for active incoming contact webhooks, mutates payload formats to enforce casing integrity, standardizes text blocks, and provisions updates flawlessly into internal records databases. |
| **`travel-log-booking.json`** | n8n, Gmail Parser, Airtable / Sheets | **State Machine Logistics:** Intercepts confirmations (hotels, transit tickets, rentals), isolates chronological scheduling data, and catalogs relational database updates automatically. |
| **`travel-consolidated-itinerary.json`** | n8n, Database Engine, Document Exporter | **Data Aggregation:** Queries separate booking rows dynamically, collapses cross-entity nodes into an optimized relational structure, and formats a pristine travel agenda interface. |
| **`calendar-scheduling.json`** | n8n, Google Calendar, Scheduling Logic | **Algorithmic Guardrails:** Protects deep-work focus windows by checking cross-calendar dependencies, assessing collision constraints, and establishing intelligent multi-party invites. |
| **`recurring-status-digest-trello.json`** | n8n, Trello API, Markdown Parser, Slack | **Agile Status Reporting:** Polls active project Kanban cards weekly, maps completion vectors across sprints, converts structural metadata to markdown lists, and relays progress to channels. |



Technical Architecture Highlights

* **Advanced Data Mutators:** Heavy usage of specialized `n8n-nodes-base.code` steps running clean JavaScript primitives to sanitize text nodes, control token allocations, compress scopes, and execute Regex parsing rules safely.
* **Resilient State Management:** Workflows utilize dynamic static memory arrays (`$getWorkflowStaticData`) to preserve identity signatures and prevent duplicate executions during production cycles.
* **Isolated Environment Schemas:** Configurations isolate authorization channels cleanly by striping active system values out of production configuration payloads before backing them up to public visibility.



Deployment & Local Ingestion

To spin up any workflow layout layer inside your local canvas infrastructure:

1. Copy the raw block contents from any desired tracking file in the `workflows/` directory tree.
2. Open an active **n8n canvas workspace** within your web interface session.
3. Click directly onto the browser interactive grid layer and press `Ctrl + V` (or `Cmd + V`).
4. Re-authenticate local API scopes within the generated node interfaces to verify access keys.

Have fun!.
