# my-mkdocs-i18n-sample
このプロジェクトは、MkDocsのプラグインmikeの試使用プロジェクトである。<br>
サンプルページ：https://tomoten-umino.github.io/my-mkdocs-mike/

# 動作確認した環境
- OS : Ubuntu 20.04
- CPU : Intel(R) Pentium(R) CPU G4560 @ 3.50GHz
- RAM : 8GB
- Software
  - docker : 20.10.5
  - docker-compose : 1.24.1
  - VSCode : 1.59.0

# 使い方
## ディレクトリ構成

```bash
my-mkdocs-mike
├── .devcontainer
│   └── devcontainer.json
├── .github
│   └── workflows
│       └── mkdocs-deploy.yml
├── Dockerfile
├── LICENSE
├── README.md
├── docker-compose.yml
├── docs
│   ├── index.ja.md
│   ├── index.md
│   └── topic1（中身は省略。参考ページ[2]参照。）
├── mkdocs.yml
├── requirements.txt
└── site
```

## devcontainer立ち上げ、セットアップ
- Gitリポジトリをcloneします。その後、my-mkdocs-mike以下に移動し、VS Codeを開きます。

```bash
(ホスト側で)
$ git clone https://github.com/tomoten-umino/my-mkdocs-mike.git
$ cd my-mkdocs-mike
$ code .
```

- VSCode左下にある「＞＜」みたいなボタンを押下して、「Reopen in Container」を押下します。
  - python3のdevcontainerが起動します。
- VSCode内でリモート接続中のコンテナ内のターミナルを開き、pipで必要なツールをインストールする。

```bash
（devcontainer内）
$ pip install -r requirements.txt
```

# mikeの使い方
- 以下のサイトを参考にすること。
  - mike : https://opensourcelibs.com/lib/mike
  - qiita記事 : https://qiita.com/tomoten/items/39b87fc114d8f41b5ebd