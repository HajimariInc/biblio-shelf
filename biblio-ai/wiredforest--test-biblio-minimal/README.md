# test-biblio-minimal

[biblio-claw](https://github.com/HajimariInc/biblio-claw) の **M2 完成判定 verify** (`scripts/verify-m2.sh`) 用の最小 biblio (= Claude Code plugin)。

## 何ができる skill か

**何も実行しない** no-op skill です。biblio-claw が「仕入れ → 検品 → カテゴライズ → 棚 PR 作成」の E2E パスを実機で検証する際の **controlled fixture** として使われます。

## 構造

```
test-biblio-minimal/
├── .claude-plugin/
│   └── plugin.json     # 必須: name / license / version / description
├── SKILL.md            # skill 本体 (no-op、検品 dangerous 軸を CLEAN にする最小本文)
├── README.md           # 本ファイル
└── LICENSE             # MIT
```

3 ファイル + LICENSE で **GitHub Git Data API 1 PR で送れる規模** (= biblio-claw の `MAX_BLOBS_PER_PR=100` 内)。

## なぜ別 repo として作るのか

biblio-claw の acquire は `owner/repo` 単位で全体を clone するため、`anthropics/skills` や `anthropics/claude-plugins-official` のような **marketplace 集約形** の repo は仕入れ対象として大きすぎる (400+ blobs)。本 repo は **1 biblio = 1 repo** の単位を維持する最小例。

## ライセンス

MIT License (LICENSE 参照)。
