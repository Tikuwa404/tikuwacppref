---
title: メンバ初期化子リストを持つコンストラクタ
---
# メンバ初期化子リストを持つコンストラクタ
メンバ初期化子リストを持つ`class`や`struct`の初期化について説明します。

# 目次
- [[#メンバ初期化子リストとは]]

# メンバ初期化子リストとは
次のソースコードを見てみましょう。
```cpp
class MyClass {
private:
    int x_val;
    float f_val;
public:
    MyClass() : x_val(42), f_val(3.14f) {}
};
```
コンストラクタの定義がされていますが、`: x_val(42), f_val(3.14f)`という普通の関数やメンバ関数には無い部分があります。この部分がメンバ初期化子リストです。（初期化子リストとは異なります。）メンバ初期化子リストでメンバ変数名の後ろにつける括弧は`()`と`{}`だと意味が異なる場合があります。これは、その型の変数の初期化にどちらの括弧を用いるべきかによって使い分けることができます。

メンバ定数も初期化できます。また、デフォルトメンバ初期化子（次の例では`= 10`）を持つメンバ変数やメンバ定数もメンバ初期化子リストの値で初期化できます。
## 例
`()`と`{}`で初期化する
### ソースコード
```cpp
#include <print>
#include <vector>

class MyClass {
public:
    const int val1, val2 = 10;
    std::vector<float> vec1, vec2;

    MyClass() : val1(42)
              , val2{42}
              , vec1(3, 3.14f)
              , vec2{3, 3.14f} {}

    void print() {
        std::println("{}", this->val1);
        std::println("{}", this->val2);
        std::println("{}", this->vec1);
        std::println("{}", this->vec2);
    }
};

int main() {
    MyClass my_class;
    my_class.print();
}
```
### 出力結果
```plain
42
42
[3.14, 3.14, 3.14]
[3, 3.14]

```

# 関連ページ