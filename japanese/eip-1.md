---
original: ae46d7bbaeed49fc0d6528a515ac13201268f5108cc6cf1b67eb797c628f89ed
---

---
eip: 1
title: EIPの目的とガイドライン
status: Living
type: Meta
author: Martin Becze &lt;mb@ethereum.org&gt;, Hudson Jameson &lt;hudson@ethereum.org&gt;, 他
created: 2015-10-27
---

## EIPとは何ですか?

EIPはEthereum Improvement Proposalの略で、Ethereumコミュニティに情報を提供したり、Ethereumの新機能や処理、環境についての提案書です。EIPには、その機能の簡潔な技術仕様と根拠が記載されています。EIPの著者は、コミュニティのコンセンサスを形成し、反対意見を文書化する責任があります。

## EIPの根拠

EIPは、新機能の提案、技術的な問題に関するコミュニティの意見収集、Ethereumの設計決定の記録という主要な手段として位置付けられています。EIPはバージョン管理されたリポジトリ内のテキストファイルとして維持されるため、機能提案の履歴が記録されます。

Ethereumの実装者にとって、EIPはその実装の進捗を追跡する便利な方法です。理想的には、各実装のメンテナーがどのEIPを実装したかを一覧表示するでしょう。これにより、ユーザーは特定の実装やライブラリの現在の状況を簡単に知ることができます。

## EIPの種類

EIPには3つのタイプがあります:

- **Standards Track EIP**は、ネットワークプロトコルの変更、ブロックやトランザクションの有効性ルールの変更、提案されたアプリケーション標準/規約、相互運用性に影響を与える変更や追加など、ほとんどすべてのEthereum実装に影響を及ぼす変更を記述します。Standards Track EIPは、設計文書、実装、(必要に応じて)正式な仕様の更新の3部構成になっています。さらに、Standards Track EIPは以下のカテゴリに分類されます:
  - **Core**: コンセンサスフォークを必要とする改善([EIP-5](./eip-5.md)、[EIP-101](./eip-101.md)など)、および["コア開発者"の議論](https://github.com/ethereum/pm)に関連する可能性のある、必ずしもコンセンサス重要ではない変更([EIP-90]、[EIP-86](./eip-86.md)のマイナー/ノード戦略変更2、3、4など)。
  - **Networking**: [devp2p](https://github.com/ethereum/devp2p/blob/readme-spec-links/rlpx.md)([EIP-8](./eip-8.md))や[Light Ethereum Subprotocol](https://ethereum.org/en/developers/docs/nodes-and-clients/#light-node)の改善、[whisper](https://github.com/ethereum/go-ethereum/issues/16013#issuecomment-364639309)や[swarm](https://github.com/ethereum/go-ethereum/pull/2959)のネットワークプロトコル仕様の提案された改善を含みます。
  - **Interface**: メソッド名([EIP-6](./eip-6.md))や[contract ABI](https://docs.soliditylang.org/en/develop/abi-spec.html)などの言語レベルの標準の改善を含みます。
  - **ERC**: トークン標準([ERC-20](./eip-20.md))、名称レジストリ([ERC-137](./eip-137.md))、URIスキーム、ライブラリ/パッケージ形式、ウォレット形式などのアプリケーションレベルの標準と規約を含みます。

- **Meta EIP**は、Ethereumに関するプロセスを記述したり、プロセスの変更を提案するものです。プロセスEIPはStandards Track EIPのようなものですが、Ethereumプロトコル自体ではなく、他の領域に適用されます。実装を提案する場合もありますが、Ethereumのコードベースではありません。通常、コミュニティのコンセンサスを必要とし、Informational EIPのように自由に無視されるものではありません。手順、ガイドライン、意思決定プロセスの変更、Ethereum開発に使用されるツールや環境の変更などが例として挙げられます。任意のmeta-EIPはプロセスEIPとも見なされます。

- **Informational EIP**は、Ethereumの設計上の問題を説明したり、Ethereumコミュニティに一般的なガイドラインや情報を提供するものですが、新機能を提案するものではありません。Informational EIPは必ずしもEthereum コミュニティのコンセンサスや推奨事項を表すものではないため、ユーザーや実装者は自由にInformational EIPを無視したり従ったりすることができます。

単一のEIPには、単一の主要な提案や新しいアイデアを含めることが強く推奨されます。EIPが焦点を絞っているほど、成功する可能性が高くなります。1つのクライアントの変更にはEIPは必要ありませんが、複数のクライアントに影響を与える変更や、複数のアプリケーションが使用する標準を定義する場合にはEIPが必要です。

EIPは一定の最小基準を満たす必要があります。提案された機能の明確で完全な説明が必要です。その機能は全体として改善を表すものでなければなりません。該当する場合は、提案された実装が堅牢であり、プロトコルを過度に複雑化させてはいけません。

### Coreに関する特別な要件

**Core** EIPがEVM(Ethereum Virtual Machine)に言及または変更を提案する場合は、ニーモニックによる命令を参照し、少なくとも一度はそれらのニーモニックのオペコードを定義する必要があります。推奨される方法は以下の通りです:

```
REVERT (0xfe)
```

## EIPワークフロー

### EIPの世話

関係者は、あなた(EIPの提唱者または*EIPの著者*)、[*EIPエディター*](#eip-editors)、[*Ethereum コア開発者*](https://github.com/ethereum/pm)です。

正式なEIPを書く前に、アイデアを検討する必要があります。重複を避けるために、まずEthereum コミュニティにアイデアを提示し、承認を得る必要があります。そのため、[Ethereum Magiciansフォーラム](https://ethereum-magicians.org/)で議論スレッドを開くことをお勧めします。

アイデアが承認されたら、次の責任は(EIPを通じて)その提案をレビュー担当者とすべての関係者に提示し、上記のチャンネルでエディター、開発者、コミュニティからフィードバックを求めることです。EIPを実装するために必要な作業量と、それに準拠しなければならない当事者の数に見合った関心があるかどうかを判断する必要があります。たとえば、Coreに関するEIPの実装には、ERCに関するEIPよりもはるかに多くの作業が必要です。また、Ethereumクライアントチームからの十分な関心が必要です。コミュニティからのネガティブなフィードバックは考慮され、EIPがDraft段階を通過するのを防ぐ可能性があります。

### Core EIPs

Coreに関するEIPは、**Final**ステータスになるためにクライアントの実装が必要なため(「EIPsプロセス」を参照)、自身で実装を提供するか、クライアントにEIPを実装させる必要があります。

クライアントの実装者にEIPをレビューしてもらう最良の方法は、AllCoreDevsコールで発表することです。[AllCoreDevsアジェンダのGitHubイシュー](https://github.com/ethereum/pm/issues)にコメントを投稿してリクエストできます。

AllCoreDevsコールには3つの目的があります。1つ目は、EIPの技術的な長所を議論すること。2つ目は、他のクライアントが何を実装するかを把握すること。3つ目は、ネットワークアップグレードのためのEIP実装を調整することです。

これらのコールでは通常、「大まかなコンセンサス」が得られます。この「大まかなコンセンサス」は、EIPが分裂を引き起こすほど論争的ではなく、技術的に健全であるという前提に基づいています。

:warning: EIPsプロセスとAllCoreDevsコールは、論争的な非技術的な問題に対処するために設計されたものではありませんが、他の方法がないため、しばしばそれらに巻き込まれます。これにより、クライアントの実装者がコミュニティの意向を把握しようとする負担が増えており、EIPsとAllCoreDevsコールの技術的な調整機能を阻害しています。EIPの世話をする際は、[Ethereum Magiciansフォーラム](https://ethereum-magicians.org/)のスレッドにコミュニティの議論の内容や関係者が十分に反映されるようにすることで、コンセンサスを形成するプロセスを容易にできます。

*要するに、提唱者としての役割は、以下のスタイルとフォーマットを使ってEIPを書き、適切なフォーラムでの議論を世話し、そのアイデアに関するコミュニティのコンセンサスを形成することです。*

### EIPプロセス

すべてのトラックのEIPに対して標準化されたプロセスは以下の通りです:

![EIPステータスダイアグラム](../assets/eip-1/EIP-process-update.jpg)

**Idea** - 事前草案の段階のアイデア。EIPリポジトリ内では追跡されません。

**Draft** - 正式に追跡されるEIPの最初の段階。適切にフォーマットされている場合、EIPエディターがEIPリポジトリにマージします。

**Review** - EIPの著者がピアレビューの準備ができ、リクエストしたことを示します。

**Last Call** - EIPを**Final**に移行する前の最終レビューウィンドウです。EIPエディターが`Last Call`ステータスを割り当て、通常14日後のレビュー終了日(`last-call-deadline`)を設定します。

この期間に必要な規範的な変更がある場合は、EIPを`Review`に戻します。

**Final** - これはファイナルな標準を表します。Finalのエイリアスは、errata の修正と非規範的な明確化の追加以外は更新されません。

FinalへのPRには、ステータスの更新以外の変更を含めるべきではありません。内容や編集上の変更提案は、このステータス更新PRとは別にコミットされるべきです。

**Stagnant** - Draft、Review、Last CallのいずれかのステータスにあるEIPで、6か月以上非アクティブだった場合、`Stagnant`に移行されます。著者やEIPエディターがそれを`Draft`やより早期のステータスに復活させることができます。復活されない場合、提案は永久にこのステータスにとどまります。

>*EIPの著者は、EIPのステータスが自動的に変更された場合に通知されます*

**Withdrawn** - EIPの著者(ら)がEIPの提案を取り下げました。この状態は最終的なものであり、このEIP番号を使って再び復活させることはできません。アイデアがその後追及される場合は、新しい提案として扱われます。

**Living** - 最終的な状態に達せず、継続的に更新されるように設計されたEIPに対する特別なステータスです。EIP-1がその代表例です。

## 成功したEIPに含まれるべきものは何ですか?

各EIPには以下の部分が含まれている必要があります:

- 前文 - EIPの番号、簡潔な説明タイトル(最大44文字)、説明(最大140文字)、著者の詳細を含むRFC 822形式のヘッダー。カテゴリに関係なく、タイトルと説明にはEIP番号を含めてはいけません。詳細は[以下](./eip-1.md#eip-header-preamble)を参照してください。
- 概要 - 技術的な要約となる短い段落です。この仕様セクションの要約を簡潔かつ人間が読みやすい形で提示します。概要のみを読んでも、この仕様が何をするのかがわかるはずです。
- 動機 *(オプション)* - Ethereumプロトコルを変更するEIPには、動機セクションが不可欠です。既存のプロトコル仕様が、EIPが解決しようとする問題に不十分であることを明確に説明する必要があります。動機が明らかな場合は、このセクションを省略できます。
- 仕様 - 新機能の構文と意味論を詳細に記述します。仕様は、現在のEthereum プラットフォーム(besu、erigon、ethereumjs、go-ethereum、nethermind、その他)の間で競合し、相互運用可能な実装を可能にするほど詳細でなければなりません。
- 根拠 - 仕様の詳細を説明し、デザインの動機と特
定理を説明します。代替案も検討し、関連する作業についても説明します。EIPの議論中に提起された重要な異論や懸念についても議論する必要があります。
- 下位互換性 *(オプション)* - 下位互換性を損なう全てのEIPには、これらの非互換性とその影響を説明するセクションが含まれている必要があります。著者がこれらの非互換性にどのように対処するかを説明する必要があります。提案に下位互換性がない場合は、このセクションを省略できますが、下位互換性がある場合は必ず含める必要があります。
- テストケース *(オプション)* - コンセンサスの変更に影響するEIPには、実装のためのテストケースが必須です。テストは、EIPに直接データ(入力/期待出力ペアなど)として埋め込むか、`../assets/eip-###/<filename>`に含める必要があります。このセクションは、コア以外の提案では省略できます。
- 参考実装 *(オプション)* - この仕様の理解や実装を支援するための参考/サンプル実装を含む任意のセクションです。すべてのEIPでこのセクションを省略できます。
- セキュリティ上の考慮事項 - すべてのEIPには、提案された変更に関連するセキュリティの影響/考慮事項を議論するセクションが含まれている必要があります。セキュリティに関連する設計上の決定、懸念、重要な議論、実装固有のガイダンスとピットフォール、脅威と リスクの概要、それらへの対処方法などを含める必要があります。セキュリティ上の考慮事項のセクションがないEIPは却下されます。EIPが**Final**ステータスに進むには、レビュー担当者が十分なセキュリティ上の考慮事項の議論があると判断する必要があります。
- 著作権放棄 - すべてのEIPは公有財産でなければなりません。著作権放棄は、ライセンスファイルにリンクし、以下の文言を使用する必要があります: `Copyright and related rights waived via [CC0](../LICENSE.md).`

## EIPのフォーマットとテンプレート

EIPは[markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)フォーマットで書く必要があります。[テンプレート](https://github.com/ethereum/EIPs/blob/master/eip-template.md)に従う必要があります。

## EIPヘッダー前文

各EIPは、3つのハイフン(`---`)で囲まれた[RFC 822](https://www.ietf.org/rfc/rfc822.txt)形式のヘッダー前文で始まる必要があります。このヘッダーは、Jekyllの["front matter"](https://jekyllrb.com/docs/front-matter/)とも呼ばれています。ヘッダーは以下の順序で表示される必要があります。

`eip`: *EIP番号*

`title`: *EIPのタイトルは数語で、完全な文章ではありません*

`description`: *説明は1つの完全な(短い)文章です*

`author`: *著者または著者の名前と/またはユーザー名、または名前とメールアドレス。詳細は以下のとおりです。*

`discussions-to`: *公式の議論スレッドを指すURL*

`status`: *Draft、Review、Last Call、Final、Stagnant、Withdrawn、Living*

`last-call-deadline`: *(オプションのフィールド、`Last Call`ステータスの場合のみ必要) Last Callの期限*

`type`: *`Standards Track`、`Meta`、または`Informational`のいずれか*

`category`: *`Core`、`Networking`、`Interface`、または`ERC`のいずれか* (オプションのフィールド、`Standards Track`EIPの場合のみ必要)

`created`: *EIPが作成された日付*

`requires`: *EIP番号* (オプションのフィールド)

`withdrawal-reason`: *(オプションのフィールド、`Withdrawn`ステータスの場合のみ必要) EIPが取り下げられた理由の文章*

リストを許可するヘッダーは、要素をカンマで区切る必要があります。

日付を要求するヘッダーは、常にISO 8601形式(yyyy-mm-dd)で指定する必要があります。

### `author`ヘッダー

`author`ヘッダーには、EIPの著者/所有者の名前、メールアドレス、またはユーザー名が記載されます。匿名を希望する場合は、ユーザー名のみ、または名前とユーザー名を使用できます。`author`ヘッダーの値の形式は以下のようになります:

> Random J. User &lt;address@dom.ain&gt;

または

> Random J. User (@username)

または

> Random J. User (@username) &lt;address@dom.ain&gt;

メールアドレスやGitHubユーザー名が含まれている場合、および

> Random J. User

メールアドレスもGitHubユーザー名も提供されていない場合。

少なくとも1人の著者がGitHubユーザー名を使う必要があり、変更リクエストの通知を受け取り、承認または拒否する機能を持つ必要があります。

### `discussions-to`ヘッダー

EIPがドラフト段階にある間は、`discussions-to`ヘッダーにEIPが議論されているURLが示されます。

推奨される議論のURLは、[Ethereum Magicians](https://ethereum-magicians.org/)のトピックです。GitHubのプルリクエスト、一時的なURL、時間とともに固定化されるURL(Redditのトピックなど)を指すことはできません。

### `type`ヘッダー

`type`ヘッダーは、EIPのタイプ(Standards Track、Meta、Informational)を指定します。Standardsトラックの場合は、サブカテゴリ(core、networking、interface、またはERC)も含める必要があります。

### `category`ヘッダー

`category`ヘッダーは、EIPのカテゴリを指定します。これは、Standards Trackのみに必要です。

### `created`ヘッダー

`created`ヘッダーは、EIPに番号が割り当てられた日付を記録します。両方のヘッダーは、yyyy-mm-dd形式(例: 2001-08-14)で記述する必要があります。

### `requires`ヘッダー

EIPには`requires`ヘッダーがある可能性があり、このEIPが依存するEIP番号を示します。そのような依存関係がある場合は、このフィールドが必要です。

`requires`の依存関係は、現在のEIPを理解または実装するためには、別のEIPからの概念や技術的要素が必要な場合に作成されます。単に別のEIPに言及しただけでは、必ずしも依存関係は作成されません。

## 外部リソースへのリンク

以下の特定の例外を除いて、外部リソースへのリンクを**含めるべきではありません**。外部リソースは消失、移動、または予期せず変更される可能性があります。

許可された外部リソースを管理するプロセスは、[EIP-5757](./eip-5757.md)で説明されています。

### 実行クライアント仕様

通常のMarkdownの構文を使って、Ethereumの実行クライアント仕様へのリンクを含めることができます。例:

```markdown
[Ethereum Execution Client Specifications](https://github.com/ethereum/execution-specs/blob/9a1f22311f517401fed6c939a159b55600c454af/README.md)
```

これは以下のように表示されます:

[Ethereum Execution Client Specifications](https://github.com/ethereum/execution-specs/blob/9a1f22311f517401fed6c939a159b55600c454af/README.md)

許可された実行クライアント仕様のURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^(https://github.com/ethereum/execution-specs/(blob|commit)/[0-9a-f]{40}/.*|https://github.com/ethereum/execution-specs/tree/[0-9a-f]{40}/.*)$
```

### 実行仕様テスト

通常のMarkdownの構文を使って、Ethereum実行仕様テスト(EEST)へのリンクを含めることができます。例:

```markdown
[Ethereum Execution Specification Tests](https://github.com/ethereum/execution-spec-tests/blob/c9b9307ff320c9bb0ecb9a951aeab0da4d9d1684/README.md)
```

これは以下のように表示されます:

[Ethereum Execution Specification Tests](https://github.com/ethereum/execution-spec-tests/blob/c9b9307ff320c9bb0ecb9a951aeab0da4d9d1684/README.md)

許可された実行仕様テストのURLは、特定のコミットにアンカーされている必要があり、次のいずれかの正規表現に一致する必要があります:

```regex
^https://(www\.)?github\.com/ethereum/execution-spec-tests/(blob|tree)/[a-f0-9]{40}/.+$
```

```regex
^https://(www\.)?github\.com/ethereum/execution-spec-tests/commit/[a-f0-9]{40}$
```

### コンセンサスレイヤー仕様

通常のMarkdownの構文を使って、Ethereumコンセンサスレイヤー仕様の特定のコミットへのリンクを含めることができます。例:

```markdown
[Beacon Chain](https://github.com/ethereum/consensus-specs/blob/26695a9fdb747ecbe4f0bb9812fedbc402e5e18c/specs/sharding/beacon-chain.md)
```

これは以下のように表示されます:

[Beacon Chain](https://github.com/ethereum/consensus-specs/blob/26695a9fdb747ecbe4f0bb9812fedbc402e5e18c/specs/sharding/beacon-chain.md)

許可されたコンセンサスレイヤー仕様のURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^https://github.com/ethereum/consensus-specs/(blob|commit)/[0-9a-f]{40}/.*$
```

### ネットワーキング仕様

通常のMarkdownの構文を使って、Ethereumネットワーキング仕様の特定のコミットへのリンクを含めることができます。例:

```markdown
[Ethereum Wire Protocol](https://github.com/ethereum/devp2p/blob/40ab248bf7e017e83cc9812a4e048446709623e8/caps/eth.md)
```

これは以下のように表示されます:

[Ethereum Wire Protocol](https://github.com/ethereum/devp2p/blob/40ab248bf7e017e83cc9812a4e048446709623e8/caps/eth.md)

許可されたネットワーキング仕様のURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^https://github.com/ethereum/devp2p/(blob|commit)/[0-9a-f]{40}/.*$
```

### ポータル仕様

通常のMarkdownの構文を使って、Ethereumポータル仕様の特定のコミットへのリンクを含めることができます。例:

```markdown
[Portal Wire Protocol](https://github.com/ethereum/portal-network-specs/blob/5e321567b67bded7527355be714993c24371de1a/portal-wire-protocol.md)
```

これは以下のように表示されます:

[Portal Wire Protocol](https://github.com/ethereum/portal-network-specs/blob/5e321567b67bded7527355be714993c24371de1a/portal-wire-protocol.md)

許可されたネットワーキング仕様のURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^https://github.com/ethereum/portal-network-specs/(blob|commit)/[0-9a-f]{40}/.*$
```

### World Wide Web Consortium (W3C)

W3C「勧告」ステータスの仕様へのリンクは、通常のMarkdownの構文を使って含めることができます。例えば、次のリンクは許可されます:

```markdown
[Secure Contexts](https://www.w3.org/TR/2021/CRD-secure-contexts-20210918/)
```

これは以下のように表示されます:

[Secure Contexts](https://www.w3.org/TR/2021/CRD-secure-contexts-20210918/)

許可されるW3C勧告のURLは、技術レポートの名前空間にある日付付きの仕様を指す必要があり、次の正規表現に一致する必要があります:

```regex
^https://www\.w3\.org/TR/[0-9][0-9][0-9][0-9]/.*$
```

### Web Hypertext Application Technology Working Group (WHATWG)

WHATWG仕様へのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[HTML](https://html.spec.whatwg.org/commit-snapshots/578def68a9735a1e36610a6789245ddfc13d24e0/)
```

これは以下のように表示されます:

[HTML](https://html.spec.whatwg.org/commit-snapshots/578def68a9735a1e36610a6789245ddfc13d24e0/)

許可されるWHATWG仕様のURLは、`spec`サブドメインで定義された仕様(アイデア仕様は許可されない)に、コ
ミットスナップショットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^https:\/\/[a-z]*\.spec\.whatwg\.org/commit-snapshots/[0-9a-f]{40}/$
```

WHATWGによって推奨されていないものの、EIPはEIPが最終化された時点で参照されていた正確なバージョンの生きた標準を読者に提供するために、特定のコミットにアンカーされる必要があります。これにより、読者は、EIPが参照するバージョンと現在の生きた標準との互換性を維持することができます。

### Internet Engineering Task Force (IETF)

IETF Request For Comment (RFC)仕様へのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[RFC 8446](https://www.rfc-editor.org/rfc/rfc8446)
```

これは以下のように表示されます:

[RFC 8446](https://www.rfc-editor.org/rfc/rfc8446)

許可されるIETF仕様のURLは、割り当てられたRFC番号を持つ仕様(インターネットドラフトを参照することはできません)を指す必要があり、次の正規表現に一致する必要があります:

```regex
^https:\/\/www.rfc-editor.org\/rfc\/.*$
```

### Bitcoin Improvement Proposal

Bitcoin Improvement Proposalsへのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[BIP 38](https://github.com/bitcoin/bips/blob/3db736243cd01389a4dfd98738204df1856dc5b9/bip-0038.mediawiki)
```

これは以下のように表示されます:

[BIP 38](https://github.com/bitcoin/bips/blob/3db736243cd01389a4dfd98738204df1856dc5b9/bip-0038.mediawiki)

許可されるBitcoin Improvement ProposalのURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^(https://github.com/bitcoin/bips/blob/[0-9a-f]{40}/bip-[0-9]+\.mediawiki)$
```

### National Vulnerability Database (NVD)

National Institute of Standards and Technology (NIST)が公開する Common Vulnerabilities and Exposures (CVE)システムへのリンクは、最新の変更日付で修飾されている場合に含めることができます。以下の構文を使用します:

```markdown
[CVE-2023-29638 (2023-10-17T10:14:15)](https://nvd.nist.gov/vuln/detail/CVE-2023-29638)
```

これは以下のように表示されます:

[CVE-2023-29638 (2023-10-17T10:14:15)](https://nvd.nist.gov/vuln/detail/CVE-2023-29638)

### Chain Agnostic Improvement Proposals (CAIPs)

Chain Agnostic Improvement Proposals (CAIPs)仕様へのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[CAIP 10](https://github.com/ChainAgnostic/CAIPs/blob/5dd3a2f541d399a82bb32590b52ca4340b09f08b/CAIPs/caip-10.md)
```

これは以下のように表示されます:

[CAIP 10](https://github.com/ChainAgnostic/CAIPs/blob/5dd3a2f541d399a82bb32590b52ca4340b09f08b/CAIPs/caip-10.md)

許可されるChain Agnostic URLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^(https://github.com/ChainAgnostic/CAIPs/blob/[0-9a-f]{40}/CAIPs/caip-[0-9]+\.md)$
```

### Ethereum Yellow Paper

Ethereum Yellow Paperへのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[Ethereum Yellow Paper](https://github.com/ethereum/yellowpaper/blob/9c601d6a58c44928d4f2b837c0350cec9d9259ed/paper.pdf)
```

これは以下のように表示されます:

[Ethereum Yellow Paper](https://github.com/ethereum/yellowpaper/blob/9c601d6a58c44928d4f2b837c0350cec9d9259ed/paper.pdf)

許可されるYellow PaperのURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^(https://github\.com/ethereum/yellowpaper/blob/[0-9a-f]{40}/paper\.pdf)$
```

### 実行クライアント仕様テスト

Ethereum実行クライアント仕様テストへのリンクは、通常のMarkdownの構文を使って含めることができます。例:

```markdown
[Ethereum Execution Client Specification Tests](https://github.com/ethereum/execution-spec-tests/blob/d5a3188f122912e137aa2e21ed2a1403e806e424/README.md)
```

これは以下のように表示されます:

[Ethereum Execution Client Specification Tests](https://github.com/ethereum/execution-spec-tests/blob/d5a3188f122912e137aa2e21ed2a1403e806e424/README.md)

許可された実行クライアント仕様テストのURLは、特定のコミットにアンカーされている必要があり、次の正規表現に一致する必要があります:

```regex
^(https://github.com/ethereum/execution-spec-tests/(blob|commit)/[0-9a-f]{40}/.*|https://github.com/ethereum/execution-spec-tests/tree/[0-9a-f]{40}/.*)$
```

### デジタルオブジェクト識別子システム

デジタルオブジェクト識別子(DOI)で修飾されたリンクは、以下の構文を使って含めることができます:

````markdown
これは脚注付きの文章です。[^1]

[^1]:
    ```csl-json
    {
      "type": "article",
      "id": 1,
      "author": [
        {
          "family": "Jameson",
          "given": "Hudson"
        }
      ],
      "DOI": "00.0000/a00000-000-0000-y",
      "title": "An Interesting Article",
      "original-date": {
        "date-parts": [
          [2022, 12, 31]
        ]
      },
      "URL": "https://sly-hub.invalid/00.0000/a00000-000-0000-y",
      "custom": {
        "additional-urls": [
          "https://example.com/an-interesting-article.pdf"
        ]
      }
    }
    ```
````

これは以下のように表示されます:

<!-- markdownlint-capture -->
<!-- markdownlint-disable code-block-style -->

これは脚注付きの文章です。[^1]

[^1]:
    ```csl-json
    {
      "type": "article",
      "id": 1,
      "author": [
        {
          "family": "Jameson",
          "given": "Hudson"
        }
      ],
      "DOI": "00.0000/a00000-000-0000-y",
      "title": "An Interesting Article",
      "original-date": {
        "date-parts": [
          [2022, 12, 31]
        ]
      },
      "URL": "https://sly-hub.invalid/00.0000/a00000-000-0000-y",
      "custom": {
        "additional-urls": [
          "https://example.com/an-interesting-article.pdf"
        ]
      }
    }
    ```

<!-- markdownlint-restore -->

[Citation Style Language Schema](https://resource.citationstyles.org/schema/v1.0/input/json/csl-data.json)でサポートされているフィールドを参照してください。スキーマに対する検証に加えて、参考文献にはDOIと少なくとも1つのURLが含まれている必要があります。

トップレベルのURLフィールドは、参照されたドキュメントのコピーにゼロコストで表示できるURLでなければなりません。`additional-urls`の下の値は、参照されたドキュメントのコピーにも解決される必要がありますが、料金を請求することができます。

## 他のEIPへのリンク

他のEIPへの参照は、参照しているEIP番号`EIP-N`の形式で行う必要があります。EIPを参照する際は、最初の参照時に必ず相対Markdownリンクを付ける必要があり、その後の参照では任意でリンクを付けることができます。リンクは常に相対パスで行う必要があり、このGitHubリポジトリ、このリポジトリのフォーク、メインのEIPサイト、メインのEIPサイトのミラーなどで機能するようにする必要があります。例えば、このEIPにリンクするには`./eip-1.md`のように記述します。

## 補助ファイル

画像、図、補助ファイルは、そのEIPの`assets/eip-N`サブディレクトリ(NはそのファイルのためのEIP番号)に含める必要があります。EIPでイメージにリンクする場合は、`../assets/eip-1/image.png`のような相対リンクを使用してください。

## EIPの所有権の移転

時折、新しいチャンピオンにEIPの所有権を移転する必要が生じることがあります。一般的に、元の著者を移転後のEIPの共著者として保持したいと思いますが、これは元の著者次第です。EIPの所有権を移転する良い理由は、元の著者がもはらそれを更新したり、EIPプロセスを進めるための時間や興味がなくなった場合、または「ネット上から消えた」(つまり、メールに返事がない)場合です。EIPの方向性に同意しないからEIPの所有権を移転するのは良い理由ではありません。我々はEIPに関してコンセンサスを形成しようとしていますが、それが不可能な場合は、常に競合するEIPを提出することができます。

EIPの所有権を引き継ぐことに興味がある場合は、元の著者とEIPエディターの両方に引き継ぐ旨のメッセージを送ってください。元の著者がタイムリーにメールに返事をしない場合、EIPエディターが一方的な決定を下します(そのような決定は取り消すことができないわけではありません:)).

## EIPエディター

現在のEIPエディターは以下の通りです:

- Alex Beregszaszi (@axic)
- Greg Colvin (@gcolvin)
- Matt Garnett (@lightclient)
- Sam Wilson (@SamWilsn)
- Zainan Victor Zhou (@xinbenlv)
- Gajinder Singh (@g11tech)

EIPエディターの名誉職は以下の通りです:

- Casey Detrio (@cdetrio)
- Gavin John (@Pandapip1)
- Hudson Jameson (@Souptacular)
- Martin Becze (@wanderer)
- Micah Zoltu (@MicahZoltu)
- Nick Johnson (@arachnid)
- Nick Savers (@nicksavers)
- Vitalik Buterin (@vbuterin)

EIPエディターになりたい場合は、[EIP-5069](./eip-5069.md)を確認してください。

## EIPエディターの責任

新しいEIPが提出されるたびに、エディターは以下のことを行います:

- EIPが準備ができているかどうかを確認します: 健全で完全であること。アイデアは技術的に合理的でなければならず、最終ステータスになる可能性が高くなくてはなりません。
- タイトルは内容を正確に説明するものでなければなりません。
- 言語(スペリング、文法、文章構造など)、マークアップ(GitHub Flavored Markdown)、コードスタイルをチェックします。

EIPが リポジトリに準備ができていない場合、エディターは著者に修正を求め、具体的な指示を送ります。

EIPがリポジトリに準備ができたら、EIPエディターは以下のことを行います:

- EIP番号を割り当てます(通常は順次; エディターは番号の先取りが疑われる場合は再割り当てできます)
- 対応する[プルリクエスト](https://github.com/ethereum/EIPs/pulls)をマージします
- EIPの著者にNextステップを知らせるメッセージを送ります。

多くのEIPは、Ethereumコードベースへの書き込み権限を持つ開発者によって書かれ、維持されています。EIPエディターはEIPの変更を監視し、構造、文法、スペリング、マークアップの間違いを修正します。

エディターはEIPに対して判断を下すわけではありません。私たちは管理と編集の部分を担当しているだけです。

## スタイルガイド

### タイトル

前文の`title`フィールド:

- "standard"や"標準"という言葉を含めてはいけません。
- EIPの番号を含めてはいけません。

### 説明

前文の`description`フィールド:

- "standard"や"標準"という言葉を含めてはいけません。
- EIPの番号を含めてはいけません。

### EIP番号

`category`が`ERC`のEIPを参照する場合は、ハイフン付きの形式`ERC-X`(XがそのEIPの割り当て番号)で記述する必要があります。他のすべての`category`のEIPを参照する場合は、ハイフン付きの形式`EIP-X`(XがそのEIPの割り当
て番号)で記述する必要があります。

### RFC 2119およびRFC 8174

EIPは、[RFC 2119](https://www.ietf.org/rfc/rfc2119.html)および[RFC 8174](https://www.ietf.org/rfc/rfc8174.html)の用語に従うことが推奨されており、仕様セクションの冒頭に以下を挿入する必要があります:

> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 and RFC 8174.

## 歴史

このドキュメントは、[Bitcoin's BIP-0001](https://github.com/bitcoin/bips)を大幅に参考にしており、その多くの部分がそのまま使用されています。Bitcoin's BIP-0001は、[Python's PEP-0001](https://peps.python.org/)に基づいて書かれたものです。多くの箇所でテキストがそのまま複製され、変更されています。PEP-0001のテキストはBarry Warsaw、Jeremy Hylton、David Goodgerによって書かれましたが、彼らはEthereum Improvement Processにおけるその使用について責任を負うものではなく、Ethereumや EIPに関する技術的な質問については相談されるべきではありません。コメントは全てEIPエディターに向けてください。

## 著作権

Copyright and related rights waived via [CC0](../LICENSE.md).