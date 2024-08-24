# String Method

以下是 JavaScript 的 String Method 整理。

<br />

## includes()

用於檢查字串中是否包含某個子字串。這個方法會回傳布林值 (true 或 false)，表示字串是否包含指定的子字串。

includes() 是檢查字串中是否存在某些關鍵字或特定內容的常用方法。

```
let str = "Hello, world";

console.log(str.includes('Hello'));   // true
console.log(str.includes('World'));   // false
```

在這個範例中，`console.log(str.includes('Hello'))` 回傳 true 是因為 Hello 存在於字串中。但 `console.log(str.includes('World'))` 回傳 false 是因為 includes() 會區分大小寫。

<br />

## indexOf()

找出子字串第一次出現的位置，回傳其索引 (從 0 開始)。如果沒有找到子字串會回傳 -1。

indexOf() 常用於判斷子字串的起始位置或確定子字串是否存在。

```
let str = "Hello, world";

console.log(str.indexOf('Hello'));   // 0
console.log(str.indexOf('world'));   // 7
console.log(str.indexOf('World'));   // -1
```

在這個範例中，`console.log(str.indexOf('Hello'))` 回傳 0 是因為 Hello 從字串中的第一個位置開始，`console.log(str.indexOf('world'))` 回傳 7 是因為 world 從字串中的第七個位置開始，而 `console.log(str.indexOf('World'))` 回傳 -1 是因為字串中找不到 World。
