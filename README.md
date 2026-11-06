# n8n Automation Engine & Workflow Backups

![n8n](https://img.shields.io/badge/built%20with-n8n-EA4B71)
![License: MIT](https://img.shields.io/badge/license-MIT-blue)

A centralized repository of local **n8n** workflows, AI integrations, and background automations built for Executive Assistant / Virtual Assistant operations — document parsing, scheduling, event briefings, travel logistics, and automated workflow backups.

**Author:** Marvin Liemor ([@toestedsioapo](https://github.com/toestedsioapo))

---

## Core Automation Ecosystem

| Workflow File | Stack | Purpose |
| :--- | :--- | :--- |
| [`meeting-prep-briefing.json`](workflows/meeting-prep-briefing.json) | n8n, Google Calendar, Gmail, Gemini AI, Slack | **Executive Intelligence:** Watches the calendar 45–60 minutes ahead, pulls related attendee email threads, adds web context via Gemini, and sends a single meeting summary to Slack. |
| [`expense-receipt-logging.json`](workflows/expense-receipt-logging.json) | n8n, Gmail, Gemini AI, Google Drive | **Document Parsing:** Detects receipt attachments in Gmail, stores the files in Google Drive, and extracts structured expense fields with a Gemini schema. |
| [`backup-n8n-workflows-to-github.json`](workflows/backup-n8n-workflows-to-github.json) | n8n, GitHub API | **Workflow Backups:** Scheduled job that exports local workflows, strips credential data, normalizes file names, and commits the JSON to this repository. |
| [`flight-finder.json`](workflows/flight-finder.json) | n8n, Google Flights, Email | **Price Monitoring:** Checks Google Flights for configured routes and dates and flags price drops. |
| [`inbox-triage-daily-briefing.json`](workflows/inbox-triage-daily-briefing.json) | n8n, Gmail, LLM classifier, Slack | **Inbox Triage:** Classifies incoming mail by urgency, filters noise, and posts an organized daily briefing to Slack. |
| [`new-contact-crm-lite-updater.json`](workflows/new-contact-crm-lite-updater.json) | n8n, Webhooks, Sheets / database | **Contact Pipeline:** Receives new-contact webhooks, normalizes names and casing, and updates the contact records. |
| [`travel-log-booking.json`](workflows/travel-log-booking.json) | n8n, Gmail parser, Airtable / Sheets | **Booking Logger:** Captures hotel, flight, and rental confirmations from email and logs them in order. |
| [`travel-consolidated-itinerary.json`](workflows/travel-consolidated-itinerary.json) | n8n, Sheets / database, document export | **Itinerary Builder:** Combines logged bookings into a single, clean travel itinerary. |
| [`calendar-scheduling.json`](workflows/calendar-scheduling.json) | n8n, Google Calendar | **Scheduling Guardrails:** Protects focus blocks, checks for conflicts across calendars, and sends multi-party invites. |
| [`recurring-status-digest-trello.json`](workflows/recurring-status-digest-trello.json) | n8n, Trello API, Slack | **Status Reporting:** Polls Trello cards weekly, summarizes progress as Markdown, and posts the digest to Slack. |

## Technical Highlights

- **Code nodes for data cleanup:** `n8n-nodes-base.code` steps in plain JavaScript sanitize text, trim token usage, and apply regex parsing.
- **Duplicate protection:** `$getWorkflowStaticData` stores processed IDs so the same item isn't handled twice.
- **Credential-safe exports:** Credentials are stripped from workflow JSON before it is backed up to a public repository.

## Importing a Workflow

1. Open any file in the [`workflows/`](workflows) folder and copy its raw contents.
2. Open a workflow canvas in your n8n instance.
3. Click the canvas and paste with `Ctrl + V` (or `Cmd + V`).
4. Reconnect your own credentials (Gmail, Google Calendar, Slack, Trello, Gemini, GitHub) on each node before running.

> Email addresses and IDs inside the workflows are sample or placeholder values — replace them with your own.

## Roadmap

- [ ] Add a screenshot of each workflow canvas
- [ ] Document required credentials and environment variables per workflow
- [ ] Add a `CHANGELOG.md` for tracking workflow updates

## Contributing

Issues and suggestions are welcome — open an issue or a pull request.

## License

Released under the [MIT License](LICENSE). © 2026 Marvin Liemor.
