# Generate unique id

``` javascript
let seed = 0;

function guid() {
  return "".concat(Date.now(), "_").concat(seed++);
}
```

### Usage
``` javascript
console.log( guid() );
console.log( guid() );
console.log( guid() );

// 1568828028626_0
// 1568828028627_1
// 1568828028627_2
```
