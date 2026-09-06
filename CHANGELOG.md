# Changelog

All notable changes to Recipe Book. The version number is visible in the browser tab and in the app header.

---

## [2.2] — 2026-09-06

### Added
- **Grocery list: per-recipe detail.** When a recipe writes an ingredient more precisely than the aggregated name it's grouped under (e.g. "midi cucumber" grouped under "Concombre"), that recipe's exact wording, its calculated portion, and the recipe it comes from now appear as a small line underneath — only when the wording actually differs, so most lines stay unchanged.

---

## [2.1] — 2026-07-31

### Changed
- **The food catalogue is no longer part of Food Cycling.** Managing foods — names, category, glycaemic index, organic marker, synonyms — is available whether or not the cycle features are on. Phase buttons simply appear on the same page when they are.
- Each food now opens an edit card: everything about it is editable in one place, including the synonyms the app should recognise in recipes.
- Removing a food from the built-in catalogue hides it rather than destroying it.

### Removed
- The "all phases" catch-all. Foods belong to specific phases, or to none. Fifteen foods previously marked that way are now unassigned — re-tag them as you see fit.

---

## [2.0] — 2026-07-31

Food Cycling becomes user data instead of built-in content.

### Changed
- **The food-to-phase associations and the phase guidance left the source code.** The repository now ships a neutral catalogue — 201 foods with category, glycaemic index and organic markers — and four factual phase descriptions (duration, dominant hormones). Everything interpretive is user data, held in the browser and exportable as JSON.
- **Food Cycling is off by default.** A fresh install is a plain recipe book: no cycle tab, no phase selector, no phase filters. Turn it on from ⚙ Settings, or import a Food Cycling file, which enables it automatically.
- Foods can now belong to several phases at once.

### Added
- **Food and phase editor**: browse the catalogue, attach or detach phases in one tap, add foods the catalogue is missing, search and filter by phase.
- Import and export of the Food Cycling layer, with `foodcycling.example.json` as a template.
- Ingredient recognition still powers the shopping-list aisles when Food Cycling is off.

---

## [1.9] — 2026-07-31

Preparation for the first public release.

### Added
- **Editable tags.** Tags are no longer hard-coded: they are data, editable from ⚙ Settings, and they travel with the JSON export. A fresh install starts from a generic set so everyone builds their own vocabulary.
- **Entertaining** meal type, for cooking when you have people over.
- Foods that apply across the whole cycle now have their own ♾ tab instead of crowding the four phase pages.
- Browser and home-screen icons.

### Fixed
- **Import times.** Some sites report their total time in the `cookTime` field; the app now accounts for this, and the total matches the source page. Previously a 20-minute recipe could show as 35.
- JSON pasted into the text field by mistake no longer ends up as the recipe title.
- A rendering error now shows a readable message and a way out, instead of a blank screen.

---

## [1.5] — Cycle module

### Added
- 211 foods referenced in French and English, mapped to cycle phases, with glycaemic index and organic-purchase markers.
- Phase pages: duration, hormones, mood, exercise, cooking methods, seed cycling, physiology and eating notes, plus personal notes.
- Automatic ingredient recognition in recipes, singular or plural, in either language.
- Phase-fit indicator per recipe, usable as a filter and a sort.
- Shopping list: quantities added up with unit conversion, incompatible units kept side by side, grouped by supermarket aisle, with aisle corrections remembered.

---

## [1.3] — Web import

### Added
- Bookmarklet and iOS Shortcut for one-click import from a recipe page, using `schema.org/Recipe` structured data.
- Re-importing an existing recipe (same URL) updates it instead of duplicating, preserving rating, cycle phase, status and personal tags.

### Changed
- The bookmarklet now hands over raw page data instead of pre-processed fields, so it never needs updating when the app changes.

### Fixed
- Multi-line recipe steps are no longer merged into a single paragraph.
- Section titles from the source are kept ("Get started — Trim the broccoli…").

---

## [1.0] — Initial version

### Added
- Recipe collection with the full field set: name, source, status, cuisine, meal type, tags, season, cycle phase, difficulty, rating, times, servings, nutrition, ingredients with allergen flags, numbered steps.
- Gallery grouped by meal type, search and combinable filters.
- Four cycle pages with free-text notes.
- "This week" view.
- Local persistence and JSON import/export.
