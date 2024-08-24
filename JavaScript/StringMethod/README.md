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
