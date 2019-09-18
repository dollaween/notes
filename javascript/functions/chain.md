# Chain

``` javascript
function createChainedFunction() {
    var args = [].slice.call(arguments);

    if (args.length === 1) {
      return args[0];
    }

    return function chainedFunction() {
        for (var i = 0; i < args.length; i++) {
            if (args[i] && args[i].apply) {
                args[i].apply(this, arguments);
            }
        }
    };
}
```
### Usage
``` javascript
function fn1() { console.log(1) }
function fn2() { console.log(2) }
function fn3() { console.log(3) }

createChainedFunction(fn2, fn1, fn3)
    // 2
    // 1
    // 3
```
