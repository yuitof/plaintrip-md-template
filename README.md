# Travel Plan Template

A data-only itinerary for [Travel Plan Viewer](https://github.com/yuitof/travel-plan). Edit Markdown, push to GitHub, and keep sharing the same viewer URL. There is no app to install or deploy in this repository.

## Make this yours

1. On GitHub, choose **Use this template** → **Create a new repository**.
2. Make the repository public. Private repositories are not supported yet.
3. Edit [`travel-plan.md`](./travel-plan.md). Replace the example trip rather than renaming the file.
4. Commit and push your changes.
5. Open `https://YOUR-VIEWER.example/YOUR-GITHUB-NAME/YOUR-REPOSITORY`.

For example, a public repository named `yuitof/china-travel-2026` appears at:

```text
https://YOUR-VIEWER.example/yuitof/china-travel-2026
```

The website fetches the latest committed Markdown. A GitHub update may take about a minute to appear because the viewer caches public files briefly.

## Files

```text
.
├── README.md
├── travel-plan.md       # the default itinerary
└── travel-plan.yml      # default page, aliases, and viewer access rules
```

You may add more Markdown anywhere in the repository:

```text
notes/packing.md
weekends/kyoto/travel-plan.md
```

Those files become `/OWNER/REPOSITORY/notes/packing` and `/OWNER/REPOSITORY/weekends/kyoto`. An extensionless folder route also tries the configured default filename inside that folder.

## Markdown shape

The included itinerary is a complete example. Keep these section names and the four itinerary columns if you want every part of the viewer to render:

```md
---
title: My trip
description: A short sentence friends will see below the title.
route: Tokyo → Kyoto → Osaka
budget: 100,000 JPY
updated: 2026-08-22
---

## Before you go

- [ ] Reserve a hotel

## Itinerary

### Saturday 1 August · Tokyo → Kyoto
`2026-08-01` · Japan Standard Time

| Time | Plan | Details | Status |
| --- | --- | --- | --- |
| 09:00–11:15 | Train to Kyoto | Window seats | Booked |

## Ideas to discuss

### Kyoto

- Pick one temple before lunch.

## Practical notes

- Times are local.
```

Available statuses are `Booked`, `Planned`, `Flexible`, `Confirm`, `Decide`, and `Idea`. Separate route stops with `→`, and use an en dash in ranges such as `09:00–11:15`.

## Change URLs and access

Edit [`travel-plan.yml`](./travel-plan.yml):

```yaml
version: 1
default_file: travel-plan.md

pages:
  packing: notes/packing.md

access:
  default: public
  rules:
    - path: drafts/**
      access: hidden
    - path: drafts/share-this.md
      access: public
```

- `default_file` is shown at `/OWNER/REPOSITORY`.
- `pages` maps a friendly URL to a Markdown file.
- access patterns support `*`, `**`, and `?`.
- rules run top to bottom; the last matching rule wins.
- `hidden` makes the viewer return a not-found page.

Viewer access rules are not secrecy. Because this repository is public, hidden Markdown remains readable on GitHub and through GitHub's raw-file URL. Never commit passport details, booking codes, home addresses, API keys, or other secrets.
