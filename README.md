study-go
---

# 標準入力の受付

## fmt.Scan()によるスキャン
半角スペース区切りで読み込む。複数個の値を指定可能。

```go
func main() {
	var a, b string
	fmt.Scan(&a, &b)
	fmt.Println(a, b)
```

## bufioによるスキャン
行ごと読み込む。

```go
var sc = bufio.NewScanner(os.Stdin)

func main() {
	sc.Scan()
	// 半角スペース区切りで配列にする
	strings := strings.Splist(sc.Text(), " ")
	// 1文字ずつの配列にしたいなら
	// strings := strings.Split(sc.Text(), "")
}
```

# forループ

## 配列(文字列)
`rune` の扱いに困りたくないので、 `[]string` 型にしてから `range` でループするのが手っ取り早そう。

```go
func main() {
	var a string
	fmt.Scan(&a)
	strs := strings.Split(a, "")

	for _, s := range strs {
		fmt.Println(s)
}
```

# 配列の操作

## 結合
`strings.Join()` を使う。

```go
fmt.Println(strings.Join(strs, "")
```

## 挿入
`append()` を使う。(元々のオブジェクトに挿入するのではなく)挿入したオブジェクトを戻り値として戻すので注意。

```go
// 正
strs = append(strs, s)

// 誤
append(strs, s)
```

# マップの操作

## 初期化
初期化しないと、要素を挿入した時panicで落ちる(コンパイルエラーにはならない)。

```go
m := map[string]string{}

// もしくは
var m map[string]string
m = map[string]string{}
```

## マップ内にキーが存在するかを調べる

```go
_, ok := m["key"]
if ok {
	fmt.Println("Key is exist")
} else {
	fmt.Println("Key is not exist")
}
```
