---
original: a081e05f53a500bcc24189b68c0b29c7712e71633dfd3d699d563f56f98563d9
---

# イーサリアム改善提案（EIP）AI翻訳

> **_注意_**: EIPリポジトリは最近、ERCとEIPの[分離](https://github.com/ethereum/EIPs/pull/7206)を行いました。ERCは現在 [https://github.com/ethereum/ercs](https://github.com/ethereum/ercs) でアクセスできます。新しいERCや既存のERCの更新はすべてこの新しいリポジトリに向けられる必要があります。この不便をお詫び申し上げます。

EIPプロジェクトの目的は、イーサリアム自体とその上に構築された規約を標準化し、高品質なドキュメントを提供することです。このリポジトリは、イーサリアム改善提案（EIP）の形で、イーサリアムの過去および進行中の改善を追跡します。[EIP-1](https://eips.ethereum.org/EIPS/eip-1)がEIPの公開方法を規定しています。

[ステータスページ](https://eips.ethereum.org/)はEIPを追跡し、リストアップしています。EIPは以下のカテゴリに分類されます：

- [コアEIP](https://eips.ethereum.org/core)は、イーサリアムのコンセンサスプロトコルの改善です。
- [ネットワーキングEIP](https://eips.ethereum.org/networking)は、イーサリアムのピアツーピアネットワーキング層を規定します。
- [インターフェースEIP](https://eips.ethereum.org/interface)は、ユーザーとアプリケーションがブロックチェーンとどのように相互作用するかを決定するイーサリアムへのインターフェースを標準化します。
- [ERC](https://eips.ethereum.org/erc)は、イーサリアム上で動作するアプリケーションがどのように相互作用できるかを決定するアプリケーション層の標準を規定します。
- [メタEIP](https://eips.ethereum.org/meta)は、何らかの形のコンセンサスを必要とするその他の改善です。
- [情報提供EIP](https://eips.ethereum.org/informational)は、コンセンサスを必要としない非標準の改善です。

**EIPを書く前に、アイデアは[Ethereum Magicians](https://ethereum-magicians.org/)または[Ethereum Research](https://ethresear.ch/t/read-this-before-posting/8)で徹底的に議論されなければなりません。コンセンサスが得られたら、EIPプロセスを説明している[EIP-1](https://eips.ethereum.org/EIPS/eip-1)を徹底的に読み、レビューしてください。**

このリポジトリは標準を文書化するためのものであり、それらの実装を支援するためのものではないことにご注意ください。これらの種類の問い合わせは[Ethereum Stack Exchange](https://ethereum.stackexchange.com)に向けられるべきです。EIPに関する具体的な質問や懸念事項については、EIPの前文にある`discussions-to`タグで示されているEIPの関連する議論スレッドにコメントするのが最適です。

EIPエディターになりたい場合は、[EIP-5069](./EIPS/eip-5069.md)をお読みください。

## 推奨される引用形式

ドラフトステータスに達したEIPの正規URLは<https://eips.ethereum.org/>にあります。例えば、EIP-1の正規URLは<https://eips.ethereum.org/EIPS/eip-1>です。

<https://eips.ethereum.org/>で公開されていないドキュメントはワーキングペーパーとみなしてください。また、「ドラフト」、「レビュー」、または「ラストコール」のステータスで公開されているEIPは不完全なドラフトとみなし、その仕様が変更される可能性が高いことに注意してください。

## 検証と自動マージ

このリポジトリのすべてのプルリクエストは、自動的にマージされる前に自動チェックに合格する必要があります：

- [eip-review-bot](https://github.com/ethereum/eip-review-bot/)は、PRがいつ自動的にマージできるかを判断します[^1]
- EIP-1ルールは[`eipw`](https://github.com/ethereum/eipw)を使用して適用されます[^2]
- HTMLフォーマットとリンク切れは[HTMLProofer](https://github.com/gjtorikian/html-proofer)を使用してチェックされます[^2]
- スペルチェックは[CodeSpell](https://github.com/codespell-project/codespell)で行われます[^2]
  - 偽陽性が発生することがあります。これが発生した場合は、[.codespell-whitelist](https://github.com/ethereum/EIPs/blob/master/config/.codespell-whitelist)を編集するPRを提出してください。**.codespell-whitelist**のみを編集してください。
- Markdownのベストプラクティスは[markdownlint](https://github.com/DavidAnson/markdownlint)を使用してチェックされます[^2]

[^1]: https://github.com/ethereum/EIPs/blob/master/.github/workflows/auto-review-bot.yml
[^2]: https://github.com/ethereum/EIPs/blob/master/.github/workflows/ci.yml

EIPバリデーターをローカルで実行することが可能です：

```sh
cargo install eipv
eipv <INPUT FILE / DIRECTORY>
```

## ステータスページをローカルでビルドする

### 前提条件のインストール

1. ターミナルを開きます。

2. Ruby 3.1.4がインストールされているか確認します。[後のバージョンはサポートされていません](https://stackoverflow.com/questions/14351272/undefined-method-exists-for-fileclass-nomethoderror)。

   ```sh
   ruby --version
   ```

3. Rubyがインストールされていない場合は、Ruby 3.1.4をインストールします。

4. Bundlerをインストールします：

   ```sh
   gem install bundler
   ```

5. 依存関係をインストールします：

   ```sh
   bundle install
   ```

### ローカルJekyllサイトをビルドする

1. アセットをバンドルし、サーバーを起動します：

   ```sh
   bundle exec jekyll serve
   ```

2. ウェブブラウザで`http://localhost:4000`にアクセスして、ローカルJekyllサイトをプレビューします。

JekyllとGitHub Pagesに関する詳細情報は[こちら](https://docs.github.com/en/enterprise/2.14/user/articles/setting-up-your-github-pages-site-locally-with-jekyll)をご覧ください。