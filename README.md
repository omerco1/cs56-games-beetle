# cs56-games-beetle

## Authors

* W16 READY Hanna
* F16 Yuanqi Samarth

## Testing the Text-based game
To run the text-based game, you can't use ant at the command line. Instead you have to cd into the build directory and then use the command `java edu.ucsb.cs56.projects.games.beetle.BeetleGame -t`.

## Project Description

This is a dice rolling game in which the user can choose between four levels: Beetle, Ant, Person, and Ladybug. 
The game can be played against the computer or against another person.

This game is played by clicking a "Roll" button that randomly rolls a value (1-6) for each play. This value corrensponds to the number on a dice and each number represents a body part of the insect/person trying to be created.
The player must first roll the number representing the "body" or "thorax" before adding on other parts of the insect/person.
The game is won by being the first player to roll all parts of the insect/person.

## Screenshots

![StartScreen](./gamePictures/StartScreen.png)
![PlayerSelectScreen](./gamePictures/PlayerSelectScreen.png)
![GameScreen](./gamePictures/GameScreen.png)
![GameEndScreen](./gamePictures/GameEndScreen.png)

## F16 Final Remarks

When the game is launched, there is a menu giving the option of which game mode the user wants to choose. After the user selects which game mode they want (Ant, Beetle, Ladybug, or Person) a prompt displays them asking if they want to play with 1 Player or 2. Then it makes them enter in their name(s), and the actual game GUI displays. In this GUI the user(s) can play the game, rolling the die until one of them wins. After they can choose to replay the game or to quit. 

The user can also select to run the text-based version of game by cd-ing into the build directory and then use the command "java edu.ucsb.cs56.projects.games.beetle.BeetleGame -t". In this game mode, they do the exact same thing as the normal version, except everything is text-based without a GUI. 

The way the code is set up, nothing needs to be refactored as we took care of that. The entry point to the game is the `BeetleGame` class. `GuiBased` and `TextBased` are the two views of the game using the MVC design pattern. All of the game classes such as `Ant` and `Beetle` extend `Player` so if you want to create more game modes, all you have to do is create new classes extending `Player`.

## W16 Final Remarks

When the game is run, the startGUI window appears with options for the level. When a level is selected, the corresponding GUI is launched and an instance of a Player object for that level is created. The GUI class for each level contains the code for the buttons and text fields while the Player class contains for for handling the rolls and adding parts.

The main feature that can be improved is improving the graphics. It would be nice for the user to see the animal being built as they play the game.

A couple of bugs that exist is that the exit window pops up right when the game ends, which can cause confusion as to who won the game. Also, after a game ends and the user selects a new level, the window for entering a name reappears. These are further explained in the Issues section ing Github.

As of now, each level has its own Player class. However, these Player classes are very similar to each other. There is possibility to combine them all into one generic class or create a parent class that they inherit from in order to keep the code DRY.

## F17 Final Remarks

Upon running the game, a GUI window is opened prompting the user to select an insect/person to play as. Not immediately obvious, but the insects users can select from correspond to different difficulties. The game then prompts the user with JOption windows asking him/her whether they want single or double player, followed by another JOption window that prompts for the player names. Thereafter, the main game window is opened and the user can press the roll GUI button and play. 

Many design improvements have been made to make the game more intuitive and more playable. However, there exist major game logic issues that should be addressed in the future. For starters, as mentioned before, the difficulty portion of the game is not immediately clear, more importantly it is not implemented well. Each level is actually its own class that extends the "Player" class, which makes it easy to add new difficulties. However, with regard to the insects, each bug class's partNeed array is initialized with the same value, so the only thing that is different about them is the picture that appears. This is doesn't make the game anymore difficult for the user which should be changed. 

Moreover, some sort of skill element should be added to the game to make it more fun and interesting. That way JUnit tests could be added to ensure the game runs more smoothly. Finally, the mainFrame() method in the GuiBased.java needs refactoring. The method does far too many things at once and should better emulate the Single Responsibility Principle, it should delegate operations to other methods. 
