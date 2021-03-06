# zipcode-japan-es / 郵便番号ESモジュール

KEN_ALL.ZIPをデータソースとして使った、郵便番号データを[地方公共団体コード](https://github.com/code4sabae/lgcode)と町名、町名のよみへ変換するESモジュールです。  
This ES module converts Japanese zip codes to addresses. (Local government codes and town names.)  

[![esmodules](https://taisukef.github.com/denolib/esmodulesbadge.svg)](https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Modules)
[![deno](https://taisukef.github.com/denolib/denobadge@1.5.2.svg)](https://deno.land/)

## ブラウザ上での使用例

ブラウザで開く [郵便番号から地方公共団体コードと町名変換](https://code4sabae.github.io/zipcode-japan-es/main.html)  
src on GitHub [main.html](https://github.com/code4sabae/zipcode-japan-es/blob/master/main.html)  


## API (web / Deno)

```
import { fromZipCode } from "https://code4sabae.github.io/zipcode-japan-es/zipcode.mjs";

console.log(await fromZipCode(9160042));
```
出力
```
[{ zipcode: "9160042", lgcode: "18207", town: "新横江", townyomi: "シンヨコエ" }]
```
郵便番号（半角、全角、ハイフン付き、空白付きOK！）を渡すと、該当する配列と正規化した郵便番号を返します。見つからない場合は長さ0の配列 [] を返します。  
toplevel await 非対応のブラウザでは、async関数内で使用してください。  


- 地方公共団体コードは、[地方公共団体コード ESモジュール](https://github.com/code4sabae/lgcode)を使って都道府県と市区町村に変換できます

## インストール

以下の手順でインストールしローカルでも使用できます。

```
$ github clone https://github.com/code4sabae/zipcode-japan-es.git
```

## データ生成、データ更新

```
$ cd tools
$ sh makedata.sh
```
[読み仮名データの促音・拗音を小書きで表記するもの - zip圧縮形式 日本郵便](https://www.post.japanpost.jp/zipcode/dl/kogaki-zip.html) を使用します

## テスト

```
$ deno test -A
```

## 依存モジュール

util.mjs (decodeCSV, encodeCSV)  
https://github.com/taisukef/util  

全角半角統一コンポーネント IMIMojiConverter  
https://github.com/code4sabae/imi-moji-converter-es  

## 関連記事

KEN_ALL!? 郵便番号ESモジュールで開発効率化！ 経産省もGitHub公開スタート
https://fukuno.jig.jp/2871

Deno対応ESモジュール対応、IMIコンポーネントツールx4とDenoバッジ  
https://fukuno.jig.jp/2866  

日本政府発のJavaScriptライブラリを勝手にweb標準化するプロジェクト、全角-半角統一コンポーネントのESモジュール/Deno対応版公開  
https://fukuno.jig.jp/2865  
