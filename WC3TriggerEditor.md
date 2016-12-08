# Objects

## Player
* Base (a Unit)
* Name
* Ressources
  * Type A
  * Type B
  * ...
* Points
* [units] or getUnits()
* Code?


## Marker
* position
* eventRange (range that triggers events)
* owner (Player or global?)
* event
  * type
  * data?

## Region
* topLeft
* bottomRight
* owner (Player or global?)
* event
  * type
  * data?

## Unit
* Owner
* Position
* Lifepoints
  * MAX
  * CURRENT
* Orders
  * Code Snippet
  * current statement = current order (eg. walk forward)
* getFriendsCloseBy()
* getEnemiesCloseBy()
* [Active Events] - eg. gathered Ressources, discovered enemy
* (Range) - units or Meelee/Range?
* (Speed)

# Events

## Legend for Events
* Eventname
  * data 1
  * (optional data2)
  * [array of data 3]
    
"triggering unit" will be the unit, that triggered the event.  

### Events
* finished current Order (basically a unit has nothing to do)
  * triggering unit
* moves in range of OBJECT (building, ressource, enemy, marker)
  * triggering unit
  * ObjectType
  * Object
* moves into region (area, might prove useful for tutorials/quests etc.)
  * triggering unit
  * region
* moves out of region
  * triggering unit
  * region

* gathered ressources
  * triggering unit
  * Ressource Type
  * Ressource Amount

* finished building (when building buildings, not sure if we need this for now)
  * triggering unit
  * building
* produced a unit (one unit/building creating another unit)
  * triggerin unit
  * produced unit

* discovered enemy
  * triggering unit
* meets friend
  * triggering unit

* attacks unit
  * triggering unit
  * target unit
* is being attacked
  * triggering unit
  * attacking unit

* kills unit
  * triggering unit
  * killed unit
* dies
  * triggering unit
  * (killing unit) - optional, cause might be killed by some event/timer

# Actions
## Thoughts
* let users create own 'actions', they can use/save in their IDE? like patrol from move, or attack-to from move and discovering an enemy, return ressources
* Could explain simple concepts by creating actions in a tutorial
  * for example Quest 1: make unit bring back ressources:
    * move to player.getbase
    * give ressources to player.getbase (or maybe the ressources are automatically removed on getting close)
  * for the next quest, or maybe the second (forces player to re program and thus practice) next quest the function is available as a block, or player uses his "old" function
* Make IDE customizable, at least groups for blocks

## Suggestions
### very basic actions
(may be useful to teach some concepts, but not very nice to be used in the actual game)  
* move forward
* turn
  * left/right

### basic actions
(basic, necessary actions for the game)  
* move
  * position
  * (base?)
* gather ressource
  * ressource
* pass ressources to
  * unit (valid so far would only be the base)
* attack
  * unit
* build
  * building
  * position
* hold Position
* setRallyPoint (producing buildings will send newly created units to that point)
* (use ability)

### more sophisticated
(may be custom created or unlocked to simplify more difficult statements, maing the code more modular)  
* bring back ressources (moves back to base, unloads ressources)
* patrol (walks repeatedly from point A to B to C etc...)
  * [positions]
* attack-to (moves, engages enemies on sight)
  * position
* gather friends
* scout
* flee (run back to base)
* find ressources
* gather ressources
