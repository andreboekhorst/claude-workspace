---
name: travel-planning
description: Plan trips from research to packed bags.
parameters:
  - destination: Where are you going?
  - dates: When are you traveling?
---

# Travel Planning

**Follow-up:** Where are you headed, and when?

## Skills

### Research
Destinations, visa requirements, weather, and culture.
1. Clarify destination, dates, and travel style
2. Gather visa, health, and entry requirements
3. Research weather, local customs, and safety notes
4. Summarize key facts in a destination brief

In: destination, dates | Out: destination brief → `files/trips/`

### Plan
Build a day-by-day itinerary.
1. Review destination brief and user priorities
2. Map activities by day with timing and logistics
3. Add transit, meals, and buffer time
4. Output a clean itinerary with map-ready addresses

In: destination brief, preferences | Out: itinerary → `files/trips/`

### Compare
Accommodations, flights, and activities side-by-side.
1. Define what's being compared and criteria
2. List options with key specs — price, location, reviews
3. Score each option against criteria
4. Recommend with trade-offs noted

In: options, screenshots, CSVs, links | Out: comparison table → `files/trips/`

### Checklist
Packing lists and pre-departure tasks.
1. Review destination, duration, and activities planned
2. Generate categorized packing list
3. Add pre-departure tasks — bookings, documents, notifications
4. Output as a checkable list

In: itinerary, destination brief | Out: checklist → `files/templates/`

### Summarize
Condense itinerary into a pocket guide.
1. Pull key details from full itinerary
2. Strip to essentials — addresses, times, confirmations
3. Format for quick mobile reference
4. Include emergency contacts and key phrases

In: full itinerary, bookings | Out: pocket guide → `files/trips/`

## Tools
- **WebSearch** — look up visa rules, weather, local info

## Folders
- `files/trips/` — subfolder per destination with itineraries, briefs, comparisons
- `files/templates/` — reusable packing lists, checklist templates
