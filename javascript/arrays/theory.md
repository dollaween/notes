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