# JavaScript Array Methods

以下是 JavaScript 的 Array Methods 整理。

<br />

## length property (length 屬性)

返回陣列的長度。

```
const arr = [1, 2, 3];

console.log(arr.length);   // 3
```

<br />

## push()

將元素添加到陣列的末尾。

```
const arr = [1, 2, 3];
arr.push(5);

console.log(arr);   // [1, 2, 3, 5]
```

<br />

## pop()

移除並返回陣列的最後一個元素。

```
const arr = [1, 2, 3];
const last = arr.pop();

console.log(last);   // 3
console.log(arr);   // [1, 2]
```

<br />

## shift()

移除並返回陣列的第一個元素。

```
const arr = [1, 2, 3];
const first = arr.shift();

console.log(first);   // 1
console.log(arr);   // [2, 3]
```
