### Case: let users create own 'actions', they can use/save in their IDE

#### Toolbox updates
Blockly allows for toolbox updates while still in use

```javascript
workspace.updateToolbox(newTree)
```

where 'newTree' is either a tree of nodes, or a string representation of the toolbox.  

##### -> This could also be helpful with the eventHandler- and main game block, where we only want on block each.

---

#### Events

Blockly allows for custom events which could be helpful e.g. for 'achievements' or maximum block sizes

```javascript 
function onFirstComment(event) {
  if (event.type == Blockly.Events.CHANGE &&
      event.element == 'comment' &&
      !event.oldValue && event.newValue) {
    alert('Congratulations on creating your first comment!')
    workspace.removeChangeListener(onFirstComment);
  }
}
workspace.addChangeListener(onFirstComment);a
```
---
#### Advanced Blocks

It is also possible to save nested blocks with more advanced logic
![blockly_nested](./img/blockly_nested.png)

---
#### -> Features combined could let users create their 'own' blocks with advanced behaviour which could then be saved and reused late.
