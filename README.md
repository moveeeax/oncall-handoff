# oncall-handoff

> The next person on call should not have to read Slack backwards.

**Status:** 🚧 In development

## Overview

Generate an on-call handoff summary from alerts fired, deploys shipped and incidents still open in the window, so the next person starts informed.

## Features

- Pulls alerts from Alertmanager, open incidents from the tracker, and deploys from CI for the shift window
- Collapses repeat firings into one line with a count, so a flapping check does not fill the page
- Carries forward what is still live: open incidents, silences about to expire, manual state left set
- Markdown for the wiki plus a short form for Slack or Telegram
- Window taken from the rotation schedule, or set by hand with `--since` / `--until` for an off-cycle handoff
- Stable, diffable output, so two consecutive handoffs show what changed

## Stack

Go + cobra, the Alertmanager v2 API client, slack-go/slack for delivery.

## Usage

```bash
oncall-handoff generate --since 2026-07-25T09:00Z --until now --format markdown --post slack:#sre
```

## License

MIT
