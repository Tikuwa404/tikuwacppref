---
title: VSCodeの導入
---
# VSCodeの導入
Visual Studio Codeをインストールして、初期設定を行います。

# 目次
- [[#VSCodeのインストール]]
- [[#Extensionのインストール]]
- [[#設定の変更]]

# VSCodeのインストール
VSCodeとは、Visual Studio Codeの略で、Microsoftが無料で提供してくれている開発環境です。簡単に言うと、ものすごく便利なテキストエディタです。

VSCodeのインストールはとても簡単です。公式サイトからインストーラーを入手し、インストールするだけです。
おすすめのオプションは次の通りです：
- デスクトップ上にアイコンを作成する
- サポートされているファイルの種類のエディターとして、Codeを登録する
- PATHへの追加

# Extensionのインストール
Extensionとは、VSCodeの拡張機能のことです。VSCodeが便利なのは、このExtensionsから好みのプログラミング言語をマークアップする機能を増やしたり、ビルド・デバッグの機能を増やしたりできるからなんですね。

Extensionのインストールはとても簡単です。VSCodeアプリ内のExtensionsタブに移動し、インストールするだけです。
おすすめのExtensionは次の通りです：
- Japanese Language Pack for Visual Studio Code
  VSCodeのUIを日本語にしてくれます
- C/C++ Extension Pack
  4つのC++用Extensionがセットになったものです

# 設定の変更
Ctrl+Shift+Pを押して、「C/C++: 構成の編集 (JSON)」をクリックします。出てきたファイルに、次のJSONを貼り付けます。これで、自動補完がC++23に対応します。g++.exeのパスはあなたのコンピュータに合わせてください。
```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "compilerPath": "（g++.exeのパス）",
            "compilerArgs": [
                "-std=c++23"
            ],
            "cStandard": "c17",
            "cppStandard": "gnu++23",
            "intelliSenseMode": "windows-gcc-x64"
        }
    ],
    "version": 4
}
```

# 関連ページ
[コンパイラのインストール](install-compiler)