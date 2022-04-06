---
title: 【克服JS的奇怪部分】Types and Operators
date: 2022-03-15 15:28:52
tag:
- JavaScript
---

此篇是記錄 Udemy 上面的課程 JavaScript: Understanding the Weird Parts 的筆記。

<!-- more -->

## Concept Asides 名詞解釋

#### Dynamic Typing 動態型別

> You don't tell the engine what type of data a variable holds, it figures it out while your code is running.
> Variables can hold different types of values because it's all figured out during execution.

什麼是動態型別？

有很多程式語言是屬於強型別的語言，當使用強行別的語言時，在宣告變數的時候，同時也需要宣告這個變數的型別。但 JavaScript 不需要在宣告一個變數時，同時宣告該變數的型別， JavaScript Engine 會自己去判斷變數的型別。所以，JavaScript 是一種動態型別的語言。

#### Primitive Type 原始型別

> A type of data that represents a single value.

JavaScript 總共有六種原始型別，分別是：string、boolean、number、undefined、null、symbol。

#### Operator 運算子

> A special function that is syntactically (written) differently.
> Generally, operators take two parameters and return one result.

當打出以下的程式碼時，我們會很直覺地認為會印出 7，但那是從人類的角度出發去做加減法，至於在 JavaScript Engine 當中是如何執行這段程式碼的？

```javascript
var a = 3 + 4;
console.log(a)
```

其實對 JavaScript Engine 來說，他在背後做的事情比較像是這樣：

```javascript
function +(a, b) {
    return // add the two variable
}

// 三種不同的運算子表示方式 //
+3 4 // prefix notation
3 + 4 // infix notation
3 4+ // postfix notation
```

`+` 其實是一個 JavaScript 裡面本來就有的 function，所以當我們寫了 `+` 時，就是呼叫這個 function ，然後將兩個變數傳進去做加法，然後回傳出一個新的值。只是這個 function 是寫在兩個變數中間，也就是 `3 + 4`，這樣將運算子寫在中間的表示方式稱為 infix notation。

總之，在 JavaScript 中，運算子其實是一種 function，傳入兩個值，然後會回傳一個值。

#### Coercion 強制轉型
> Converting a value from one type to another.
> This happens quite often in JavaScript because it's dynamically typed.

## Operator Precedence and Associativity

首先要來定義什麼是 Operator Precedence 和 Associativity：
> <b>Operator Precedence:</b> which operator get called first.
> Functions are called in order of precedence. (Higher precedence wins.)

> <b>Associativity:</b> what order operator functions get called in: left-to-right or right-to-left, when functions have the same precedence.

簡單來說，當有多個運算子出現在一個運算式當中的時候，需要透過 Precedence 來決定要先執行哪個運算，如果每個運算子的優先順序都相同的話，再透過 Associativity 去決定是要從左到右或是從右到左執行優先級相同的運算子。

先來看看一個只需要用到 Precedence 的簡單範例：

```javascript
var a = 3 + 4 * 5;
console.log(a);
```

在上述的程式碼當中，因為 `*` 的優先級比 `+` 高，所以 JavaScript Engine 會先做 `*` 再做 `+`：

```javascript
// 先做 *
var a = 3 + 20;

// 再做 +
var a = 23;

// 最後印出
23
```

JavaScript Engine 就是如上在執行運算子的運算，先將兩個值丟進一個運算的 function，然後回傳出一個新的值，再繼續做下一個運算子的運算，但也是因為這樣的運作方式，還有 JavaScript 本身是動態型別語言的關係，會導致一些奇怪的現象。

但在觀察這些奇怪的現象之前，先繼續來看看 Operator Precedence 和 Associativity 合在一起的例子。

```javascript
let a = 2;
let b = 3;
let c = 4;

a = b = c;

console.log(a);
console.log(b);
console.log(c);
```

在上述的例子當中，可以看到 `a = b = c` 這一行的運算子優先級是相同的（因為都是 =，每個 = 的優先級相同），接下來要看的就是 = 的 Associativity，到 MDN 文件查之後，知道 = 的 Associativity 是從右到左，所以 `a = b = c` 會從右到左執行，先執行 `b = c` 再執行 `a = b`，也就是說會先將 c 賦值給 b，再將 b 賦值給 c，所以最後 a、b、c 都會印出 4。

從以上兩個例子中，可以很清楚的知道 Operator Precedence 和 Associativity 的作用。

## 參考資源
- MDN 文件：https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Operator_Precedence