# Main



## Tools
Создание копии массива
``` javascript
array.slice()
```






## Фильтрация
Убрать все false значения из массива
``` javascript
array.filter(_ => _)
array.filter(Boolean)
```





## Сортировка
Отсортировать по длине строки и алфавиту
``` javascript
array = [String]
array.sort( (a, b) => a.length - b.length || a.localeCompare(b))
```


Отсортировать по заданному порядку
``` javascript
arr = ['A', 2, 9, 18, 3, 666, 'BA', 'AA', 7]

arr.sort( (a, b) => {
  let ideal = ['A', 'AA', 'BA', 2, 3, 4, 5, 6, 7, 8, 9, 18, 666]
  return ideal.indexOf(a) - ideal.indexOf(b)
})


  // Четные числа отсортировать по уменьшению, нечетные - по возрастанию
  // Четные должны стоять в новом порядке на месте четных, нечетные - на месте нечетных

arr = [2, 22, 37, 11, 4, 1, 5, 0]

let odds  = array.filter(val => val % 2).sort( (a, b) => a - b )
let evens = array.filter(val => !(val % 2)).sort( (a, b) => b - a )
return array.map( item => item % 2 ? odds.shift() : evens.shift())
  // [22, 4, 1, 5, 2, 11, 37, 0]
```



## Преобразование
Преобразование Array-like объектов в Arrays
``` javascript
let argsArray = [].slice.call(arguments)
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



Преобразование двумерного массива в одномерный
``` javascript
[].concat(...array)
[].concat.apply([], array)
array.reduce((a, b) => a.concat(b))
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



Найти все элементы в массиве равные значению val
``` javascript
array = ['one', 'two', 'one', 'three', 'four', 'one']
array.filter(item => item === 'one')
  // ['one', 'one', 'one']
```



## Дубликаты
``` javascript
arr = ['some', 'way', 0, 1, 'some', 0, '1', 0]

// Оставить только уникальные значения в массиве
[...new Set(arr)]
  /// [ 'some', 'way', 0, 1, '1' ]

arr.filter((e, i)=> arr.indexOf(e) >= i)
  // [ 'some', 'way', 0, 1, '1' ]

arr.reduce((a, b) => {
  if (a.indexOf(b) < 0) a.push(b)
  return a
}, [])
  // [ 'some', 'way', 0, 1, '1' ]


// Вернуть все дубликаты
arr.filter( (e, i) => arr.indexOf(e) !== i && arr.lastIndexOf(e) === i )
  // [ 'some', 0 ]
```



Дубликаты у вложенного объекта
``` javascript
obj = [
  { id: 1, name: "Leo" },
  { id: 2, name: "Raf" },
  { id: 2, name: "Mikky" },
  { id: 1, name: "Leo" },
  { id: 4, name: "Splinter" },
  { id: 4, name: "Shredder" }
]

// Вернуть элементы с уникальным id
Array
  .from(new Set(turtles.map(e => e.id)))
  .map( id => {
    return turtles.find(e => e.id === id)
  })
  // [
  //    { id: 1, name: 'Leo' },
  //    { id: 2, name: 'Raf' },
  //    { id: 4, name: 'Splinter' }
  // ]

turtles.reduce((acc, cur) => {
  const x = acc.find(e => e.id === cur.id)
  return !x ? acc.concat([cur]) : acc
}, [])
  // [
  //    { id: 1, name: 'Leo' },
  //    { id: 2, name: 'Raf' },
  //    { id: 4, name: 'Splinter' }
  // ]

let seen = new Set()
turtles.filter(e => {
  const duplicate = seen.has(e.id)
  seen.add(e.id)
  return !duplicate
})
  // [
  //    { id: 1, name: 'Leo' },
  //    { id: 2, name: 'Raf' },
  //    { id: 4, name: 'Splinter' }
  // ]
```





