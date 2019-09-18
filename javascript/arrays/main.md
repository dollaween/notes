# Main

Создание копии массива
``` javascript
array.slice()
```

## Преобразование типов в массиве
``` javascript
arr = [0, 14, -98, '-6', '129', '5670with', undefined, null, false]

arr.map(Number)
// [ 0,  14, -98, -6, 129, NaN, NaN, 0, 0 ]

arr.map(String)
// [ '0', '14', '-98', '-6', '129', '5670with', 'undefined', 'null', 'false' ]

arr.map(Boolean)
// [ false, true, true, true, true, true, false, false, false ]
```

## Поиск по массиву
Поиск по массивую из чисел
``` javascript
arr = [0, -6, 14, 129, -98, 2, 5670]

// Найти наименьшее и наибольшее числа
Math.min(...arr)                          // -98
Math.max(...arr)                          // 5670
```

Поиск по массиву из строк
``` javascript
arr = ['Johnny', 'they', 'are', 'on', 'the', 'trees']

// Найти самое короткое слово
arr.sort( (a, b) => a.length - b.length)[0]
  // on

arr.reduce((acc, cur) => acc.length < cur.length ? acc : cur )
  // on
```

Преобразование Array-like объектов в Arrays
``` javascript
let argsArray = [].slice.call(arguments)
```
