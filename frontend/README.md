# Next.js × Laravelのフルスタック環境構築

- frontend
  - Next.js
  - TypeScript
  - TailwindCSS

## プロジェクト作成

※私がtailwind中毒者なので最初からtailwind入りのもので始める。

```
npx create-next-app -e with-tailwindcss frontend 
```

## Axiosをインストール

バックエンドからAPI取得のためAxiosをインストールする

```
frontend> yarn add axios
```

## SWRをインストール

データ取得の必要のないページの高速レンダリング及びデータ取得後のページレンダリングを可能にするためにSwrをインストールする

```
frontend> yarn add swr
```

## prettierをインストール(欲しい人だけ)

ソースコードを整形してくれるツールであるprettierをインストール

※ちなみに私はインストールしない派なのでいれないです。

```
frontend> yarn add --save-dev prettier
```

インストールしたら.prettierrc.jsonというファイルを作成し、その中に自身の好きな設定を記載する。

※以下例(.prettierrc.json)

```json
{
  "singleQuote": false,
  "semi": true,
  "tabWidth": 4,
}
```

次にpackage.jsonのscriptに追記

```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "format": "prettier --check --ignore-path .gitignore .", //<-ここを追加
  "format:fix": "prettier --write --ignore-path .gitignore ."  //<-ここを追加
},
```

以下コマンドで実行
formatはコードが汚いところを指摘してくれる
format:fixは汚いところを修正してくれる
```
frontend> yarn format
frontend> yarn format:fix
```