# ハンズオンチームの秘密基地＃＃＃ステージング環境＃＃＃

## ここはなに？

まさるの勉強部屋参加者のハンズオンチームの検証結果置き場です。

## つかいかた

- 権限のあるメンバーは hugo を使用して記事を投稿できます。

1. Hugo をローカルに入れます
2. git を使います。

```
# ローカルリポジトリ作成
git init

# リモートリポジトリに接続
git remote add origin https://github.com/masaru-study/-----test-----verify-note.git

# リモートリポジトリの内容を取得
git fetch

# ローカルブランチ作成
git checkout -b #ローカルブランチ名# origin/main

# hugoでコンテンツを作成する
hugo new content #カテゴリ名#/#ページ名#.md
もしくは
content/#カテゴリ名#/#ページ名#.mdを手動で新規作成

# 記事を編集する（draft = falseにしないとgit actionが走らないです…）
content/#カテゴリ名#/#ページ名#.md

# ワークツリーからインデックスへのファイルの登録を行う
git add -A

# ローカルリポジトリに登録
git commit -m "#コミットコメントを入れる#"

# リモートリポジトリにコピーする
git push origin #ローカルブランチ名#
```

3. [Github リポジトリ](https://github.com/masaru-study/-----test-----verify-note)に Web アクセスして結合する。
   1. Pull Request
   2. New Pull Request
   3. base:main ← compare:#ローカルブランチ名#
   4. Create request
   5. （説明を追加）
   6. Create pull request
   7. Merge pull request
   8. Conform Merge
4. [公開 Web ページ](https://masaru-study.github.io/-----test-----verify-note/)を確認して更新されていれば完了

## 付録:Discord 通知を無しにする場合

プロジェクトのルートディレクトリに no_discord.txt を配置すると Discord 通知を行わなくなります。
ステージング環境ではテストする際に Github の設定から secrets の書き換えが必要になります。
書き換えると他の人がテストできないので注意してください。書き換え後に復元はできません。

1. Settings
2. Secrets and variables
3. Actions
4. Repository secrets → DISCORD_WEBHOOK_STAGING → 鉛筆マーク
5. Discord から発行してきた URL を貼り付ける
6. 末尾に /github をつける

## 付録:ディレクトリ構造

```
│
├── content
│   ├── _index.md         ・・・トップページの記事ファイル。
│   │
│   ├── cloud             ・・・Cloudカテゴリの記事を入れるフォルダ。_index.mdはカテゴリトップページ。
│   │   ├── _index.md
│   │   └── ＊＊＊.md
│   ├── general           ・・・Generalカテゴリの記事を入れるフォルダ。_index.mdはカテゴリトップページ。
│   │   ├── _index.md
│   │   └── ＊＊＊.md
│   ├── network           ・・・Networkカテゴリの記事を入れるフォルダ。_index.mdはカテゴリトップページ。
│   │   ├── _index.md
│   │   └── ＊＊＊.md
│   ├── other             ・・・Otherカテゴリの記事を入れるフォルダ。_index.mdはカテゴリトップページ。
│   │   ├── _index.md
│   │   └── ＊＊＊.md
│   └── server            ・・・Serverカテゴリの記事を入れるフォルダ。_index.mdはカテゴリトップページ。
│       ├── _index.md
│       └── ＊＊＊.md
│
├── static
│   ├── img               ・・・画像を入れるフォルダ。記事内で../../img/＊＊＊とすると参照する。
│   │   ├── ＊＊＊.py
│   │   └── ＊＊＊.zip
│   └── other             ・・・画像以外を入れるフォルダ。記事内で../../file/＊＊＊とすると参照する。
│       ├── ＊＊＊.svg
│       └── ＊＊＊.jpg
│
├── README.md             ・・・Githubリポジトリに表示される説明文。公開Webページには表示されない。
│
├── hugo.toml             ・・・公開Webページの設定ファイル。原則編集しない。
│
├── archetypes
│   └── default.md        ・・・記事ファイルのテンプレートファイル。原則編集しない。
│
└── themes                ・・・テーマが入っているフォルダ。原則編集しない。
    └── ＊＊＊
```
