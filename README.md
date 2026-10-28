# The Cooking Game

A timed kitchen game where players follow a recipe, collect ingredients and tools, prepare dough, and bake chocolate chip cookies as quickly as possible.

## Current status

The core gameplay for one recipe is implemented in a single HTML file using HTML, CSS, JavaScript, and inline SVG illustrations. This progress summary is based on the current source code and SPEC.md; it is not a record of completed browser testing.

## How to run

Open `Cooking-Game-3D.html` in a web browser. No build step or package installation is required. Google Fonts are requested online; fallback fonts are provided.

To access from terminal, go to folder holding `Cooking-Game-3D.html` and enter:
python3 -m http.server 8080

Then in a web browser:
http://localhost:8080/Cooking-Game-3D.html

## What I have done so far

### Base game and Priority 1 features

- Created an opening recipe screen with all five ingredients, all three tools, illustrated icons, and numbered instructions.
- Added a Start Cooking button that closes the recipe and starts the timer.
- Made the refrigerator, cabinet, counter, and oven clickable. Each station opens a full-screen view with a Close button.
- Stocked the refrigerator and cabinet with required items and extra items.
- Added a fixed, horizontally scrollable inventory bar. Collecting an item removes it from storage so it cannot be collected twice.
- Implemented using inventory items while the counter or oven view is open.
- Added the cookie preparation sequence: place the bowl; add flour, sugar, butter, and egg in any order; mix with the spoon; add chocolate chips; mix again; transfer dough to the tray; and bake.
- Added messages and five-second penalties for incorrect preparation actions without consuming the item or advancing the recipe.
- Added a five-second baking countdown that prevents early collection.
- Added a completion screen showing the final time, including penalties.
- Added a Cook again button that resets the run after finishing.
- Allowed the recipe to be reopened while the timer continues running.

### Kitchen design and manual adjustments

- Replaced the original flat station artwork with dimensional SVG illustrations inspired by miniature kitchens.
- Kept the refrigerator, oven, cabinet, and counter space as the main focal points.
- Added pastel finishes, perspective faces, highlights, and shadows to give the objects a 3D appearance.
- Adjusted the kitchen station positions, including moving the counter manually through CSS.
- Reduced the station label text and adjusted label sizing.

The kitchen uses 3D-style SVG artwork, rather than an interactive 3D engine. The current upload retains shadows.

## What I have left

### Priority 1: verify and polish the playable recipe

- [ ] When I was making size adjustments, I did not yet change the separate layout rules for smaller screens. These rules need to be adjusted to make the kitchen structure match that of a larger screen.
- [ ] Review the spec's bowl-click interaction. Currently, clicking the spoon in the inventory while the counter view is open mixes immediately when the recipe is ready; the bowl does not need to be selected first. (This is an okay adjustment to keep)

### Priority 2: replay and scoring

- [ ] Add a five-second penalty when collecting an unnecessary ingredient, such as milk or vanilla. Currently, collecting extras does not add a penalty; incorrect preparation actions do.
- [ ] Add a top-right menu and expose options as their features become available.
- [ ] Add Restart during an active run. It should stop the timer and reset storage, inventory, preparation, penalties, and time before reopening the same recipe.
- [ ] Save the best completion time for each recipe so records remain after refreshing the page, for example with localStorage.
- [ ] Add a Past Results screen displaying saved best times.

### Priority 3: memory challenge

- [ ] Add difficulty selection before starting.
- [ ] Easy: allow unlimited recipe reopens.
- [ ] Medium: allow three recipe reopens.
- [ ] Hard: show the recipe only before starting.
- [ ] Display the number of remaining reopens, or an unlimited indicator.
- [ ] Disable recipe reopening when no views remain.

### Lowest priority: additional recipes

- [ ] Add another complete recipe with ingredients, tools, instructions, and preparation logic.
- [ ] Add New Recipe to the menu once multiple recipes are available.
- [ ] Make New Recipe stop the current run and open the recipe/results selection screen.
- [ ] Start a fresh run when a recipe is selected and track best times separately.


## Controls and player instructions

- Click the refrigerator or cabinet to open storage, then click items to collect them.
- Click Close to return to the kitchen without losing progress.
- Open the counter, then click inventory items to use them there. Place the bowl first, add the four base ingredients, use the spoon, add chocolate chips, use the spoon again, and use the tray.
- Open the oven and click the tray of dough in the inventory to start baking. Wait five seconds, then click the oven door to collect the cookies.
- Click Recipe to review the instructions. The timer keeps running.
- Incorrect preparation actions add five seconds. Collecting unnecessary items currently does not (but should).
- Scroll the inventory horizontally when it contains more items than fit on screen.
- Press Escape to close a station view or a reopened recipe. The initial recipe stays open until Start Cooking is pressed.
- Click Cook again on the completion screen to reset.
- Buttons support standard keyboard focus and activation. There are no movement keys or drag-and-drop controls.

## Acceptance criteria status

These statuses describe the implementation found in the source. End-to-end browser validation remains outstanding. Criterion 10 is absent from the supplied spec.

| Criterion | Status | Evidence or remaining gap |
| --- | --- | --- |
| 1: opening recipe, icons, ingredients, tools, numbered steps | Implemented | Recipe overlay and `renderRecipe()` populate these. |
| 2: difficulty selection | Not implemented | No Easy/Medium/Hard selector. |
| 3: Start Cooking reveals kitchen and starts timer | Implemented | `start()` closes the recipe and starts timing. |
| 4: station views and Close buttons preserve progress | Implemented | `openSheet()` and `hideStationSheets()` manage views. |
| 5: required stock plus an extra ingredient | Implemented | `fresh()` includes required items, milk, and vanilla. |
| 6: collected items move to inventory and cannot be collected twice | Implemented | `collect()` removes each item from stock. |
| 7: visible, horizontally scrollable inventory | Implemented | Fixed inventory with horizontal overflow. |
| 8: extra ingredient collection adds five seconds | Not implemented | `collect()` does not check recipe membership. |
| 9: use inventory items at counter or oven | Implemented | `useItem()` dispatches according to the open station. |
| 11: ordered mixing, chips, mixing, and transfer; bowl selection | Partial | Order is enforced and spoon mixing is automatic, but there is no separate bowl-selection interaction. |
| 12: incorrect preparation preserves state/items and adds penalty | Implemented | Failed actions call `wrong()` without consuming the item. |
| 13: five-second bake, no early collection | Implemented | `atOven()`, `tick()`, and `ovenClick()` enforce this. |
| 14: collecting cookies stops timer and shows penalized total | Implemented | `finish()` freezes and displays the total. |
| 15: difficulty-specific recipe limits | Partial | Unlimited reopening works; Medium and Hard limits are absent. |
| 16: remaining-view indicator and disabled reopens | Partial | Timer continues while recipe is open; view counts and limits are absent. |
| 17: Restart/New Recipe/Past Results menu | Not implemented | Only Recipe is available in the top-right HUD. |
| 18: Restart during a run | Partial | `reset()` resets state after completion, but no in-run Restart control exists. |
| 19: New Recipe and recipe selection | Not implemented | Only one recipe is supported. |
| 20: persistent best times and Past Results | Not implemented | Completion time is shown but not saved. |

## Code map for the next developer

### Files

| File | Responsibility |
| --- | --- |
| `Cooking-Game-3D(1).html` | Complete game: styles, SVG assets, interface markup, state, and event handlers. |
| `SPEC.md` | Intended behavior, acceptance criteria, and feature priorities. |
| `README.md` | Setup, implementation status, handoff notes, and prompt log. |

There are no classes or imported JavaScript modules. Game logic is enclosed in one immediately invoked function, with state held in `S`.

### Major code sections and functions

| Section/function | Responsibility |
| --- | --- |
| CSS variables and layout rules | Colors, typography, HUD, inventory, station positioning, and responsive layout. |
| Inline SVG symbols and station artwork | Ingredient/tool icons and dimensional kitchen illustrations. |
| HTML sheets | Refrigerator, cabinet, counter, oven, recipe, and result views. |
| `ITEMS`, `RECIPE`, `BASE` | Item names, recipe content, and required base ingredients. |
| `PENALTY`, `BAKE` | Penalty duration and bake duration in milliseconds. |
| `fresh()` | Initial storage, inventory, phase, timing, and view state. |
| `now()`, `elapsed()`, `total()`, `fmt()`, `updateTimer()` | Clock calculations, penalty inclusion, time formatting, and timer UI. |
| `icon()`, `tile()` | Generate reusable item markup. |
| `toast()` | Temporary success/error feedback. |
| `renderRecipe()`, `renderInv()`, `renderStore()` | Populate recipe, inventory, and storage views. |
| `bowlSVG()`, `counterCaption()`, `renderCounter()` | Display the bowl and its preparation state. |
| `renderOven()`, `renderStations()`, `renderAll()` | Display oven state, station summaries, and coordinated UI updates. |
| `openSheet()`, `hideStationSheets()` | Open/close station views without resetting gameplay. |
| `openRecipe()`, `closeRecipe()` | Recipe overlay and its start/review behavior. |
| `take()` | Remove an item from inventory. |
| `atCounter()` | Enforce the cookie preparation state machine. |
| `atOven()` | Accept the dough tray and start baking. |
| `wrong()`, `useItem()` | Validate item use and apply error penalties. |
| `collect()` | Move an item from storage into inventory. Add extra-item collection penalties here. |
| `ovenClick()` | Handle early collection attempts and finished-cookie collection. |
| `start()`, `finish()`, `reset()` | Run lifecycle. Add result persistence in `finish()` and menu restart wiring around `reset()`. |
| `tick()` | Update elapsed time and detect completed baking every 100 milliseconds. |
| Event listeners at end of script | Connect station, item, recipe, replay, and Escape controls to game logic. |

## Next steps, in priority order

1. Add an in-run Restart menu action using the existing reset behavior.
2. Save best times and build Past Results, including persistence after refresh.
3. Add difficulty selection, recipe-view counts, and reopening limits.
4. Add another recipe, then enable New Recipe and recipe selection.
5. Polish layouts and interactions based on desktop/mobile playtesting.

## Known bugs, limitations, and developer traps

- **Small screen resizing:** I changed the position of the oven, refrigerator, cabinet, and counter but did not adjust the separate layout rules for smaller screens to match.
- **No persistence:** refreshing the page loses the current run and all results.
- **Collection penalty gap:** extra ingredients can be collected without the spec's five-second penalty, but the penalty does apply if the player attempts to use the ingredients.
- **Absolute positioning:** station placement depends on percentage positions and illustration aspect ratios. Overlap or awkward label placement is possible at untested sizes; no resize bug has been confirmed through browser testing.
- **No in-run restart:** the current replay button is only available after completion.

## Where I cut corners, and why

- **Small screen resizing:** I changed the position of the oven, refrigerator, cabinet, and counter but did not adjust the separate layout rules for smaller screens to match.
- **One HTML file:** kept setup simple and made the prototype easy to share. Splitting styles, assets, and game logic would help as the project grows.
- **One hardcoded recipe:** prioritized a complete playable cookie flow before building a general recipe engine.
- **Unlimited recipe reopening:** supports the base game before adding the memory-challenge difficulty system.
- **Deferred menu and saved scores:** prioritized the recipe loop; these remain unfinished requirements rather than completed features.
