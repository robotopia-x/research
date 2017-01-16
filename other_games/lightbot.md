# General
## What does the player do
The player drag and drops Code Blocks into a Sequence executed by a robot. The goal in each level is the same: Lighten all the blue tiles.
As soon as all tiles that used to be blue are lit up a level is won.

## Sequence
I am not really sure what to call them to not interfere with further explanation.  
Let's just say a sequence is an Area on Screen that can fit X Code Blocks inside, which are then executed in order.

## Levels
The levels are grid-based with every grid entry having a given height. In the beginning the levels are fully flat.
Lateron a "Jump" Block is introduced so a higher terrain level can be reached.

# Game Progress

1. "Move Forward" and "Light block" are available to be used in one Main Sequence
1. "Turn Left/Right" are added
1. "Jump" is added. The robot will attempt to jump onto the tile in front of him (or down if he is higher)
1. "Procedures" are added. Below the Main Sequence Are another Are called Proc1 appears, that can be started via a "P1" Block
1. Adds a second procedure, that can be combined with the first one (Like P1 calls P2 or just simply the main calling P1, P2, P1, P2, ...)
1. Loops are "added". Basically the player gets a hint, that he can use the call to P1 inside of P1 creating a recursive call.

# What's Good / Bad

## Good
### Code Blocks are highlighted upon Execution (although very slightly, almost impossible to see)
### Cute Robot
### Code Blocks are very easy to understand

## Bad
### Did not run in Chrome as I tested
### Sequence Capacity
The Sequence Capacity is strictly set by the game, which means if I have a different Solution, that requires one of my Sequences to hold another element, it is not possible to use that solution.
![alt text](../img/lightroboLimit.png "Screenshot")
### Loops are forced
As soon as Loops are introduced the player has no choice but to use them thanks to the Sequence Capacity and the Main Sequence only having one Slot for a Block
