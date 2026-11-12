# quiz-data

bem130/quiz 用の問題ファイルを置くリポジトリである。GitHub Pages で公開し、アプリから外部 entry として読み込む。

## 読み込み方法

アプリの設定「ユーザー・表示・問題一覧」にある「問題一覧のURL」へ次を入力し、「問題一覧を読み込む」を押す。

```
https://bem130.github.io/quiz-data/entry.json
```

## 問題ファイルの追加

1. v3 スキーマの問題 JSON をこのリポジトリへ追加する。
2. `entry.json` の `files` へ、そのファイルへの相対パスを追加する。
3. push すると Pages へ再公開される。アプリ側では「更新」で最新化できる。

`entry.json` の形式は次のとおりである。

```json
{
    "version": 3,
    "label": "表示名",
    "files": ["./example-v3.json"]
}
```

同梱の `standalone-choice-v3.json` は、通常の択一問題（`display: "none"` と `choice_from_field`）のサンプルである。
