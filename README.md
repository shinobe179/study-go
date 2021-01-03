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
行ごと読み込む。実行回数が増えてくるとこっちのほうが早い。

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

`fmt.Scan()` のように半角スペース区切りで読み込みたい場合は以下のようにする。

```go
func main() {
	sc.Split(bufio.ScanWords)
	sc.Scan()
...
```

# forループ

## 指定回数のループ

```go
for i :=0; i < n; i++ {
	// some processing
}
```

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

`[]string` にしなくても、 `string()` を使えばよさそう。

```go
func main() {
	var a string
	fmt.Scan(&a)

	for _, s := range a {
		fmt.Println(string(s))
	}
}
```

# 配列(スライス)の操作

## 配列宣言時の要素数
要素数は定数でないといけない。

```go
// こういうことはできない
let n int
fmt.Scan(&n)
ss = [n]string
```

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

## 配列の挿入(多次元配列)

```go
// 宣言
arr := [][]int{}

// 挿入
arr = append(arr, []int{1, 2})
```

## ソート
`sort` ライブラリを使えばいいっぽい

```go
// 文字列ソート ABC042 Bより
func main() {
	var n, l int
	fmt.Scan(&n, &l)
	ss := []string{}

	for i := 0; i < n; i++ {
		sc.Scan()
		ss = append(ss, sc.Text())
	}
	sort.Sort(sort.StringSlice(ss)) // sort.IntSlice()などもある
	fmt.Println(strings.Join(ss, ""))
}
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
