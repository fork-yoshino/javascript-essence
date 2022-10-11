# プロトタイプ (prototype)

プロトタイプとは、インスタンス化に関係する特別なプロパティとして、関数オブジェクトに保持されている。

```javascript
function Test() {}

console.log('prototype' in Test); // true

console.log(typeof Test.prototype); // object
```

prototypeプロパティは、関数を定義したときに自動的に設定される。<br>
また、prototypeプロパティに設定されている値はオブジェクトになる。


## prototypeオブジェクト

prototypeオブジェクト（prototypeプロパティに設定されているオブジェクト）に登録された関数は、インスタンスから実行可能なメソッドになる。

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Personコンストラクタのprototypeオブジェクトのhelloプロパティに無名関数を登録
Person.prototype.hello = function() {
  console.log('hello ' + this.name);
}

const bob = new Person('Bob', 18);

bob.hello(); // hello Bob
```

上記のコードでは、`bob.hello()`としたときに、prototypeに登録したhello関数で使われる`this`が呼び出し元オブジェクト（bob）を参照している。<br>
そのため、prototypeに登録される関数は、クラスのメソッドと同等に扱われることが分かる。


## __proto__

```javascript
function Test() {}
Test.prototype.hello = function() {console.log('こんにちは')};
const test = new Test();

console.log(test.__proto__ === Test.prototype); // true

test.__proto__.hello(); // こんにちは
```

new演算子によってインスタンスを作成するとき、コンストラクタ関数のprototypeプロパティに格納されているオブジェクトへの参照が、インスタンスの`__proto__`という特別なプロパティにコピーされる。<br>
インスタンス化されたオブジェクトからは、`__proto__`を通してprototypeに登録した関数を実行できる。

```javascript
function Test() {}
Test.prototype.hello = function() {console.log('こんにちは')};
const test = new Test();

console.log(test.__proto__.hello === test.hello()); // true

test.hello(); // こんにちは
```

`__proto__`は記述を省略することができる。<br>
そのため、一般的にはインスタンスのメソッドの実行時には`__proto__`は記述されない。<br>

コンストラクタ関数には`prototype`、インスタンスには`__proto__`という特別なプロパティが存在し、同じオブジェクトを参照している。<br>
これによって、コンストラクタのprototypeに定義したメソッドは、生成したすべてのインスタンスで共有され、インスタンスのメソッドとして呼び出すことができる。
