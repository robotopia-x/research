# Robot IDE

## Goals

The most important goal of the IDE is to be easy to use for beginners while not annoying more advanced users.
In order to learn programming it's important to understand what your programming is doing and if there is unexpected behavior how to fix it in your code.
Therefore we need to give the users a good sense of what state her programm is and how it's effecting the game world.
Ideally we would like to have the follwing features:

- Always hightlight which code block is currently executed, to make it easy to follow the flow of execution
- Allow to pause the game and inspect the current state of the world
- Allow to go back in time and replay the execution of the program
- Give visual hints inside the game to show what action is executed, these can be optionally turned on and off again
  - Example: a robot is moving to a specific target render a dotted line to the target until it's reached


## Implementation

We can't just generate JavaScript code from Blockly and run it directly because we want to have step by step execution.
Therefore we need some kind of custom interpreter which executes our code.

### Option 1: [JS Interpreter](https://developers.google.com/blockly/guides/app-integration/running-javascript#js_interpreter)
  - Advantages
    - full power of JavaScript (es5)
  - Disadvantages
    - state is kept inside interpreter
    - doesn't support timetravel
    - additional dependency (85kb)

### Option 2: Custom Interpreter
directly execute blocks sequentially. Each block has a type, params and state.

```javascript

/* MOVE BLOCK */

{ type: 'move', params: { direction: 'up' } }

/* LOOP BLOCK */

{
  type: 'loop',
  params: {
    blocks: [ ... ],
    condition: {
      type: 'lessThan',
      params: { a: 'i', b: '3' }
    }
  },
  initialState: { i : 0 }
}
```
  - Advantages
    - supports timetravel
    - all state is kept inside of store
    - better extensible
  - Disadvantages
    - not as powerful (but we probably don't need anything more complex than loops, conditionals and global variables)
    - more effort to implement
