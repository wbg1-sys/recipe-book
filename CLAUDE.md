# Recipe Book: instructions for Claude

This repo is Will's recipe book app, served by GitHub Pages at https://wbg1-sys.github.io/recipe-book/ and installed on his iPhone Home Screen.

## Adding or changing a recipe

- Edit only `recipes.json` (an object keyed by recipe id, a lowercase hyphenated slug of the title). The schema is in `README.md`.
- Ingredients must be structured: `qty` as a decimal number (null for "to taste" items), optional `qtyMax` for ranges, `unit` only from: tsp, tbsp, cup, oz, lb, g, kg, ml, l, pinch, clove, can, stalk, sprig, strip, link, head, slice, bunch, package (otherwise put the word in `item`), and `item` for the rest of the line. Use `group` for "For the sauce" style sections.
- Steps are plain strings in the source's wording; times written like "10 minutes" become timers automatically.
- Categories in use: Chicken, Beef, Pork & Sausage, Seafood. Others allowed: Vegetarian, Pasta, Soups & Stews, Sides, Breakfast, Baking, Desserts.
- Set `updatedAt` (and `createdAt` for new recipes) to the current UTC ISO time. For NYT Cooking or other sources, fill `source.label` and `source.url`.
- Validate the JSON (`python3 -m json.tool recipes.json`) before committing.
- Commit with a message naming the recipe, then push to `main`. Pages redeploys in about a minute.

## Changing the app itself

- The app is all in `index.html`. After changing it, bump `CACHE` in `sw.js` (e.g. `recipe-book-v1` to `recipe-book-v2`) so installed copies update.
- Keep it dependency-free, accessible (Atkinson Hyperlegible, high contrast, 14pt+ body), and working offline.
