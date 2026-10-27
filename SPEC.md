## COOKING GAME

### Game Description
The Cooking Game is a timed kitchen game that challenges the player to follow a recipe accurately and finish as quickly as possible. 

The player reads a recipe, gathers ingredients and tools from the kitchen, prepares the food, and cooks the finished dish. The recipe includes pictures with the materials (measuring cups, bowls, etc) and ingredients of what they look like and step by step instructions of what to do. The goal of the game is to make the recipe as fast as possible. Players can retry recipes to beat their previous time. Difficulty level can be added to the game by limiting the number of times you can refer back to the recipe. For example, the hardest difficulty would be seeing the recipe one time at the beginning and attempting to make the dish from memorizing the recipe after seeing it once. 

This game is fun because it combines memory, speed, and following a sequence of instructions. Replaying lets players learn the recipe and improve their performance.

### How does the player play?
1. The game opens with a recipe displayed over the kitchen.
2. The recipe shows the required ingredients, tools, and numbered steps.
3. The player clicks "Start Cooking" to close the recipe and start
   the timer.
4. The player clicks the refrigerator to view ingredients or the
   cabinet to view tools.
5. Clicking an ingredient or tool adds it to an inventory bar at the
   bottom of the screen.
6. The player selects items from the inventory and clicks a kitchen
   station to perform the current recipe step.
7. Correct actions advance the recipe. Incorrect actions show a
   message without advancing the recipe.
8. Completing the final step stops the timer and displays the
   player's completion time.
9. The player can restart to try to beat their best time.

### Initial Recipe: Chocolate Chip Cookies

**Ingredients**
- Flour
- Sugar
- Butter
- Egg
- Chocolate chips

**Tools**
- Mixing bowl
- Spoon
- Baking tray

**Preparation Steps**
1. Gather all five ingredients and all three tools.
2. Select the mixing bowl and place it on the counter.
3. Select and add flour, sugar, butter, and egg to the bowl.
   These four ingredients can be added in any order.
4. Select the spoon and click the bowl to mix.
5. Select the chocolate chips and click the bowl to add them.
6. Select the spoon and click the bowl to mix again.
7. Select the baking tray and click the bowl to transfer the dough.
8. Select the tray of dough and click the oven to bake.
9. After a five-second countdown, click the oven to collect the
   cookies and finish the recipe.

### Feature Set

**Features**
1. Recipe button that can be reopened
2. Clickable refrigerator, cabinet, counter, and oven
3. Inventory button
4. Menu bar with "Restart", "New Recipe", and "Past Results" buttons.
5. Timer
6. Pictures or icons for ingredients and tools in the recipe
7. Best completion time saved for each recipe
8. Difficulty selection: Easy - unlimited recipe views, Medium - 3 recipe reopens, Hard - 1 recipe view
9. Ingredients and appliances in cabinets and refrigerator
   
**Actions**
1. Clicking the refrigerator, cabinet, appliance, workspace, or recipe opens its contents fulls screen.
2. The full screen view of any function has a close button.
3. When an item is clicked in the refrigerator or cabinet, the item disappears and it appears in the inventory bar at the bottom of the screen. A 5 seconds penalty is added for any ingredient added to the inventory that is not required in the recipe.
4. The recipe icon opens or closes the recipe during play. The icon has a number on it labeling how many more recipe views are permitted.
5. There is a menu bar in top right corner with a "New Recipe" or "Restart" drop down.
6. The time is displayed in the top left corner and continues until the player completes the game or clicks "New Recipe" or "Restart" buttons in the menu bar
7. The "Past Results" button in the menu bar keeps track of best completion times for each recipe

### Acceptance criteria
1. Opening the game displays the chocolate chip cookie recipe with all five ingredients, all three tools, pictures or icons of each, and numbered preparation steps.
2. The player can select Easy, Medium, or Hard before starting.
3. Clicking “Start Cooking” closes the recipe, reveals the kitchen, and starts a timer displayed in the top left corner.
4. Clicking the refrigerator, cabinet, counter, or oven opens a full-screen view of that area. Each view has a close button that returns to the kitchen without losing progress.
5. The refrigerator and cabinet contain all required ingredients and tools, along with at least one ingredient that is not required.
6. Clicking an item in the refrigerator or cabinet removes it from storage and adds it to the inventory. The same item cannot be collected twice.
7. The inventory bar stays visible at the bottom of the screen and you can horizontally scroll through it.
8. Collecting an ingredient that is not required adds five seconds to the timer.
9. To use an item, the player goes to the counter or oven and can click items in the inventory if they want to use them at this location.
11. The player must mix with the spoon, add chocolate chips, mix again, and transfer the dough to the baking tray in that order. When the spoon is clicked from the inventory after clicking the bowl at the counter the spoon should automatically be used to mix without being prompted. 
12. An incorrect preparation action displays a message without advancing the recipe or consuming the selected item and adds 5 seconds to the timer.
13. Placing the tray of dough in the oven starts a five-second countdown. The player cannot collect the cookies before the countdown finishes.
14. Collecting the finished cookies stops the timer and displays the final completion time, including any penalties.
15. On Easy, the player can reopen the recipe unlimited times. On Medium, the player can reopen it three times. On Hard, the player can only view it before starting.
16. The recipe icon displays the remaining reopens, or an unlimited indicator on Easy. Reopening is disabled when no views remain, and the timer continues while the recipe is open.
17. The top right menu includes “Restart,” “New Recipe,” and “Past Results.”
18. Clicking “Restart” stops the current run and resets the ingredients, tools, inventory, preparation progress, penalties, and timer before displaying the same recipe again.
19. Clicking “New Recipe” stops the current run and opens the "Past Results" screen where all the recipes and their best scores sit. Selecting a recipe starts a fresh game.
20. Completing a recipe saves its time. “Past Results” displays the best completion time for each completed recipe, and these records remain after refreshing the page.

### Priorities
Highest priority — complete one playable recipe:
Criteria 1, 3–7, and 9–14. The player must be able to read the cookie recipe, gather items, prepare and bake the cookies, and receive a completion time. Use a fixed inventory bar initially if the inventory toggle takes too long.

Second priority — replay and scoring:
Criteria 8, 17, 18, and 20. Add the five-second penalty, menu, restart functionality, and saved best times. Build menu options as their corresponding features become available.

Third priority — memory challenge:
Criteria 2, 15, and 16. Add difficulty selection, limits on recipe views, and the remaining-view indicator.

Lowest priority — additional recipes:
Criterion 19. Add another complete recipe and enable the “New Recipe” option after the cookie recipe works.
