---
name: recipe-collection
description: Organize recipes, plan meals, build grocery lists.
parameters:
  - cuisine: Any cuisine focus or dietary style?
  - household_size: How many people are you cooking for?
---

# Recipe Collection

**Follow-up:** Any cuisine preferences or dietary needs to keep in mind?

## Skills

### Draft
Write and format recipes from notes, photos, or links.
1. Extract recipe details from the source material
2. Standardize format — ingredients, steps, timing, yield
3. Add prep notes and substitution suggestions
4. Output a clean recipe card

In: handwritten recipe photos, screenshots of online recipes, notes, URLs | Out: formatted recipe → `files/recipes/`

### Plan
Weekly meal plans with variety and nutrition balance.
1. Review available recipes and dietary preferences
2. Map meals across the week — balance protein, variety, effort
3. Flag meals that share ingredients to reduce waste
4. Output a clean weekly plan

In: recipe collection, preferences, household size | Out: meal plan → `files/meal-plans/`

### Checklist
Generate grocery lists from meal plans.
1. Pull all ingredients from the week's recipes
2. Combine duplicates and convert units
3. Organize by store section — produce, dairy, pantry, etc.
4. Flag items likely already in the pantry

In: meal plan, pantry inventory | Out: grocery list → `files/grocery-lists/`

### Compare
Evaluate recipe variations side-by-side.
1. Identify what's being compared — same dish, different approaches
2. Line up ingredients, technique, and timing
3. Note key differences in effort, flavor, and dietary fit
4. Recommend based on the user's priorities

In: two or more recipes, photos, screenshots | Out: comparison → `files/recipes/`

### Summarize
Condense recipes into quick-reference cards.
1. Strip recipe to essentials — ingredients and steps only
2. Shorten steps to imperative phrases
3. Format for quick kitchen reference
4. Include timing and temperature at a glance

In: full recipe | Out: quick-reference card → `files/recipes/`

## Tools
None required.

## Folders
- `files/recipes/` — organized by category (mains, sides, desserts, etc.)
- `files/meal-plans/` — weekly and monthly meal plans
- `files/grocery-lists/` — generated shopping lists
