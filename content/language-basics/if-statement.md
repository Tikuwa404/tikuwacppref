---
title: if文について
---
# `if`文について
`if`文の使い方を紹介します。

# 目次
- [[#基本の使い方]]
- [[#`bool`型へのキャストが可能な型を条件にした`if`文]]
- [[#変数定義を組み合わせた`if`文]]

# 基本の使い方
`if`文は括弧の中の`bool`型が`true`なら続く文を実行します。また、`if-else`文を使用することで括弧の中の`bool`型が`true`の場合と`false`の場合のそれぞれの文に分岐できます。

文は1つの文か`{}`で囲った複数の文が使用可能です。

## 例
整数が42ならYesを出力する。また、その整数が奇数か偶数か出力する。
### ソースコード
```cpp
#include <iostream>

int main()
{
    int number = 42;

    if (number == 42) {
        std::cout << "Yes\n";
    }

    if (number % 2 == 0)
        std::cout << "Even number\n";
    else
        std::cout << "Odd number\n";
}
```
### 出力結果
```plain
Yes
Even number

```

# `bool`型へのキャストが可能な型を条件にした`if`文
`bool`型へのキャストが実装されている型は`if`文の条件に使用可能です。いくつか例を挙げます。ここで`T`は任意の型です。

| 型名                         | どのように変換されるか（変数名を`x`とする） |
| -------------------------- | ----------------------- |
| `int`                      | `x != 0`                |
| `float`                    | `x != 0.0f`             |
| `T*`                       | `x != nullptr`          |
| `std::uniqur_ptr<T>`       | `x.get() != nullptr`    |
| `std::basic_istream<char>` | `x._M_ok`               |
`std::cin`は`std::basic_istream<char>`のオブジェクトで、`_M_ok`は次の入力があるかを指す`bool`型の値です。`std::cin >> obj`が`std::cin`を返すことから、`if`文や`while`文の条件に`std::cin >> obj`を指定すると入力と同時に次の入力があるかを調べられます。

## 例
整数へのポインタが値を保持しているか確認し、その整数が42ならYesを出力する。
### ソースコード
```cpp
#include <iostream>
#include <memory>

int main()
{
    std::unique_ptr<int> p(new int(42));

    if (p && *p == 42)
        std::cout << "Yes\n";
}
```
### 出力結果
```plain
Yes

```

# 変数定義を組み合わせた`if`文
`if(変数定義; 条件式)`は、定義した変数がその`if`文のスコープの中に生成されます。その変数は条件式内でも使用できます。
## 例
文字列の中から最初の`'o'`を探し、次の文字を出力する。`'o'`が無ければ何も出力しない。
### ソースコード
```cpp
#include <iostream>
#include <string>

int main()
{
    std::string s("Hello, World!");
    if (std::size_t i = s.find('o'); i != std::string::npos) {
        std::cout << s[i + 1] << '\n';
    }
}
```
### 出力結果
```plain
,

```

# 変数定義を条件にした`if`文
`if(変数定義)`は、配列ではない変数を、代入または初期化をする形で定義した場合、条件として使用できます。代入または初期化後の値が`bool`型か`bool`型に変換できる型である必要があります。

# 関連ページ