# Recipe Book

Will Gruppo's recipe book: a small web app that installs to an iPhone Home Screen and works offline.

## Files

- `index.html`: the whole app (library, recipe pages, scaling, US/metric, timers, cooking mode).
- `recipes.json`: every recipe, keyed by an id like `pot-roast`. This is the only file that changes when recipes are added or edited.
- `sw.js`: offline support. Bump `CACHE` (e.g. `recipe-book-v2`) when `index.html` changes so phones pick up the new version.
- `manifest.webmanifest`, `icons/`: Home Screen name and icon.

## Recipe format

```json
"recipe-id": {
  "title": "Pot Roast",
  "category": "Beef",
  "description": "One or two sentences.",
  "servings": 6, "servingsText": "6-8",
  "prep": "30 minutes", "cook": "4 hours", "total": "4-4.5 hours",
  "ingredients": [
    { "qty": 2, "unit": "tbsp", "item": "unsalted butter" },
    { "qty": 2, "qtyMax": 3, "unit": "cup", "item": "beef broth" },
    { "qty": null, "item": "Kosher salt and pepper" }
  ],
  "steps": ["One string per step. Times like 5 minutes become tap-to-start timers."],
  "tips": [], "notes": [],
  "source": { "label": "NYT Cooking", "url": "https://..." },
  "createdAt": "2026-10-23T19:30:00Z", "updatedAt": "2026-10-23T19:30:00Z"
}
```

Units that scale and convert: `tsp`, `tbsp`, `cup`, `oz`, `lb`, `g`, `kg`, `ml`, `l`. Other units (`clove`, `can`, `stalk`, `sprig`, `pinch`, ...) scale but don't convert.

## Hosting

Served by GitHub Pages from the `main` branch, root folder.
