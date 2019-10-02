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










## МЕТОДЫ ИЗМЕНЕНИЯ

### Array.fill()
Заполняет все элементы массива от начального до конечного индексов одним значением
``` javascript
Array.fill(value, start, end)

arr = [1, 2, 3, 4]
arr.fill(0)
    // [0, 0, 0, 0]
```



### Array.pop()
Удаляет последний элемент из массива и возвращает его
``` javascript
Array.pop()
```



### Array.push()
Добавляет один или более элементов в конец массива и возвращает новую длину массива
``` javascript
Array.push()
```



### Array.reverse()
Переворачивает порядок элементов в массиве — первый элемент становится последним, а последний — первым
``` javascript
Array.reverse()
```



### Array.shift()
Удаляет первый элемент из массива и возвращает его
``` javascript
Array.shift()
```



### Array.sort()
Сортирует элементы массива на месте и возвращает отсортированный массив
``` javascript
Array.sort()
```



### Array.splice()
Добавляет и/или удаляет элементы из массива
``` javascript
arr.splice(start, deleteCount, item1, item2...)

arr = ['Johnny', 'they', 'are', 'on', 'the', 'trees']

arr.splice(0, 1, 'Carl')
    // [ 'Carl', 'they', 'are', 'on', 'the', 'trees' ]

arr.splice(3, 0, 'aliens')
    // [ 'Johnny', 'they', 'are', 'aliens', 'on', 'the', 'trees' ]
```



### Array.unshift()
Добавляет один или более элементов в начало массива и возвращает новую длину массива
``` javascript
Array.unshift()
```










## Методы доступа

### Array.concat()
Возвращает новый массив, состоящий из данного массива, соединённого с другим массивом и/или значением (списком массивов/значений)
``` javascript
Array.concat()
```



### Array.from()
Создаёт новый экземпляр Array из массивоподобного или итерируемого объекта
``` javascript
Array.from(iterable)

Array.from('some')                // [s, o, m, e]
Array.from(100)                   // []

// Второй аргумент — функция map
Array.from('some', (value, index) => value.toUpperCase())
    // [ 'S', 'O', 'M', 'E' ]

// Можно передать длину массива объектом со свойством length
Array.from({length: 5}, (value, index) => index)
    // [ 0, 1, 2, 3, 4 ]
```



### Array.join()
Объединяет все элементы массива в строку
``` javascript
Array.join()
```



### Array.slice()
Извлекает диапазон значений и возвращает его в виде нового массива
``` javascript
Array.slice()
```



### Array.toString()
Возвращает строковое представление массива и его элементов. Переопределяет метод Object.prototype.toString()
``` javascript
Array.toString()
```



### Array.toLocaleString()
Возвращает локализованное строковое представление массива и его элементов. Переопределяет метод Object.prototype.toLocaleString()
``` javascript
Array.toLocaleString()
```



### Array.indexOf()
Возвращает первый (наименьший) индекс элемента внутри массива, равный указанному значению; или -1, если значение не найдено
``` javascript
arr.indexOf(value, fromIndex)

arr = ['hasta', 'la', 'vista', 'baby']

arr.indexOf('vista')              // 2
arr.indexOf('wrong')              // -1
```



### Array.lastIndexOf()
Возвращает последний (наибольший) индекс элемента внутри массива, равный указанному значению; или -1, если значение не найдено
``` javascript
Array.lastIndexOf()
```