# Kitchen Chaos

A simpler version of *Overcooked*, currently single player, one level. Playable with keyboard and gamepad. 
***
### Overview
The player is enclosed in a kitchen. Recipes are lining up. The player has to use correct ingredients to deliver a correct recipe. Vegetables and cheese have to be chopped, the meat has to be fried and everything has to be combined in a bun on a plate. The player has to deliver as many recipes as (s)he can before the level timer runs out. There is currently a limited selection of recipes available.
***
### Gameplay
The gameplay is controlled by a simple state machine with four states:
* WaitingToStart - the tutorial screen is displayed, overview of key bindings
* CountdownToStart - after the player presses the interaction key, the countdown is triggered
* GamePlayingTime - after the countdown finishes, the player can start interacting with kitchen objects and counters to create recipes
* GameOver - after the level timer is finished, the total number of recipes delivered is displayed, along with the high score. The game can then be replayed. 
***
### Input system
The game uses the new Unity input system and currently supports keyboard and gamepads. I plan to implement touch screen as well.<br>
Default controls: 
* keyboard: move with WASD/arrows, interact with E, alternative interact with F, pause with ESCAPE; 
* gamepad: move with the left analog stick, interact with A, alternative interact with X, pause with START.
***
### Code
The game uses events, scriptable objects and state machines extensively. Since the states are very simple, I didn't bother with creating a separate state class for every state and instead I used a dictionary (for gameplay states) or switch statements (in super simple cases, for example when it comes to input). There is currently one case I plan to refactor from using a switch to  at least using a dictionary (stove counter states).

Logic is nicely separated from visuals and from UI. I also used namespaces to make sure there are no unnecessary dependencies.

There are several singletons. I made sure there are a minimal number of them (3 so far), but I plan to refactor this by using a service locator pattern, to practice the use of the pattern and to prepare for what may come in the multiplayer implementation.

Saving system is using PlayerPrefs. Since this is just a practice project and the only things that are saved are key bindings, music/sound volume and high score, I don't think I should be using a more complicated system at this point.
***
### TO DO
As of 22 Feb 2023:
* pooling instead of spawning
* fix sound: the countdown sound; burning warning sound - FIXED 04 Mar 2023
* fix the scoring system - currently all recipes are scored equally - recipes with more ingredients should give more points - FIXED 04 Mar 2023
* BACKGLOG: instead of spawning plates on the plates counter right away, start with plates on several counters; player should be able to put ingredients directly on the plate if the plate is on the counter; player should be able to put ingredients in a bun even if the bun isn't on a plate; logic and input for boosting the player's movement.
