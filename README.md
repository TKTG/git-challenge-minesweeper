問題: Minesweeper
=================

あなたが転職した会社のリポジトリをみたところ、よくチェックされていない commit が散見されました。
これらの commit に checkout してしまうと、提供しているサービスがダウンしてしまいます。
データのバックアップに戻るだけで、サービスがダウンしてしまうようでは夜も眠れません。

`main` ブランチの祖先の commit に、壊れた CSV ファイルが含まれないようにしてください。
ただし、CSV を壊した commit とその修正の commit 以外の履歴を書き換えてはいけません。

CSV が壊れているかどうかは、`checker.pl`によって検証できます。
この `checker.pl` は `checker` ブランチから入手してください。

| 主要なブランチ              | ブランチ名 |
|:----------------------------|:-----------|
| リリースブランチ            | `main`   |
| 開発用ブランチ              |`develop`   |
| `checker.pl` のあるブランチ | `checker`  |


チェッカーの実行の仕方
----------------------

`checker.pl` の標準入力に CSV を入力してください。
終了コードから正常/異常を知ることができます。

```
cat users.csv | ./checker.pl

# メッセージで表示したければ、次のようにするとよい
cat users.csv | ./checker.pl && echo OK || echo NG
```


正答条件
--------

- 解答は、`origin` の `main` に push してください
- 間違っている commit とその修正の commit 以外の変更履歴を書き換えてはいけません
  - それ以外に、余分な commit があったり、commit が消えていたりすると NG です
