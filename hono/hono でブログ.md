## hono setup
まず bun をインストール
```bash
curl -fsSL https://bun.sh/install | bash
```

新しいプロジェクトを作る
```bash
bun create hono@latest my-app
```

ローカルで実行する
```bash
bun run dev
```

# hono x 

```bash
bun create hono@latest my-app
```
コマンド自体は同じだが、使うテンプレートを `x-basic`にする

静的なブログなのでクライアント側のコードを削除する

- `app/client.ts`と`islands`を消す
- `vite.confit.tx`のクライアントの設定を消す
- `package.json`でクライアントをビルドしないようにする

クライアント側のコードもいるのかもしれない

[[SSG]] をするために `@hono/vite-ssg`をインストールする

```
bun add @hono/vite-ssg
```

[[MDX]] を使えるようにするため `@mdx-jp/rollup` をインストール

```bash
bun add @mdx-js/rollup
```

`app/routes/test.mdx`を作ると `localhost/test` でアクセスできるようになる

CSS が適用されない。

[[frontmatter]] も使えるように

```bash
bun add remark-frontmatter remark-mdx-frontmatter
```

