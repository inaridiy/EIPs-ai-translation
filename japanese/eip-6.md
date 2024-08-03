---
original: 4b415d03226756c99a8808d6d23982459cbbc6c96b8eb79b0323634f79bbb963
---

---
eip: 6
title: `SUICIDE`オペコードの名称変更
author: Hudson Jameson <hudson@hudsonjameson.com>
status: 最終版
type: 標準化トラック
category: インターフェース
created: 2015-11-22
---

### 概要
このEIPで提案されているソリューションは、Ethereumプログラミング言語の`SUICIDE`オペコードの名称を`SELFDESTRUCT`に変更することです。

### 動機
メンタルヘルスは多くの人々にとって非常に重要な問題であり、小さな変化でも大きな影響を与えることができます。自殺や喪失、うつ病に苦しむ人々にとって、プログラミング言語に「自殺」という単語が含まれていることは負担になるでしょう。推定では、世界中で3億5000万人もの人々がうつ病に苦しんでいます。Ethereumのプログラミング言語のセマンティクスは、エコシステムをあらゆるタイプの開発者に広げていくために、頻繁に見直す必要があります。

DEVolution GmbHが委託したEthereum向けのセキュリティ監査で、[Least Authorityが以下のように提案しています](https://github.com/LeastAuthority/ethereum-analyses/blob/master/README.md):
> 「自殺」という命令名を、「自己破壊」、「破壊」、「終了」、「閉鎖」など、より意味合いの軽い言葉に置き換えるべきです。特に、それはコントラクトの自然な終了を表す用語であるため。

自殺という用語を変更する主な理由は、コードよりも人々が大切であり、Ethereumは十分に成熟したプロジェクトであり、この変更の必要性を認識していることを示すためです。自殺は重い話題であり、うつ病や自殺で大切な人を亡くした開発者に影響を与えないよう、できる限りの努力をする必要があります。Ethereumは若いプラットフォームであり、早期にこの変更を実装すれば、後々の問題を最小限に抑えられるでしょう。

### 実装
`SELFDESTRUCT`は`SUICIDE`オペコードのエイリアス(置き換えではなく)として追加されます。
https://github.com/ethereum/solidity/commit/a8736b7b271dac117f15164cf4d2dfabcdd2c6fd
https://github.com/ethereum/serpent/commit/1106c3bdc8f1bd9ded58a452681788ff2e03ee7c