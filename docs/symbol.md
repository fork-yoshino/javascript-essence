# シンボル (Symbol)

```javascript
// シンボルの定義
const s = Symbol('hello');
console.log(s); // Symbol(hello)
console.log(typeof s); // symbol 
```

シンボルは、オブジェクトのプロパティの重複を避けるための一意の値を生成するときに使用される。<br>
また、シンボルはES6で追加された特殊な型であり、シンボル型はプリミティブ型に分類される。

```javascript
const s1 = Symbol('hello');
const s2 = Symbol('hello');
console.log(s1 === s2); // false
```

シンボルの定義時に引数にラベルを渡すことができるが、ラベルの値が同じでも生成される値は異なる。<br>
ラベルは、コンソール上でシンボルを区別するための目印として使用される。

```javascript
const key1 = Symbol();
const key2 = Symbol();

// シンボルをキーにプロパティとメソッドを定義
const obj = {
  [key1]: 'hello',
  [key2]() {
    console.log('こんにちは');
  }
}

// 呼び出し
console.log(obj[key1]); // hello
obj[key2](); // こんにちは
```

シンボルを使用して定義したプロパティを呼び出す場合、必ずブラケット記法を使用する必要があり、ドット記法で呼び出すことはできない。
