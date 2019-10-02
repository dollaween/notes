# Теория массивов



## Методы обхода
### Array.forEach()
Вызывает функцию для каждого элемента в массиве
``` javascript
Array.forEach( (elem, index, array) => console.log(elem) )
```



### Array.every()
Возвращает true, если каждый элемент в массиве удовлетворяет условию проверяющей функции
``` javascript
arr.every(callback(elem, index, array))

[2, 4, 6, 8].every(elem => elem > 0)
    // true
[2, 4, 6, 8].every(elem => elem > 4)
    // false
```



### Array.some()
Возвращает true, если хотя бы один элемент в массиве удовлетворяет условию проверяющей функции
``` javascript
arr.some(callback(elem, index, array))

[2, 4, 6, 8].some(elem => elem > 4)
    // true
[2, 4, 6, 8].some(elem => elem > 9)
    // false
```



### Array.filter()
Создаёт новый массив со всеми элементами этого массива, для которых функция фильтрации возвращает true
``` javascript
arr.filter(callback(elem, index, array))

[1,5,2,6,3,8,0].filter(el => !(el % 2))
    // [ 2, 6, 8, 0 ]
```



### Array.map()
Создаёт новый массив с результатами вызова указанной функции на каждом элементе данного массива
``` javascript
users = [ {name: 'John', age: 28}, {name: 'Emily', age: 24} ]

names = users.map(user => user.name)
    // ['John', 'Emily']

// форматирование вывода
users.map(user => `${user.name} is now ${user.age} years`)
    // John is now 28 years
```



### Array.reduce()
Применяет функцию к аккумулятору и каждому значению массива (слева-направо), сводя его к одному значению
``` javascript
items = [ {price: 100}, {price: 200}, {price: 300} ]
items.reduce( (accumulator, currentValue, index, array) => {
    return accumulator + currentValue.price
}, 0)
    // где 0 — стартовое значение, которое принимает accumulator при первой итерации
    // 600
```



### Array.reduceRight()
Применяет функцию к аккумулятору и каждому значению массива (справа-налево), сводя его к одному значению
``` javascript
Array.reduceRight()
```



### Array.findIndex()
Возвращает индекс в массиве, если элемент удовлетворяет условию проверяющей функции. В противном случае возвращается -1
``` javascript
arr = ['one', 'two', 'three', 'four']
arr.findIndex( (elem, index, array) => elem === 'three' )
    // 2
```



### Array.includes()
Определяет, содержит ли массив определённый элемент, возвращая в зависимости от этого true или false
``` javascript
arr = ['one', 'two', 'three', 'four']
arr.includes('two')
    // true
```




``` javascript
```