# [Method Map](https://www.youtube.com/watch?v=WCYy8jpp7R8)

Современным способом принять все (или оставшиеся) аргументы функции в массив является применение `rest parameters` или [остальных параметров](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Rest_parameters), которые были приняты в стандарте ES6. Допустим, мы хотим найти сумму произвольного количества чисел, передаваемых функции как аргументы, для этого мы можем использовать код ниже:

```js
function addArgs1(...theArgs) {
	let sum = 0;
	theArgs.map(arg => (sum += arg));
	return sum
}
console.log(addArgs1(1,2,3,4));
console.log(addArgs1(1,2,3,4,5,6,7,8));
```

В своей [лабораторной](https://jscomplete.com/learn/lab-functions-args) по аргументам функций `Samer Buna` отмечает, что другим способом, пригодным для ES5 является применение встроенного объекта функции [`arguments`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/arguments). В данном случае прямое применение метода массива [`Array.map`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/map) невозможно, так как `arguments` является скорее объектом, поэтому посредством [`prototype.call`](http://adripofjavascript.com/blog/drips/invoking-javascript-functions-with-call-and-apply.html) мы добавляем объекту новый метод:

```js
function addArgs2() {
	let sum = 0;
	Array.prototype.map.call(arguments, arg => (sum += arg));
	return sum;
}
console.log(addArgs2(5,6,7,8));
console.log(addArgs2(1,2,3,4,5,6,7,8));
```

Использование метода массива [`Array.from`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/from) является еще одним способом преобразования объекта `arguments` в массив:

```js
function addArgs3() {
	let sum = 0;
  Array.from(arguments).map(arg => (sum += arg));
  return sum;
}
console.log(addArgs3(1,2,3,4));
console.log(addArgs3(1,2,3,4,5,6,7,8));
```

Примечательно, что метод `Array.map` может использоваться также и для строковых преобразований. В следующем примере мы обращаем строку с помощью метода `map`. Имейте в виду, что нотация `[]` фактически [равнозначна](https://2ality.com/2011/08/array-prototype-performance.html) прототипу массива `Array.prototype`:

```js
function reverseString1(string) {
	return [].map.call(string, symb => symb).reverse().join('');
}
console.log(reverseString1("ababcdcd"));
```

Более простым способом обращения строки в данном случае является использование метода строки [`split`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String/split):

```js
function reverseString2(string) {
	return string.split('').reverse().join('');
}
console.log(reverseString2("ababcdcd"));
```

Еще одной важной [особенностью](https://yazeedb.com/posts/array-map-explained-in-4-levels-of-difficulty#to-a-react-developer) метода массивов `map` является то, что его можно использовать в цепи методов, как например [генерирование](https://codesandbox.io/s/map-method-chain-7if2q) элементов списка в библиотеке `React`:

```jsx
users = [
  {
    name: 'Bruce Wayne',
    location: 'Gotham City',
    heroName: 'Batman'
  },
  {
    name: 'Barry Allen',
    location: 'Central City',
    heroName: 'The Flash'
  },
  {
    name: 'Clark Kent',
    location: 'Kryptonopolis',
    heroName: 'Superman'
  }
];

const App = (users) => {
  return (
    <ul>
      {users
        .map(user => user.name)
      	.map(name => <li>My name is {name}!</li>)
      }
    </ul>
  );
};
```



# Содержание разделов

[Как изучать JavaScript](./README.md)

[Шифр Виженера](./01_Chiffre_de_Vigenère.md)

[Method Map](./02_Method_Map.md)
