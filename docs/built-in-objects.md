# 組み込みオブジェクト (Built-in objects)

組み込みオブジェクトとは、JavaScriptエンジンによってあらかじめ提供されているオブジェクト群のことである。


## Windowオブジェクト

Windowオブジェクトは、開発者が書いたコードが実行される前にすでに`window`という識別子（オブジェクト名）で、JavaScriptエンジンによってインスタンス化されており、この`window`を通してブラウザを操作することができる。

```javascript
const arry = new window.Array(1, 2, 3, 4);
console.log(arry); // [1, 2, 3, 4]
```
```javascript
const arry = new Array(1, 2, 3, 4);
console.log(arry); // [1, 2, 3, 4]
```

Windwowオブジェクト（window）はグローバルオブジェクトと呼ばれる特別なオブジェクトであり、グローバルオブジェクト名を省略してプロパティやメソッドを呼び出せるという特徴がある。


## ラッパーオブジェクト

ラッパーオブジェクトとは、プリミティブ値を内包するオブジェクトのことである。

```javascript
// ラッパーオブジェクト（String）を呼び出して使用
const str = 'hello';
console.log(str.toUpperCase()); // HELLO
```

文字列などのプリミティブ型は、単なる値のためオブジェクトのようにメソッドなどは保持していない。しかし、JavaScriptでは、上記のようにプリミティブ値に続けてメソッドを記述することができる。<br>
これは、プリミティブ値に続けてメソッドやプロパティが記述された場合には、そのプリミティブ値に対応するラッパーオブジェクトのメソッドやプロパティが暗黙的に呼び出されるという仕様になっているためである。

```javascript
// Stringオブジェクトとして宣言して使用
const str = new String('hello');
console.log(str.toUpperCase()); // HELLO
```

`'hello'`のような文字列のような場合のラッパーオブジェクトは、`String`オブジェクトである。そのため、`'hello'`に続けてStringオブジェクトのメソッドやプロパティを使用することができる。<br>
また、文字列をStringオブジェクトとして宣言することもできる。

```javascript
const str = 'hello';
console.log(str instanceof String); // false
```

プリミティブ型として宣言した値はあくまでプリミティブ値なので、変数に代入したとしてもオブジェクトに変換されるわけではない。メソッドやプロパティにアクセスするときのみ、ラッパーオブジェクトを通してメソッドやプロパティにアクセスしている。
