# Depth First Search

Проходится по переданному массиву из объектов `arr`, сравнивает поле `field` с нужным значением `target`. Если значения не совпадают, и у объекта есть потомки `children` — повторяет процедуру с ними. Возвращает элемент массива, либо `null`.

### Code
``` javascript
function dfs(arr, target, key = 'id', children = 'children') {
    if (arr.length > 0) {
        for (let obj of arr) {
            if (obj[key] === target) {
                return obj;
            } else if (obj[children]) {
                let found = dfs(obj[children], target, key, children);
                if (found !== null) {
                    return found;
                }
            }
        }
    }
    return null;
}
```



### Usage
``` javascript
dfs(arr, 7, 'id', 'children')
    // {id: 7, title: "Bane"}

dfs(arr, 18)
    // {id: 18, title: "Hawk"}

dfs(arr, 'Batman', 'title', 'children')
    // {id: 3, title: "Batman", children: Array(3)}
```



### Array example
``` javascript
const arr = [{
    id: 1,
    title: 'Defenders',
    children: []
}, {
    id: 2,
    title: 'DC',
    children: [{
        id: 3,
        title: 'Batman',
        children: [{
            id: 4,
            title: 'Robin'
        }, {
            id: 5,
            title: 'Catwoman'
        }, {
            id: 6,
            title: 'Joker',
            children: [{
                id: 7,
                title: 'Bane'
            }, {
                id: 8,
                title: 'Doomsday'
            }]
        }]
    }, {
        id: 9,
        title: 'Flash',
        children: [{
            id: 10,
            title: 'Killer Frost'
        }, {
            id: 11,
            title: 'Kid Flash'
        }]
    }]
}, {
    id: 12,
    title: 'Marvel',
    children: [{
        id: 13,
        title: 'X-Man',
    }, {
        id: 14,
        title: 'Avengers',
        children: [{
            id: 15,
            title: 'Captain America'
        }, {
            id: 16,
            title: 'Iron Man',
            children: [{
                id: 17,
                title: 'Hulk'
            }, {
                id: 18,
                title: 'Hawk'
            }]
        }]
    }]
}];
```