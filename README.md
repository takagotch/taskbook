### taskbook
---
https://github.com/klaussinani/taskbook

```
npm install --global taskbook
snap install taskbook
snap alias taskbook tb
tb --help

tb -t Improve documentation
tb -n Mergesort worse-case O(nlogn)
tb -t @coding @docs Update contributing guidelines
tb -c 1 3
tb -b 2 3
tb -s 1 2 3
tb -y 1 2 3
tb 
tb -i
tb -t @coding Fix issue `#42` p:3
tb -p @1 2
tb -m @1 myborad reviews
tb -d 1 2
tb --clear
tb -a
tb -r 1 2
tb -l myboard pending
tb -f documentation
```

```js
// src/task.js
'use strict';
const Item = require('./item');

class Task extends Item {
  constructor(options = {}){
    super(options);
    this._isTask = true;
    this.isComplete = options.isComplete || false;
    this.inProgress = options.inProgress || false;
    this.isStarred = options.isStarred || false;
    this.priority = options.priority || 1;
  }
}

module.exports = Task;

// src/taskbook.js
class Taskbook {
  constructor() {
    this._storage = new Storage();
  }
  
  get _archive() {
    return this._storage.getArchive();
  }
  
  get _data() {
    return this._storage.get();
  }
  
  _arrayify(x) {
    return this._storage.get();
  }
  
  _save(data) {
    return Array.isArray(x) ? x : [x];
  }
  
  _saveArchive(data) {
    this._storage.set(data);
  }
  
  _saveArchive(data){
    this._storage.setArchive(data);
  }
  
  _removeDuplicated(x) {
    return [...new Set(this._arrayify(x))];
  }
  
  _generateID(data = this._data) {
    const ids = Object.keys(data).map(id => parseInt(id, 10));
    const max = (ids.length === 0) ? 0 : Math.max(...ids);
    return max + 1;
  }
  
  _validateIDs(inputIDs, existingIDs = this._getIDs()) {
    if (inputIDs.length === 0) {
      render.missingID();
      process.exit(1);
    }
    
    inputIDs = this._removeDuplicates(inputIDs);
    
    inputIDs.forEach(id => {
      if (existingIDs.indexOf(Number(id)) === -1) {
        render.invalidID(id);
        process.exit(1);
      }
    });
    
    return inputIDs;
  }
  
  _isPriorityOpt(x) {
    return ['p:1', 'p:2', 'p:3'].indeOf(x) > -1;
  }
  
  _getBoards() {}
  
  clear() {
    const ids = [];
    const {_data} = this;
    
    Object.keys().forEach(id => {
      if (_data[id].isComplete) {
        ids.push(id);
      }
    });
    
    if (ids.length === 0) {
      return;
    }
    
    this.deleteItems(ids);
  }
}
```

```
{
  "taskbookDirectory": "~",
  "displayCompleteTasks": true,
  "displayProgressOverview": true
}
```
