### Case: let users create own 'actions', they can use/save in their IDE

blockly allows for toolbox updates while still in use

```javascript
workspace.updateToolbox(newTree)
```

where 'newTree' is either a tree of nodes, or a string representation of the toolbox.  

##### -> This could also be helpful with the event-handler and main game block, where we only want on block each.

---

It is also possible to save nested blocks with more advanced logic
![blockly_nested](./blockly_nested.png)

---
#### -> Both features combined could let users create their 'own' blocks with advanced behaviour which could then be saved and reused late.
