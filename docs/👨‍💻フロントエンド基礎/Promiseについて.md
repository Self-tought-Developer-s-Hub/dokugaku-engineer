# Promiseについて
TypeScript（およびJavaScript）における`Promise`は、非同期操作の最終的な完了（または失敗）およびその結果の値を表します。簡単に言うと、`Promise`は将来的に利用可能になる値（または失敗の理由）を表すオブジェクトです。これは非同期プログラミングを容易にするための強力な抽象化です。

### Promise.all()

`Promise.all()`は、複数のPromiseを並行して実行し、すべてのPromiseが解決された場合にのみ解決する新しいPromiseを返します。一つでも拒否されると、`Promise.all()`は直ちに拒否されます。

#### コード例
```typescript
let promise1 = Promise.resolve(3);
let promise2 = 42;
let promise3 = new Promise<string>((resolve, reject) => {
    setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
    console.log(values);  // [3, 42, "foo"]
});
```

### async-await

`async`と`await`は、非同期操作をより読みやすく書くためのシンタックスシュガーです。`async`関数は自動的にPromiseを返し、その関数内で`await`キーワードを使うことで、Promiseの解決を待つことができます。

#### コード例
```typescript
async function asyncCall() {
    let result = await Promise.resolve("Hello");
    console.log(result); // "Hello"
}

asyncCall();
```

### Promise.then, Promise.catch

- `Promise.then()`: Promiseが解決されたときに実行される処理を追加します。`.then()`は別のPromiseを返し、チェーンすることができます。
- `Promise.catch()`: Promiseが拒否されたときに実行される処理を追加します。これはエラーハンドリングに使われます。

#### コード例
```typescript
let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("done"), 1000);
});

promise.then(
    result => console.log(result), // "done" が表示される
    error => console.log(error)    // 実行されない
);

let promiseWithError = new Promise((resolve, reject) => {
    setTimeout(() => reject(new Error("Error!")), 1000);
});

promiseWithError.then(
    result => console.log(result),
    error => console.log(error)    // "Error!" が表示される
);

// または catch() を使用してエラーを捕捉する
promiseWithError.catch(
    error => console.log(error)    // "Error!" が表示される
);
```

これらの例を通じて、TypeScriptにおける非同期処理の基本的なパターンを理解できます。非同期処理は非常に強力ですが、適切に理解し使用することが重要です。

### 参考リンク
- [イベントループとプロミスチェーンで学ぶJavaScriptの非同期処理](https://zenn.dev/estra/books/js-async-promise-chain-event-loop)