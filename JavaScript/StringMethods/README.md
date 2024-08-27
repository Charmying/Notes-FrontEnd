# String Methods

以下是 JavaScript 的 String Methods 整理。

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

<br />

## lastIndexOf()

功能與 indexOf() 類似，但 lastIndexOf() 回傳子字串最後一次出現的位置的索引。如果沒有找到子字串會回傳 -1。

lastIndexOf() 適合需要從後向前找子字串的位置。

```
let str = "Hello, world! Hello";

console.log(str.lastIndexOf('Hello'));   // 14
console.log(str.lastIndexOf('world'));   // 7
```

在這個範例中，`console.log(str.lastIndexOf('Hello'))` 回傳 14 是因為 Hello 在字串中最後一次出現於索引 14 的位置。

<br />

## startsWith()

檢查字串是否以指定的子字串開頭。回傳布林值 true 或 false。

startsWith() 常用於判斷字串是否符合某種開頭模式。

```
let str = "Hello, world";

console.log(str.startsWith('Hello'));   // true
console.log(str.startsWith('world'));   // false
```

<br />

## endsWith()

檢查字串是否以指定的子字串結束。回傳布林值 true 或 false。這方法常用於判斷字串是否符合某種結尾模式。

```
let str = "Hello, world";

console.log(str.endsWith('Hello'));   // false
console.log(str.endsWith('world!'));   // true
```

<br />

## search()

使用正規表達式在字串中搜尋，並回傳第一個匹配項的索引。如果沒有匹配項，回傳 -1。

search() 在需要複雜搜尋模式時非常有用。

```
let str = "My name is Charmy.";

console.log(str.search(/Charmy/));   // 11
console.log(str.search(/QQQ/));   // -1
```

<br />

## match()

使用正規表達式比對字串，回傳一個包含匹配結果的陣列或 null。

match() 常用於提取符合特定模式的子字串。

```
let str = "My name is Charmy. Charmy is so cooooooooool";

console.log(str.match(/Charmy/gi));   // ['Charmy', 'Charmy']
console.log(str.match(/QQQ/));   // null
```

<br />

## slice()

擷取字串的一部分，回傳新字串。

可接受兩個參數：起始索引 (包含) 和結束索引 (不包含)。

若未指定結束索引，則擷取到字串的結尾。支援負索引，從字串末尾開始計算。

```
let str = "Hello, world";

console.log(str.slice(0, 5));   // Hello
console.log(str.slice(7));   // world
console.log(str.slice(-5));   // world
```

在這個範例中，`str.slice(0, 5)` 擷取從索引 0 到索引 5 的字串 (不包含索引 5)，也就是 Hello。`str.slice(7)` 擷取從索引 7 開始到結尾的字串，也就是 world。`str.slice(-6)` 使用負索引，從字串末尾擷取 world。

<br />

## substring()

與 slice() 類似，但不接受負索引。

substring() 擷取的字串部分從 start 開始到 end (不包含)。

若未指定 end，則擷取到字串的結尾。

```
let str = "Hello, world";

console.log(str.substring(0, 5));   // Hello
console.log(str.substring(7));   // world
```

在這個範例中，`str.substring(0, 5)` 和 `str.slice(0, 5)` 相似，回傳 Hello。而 `str.substring(7)` 與 `str.slice(7)` 相似，回傳 world。

<br />

## split()

將字串依照指定的分隔符號分割成多個子字串，並回傳一個陣列。

split() 常用於將字串轉換為陣列，以便進行更靈活的操作。

```
let str = "aaa, bbb, ccc";

console.log(str.split(', '));   // ['aaa', 'bbb', 'ccc']
console.log(str.split(''));   // ['a', 'a', 'a', ',', ' ', 'b', 'b', 'b', ',', ' ', 'c', 'c', 'c']
```

<br />

## replace()

將字串中符合條件的部分替換為另一個字串，可接受字串或正規表達式作為替換條件。

replace() 常用於格式化或清理字串內容。

```
let str = "Hello, world";

console.log(str.replace('world', 'JavaScript')); // "Hello, JavaScript"
console.log(str.replace(/hello/i, 'Hi')); // "Hi, world"
```

<br />

## toLowerCase()

將字串中的所有字元轉換為小寫字母，並回傳新字串。

toLowerCase() 常用於處理不分大小寫的比較。

```
let str = "Hello, WORLD";

console.log(str.toLowerCase());   // hello, world
```

<br />

## toUpperCase()

將字串中的所有字元轉換為大寫字母，並回傳新字串。

toUpperCase() 常用於需要強調或統一格式的情況。

```
let str = "Hello, world";

console.log(str.toUpperCase());   // HELLO, WORLD
```

<br />

## trim()

移除字串開頭和結尾的空白字元 (包括空格、換行符號等)，並回傳新字串。

trim() 常用於清理使用者輸入或格式化字串。

```
let str = "   Hello, world   ";

console.log(str.trim());   // Hello, world
```
