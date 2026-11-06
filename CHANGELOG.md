# Changelog

All notable changes to the workflows in this repository.

## 2026-11-06

### Added
- `follow-up-tracker.json`: drafts follow-ups for emails labeled *Awaiting reply*, clears the label when a reply arrives, and posts a daily Slack digest.
- `meeting-time-finder.json`: form-based, time-zone-aware slot finder that books the chosen slot with a Google Meet link.
- `invoice-payment-reminders.json`: staged invoice reminders drafted from a Google Sheet, plus unpaid totals in Slack.
- `client-onboarding-kit.json`: one form sets up the Drive folder, Trello board and checklist, kickoff hold, welcome draft and client log.
- `meeting-notes-action-items.json`: turns meeting notes in Google Docs into a recap draft, a Slack summary and Trello cards.
- `templates/invoices-template.csv`: starter sheet for the invoice workflow.
- `LICENSE` (MIT) and this changelog.

### Fixed
- Backup workflow pointed at placeholder `YOUR_GITHUB_USERNAME` / `YOUR_REPO_NAME` values.
- Renamed a workflow file whose name started with a stray space and tab.
- README rewritten with proper Markdown, author and license sections.
