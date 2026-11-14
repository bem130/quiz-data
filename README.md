# quiz-data

[bem130/quiz](https://github.com/bem130/quiz)用の問題JSONを収録する。

## 読み込み方法

アプリの「ユーザー・表示・問題一覧」→「問題一覧のURL」へ次のURLを入力し、「問題一覧を読み込む」を押す。

```text
https://bem130.github.io/quiz-data/entry-v3.json
```

GitHub Actionsが`main`へのpushでGitHub Pagesへ自動公開する。Raw URLからも読み込める。

```text
https://raw.githubusercontent.com/bem130/quiz-data/main/entry-v3.json
```

一覧ファイル名は`entry-v3.json`である。`entry.json`も同じ7種類を参照する互換用の入口として維持する。

## 収録内容

| ファイル | 内容 | 問題数 |
|---|---|---:|
| `chemistry-2017-2026-v3.json` | 2017–2026年の出題論点に基づく独自演習 | 137 |
| `amino-protein-detection-v3.json` | amino acid・proteinの検出反応 | 24 |
| `sugar-detection-v3.json` | 糖類の検出反応・加水分解・電子収支 | 24 |
| `sugar-names-v3.json` | 糖10種の構造と名称・双方向 | 20 |
| `amino-acid-names-v3.json` | 標準amino acid 20種の構造と名称・双方向 | 40 |
| `sugar-occurrence-v3.json` | 糖の含有・構成成分・生成源 | 10 |
| `sugar-hydrolysis-v3.json` | 二糖の基質・酵素・生成物 | 12 |

合計267問。構造式SVG、反応式、解説、出典は各JSONに収録する。名称問題の解説には語源、存在例、直接関連する反応・酵素も収録する。

糖の環構造・anomer・glycosidic結合にはHaworth投影式、鎖状構造・立体配置の比較にはFischer投影式を用いる。反応位置や結合位置の説明に必要な炭素番号を図に付記する。

Haworth図は下側を手前とする視点に揃え、奥側の環結合を細線、左右の手前へ向かう辺をwedge、最前の辺を太線で描く。図示の基準は[IUPAC ST-1.9](https://iupac.qmul.ac.uk/drawing/stereo.html#ST19)および[2-Carb-5.4・5.5](https://iupac.qmul.ac.uk/2carb/05.html)である。

名称問題では各糖・amino acidをtableの1行として、名前と構造を一対一に対応づける。`choice_from_entities`で他の行から選択肢を生成し、構造から名称、名称から構造の両方向を出題する。

含有問題は、蜂蜜のGlucose／Fructoseなどを`listkey`の正答集合として表す。二糖の酵素問題は1反応をtableの1行とし、酵素から基質、基質から酵素を出題する。生成物を問うpatternは各行の`productChoices`から4択を生成する。各穴埋めは`display: "inline"`を用い、pattern直下に解答欄を1個持つ。

`standalone-choice-v3.json`は通常の択一問題のサンプルとして残している。一覧には上記7種類を登録している。

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
