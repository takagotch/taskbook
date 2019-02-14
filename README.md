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
}
```

```
{
  "taskbookDirectory": "~",
  "displayCompleteTasks": true,
  "displayProgressOverview": true
}
```
