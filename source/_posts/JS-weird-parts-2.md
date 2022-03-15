---
title: 【克服JS的奇怪部分】Types and Operators
date: 2022-03-15 15:28:52
tags:
- JavaScript
---

測試測試
此篇是記錄 Udemy 上面的課程 JavaScript: Understanding the Weird Parts 的筆記。

<!-- more -->

## 🐳 Concept Asides 名詞解釋

### 🦀 Dynamic Typing 動態型別

> You don't tell the engine what type of data a variable holds, it figures it out while your code is running.
> Variables can hold different types of values because it's all figured out during execution.

什麼是動態型別？

有很多程式語言是屬於強型別的語言，當使用強行別的語言時，在宣告變數的時候，同時也需要宣告這個變數的型別。但 JavaScript 不需要在宣告一個變數時，同時宣告該變數的型別， JavaScript Engine 會自己去判斷變數的型別。所以，JavaScript 是一種動態型別的語言。

### 🦀 Primitive Type 原始型別

> A type of data that represents a single value.

JavaScript 總共有六種原始型別，分別是：string、boolean、number、undefined、null、symbol。

### 🦀 Operator
