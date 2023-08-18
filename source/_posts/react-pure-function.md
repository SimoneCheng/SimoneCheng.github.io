---
title: 【React】什麼是 Pure Function？在 React 當中的重要性是什麼？
date: 2022-01-19 17:36:23
tag:
- React
- funcitonal programming
---

在 functional programming 當中，有一個重要的概念稱為 pure function，而這個概念在 React 的官方文件當中被提起，那麼 pure function 在 React 當中到底扮演了什麼樣的角色呢？這是本文試圖理解並回答的問題。

<!-- more -->

目前的文章架構如下：
- 什麼是 pure function？  
- 為什麼我們需要 pure function？
- 為什麼 pure function 在 React 裡面是重要的？

在閱讀本文之前，你可能要有的先備知識：
- 了解 React hooks 如何運作
- 了解 React functional components 裡面的 life cycle
- 了解一點點 Redux
- 最重要的是：了解 JavaScript

## 🐳 什麼是 pure function？  

> A pure function is a function which:
> - The function always returns the same result if the same arguments are passed in. It does not depend on any state, or data, change during a program’s execution. It must only depend on its input arguments.
> - The function does not produce any observable side effects such as network requests, input and output devices, or data mutation.

簡單來說，一個 function 只要符合以下兩個條件：

1. 相同的 input，永遠都輸出相同的 output。
2. 沒有產生 side effect。跟其他function不會互相干擾，不會修改/引用/存取或是依賴到到外部變數，但是當作參數傳入是可以的。

我們就可以把這個 function 稱為 pure function。但要怎麼樣才能符合這兩個條件餒？接下來可以來細看這兩個條件的意涵。

## 🐳 條件一：相同的 input，永遠都輸出相同的 output

### ❌ 不符合條件一的例子

以下兩個 function 每次的 output 都不一樣，所以不符合條件一。
```javascript
function now() {
    return new Date();
}
```

```javascript
Math.random();
```

### ✔️ 符合條件一的例子

```javascript
// a, b都是整數
function add(a, b) {
    return a + b;
}

add(1, 2); // => input 是 1, 2，永遠都 return 3
add(3, 5); // => input 是 3, 5，永遠都 return 8
add(4, 6); // => input 是 4, 6，永遠都 return 10
```

## 🐳 條件二：沒有產生 side effect

### 🦀 什麼是 side effect？

> An observable side effect is any interaction with the outside world from within a function. That could be anything from changing a variable that exists outside the function, to calling another method from within a function.
> 
> Note: If a pure function calls a pure function this isn’t a side effect and the calling function is still pure.

簡單來說，side effect 指的就是在執行某個 function 時，該 function 的作用會影響到外面（比如全域環境或是其他 function 裡的東西），那麼「會影響到該 function 外面」這個行為，就叫做 side effect。

雖然 side effect 聽起來很像是負面的名詞，但不表示 side effect 就是不好的，在程式當中，side effect 單純就只是描述在寫 function 時有可能會出現的情況或是現象而已。

### 🦀 side effect 有哪些？

以下介紹一些常見的 side effect，但不限於此：
1. Making a HTTP request
2. Mutating data
3. Printing to a screen or console
4. DOM Query/Manipulation
5. Math.random()
6. Getting the current time

接下來直接以程式碼來舉例有 side effect 的 function 長什麼樣子：
```javascript
function impureAssoc(key, value, object) {
  object[key] = value;
};

const person = { name: 'Bobo' };

const result = impureAssoc('shoeSize', 400, person);

console.log(person); // { name: 'Bobo', shoeSize: 400 }
console.log(result); // { name: 'Bobo', shoeSize: 400 }
```

在上述的程式碼當中，當把 `person` 傳入 `impureAssoc` 這個 fucntion 裡面之後，`person` 從 `{ name: 'Bobo' }` 變成 `{ name: 'Bobo', shoeSize: 400 }`。也就是說，透過 `impureAssoc` 這個 function，改變了全域變數 `person`，這也意味著這個 function 有 side effect。

我們把程式碼稍微改一下，在原本的 function 中先將傳入的 object 複製出一份一模一樣的，然後針對複製出來的那份進行修改，就可以消除這個 function 的 side effect：

```javascript
const pureAssoc = (key, value, object) => {
  const newObject = { ...object };
  newObject[key] = value;
  return newObject;
};

const person = { name: 'Bobo' };

const result = pureAssoc('shoeSize', 400, person);

console.log(person); // { name: 'Bobo' }
console.log(result); // { name: 'Bobo', shoeSize: 400 }
```

如此一來，我們在沒有改動到原本的 `person` 的情況下，得到我們想要的 `result`。於是這個原本不 pure 的 function，也變 pure 了。

::: warning
⚠️ <b>淺拷貝 v.s.深拷貝</b><br>
你的複製真的是成功的複製嗎？有沒有可能你其實沒有複製到，所以還是會改動到原本的 data？  
:::

## 🐳 為什麼我們需要 pure function？
大概了解 pure function 的定義和什麼是 pure function 之後，就要來問：所以為什麼需要 pure function？它是用來幹嘛的？

**1.immediately testable, maintain and refactor easier**

「相同的 input，永遠都輸出相同的 output。」這個 pure function 的特性使它能夠非常容易地被拿來測試。

當你寫的程式越來越龐大，程式碼的閱讀性與語法簡潔、易於測試、維護與除錯、易於規模化等等，都會變成要考量的重點，這時 pure function 的好處就會非常明顯──好讀、好維護、data的改動可以被追蹤、比較不會出現一些預期之外的錯誤（side effect）。

**2.是 functional programming 很重要的 basic concept。**

## 🐳 為什麼 pure function 在 React 裡面是重要的？

在 React 的官方文件 [Components and Props](https://reactjs.org/docs/components-and-props.html) 中，特別提到了一句話：

> All React components must act like **pure functions** with respect to their props.

![](https://i.imgur.com/FtP80vu.png)

pure function 在 React 當中之所以重要，是因為：
1. functional component：關係到 `useState()` 會不會將傳入的 state 視為不同的資料，然後重新 render。範例：[https://codesandbox.io/s/case-1-wd1dh?file=/src/App.js](https://codesandbox.io/s/case-1-wd1dh?file=/src/App.js)
2. 確保不管在任何情況之下，傳入相同的 input，都會渲染出相同的畫面給使用者看（output）。
2. redux：和 `useState()` 也是同樣的道理，所以 reducers 也規定必須是 pure function。
3. 還沒有 hooks 時，在 functional component 裡面，讓 props 只能是唯讀的，使資料在修改的時候比較好追蹤和管理。
4. A React component should be pure, this means the result of its render method should depend solely on the props and the state, and for the same properties and state render should give the same result. If render is not pure, it means it can return different results for the same input, so React cannot tell which parts of the DOM need to be updated based on the changes to the component. This is critical as the performance of React depends of this.

## 🐳 參考資源

- [What Is a Pure Function in JavaScript? - FreeCodeCamp](https://www.freecodecamp.org/news/what-is-a-pure-function-in-javascript-acb887375dfe/)
- [JavaScript: What Are Pure Functions And Why Use Them? - Medium](https://medium.com/@jamesjefferyuk/javascript-what-are-pure-functions-4d4d5392d49c)
- [Pure Functions in React - DEV](https://dev.to/keevcodes/pure-functions-in-react-2o7n)
- [Pure functional components in React - LogRocket](https://blog.logrocket.com/react-pure-components-functional/)
- [React Class vs. Functional Components - Medium](https://betterprogramming.pub/react-class-vs-functional-components-2327c7324bdd)
- [Why ReactJS components must act like pure functions?](https://stackoverflow.com/questions/41985547/why-reactjs-components-must-act-like-pure-functions)
