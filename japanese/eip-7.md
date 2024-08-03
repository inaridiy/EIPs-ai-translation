---
original: 39de6a4c1ab7726d5095c9dd53841e607089e83cd24054388cd0d5aaa9be889f
---

---
eip: 7
title: DELEGATECALL
author: Vitalik Buterin (@vbuterin)
status: 最終版
type: 標準トラック
category: コア
created: 2015-11-15
---

### ハードフォーク
[Homestead](./eip-606.md)

### パラメータ
- アクティベーション:
  - メインネットでブロック番号 >= 1,150,000
  - Mordenでブロック番号 >= 494,000
  - 将来のテストネットでブロック番号 >= 0

### 概要

新しいオペコード `DELEGATECALL` (0xf4) を追加します。これは `CALLCODE` に似ていますが、呼び出し元のsenderとvalueが子スコープに伝播されます。つまり、作成された呼び出しは元の呼び出しと同じsenderとvalueを持ちます。

### 仕様

`DELEGATECALL`: `0xf4`, 6つのオペランドを取ります:
- `gas`: コードの実行に使用できるガス量
- `to`: 実行するコードの宛先アドレス
- `in_offset`: メモリ上の入力データのオフセット
- `in_size`: 入力データのサイズ(バイト単位)
- `out_offset`: メモリ上の出力データのオフセット
- `out_size`: 出力用のスクラッチパッドのサイズ

#### ガスに関する注意事項
- 基本的な手当てはありません。`gas`は呼び出し先が受け取る合計ガス量です。
- `CALLCODE`と同様に、アカウントの作成は行われないため、前払いガスコストは常に `schedule.callGas` + `gas` です。
- 未使用のガスは通常通り返金されます。

#### senderに関する注意事項
- `CALLER`と`VALUE`は呼び出し先の環境で呼び出し元の環境と同じように動作します。

#### その他の注意事項
- 1024の深さ制限は通常通り保持されます。

### 根拠

親スコープのsenderとvalueを子スコープに伝播することで、別のアドレスを変更可能なコードソースとして保持し、それに対して呼び出しを「中継」することが容易になります。子コードは(ガスが減少し、呼び出しスタックの深さが増加した以外は)ほぼ同じ環境で実行されます。

ユースケース1: 3m ガスの制限を回避するためにコードを分割する

```python
~calldatacopy(0, 0, ~calldatasize())
if ~calldataload(0) < 2**253:
    ~delegate_call(msg.gas - 10000, $ADDR1, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
elif ~calldataload(0) < 2**253 * 2:
    ~delegate_call(msg.gas - 10000, $ADDR2, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
...
```

ユースケース2: コントラクトのコードを格納する変更可能なアドレス:

```python
if ~calldataload(0) / 2**224 == 0x12345678 and self.owner == msg.sender:
    self.delegate = ~calldataload(4)
else:
    ~delegate_call(msg.gas - 10000, self.delegate, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
```

これらのメソッドによって呼び出される子関数は自由に `msg.sender` と `msg.value` を参照できるようになります。

### 反対の可能性のある議論

* 呼び出しデータの最初の20バイトにsenderを埋め込むことで、この機能を複製できます。ただし、これではデリゲートされたコントラクト用にコードを特別にコンパイルする必要があり、デリゲートされたコンテキストとrawコンテキストの両方で使用できなくなります。