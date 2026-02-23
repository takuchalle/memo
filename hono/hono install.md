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
bun create hono@latest my-pp
```
コマンド自体は同じだが、使うテンプレートを `x-basic`にする


SSG をするために `@hono/vite-ssg`をインストールする

```
bun add @hono/vite-ssg
```

MDX を使えるようにするため `@mdx-jp/rollup` をインストール

```bash
bun add @mdx-js/rollup
```

frontmatter も使えるように

```bash
bun add remark-frontmatter remark-mdx-frontmatter
```

