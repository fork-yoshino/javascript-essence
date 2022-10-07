# オブジェクト (Object)

JavaScriptのオブジェクトは、以下の2種類の意味に分類できる。

- Objectコンストラクタのインスタンス
- 非プリミティブ型を表すオブジェクト型


## Objectコンストラクタのインスタンス

Objectコンストラクタによって生成されるインスタンスのことをオブジェクトという。<br>
また、Objectオブジェクトは、JavaScriptで用意されている組み込みオブジェクトの1つである。

```javascript
// Objectコンストラクタ
const obj = new Object();
```

```javascript
// オブジェクトリテラル
const obj = {};
```

```javascript
console.log({} instanceof Object); // true
```

JavaScriptでは、Objectオブジェクトのコンストラクタを使う方法と、オブジェクトリテラルを使う方法の2通りでオブジェクトを生成する事ができる。<br>
オブジェクトリテラル`{}`は、Objectコンストラクタのインスタンス化（new Object）を簡略化して記述できるようにしたものである。


## 非プリミティブ型を表すオブジェクト型

JavaScriptのデータ型は、プリミティブ型とオブジェクト型に分けられる。<br>
プリミティブ型は、`Number`、`String`、`BigInt`、`Boolean`、`null`、`undefined`、`Symbol`の7つの基本の型を指し、それ以外の全てはオブジェクト型に分類される。<br>
