---
type: tripmd
title: Welcome to PlainTrip MD
description: A fictional itinerary and compact reference for writing a shareable trip in Markdown.
tags:
  - Introduction
  - Sample
  - Lisbon
budget: 450 EUR
currency: EUR
timezone: Europe/Lisbon
updated: 2027-02-01
---

## What is PlainTrip MD?

PlainTrip MD turns a small Markdown file into a calm, read-only itinerary that can be shared at one stable URL.

- **Arrange transport, stays, meals, and activities** on one timeline.
- **Keep local times understandable** when a trip crosses timezones.
- **Track an estimated budget** from event prices.
- **Edit with ordinary tools** and publish by pushing to a public GitHub repository.

# Example itinerary

Everything below is fictional. Replace it with your own dates, places, and plans.

## 2027-05-14 @Europe/Lisbon

> [10:15] flight Morning arrival :: Home airport - Lisbon Airport^LIS
>
> - price: 180 EUR
> - class: Economy
> - note: Keep the first afternoon light

> [11:30] - [12:15] subway Red Line :: Lisbon Airport - Alameda
>
> - price: 2 EUR
> - duration: 30 minutes

> [12:30] train Green Line :: Alameda - Baixa-Chiado
>
> - price: 2 EUR

> [!CAUTION] Example information only
>
> Confirm real transport times and entry requirements with official sources.

> [15:00] hotel Guesthouse check-in :: [Example Guesthouse](https://example.com/stay)
>
> - check-in: 15:00
> - check-out: 11:00
> - price: {24*2} EUR
> - wifi: Available

> [20:00] dinner First meal together :: Baixa, Lisbon
>
> - price: 30 EUR
> - note: Choose the restaurant after everyone arrives

## 2027-05-15 @Europe/Lisbon

> [!TIP] Leave breathing room
>
> One neighbourhood and an unhurried lunch may be better than crossing the city for every attraction.

> [09:00] breakfast Pastries and coffee :: Alfama, Lisbon
>
> - price: 8 EUR

> [10:30] - [13:00] sightseeing Viewpoints and old streets :: Alfama, Lisbon
>
> - price: {12*2} EUR
> - note: Walk part of the route if transit is crowded

> [13:30] lunch Market lunch :: [Example Market](https://example.com/market)
>
> - price: 20 EUR

> [15:00] - [17:00] museum Choose one museum
>
> - price: 15 EUR
> - reservation: Decide with the group

> [pm] walk Riverside stroll :: Praça do Comércio - Cais do Sodré

---

# Syntax reference

The title, locations, and metadata values may contain normal inline Markdown such as **emphasis**, `code`, and [links](https://example.com).

## 1. Event lines

Write an event inside a Markdown blockquote:

```markdown
> [time] event-type Optional title :: Place or route
>
> - detail: value
```

The title and destination are optional. Metadata lines belong to the event above them.

## 2. Event types

The event type selects its timeline icon and broad category.

### Transportation

```markdown
> [10:00] flight Morning flight :: Airport A - Airport B
> [11:00] train Intercity train :: Central Station - Coast Station
> [12:00] bus Airport bus :: Airport - Hotel
> [13:00] taxi Ride to dinner :: Hotel - Restaurant
> [14:00] subway Metro transfer :: Station A - Station B
> [15:00] ferry Island crossing :: Main Port - Island Port
> [16:00] drive Rental-car loop
> [17:00] cablecar Ride to the summit
```

### Accommodation

```markdown
> [15:00] hotel City hotel
> [18:00] ryokan Hot-spring inn
> [14:00] hostel Youth hostel
> [16:00] dormitory Shared guesthouse
> [15:00] stay Friend's home
```

### Activities

Any other word can be an activity type:

```markdown
> [09:00] breakfast Hotel breakfast
> [10:00] museum Design museum
> [12:30] lunch Market lunch
> [14:00] sightseeing Old town walk
> [16:00] cafe Coffee break
> [18:00] shopping Local shops
> [20:00] dinner Group dinner
```

## 3. Times

### Exact times

```markdown
> [09:00] breakfast Morning coffee
> [09:00@Asia/Tokyo] meeting Call in Tokyo time
> [09:00] - [11:30] activity Guided walk
> [06:30+1] arrival Overnight arrival
```

### Approximate times

```markdown
> [am] activity Morning plan
> [pm] cafe Afternoon break
> [] sightseeing Time not decided
```

## 4. Dates and timezones

Begin an itinerary day with an ISO date. A timezone on the heading applies to the events below it:

```markdown
## 2027-05-14 @Europe/Lisbon
```

An event-level timezone overrides the date heading, and the frontmatter timezone is the document-wide fallback.

## 5. Locations and routes

Use `::` for a destination. Put spaces around the dash in a journey:

```markdown
> [10:00] museum Morning visit :: Design Museum
> [12:00] train Coast service :: Central Station - Coast Station
```

The alternative `from ... to ...` form is also supported:

```markdown
> [12:00] train Coast service from Central Station to Coast Station
```

Append an alternate label with `^`, such as `Lisbon Airport^LIS`.

## 6. Event metadata

Metadata uses `key: value` list items inside the same blockquote.

### Prices

```markdown
> - price: 100 EUR
> - cost: 15000 JPY
```

`price` and `cost` contribute to the budget summary. Arithmetic such as `{25*4} EUR` is evaluated using numbers and arithmetic operators only.

### Transportation details

```markdown
> - class: Economy
> - seat: 12A
> - duration: 2h 30m
> - platform: 5
> - gate: 42
```

### Stay details

```markdown
> - check-in: 15:00
> - check-out: 11:00
> - room: Twin room
> - wifi: Available
> - breakfast: Included
```

### Notes and bookings

```markdown
> - reservation: Required
> - url: https://example.com
> - note: Move indoors if it rains
> - menu: Set menu
> - phone: +00 000 000 000
```

Custom metadata keys are welcome too.

## 7. Alerts

PlainTrip MD supports the five GitHub-style alert variants:

> [!NOTE] Note
>
> Add helpful context without making it an event.

> [!TIP] Tip
>
> Offer an optional shortcut or suggestion.

> [!IMPORTANT] Important
>
> Highlight something the group should remember.

> [!WARNING] Warning
>
> Call attention to a likely disruption.

> [!CAUTION] Caution
>
> Reserve this for information requiring extra care.

## 8. Frontmatter

The YAML block at the top controls the document heading and defaults:

```yaml
---
type: tripmd
title: My trip
description: One sentence for the people opening the link.
tags: [Weekend, Friends]
budget: 500 EUR
currency: EUR
timezone: Europe/Lisbon
---
```

Keep `type: tripmd` to enable itinerary parsing. `currency` and `timezone` provide fallbacks when an event does not specify its own values.

---

# About this template

PlainTrip MD uses the open-source itinerary and alert parsers from [TripMD / itinerary-md](https://github.com/cumuloworks/itinerary-md). The viewer is read-only: edit `plaintrip.md` on GitHub, then refresh the same shared URL.
