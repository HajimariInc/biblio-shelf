# biblio-shelf

AI Agent (Claude Code) 向けの skill を「聖典 (biblio)」に見立てて収め、配り、その出入りを記録する **本棚 (marketplace)**。棚の主は **司書 = [biblio-claw](https://github.com/HajimariInc/biblio-claw)**。収蔵・整頓・取り出し (インジェクション)・観測・成長の伝播を、人手を介さず回すことを目指します。

**位置付け**: [DevOps × AI Agent Hackathon](https://findy.co.jp/4127/) (主催: ファインディ / スポンサー: Google Cloud Japan、決勝 2026-08-19 @ Google 渋谷) の題材です。

## 何が入っているのか (棚の構造)

本棚は [Claude Code 標準の plugin marketplace 規格](https://code.claude.com/docs/en/plugin-marketplaces) に沿っています。カテゴリごとのディレクトリに biblio (= skill / plugin) が並びます。

### カテゴリ namespace

| カテゴリ | namespace |
| :--- | :--- |
| 開発 | `biblio-dev` |
| クリエイティブ | `biblio-art` |
| バックオフィス | `biblio-bf` |
| AI 運用 | `biblio-ai` |

現在の収蔵内容は [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) を参照してください。同梱される biblio の構成・数・カテゴリの種類は、司書 (biblio-claw) の運用により継続的に変動します。

## 誰のためか

本棚には 2 種類の利用者が想定されています。

| 呼称 | 誰 | 接点 | 司書の関与 |
| :--- | :--- | :--- | :--- |
| **guest** | 本棚の訪問者 | Claude Code の marketplace 標準機能 | なし (標準機能で使う) |
| **patron** | 司書 (biblio-claw) の利用者 | 司書との対話 (Slack など) | あり (依頼・対話) |

- **guest** は本棚を訪れて biblio を持ち帰る立場です。Claude Code の marketplace 標準機能を通じて、直接 biblio を発見・取得できます。
- **patron** は司書 (biblio-claw) を通じて本棚の内容を育てる立場です。仕入れ・検品・カテゴライズ・陳列といった能動的な操作は司書側に集約されています。

## 使い方

Claude Code の CLI から本棚を marketplace として追加します。

```
/plugin marketplace add HajimariInc/biblio-shelf
```

以降は Claude Code 標準の `/plugin` コマンドで一覧確認・install ができます。詳細な使い方は [Claude Code 公式ドキュメント](https://code.claude.com/docs/en/plugin-marketplaces) を参照してください。

## 司書との関係

本棚に何を並べ、どのように整頓するかは、司書 = **[biblio-claw](https://github.com/HajimariInc/biblio-claw)** が管理します。

- 本棚 (shelf) は **陳列された結果を提供する場**
- 司書 (claw) は **収蔵・整頓・観測・成長の伝播を担う運用主体**

biblio の仕入れ・検品・カテゴライズ・陳列は司書側で自動化されており、本棚に対する能動的な収蔵動作は司書側で行われます。本棚の内容についての詳細な設計や運用ワークフローは biblio-claw リポジトリの README を参照してください。

## ライセンス

- **本棚 (shelf) 全体**: [Apache License 2.0](LICENSE)
  - Copyright 2026 WiredForest, LLC (https://wforest.jp/)
- **各 biblio**: それぞれ独立したライセンスの下で提供されます。詳細は [`NOTICE`](NOTICE) および各 biblio ディレクトリの `LICENSE` ファイルを参照してください。

同梱される biblio の取扱い方針 (upstream 追従・改変ポリシー等) は [`NOTICE`](NOTICE) に記載されています。

## 問い合わせ

本リポジトリに関する問い合わせは、maintainer の GitHub プロフィール ([`wiredforest`](https://github.com/wiredforest)) を参照し、記載の連絡手段を利用してください。GitHub Issues は運用していません。
