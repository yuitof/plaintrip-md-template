# Travel Plan Template

A data-only itinerary for [Travel Plan Viewer](https://github.com/yuitof/travel-plan). Edit Markdown, push to GitHub, and keep sharing the same viewer URL. There is no app to install or deploy in this repository.

## Make this yours

1. On GitHub, choose **Use this template** → **Create a new repository**.
2. Make the repository public. Private repositories are not supported yet.
3. Edit [`travel-plan.md`](./travel-plan.md), or rename it and update [`route.yaml`](./route.yaml).
4. Commit and push your changes.
5. Open `https://YOUR-VIEWER.example/YOUR-GITHUB-NAME/YOUR-REPOSITORY`.

For example, a public repository named `yuitof/china-travel-2026` appears at both configured routes:

```text
https://YOUR-VIEWER.example/yuitof/china-travel-2026
https://YOUR-VIEWER.example/yuitof/china-travel-2026/travel-plan
```

The website fetches the latest committed Markdown. A GitHub update may take about a minute to appear because the viewer caches public files briefly.

## Files

```text
.
├── README.md
├── route.yaml       # viewer URLs mapped to source files
└── travel-plan.md   # an example filename, not a required name
```

No itinerary filename is special. `route.yaml` is the complete routing table:

```yaml
version: 1

routes:
  /: travel-plan.md
  /travel-plan: travel-plan.md
  /packing: notes/packing-list.md
  /week-one: schedules/shanghai-and-wuhan.md
```

The left side is the URL below `/OWNER/REPOSITORY`; the right side is a Markdown path in this repository. You can map several URLs to one file. Unmapped URLs show the not-found page.

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

## Optional owner home

To make `/YOUR-GITHUB-NAME` show this plan, create the public GitHub profile repository `YOUR-GITHUB-NAME/YOUR-GITHUB-NAME`. Put this `route.yaml` in it:

```yaml
version: 1

routes:
  /:
    repository: YOUR-ITINERARY-REPOSITORY
    file: travel-plan.md
```

For example, `yuitof/yuitof/route.yaml` can point to `yuitof/china-travel-2026/travel-plan.md`, making `/yuitof` the short home URL. Update `file` if your Markdown has a different name.

Routing does not hide data. Every file in this public repository remains readable on GitHub and through GitHub's raw-file URL. Never commit passport details, booking codes, home addresses, API keys, or other secrets.
