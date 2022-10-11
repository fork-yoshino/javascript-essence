# 関数 (Function)

## 関数は実行可能なオブジェクト

```javascript
// 空の関数を定義
function fn(a, b) {
  console.log(a, b);
}

fn.name = '太郎';

fn.hello = function() {
  console.log('こんにちは');
}

// 関数の実行
fn(0, 1); // 0 1

// プロパティの取得
console.log(fn.name); // 太郎

// メソッドの実行
fn.hello(); // こんにちは
```

JavaScriptにおいて、関数はオブジェクトの一種であり、オブジェクト`{}`と異なるのは「実行可能である」という点のみである。<br>
そのため、関数に対してもプロパティやメソッドを設定することができる。


## 仮引数と実引数の個数

```javascript
function fn(a, b) {
  console.log(a, b);
}

fn(0, 1) // 0 1
fn(0); // 0 undefined
```

JavaScriptの関数は、仮引数が2つ定義されていた場合でも、1つの引数のみを呼び出して実行することができる。<br>
また、呼び出さなかった仮引数には`undefined`が渡される。


## 関数名の重複

### 関数宣言の場合

```javascript
function fn(a, b) {
  console.log(a, b);
}

function fn(a) {
  console.log('2nd');
}

fn(1); // 2nd
```

関数宣言で関数名が重複している場合、エラーにはならず、後から宣言された方の関数によって上書きされる。<br>
また、JavaScriptの場合、仮引数が異なる場合でも違う関数とはみなされない。

#### 追記
関数宣言の場合でも、`ES Modules`を有効にした場合、重複した関数名を宣言したときにエラーを発生させることができる。

### 関数式の場合

```javascript
const fn = function(a, b) {
  console.log(a, b);
}

function fn(a) {
  console.log('2nd');
}

fn(1); // エラー
```

関数式の場合、`const`を使用することで、重複した関数名を宣言したときにエラーを発生させることができる。


## 実行文の記述位置

### 関数宣言の場合

```javascript
fn(0, 1); // 0 1

function fn(a, b) {
  console.log(a, b);
}
```

関数宣言で関数定義を行った場合、関数の宣言文より前に実行文を記述できる。

### 関数式の場合

```javascript
fn(0, 1); // エラー

const fn = function(a, b) {
  console.log(a, b);
}
```

関数式で関数定義を行った場合、関数定義より前に実行分を記述するとエラーが発生する。
