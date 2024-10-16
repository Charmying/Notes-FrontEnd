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

<br />

## unshift()

將元素添加到陣列的開頭。

```
const arr = [2, 3];
arr.unshift(1);

console.log(arr);   // [1, 2, 3]
```

<br />

## splice()

添加、移除或替換陣列中的元素。

```
const arr = [1, 2, 3, 4];
arr.splice(2, 1, 'a', 'b'); 

console.log(arr);   // [1, 2, 'a', 'b', 4]
```

<br />

## slice()

功返回一個新的陣列，包含從開始索引到結束索引 (不包含結束索引) 的部分元素。

```
const arr = [1, 2, 3, 4];
const newArr = arr.slice(1, 3);

console.log(newArr);   // [2, 3]
```

<br />

## concat()

合併兩個或多個陣列，返回一個新陣列。

```
const arr1 = [1, 2];
const arr2 = [3, 4];
const arr = arr1.concat(arr2);

console.log(arr);   // [1, 2, 3, 4]
```

<br />

## toString()

將陣列轉換為字串，元素之間以逗號分隔。

```
const arr = [1, 2, 3];
const str = arr.toString();

console.log(str);   // 1,2,3
```

<br />

## join()

將陣列轉換為字串，可以指定分隔符號。

```
const arr = [1, 2, 3];
const str = arr.join('-');

console.log(str);   // 1-2-3
```
