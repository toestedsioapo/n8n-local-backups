# n8n Automation Engine & Workflow Backups

![n8n](https://img.shields.io/badge/built%20with-n8n-EA4B71)
![Workflows](https://img.shields.io/badge/workflows-15-informational)
![License: MIT](https://img.shields.io/badge/license-MIT-blue)

A collection of **n8n** workflows, AI integrations and background automations built for Executive Assistant / Virtual Assistant work: inbox and calendar management, meeting preparation and follow-through, travel logistics, client onboarding, invoicing and automated workflow backups.

**Author:** Marvin Liemor ([@toestedsioapo](https://github.com/toestedsioapo))

---

## Workflows

### Meetings & scheduling

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`meeting-prep-briefing.json`](workflows/meeting-prep-briefing.json) | Google Calendar, Gmail, Gemini AI, Slack | **Executive Intelligence:** Watches the calendar 45–60 minutes ahead, pulls related attendee email threads, adds web context via Gemini, and sends a single meeting summary to Slack. |
| [`meeting-notes-action-items.json`](workflows/meeting-notes-action-items.json) | Google Drive, Gemini AI, Gmail, Slack, Trello | **Meeting Follow-Through:** Picks up new meeting notes or transcripts saved as Google Docs, extracts the summary, decisions and action items with Gemini, saves a recap email as a Gmail draft, posts the recap to Slack, and creates a Trello card for each action item. |
| [`meeting-time-finder.json`](workflows/meeting-time-finder.json) | n8n Forms, Google Calendar, Slack | **Time-Zone Meeting Finder:** A form takes attendees and their time zones, checks everyone's free/busy, ranks slots by how fair they are across time zones, lets you pick one of three options and books it with a Google Meet link. |
| [`calendar-scheduling.json`](workflows/calendar-scheduling.json) | Google Calendar | **Scheduling Guardrails:** Protects focus blocks, checks for conflicts across calendars, and sends multi-party invites. |

### Inbox & communication

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`inbox-triage-daily-briefing.json`](workflows/inbox-triage-daily-briefing.json) | Gmail, LLM classifier, Slack | **Inbox Triage:** Classifies incoming mail by urgency, filters noise, and posts an organized daily briefing to Slack. |
| [`follow-up-tracker.json`](workflows/follow-up-tracker.json) | Gmail, Slack | **Follow-Up Tracker:** Watches emails labeled *Awaiting reply*. Clears the label when a reply arrives, drafts a polite follow-up in the same thread after a set number of days, and posts a daily digest of what's still waiting. |
| [`recurring-status-digest-trello.json`](workflows/recurring-status-digest-trello.json) | Trello API, Slack | **Status Reporting:** Polls Trello cards weekly, summarizes progress as Markdown, and posts the digest to Slack. |

### Clients, finance & CRM

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`client-onboarding-kit.json`](workflows/client-onboarding-kit.json) | n8n Forms, Google Drive, Trello, Google Calendar, Gmail, Sheets, Slack | **Client Onboarding Kit:** One form submission creates the client's Drive folder and subfolders, a Trello board with an onboarding checklist, a kickoff hold on the calendar, a welcome email draft and an optional row in a clients sheet. |
| [`invoice-payment-reminders.json`](workflows/invoice-payment-reminders.json) | Google Sheets, Gmail, Slack | **Invoice Reminders:** Reads an invoices sheet daily and drafts staged reminders (heads-up before the due date, then overdue, firm and final notices), records each reminder in the sheet so none repeat, and posts unpaid totals to Slack. |
| [`expense-receipt-logging.json`](workflows/expense-receipt-logging.json) | Gmail, Gemini AI, Google Drive, Sheets | **Document Parsing:** Detects receipt attachments in Gmail, stores the files in Google Drive, and extracts structured expense fields with a Gemini schema. |
| [`new-contact-crm-lite-updater.json`](workflows/new-contact-crm-lite-updater.json) | Webhooks, Sheets / database | **Contact Pipeline:** Receives new-contact webhooks, normalizes names and casing, and updates the contact records. |

### Travel

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`flight-finder.json`](workflows/flight-finder.json) | Google Flights, Email | **Price Monitoring:** Checks Google Flights for configured routes and dates and flags price drops. |
| [`travel-log-booking.json`](workflows/travel-log-booking.json) | Gmail parser, Airtable / Sheets | **Booking Logger:** Captures hotel, flight, and rental confirmations from email and logs them in order. |
| [`travel-consolidated-itinerary.json`](workflows/travel-consolidated-itinerary.json) | Sheets / database, document export | **Itinerary Builder:** Combines logged bookings into a single, clean travel itinerary. |

### Operations

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`backup-n8n-workflows-to-github.json`](workflows/backup-n8n-workflows-to-github.json) | n8n API, GitHub API | **Workflow Backups:** Scheduled job that exports local workflows and commits the JSON to this repository. |

## Design Principles

- **Human in the loop for anything outbound:** emails to clients and contacts are saved as **Gmail drafts**, never sent automatically. Calendar invites are only sent after you pick a slot in a form.
- **Config at the top:** every Code node starts with a `CONFIG` block (names, time zones, thresholds, IDs), so a workflow can be adapted without reading the logic.
- **Duplicate protection:** `$getWorkflowStaticData` and sheet columns record what has already been processed, so the same item is never handled twice.
- **Defensive AI parsing:** Gemini calls use a JSON response schema, and every response is validated. Anything that can't be parsed is flagged in Slack instead of failing silently.
- **Credential-safe exports:** workflow files only reference credentials by name and ID. No API keys or tokens are stored in this repository.

## Importing a Workflow

1. Open any file in the [`workflows/`](workflows) folder and copy its raw contents.
2. Open a workflow canvas in your n8n instance.
3. Click the canvas and paste with `Ctrl + V` (or `Cmd + V`).
4. Reconnect your own credentials (Gmail, Google Calendar, Google Drive, Google Sheets, Slack, Trello, Gemini, GitHub) on each node.
5. Read the **Setup Notes** sticky note on the canvas and fill in its `CONFIG` values before activating.

Form-based workflows run at `http://localhost:5678/form/<path>` once active (`find-meeting-time`, `client-onboarding`).

## Templates

| File | Used by |
| :--- | :--- |
| [`templates/invoices-template.csv`](templates/invoices-template.csv) | `invoice-payment-reminders.json`: import into Google Sheets as a tab named **Invoices**. |

> Email addresses and IDs inside the workflows are sample or placeholder values. Replace them with your own.

## Roadmap

- [ ] Add a screenshot of each workflow canvas
- [ ] Document required credentials per workflow
- [ ] Parse incoming invoices from Gmail into the invoices sheet with Gemini
- [x] Track changes in [`CHANGELOG.md`](CHANGELOG.md)

## Contributing

Issues and suggestions are welcome. Open an issue or a pull request.

## License

Released under the [MIT License](LICENSE). © 2026 Marvin Liemor.
