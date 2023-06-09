### Тестовое задание: 

Часть 1 - https://github.com/elli0thammer/practice-1

Часть 2 - https://github.com/elli0thammer/practice-2

Часть 3 - https://github.com/elli0thammer/practice-3

### Теоретическая часть:

Написать что выводит данный код.
Предложите 2 варианта модификации кода, чтобы ответ был следующим: Bad: 10, Bad: 12, Good: 15, Good: 21

```code
const arr = [10, 12, 15, 21];

for (var i = 0; i < arr.length; i++) {
    setTimeout(function () {
        console.log(arr[i] > 13 ? `Good: ${arr[i]}` : `Bad: ${arr[i]}`)
    }, 3000)
}

```

Отображает: Bad: undefined, Bad: undefined, Bad: undefined, Bad: undefined

---

1) Когда мы используем var, переменная объявляется в функциональной области видимости, 
а не локальной видимости функции, в которой она объявлена. 
Если мы используем var в цикле, переменная будет иметь последнее значение из цикла вне цикла, тк
не создает новую переменную на каждой итерации цикла и при каждой итерации переменная просто перезаписывается.

В случае с let переменная будет иметь значение, определенное на каждой итерации цикла.

```code
const arr = [10, 12, 15, 21];

for (let i = 0; i < arr.length; i++) {
    setTimeout(function () {
        console.log(arr[i] > 13 ? `Good: ${arr[i]}` : `Bad: ${arr[i]}`)
    }, 3000)
}
```

Отображает: Bad: 10, Bad: 12, Good: 15, Good: 21

---

2) Либо использование самовызывающуюся функцию внутри цикла, 
которая позволяет сохранить значение переменной i на момент каждой итерации в новой области видимости, 
создавая новый контекст выполнения функции.

```code
const arr = [10, 12, 15, 21];

for (var i = 0; i < arr.length; i++) {
    (function (j) {
        setTimeout(function () {
            console.log(arr[j] > 13 ? `Good: ${arr[j]}` : `Bad: ${arr[j]}`)
        }, 3000)
    })(i)
}
```
GitHub Pages: https://elli0thammer.github.io/theory/
