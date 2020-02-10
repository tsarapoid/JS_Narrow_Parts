# Заголовок













parseInt

http://www.wirfs-brock.com/allen/posts/166

https://raddevon.com/articles/cant-use-parseint-map-javascript/

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

```js
["1", "7", "11","12"].map((n,l) => parseInt(n*100+l));
["1", "7", "11","12"].map(Number);
```



```js
console.log(['1', '7', '11'].map(parseInt));
console.log(['1', '7', '11'].map(Number));
```









var scope strict mode



```js
function strict() {
  'use strict';
  function nested() { return 'And so am I!' }
  return "Hi!  I'm a strict mode function!  " + nested()
}

function notStrict() { return "I'm not strict." }

console.log(strict());
console.log(nested());
console.log(notStrict());
```



destructuring

https://www.sitepoint.com/es6-destructuring-assignment/



Because using the “slow” system is so mentally draining, we tend to default to the “fast” one — even when dealing with intellectual tasks like coding.

Imagine that you’re in the middle of a lot of work, and you want to  quickly identify what this function does. Take a quick look at it:

```javascript
function duplicateSpreadsheet(original) {
  if (original.hasPendingChanges) {
    throw new Error('You need to save the file before you can duplicate it.');
  }
  let copy = {
    created: Date.now(),
    author: original.author,
    cells: original.cells,
    metadata: original.metadata,
  };
  copy.metadata.title = 'Copy of ' + original.metadata.title;
  return copy;
}
```





| You’ve probably noticed that:                                |
| ------------------------------------------------------------ |
| This function duplicates a spreadsheet. It throws an error if the original spreadsheet isn’t saved. It prepends “Copy of” to the new spreadsheet’s title. |



| What you might *not* have noticed (great job if you did though!) is that this function *also* accidentally changes the title of the original spreadsheet. |
| ------------------------------------------------------------ |
| Missing bugs like this is something that happens to every programmer, every  day. But now that you know a bug exists, will you read the code  differently? If you’ve been reading code in the “fast” mode, it’s likely you’ll switch to the more laborious “slow” mode to find it. |
| In the “fast” mode, we guess what the code does based on naming, comments, and its overall structure. In the “slow” mode, we retrace what the code does step by step. |





https://medium.com/javascript-in-plain-english/please-stop-using-classes-in-javascript-and-become-a-better-developer-a185c9fbede1



```js
function iAmAnObject() {}

console.log(iAmAnObject.name); // iAmAnObject
console.log(Object.keys(iAmAnObject)); // Array []
```







------

#### [JS узкие части](./README.md)