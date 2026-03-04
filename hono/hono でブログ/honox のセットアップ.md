ちょっと古いけど、シンプルなブログを作るにはちょうどいい。
https://github.com/yossydev/honox-blog-templete/
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

## hono x 

```bash
bun create hono@latest my-app
```
コマンド自体は同じだが、使うテンプレートを `x-basic`にする

静的なブログなのでクライアント側のコードを削除する

- `app/client.ts`と`islands`を消す
- `vite.confit.tx`のクライアントの設定を消す
- `package.json`でクライアントをビルドしないようにする => css を吐き出すために必要だった

[[SSG]] をするために `@hono/vite-ssg`をインストールする

```
bun add @hono/vite-ssg
```

[[MDX]] を使えるようにするため `@mdx-jp/rollup` をインストール

```bash
bun add @mdx-js/rollup
```

`app/routes/test.mdx`を作ると `localhost/test` でアクセスできるようになる

CSS が適用されない。`dist/.vite/manifest.json` が必要そう。

[[frontmatter]] も使えるように

```bash
bun add remark-frontmatter remark-mdx-frontmatter
```

