# コンストラクタ関数 (Constructor Function)

コンストラクタ関数とは、新しくオブジェクトを生成するための雛形となる関数である。<br>
関数名には、一般的な関数と区別するためにパスカルケース（アッパーキャメルケース）を使用する。

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const bob = new Person('Bob', 18);
const tom = new Person('Tom', 33);

console.log(bob); // {name: "Bob", age: 18}
console.log(tom); // {name: "Tom", age: 33}
```

`new`演算子でオブジェクトを生成することを「インスタンス化」といい、生成されたオブジェクトを「インスタンス」という。<br>

コンストラクタ関数内の`this`は、生成されるオブジェクトのインスタンスを参照する。<br>
