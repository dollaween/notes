# Main

Создание копии массива
``` javascript
array.slice()
```

Преобразование типов в массиве
``` javascript
arr = [0, 14, -98, '-6', '129', '5670with', undefined, null, false]

arr.map(Number)
// [ 0,  14, -98, -6, 129, NaN, NaN, 0, 0 ]

arr.map(String)
// [ '0', '14', '-98', '-6', '129', '5670with', 'undefined', 'null', 'false' ]

arr.map(Boolean)
// [ false, true, true, true, true, true, false, false, false ]
```

``` javascript
```

``` javascript
```

Преобразование Array-like объектов в Arrays
``` javascript
let argsArray = [].slice.call(arguments)
```
