# Changelog

All notable changes to Recipe Book. The version number is visible in the browser tab and in the app header.

---

## [3.0] — 2026-10-20

The recipe book becomes a pocket cooking app: find what to cook, plan the week, shop, and cook step by step — with your own recipes.

### Added
- **Bottom tab bar**: Accueil · Recettes · Planning · Courses (· Cycle when Food Cycling is on). Re-tapping the current tab scrolls back to the top. The browser's back gesture now works inside the app, and going back restores where you were in the list.
- **Home feed**: what's on the menu today with a one-tap "Cuisiner", quick tiles (planning, shopping, 🎲 surprise me, fridge search), and carousels — best recipes, ready in 30 min, in season, for your phase, not yet tested, to cook again soon, recently added — plus your tags shown as **collections**.
- **"Avec ce que j'ai"**: type the ingredients you have ("poulet, courgette, riz"); recipes using the most of them come first, with a ✓ 2/3 badge. Recognises French and English names through the food catalogue.
- **Library**: always-visible search (accent-insensitive, every word must match), one-tap shortcuts (favourites, 30 min max, 4★+, planned, to test, meal types) and **sorting** (best rated, quickest, newest, most cooked, highest protein, A→Z).
- **Portions on the recipe page**: a +/− stepper rescales every ingredient quantity live, written the way a cookbook would ("1½ oignon", "335 g", "2 à 3" → "4 à 6"). Recipes without base portions scale by ×½ … ×4.
- **Cook mode**: one step per screen in large type, a mise en place checklist, the ingredients used in each step at the chosen quantity, **timers detected from the text** ("20-25 minutes", "1 h 30") that keep running across screens and ring when done, swipe or ← → to move, and the screen stays awake (Safari 16.4+). The last screen lets you rate the dish and log it as cooked.
- **Weekly planner**: real dated weeks, a slot per day plus "sans jour précis", portions per meal, 🔀 swap for another idea, ✨ fill the empty days from your favourites (seasonal, not cooked in the last 10 days), copy last week, clear a week — all with undo.
- **Shopping list per week**, built from the planner: progress bar, inline add (↵ to chain items), checked items sink to the bottom of their aisle, aisle changes and removal from a bottom sheet, share or copy what's left to buy.
- **Mon placard**: mark staples you always have (salt, oil, spices…) and they move to a collapsed "Dans mes placards" section instead of cluttering every list.
- **Cook history and notes**: each recipe tracks how many times you cooked it and when; a "Mes notes" field keeps your tweaks and is shown again at the start of cook mode.
- **Favourites** with a heart on the recipe page (reuses the existing "❤️ Favorite" cuisine, so earlier favourites carry over) and inline star rating.
- **Settings**: household size (default portions when opening or planning a recipe), pantry list, and light / dark / automatic appearance.
- **Dark mode**, following the phone or Mac unless set otherwise.
- **Recipe form**: essentials first (name, photo, portions, times), then ingredients and steps, then classification; nutrition and source fold away. ↵ in an ingredient opens the next line, and pasting a whole ingredient list fills one line per ingredient. A sticky save bar stays in reach.
- Bottom sheets replace the old `prompt()` dialogs for planning, aisles and the "new recipe" menu.

### Design
- **Readable everywhere:** text and controls meet WCAG AA contrast in light and dark (slightly deeper terracotta, darker greys, visible checkbox outlines, gold stars); buttons on the accent use dark text in dark mode.
- **Easier to tap:** every button has a 44-point target, including steppers, stars, the shopping-list ⋯ and the planner's portions.
- **A calmer accent:** terracotta is kept for actions, selection and quantities; labels, notices and the planned ✓ are neutral.
- **Cookbook typography:** recipe titles in the system serif (New York on iPhone and Mac), 17 pt ingredients and steps, one label style, tabular figures, French spacing before ? and !.
- **Recipe page:** the photo goes edge to edge under the status bar (no app header on stacked screens), metadata uses line icons, nutrition shows "—" instead of "0 g", classification pills move below the recipe.
- **Recipes without a photo** get a gradient tinted by meal type instead of a beige box.
- **Cards:** one meta line (★ note · time · kcal · protein), titles clamped to two lines, the heart on a card un-favourites in one tap.
- **Cook mode:** larger step text readable from across the kitchen, a preview of the next step, bigger timer pills, a timer button that shows it's running.
- **Planner:** empty days take one line with a "+ Repas" button.
- **Shopping list:** one line of provenance per item; the exact wording from each recipe moves into the item's options.
- **Home:** two wide tiles (Surprise, Mon frigo); "recently added" only shows when it doesn't repeat "not yet tested"; each collection gets its own photo.
- **Form:** a photo tile instead of the native file button, portions/prep/cook on one line, no redundant tabs.
- Settings use a gear (distinct from the filter icon), sheets are elevated in dark mode, press feedback on touch, hover and keyboard focus styles on Mac, the menstrual phase uses one icon (🌙) everywhere, and selects no longer make iPhone zoom.

### Changed
- "Cette semaine" is now the planner. Existing data migrates automatically on first launch: recipes that were in "this week" become meals of the current week with their chosen portions, and the shopping list keeps its ticks and manual items.
- The JSON backup now carries the planner (current and future weeks), cook history and notes; importing a pre-3.0 backup turns its "this week" recipes into planned meals.
- Re-importing a recipe from the web keeps your notes and cook history in addition to rating, status and tags.
- **Recipes for my phase** now include the recipes tagged with that phase in their "Cycle" field, not only those whose ingredients are attached to the phase. With Food Cycling on, the home screen opens with "Pour ta phase…" (or a phase picker when none is set, or a short how-to when nothing matches yet); the library gets a "Ma phase" shortcut; cards say "De ta phase"; the Cycle page lists both tagged and ingredient-rich recipes; and auto-fill favours them.

### Fixed
- Importing a backup twice, or an old backup into a base that already has those recipes, no longer creates duplicates: a recipe with the same identity is updated (the most recent version wins, cook history and tags are merged).
- A full backup now restores everything it contains when moved to another device: Food Cycling associations and phase notes, current phase, custom foods and synonyms, aisle corrections, pantry, household size, appearance, unused tags, and the current shopping list — without overwriting anything already set there.
- Importing a Food Cycling file adds to your own associations and phase notes instead of replacing them, and can be undone.
- When the browser's storage is full, nothing pretends to be saved anymore: a banner stays until saving works again, with a one-tap export; the recipe form stays open; notes say "Non enregistré". Settings show how much space is used, photos included.
- Recipe identifiers from imported files are sanitised (a crafted file could inject markup).
- Malformed import files are rejected cleanly instead of failing silently or creating empty recipes.
- **Cook mode** keeps the portions you just chose on the recipe page (only a meal opened from the planner brings its own), ticks today's meal or the one "sans jour" — never another day's — and never counts the same meal twice. Timers are labelled by step ("Ét. 3 · 4 min"), can't be started twice by accident, stay clickable on Mac, and understand "3 minutes 30". If Safari reloads the tab mid-recipe, running timers carry on and the home screen offers "Reprendre".
- **Navigation:** the back gesture closes an open sheet instead of leaving the screen; switching tabs leaves no dead history entry behind; carousels keep their position when you come back. The Courses badge and the home tile always count the week that matters, whichever week you last looked at.
- **Planner:** copying last week twice no longer duplicates meals; ✨ says when some days stayed empty for lack of main dishes; 🔀 keeps a breakfast a breakfast (or says there's no other).
- **Search works in both languages.** "poulet" and "chicken" now find the same recipes, in the library, in "Avec ce que j'ai" and when adding a meal to a day: a word also matches the English and French names of the food it designates, and a plural finds its singular ("crevettes", "épinards", "tomates"). The catalogue's chicken was named "Chicken" in French; it is now "Poulet", which also fixes the shopping-list label.
- **Library:** search waits for a pause in typing (no lag on a large base) and keeps the keyboard open; the time filter no longer loses focus; "Avec ce que j'ai" respects the other filters; archived recipes are hidden unless asked for; "Tout voir" on the best recipes shows the 4★+ ones; the "add a meal" search matches every word, like the library.
- **Pasted recipe text** no longer loses lines: the portions in "Ingrédients (pour 6 personnes)" are read, durations in hours are understood, a step mentioning "5 minutes" stays a step, and the rest of the header becomes the description. Web imports decode HTML entities (&amp;, &eacute;…) and read "PT0.5H" or "1h15".
- **Re-importing** a recipe from its site keeps your own title and your own photo.
- **Form:** "www.site.fr/…" gets its https://, negative numbers are refused, a step starting with "1.5 l" keeps its number, and going back from an unchanged edit doesn't ask to discard.
- Clearing the phase or turning Food Cycling off also clears the filters that depended on it.
- **Shopping list accuracy.** Ingredients are recognised from their name only, never from the unit: "2 c. à café de cumin" no longer becomes coffee, and sugar, yeast or garam masala no longer merge into one "Café" line. An adjective is never taken for the food ("poivron vert" is not a lime, "butter beans" not peanut butter, "crème fraîche" not coriander). Potato, coconut milk, nutmeg and cream join the catalogue, with synonyms for olive oil, plant milks, peppers and stock. Stock goes to the grocery aisle, eggs to dairy, cured meats to the butcher's and cheeses to dairy.
- Shopping quantities read like a cookbook ("½ c. à soupe", "1½ kg") and whatever is bought whole is rounded up ("1 boîte", not "0.5 boîte"). "1½ kg", "⅛" and ranges ("2-3 gousses", using the upper bound) are understood.
- Scaled quantities use a French decimal comma unless the recipe writes "1.5", never show "0", and things counted whole (eggs, onions) move by halves.
- For a recipe without base portions, the ×2 chosen on its page now carries over to the planner and the shopping list.
- An aisle chosen for a recognised ingredient (e.g. moving "Oignon" to another aisle) was saved under one key and looked up under another, so it never stuck. It now does.

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
