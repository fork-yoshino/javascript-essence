# クロージャ (Closure)

クロージャとは、関数内で使用されている変数がレキシカルスコープの変数の値を保持し続ける状態のことを指す。


## 動的な関数生成

```javascript
function addNumberFactory(num) {
  fucntion addNumber(value) {
    return num + value;
  }
  return addNumber;
}

// 引数に5を足す関数
const add5 = addNumberFactory(5);
console.log(add5(10)); // 15

// 引数に10を足す関数
const add10 = addNumberFactory(10);
console.log(add10(10)); // 20
```

上記のコードでは、関数`addNumberFactory`に渡す引数によって、処理内容が異なる2つの関数`add5`、`add10`を作成している。<br>
一般的に関数内で使用される引数や変数は、関数の終了とともに参照不可能になる（ガベージコレクション）が、上記のコードのように、レキシカルスコープの変数`num`が保持する値を使用している関数`addNumber`が戻り値として実行元に返される場合には、変数`num`の値はガベージコレクションの対象とはならず、保持し続けれられることになる。<br>
このようにクロージャを利用することで、処理内容の異なる関数を動的に作成することができる。


## 変数の値の保持

```javascript
function incrementFactory() {
  let count = 0;
  return function() {
    console.log(++count);
  }
}

const increment = incrementFactory();

increment(); // 1
increment(); // 2
increment(); // 3
```

上記のコードでは、`incrementFactory`のreturnに続く無名関数内で、レキシカルスコープの変数`count`の値を使用している。これによって、`increment()`を実行したときには変数`count`の値は継続して保持されるため、`++count`によって現状のcountの値に対して1加算した結果がコンソールに表示される。<br>
このようにクロージャは、継続的に値の状態を保存することができるため、関数内で使う値の状態を保持し続けたいときにも利用される。
