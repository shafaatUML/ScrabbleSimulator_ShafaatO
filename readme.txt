Name: Shafaat Osmani
Email: shafaat.osmani@gmail.com

REPO LINK: https://github.com/shafaatUML/ScrabbleSimulator_ShafaatO
GITHUB PAGES LINK: (PLEASE USE THS LINK TO TEST OUT PROJECT): https://shafaatuml.github.io/ScrabbleSimulator_ShafaatO/

About this project: This program simulates a single-line scrabble game in which the user can drag and drop tiles onto the scrabble board in order to create
words and earn points. 

Approach: I tried to keep my approach to this project as simple as possible. I implement list elements to act as the tiles and the board spaces
and styled them in the shape of tiles. I then used JQuery features to implement the drag and droppability. There were many cases I had to consider for this
project, with the 4 main ones being; the initial startup of the game, dragging tiles from rack to the board, dragging tiles from the board to the rack, 
and submitting a word (SUBMIT PROCEEDS TO THE NEXT ROUND). 

Throughout these 4 main cases, I had to implement many variables and conditionals which would micromanage all of the important data behind the scenes.
For example, I have a variable which keeps track of the current score for the round. This score must be constantly updated in the background
in order to ensure that points are tallied correctly. Then, once the submit button was clicked, the score would be added to the total running score, which
would in turn be displayed to the screen. In addition to the score, the indexes of the bonus multiplier board spaces were necessary to keep track of
in order to make sure multipliers are applied properly. 
Along with the score, I had two things to keep track of what tiles were placed onto the board as well as a string that kept track of the word the user is trying
to build. The word string is constantly updated, similar to score, after every drag/drop/submit so that the user is able to see what word they are building. 
The board array helps identify which bonus spaces were used and which tiles are currently on the board at any given moment. 
The submit button was one of the most difficult features to implement. Coming from a C++ background, where data types are defined within the language,
Javascript does not have defined data types. This made it hard at times to differentiate between strings and numbers. I had to do a lot of research
into Javascript and how it handles data types and use console log testing as well to ensure all features work as intended. The submit button commits the efforts
of the players each round, and also gives the player new tiles to bring their hand back to 7. 
Rather than physically bringing tiles back to the rack, I decided it was easier to simply destroy and re-create them at the rack as I did not have to deal
with the weird nuances of dynamically created elements and their draggability. I had attempted this, and they were not re-draggable after dropping, so I 
stuck to my own method. This method is also evident in other functions such as dropping to the rack. Destroying and re-creating the tile allows the tile to 
be re-positioned to its original place. 
The reset button simply refreshes the page, as that accomplishes the same thing as having to put all the used elements back to their original states and whatnot. 
The tiles in this program also contain many different custom attributes through the usage of datasets. Datasets allowed for me to be able to add additional helpful
values to the tiles such as their index position and the letter they were holding. 
Tiles are selected from an associative array (created by JMH modified by me) which contains different values for each letter in the game. To end the game
each tile must either reach a count of 0, and all tiles are depleted.
Additionally, tiles can only be dropped to the BOARD and to the RACK. Dropping tiles anywhere else will activate the revert attribute on the tile, which will
display the tile swiftly return to the rack. Tiles can also only be placed next to one another. This is accomplished by constantly searching the board array to 
see if there are any spaces in between letters. If there are spaces between letters, an error case is triggered and the tile is destroyed and re-created at the rack.


Word validation: word validation is accomplished through a very simple method. First, an ajax get is called on the dictionary.txt file (this file is massive
and contains thousands of words). By getting this file, each word is seperated by the newline character and is inserted into an array called words. After 
each update is made to the word string (so when a tile is dropped or taken off the board) this dictionary is constantly being referenced in order to ensure that
the submit button is only available if the word is valid. If the word is not valid, or the word is under 2 letters (1 letter would be too easy), the submit
button is not available and the user must either restart or come up with a word with the current tiles. 
