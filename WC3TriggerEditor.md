# Objects/Entities

## Some Thoughts
* A couple of Base Entities/Objects.
* Keep it to very few base classes - generic
  * kids hopefully wont wonder (why can i do ?! with this unit but not this building? etc..)

## Player

* Base (a Unit - his base/start point/factory whatever)
* Name (Player name, for human readability etc.)
* Ressources (Keeping track of: Gold etc.)
  * Type A (eg. Gold)
  * Type B (eg. Wood)
  * ...
* Points (points earned)
* [units] or getUnits() (to address all palyer units - might prove useful when base gets attacked for example)
* Code? (bind the current code to the player object - design issue)


## Marker
* position (position of marker)
* eventRange (range that triggers events)
* owner (Player or global?)
* event (event being emitted)
  * type (type could be something like: I am a ressource marker, I am a waypoint? I am an item?)
  * data? (additional event information, if necessary, similar to the events listed for units lateron)

## Region
* topLeft (define rectangle)
* bottomRight (define rectangle)
* owner (Player or global?) (player could create a Rectangle over a ressource field for example, to make units gather ressources there) (global could be something in the style of: This area is poisoned, or belongs to player XY?)
* event (see Marker event for details)
  * type
  * data?

## Unit
* Owner
* Position (current location of unit)
* Lifepoints
  * MAX
  * CURRENT
* Orders (really depends on how the runtime executes things, Idea was for the user to be able to check a unit for doing a certain task, For example: Is this unit just standing around (holding position) - and if so group it with other units to attack or whatever.)
  * Code Snippet (the bigger routine: like: go back to base)
  * current statement = current order (eg. walk forward)
* getFriendsCloseBy() (useful for grouping up units, finding allies)
* getEnemiesCloseBy() (useful for attack/retreat decissions)
* [Active Events] - eg. gathered Ressources, discovered enemy
  * a unit might at the same tick encounter ressources and an enemy unit and thus have 2 events pending. In that case the user needs to be able to decide on a routine.
  * in this scenario starting to gather ressources might not be smart while being attacked by an enemy (lalala chopping tree - famous last words)
  * By having a list of current events we leave the decision/priorisation to the user rather than executing whatever snippet is being chosen by the runtime
* (AttackRange) - units or Meelee/Range?
* (MovementSpeed)
  * maybe we want a faster unit at some point, like a scout or smth.
  * maybe can implement this internally to make it easy lateron.

# Events

## Legend for Events
* Eventname
  * data 1 - mandatory data
  * (data2) - () mean optional
  * [data 3] - [] means array
    
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
