# PlainTrip MD itinerary template

A data-only [TripMD](https://github.com/cumuloworks/itinerary-md) itinerary for [PlainTrip MD](https://github.com/yuitof/plaintrip-md). Edit Markdown, push to GitHub, and keep sharing the same viewer URL. There is no app to install or deploy in this repository.

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

## TripMD syntax

The included itinerary is a complete example. Add `type: tripmd`, use dated `##` headings, and write events as blockquotes:

```md
---
type: tripmd
title: My trip
description: A short sentence friends will see below the title.
tags: [Japan, Friends]
budget: 100000 JPY
currency: JPY
timezone: Asia/Tokyo
---

## Before you go

- [ ] Reserve a hotel

## 2027-08-01 @Asia/Tokyo

> [09:00] - [11:15] train Shinkansen :: Tokyo - Kyoto
>
> - seat: Window
> - price: 13970 JPY
> - status: Booked

## Ideas to discuss

### Kyoto

- Pick one temple before lunch.

## Practical notes

- Times are local.
```

Times can also be `[am]`, `[pm]`, `[]`, or next-day values such as `[06:30+1]`. Use `:: Place` for one location and `:: From - To` for a journey. Metadata entries such as `price`, `status`, `seat`, and `details` appear below the event. Normal Markdown, task lists, tables, and `[!NOTE]`-style alerts work alongside the itinerary.

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
