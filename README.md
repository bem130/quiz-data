# quiz-data

[bem130/quiz](https://github.com/bem130/quiz)用の問題JSONを収録する。

## 読み込み方法

アプリの「ユーザー・表示・問題一覧」→「問題一覧のURL」へ次のURLを入力し、「問題一覧を読み込む」を押す。

```text
https://raw.githubusercontent.com/bem130/quiz-data/main/entry-v3.json
```

GitHub Pagesを`main`ブランチのルートから配信すると、次のURLでも読み込める。

```text
https://bem130.github.io/quiz-data/entry-v3.json
```

一覧ファイル名は`entry-v3.json`である。`entry.json`も同じ5種類を参照する互換用の入口として維持する。

## 収録内容

| ファイル | 内容 | 問題数 |
|---|---|---:|
| `chemistry-2017-2026-v3.json` | 2017–2026年の出題論点に基づく独自演習 | 137 |
| `amino-protein-detection-v3.json` | amino acid・proteinの検出反応 | 24 |
| `sugar-detection-v3.json` | 糖類の検出反応・加水分解・電子収支 | 24 |
| `sugar-names-v3.json` | 糖の構造と名称 | 10 |
| `amino-acid-names-v3.json` | 標準amino acid 20種の骨格構造と名称 | 20 |

合計215問。構造式SVG、反応式、解説、出典は各JSONに収録する。

`standalone-choice-v3.json`は通常の択一問題のサンプルとして残している。一覧には上記5種類を登録している。

## 更新

問題JSONを更新してpushした後、アプリの「更新」で再取得する。
一覧に追加する場合は、`entry-v3.json`と`entry.json`の`files`へ一覧ファイルからの相対パスを登録する。

```json
{
  "version": 3,
  "label": "問題集の名前",
  "files": ["./example-v3.json"]
}
```

各問題ファイルはアプリのv3スキーマを使用する。通常の択一問題では`display: "none"`、問題固有の選択肢では`choice_from_field`を使用する。
