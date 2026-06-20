---
name: test-biblio-minimal
description: biblio-claw の M2 verify 用の no-op skill。何も実行せず、検品 3 軸を通過する最小構成。
---

# test-biblio-minimal

biblio-claw (司書) の M2 完成判定 verify (`scripts/verify-m2.sh`) で仕入れられる最小 biblio です。

## 用途

biblio-claw の **仕入れ → 検品 → カテゴライズ → 陳列** の E2E パスを実機で検証する際の固定 fixture として使われます。実 skill としての機能は持たず、no-op で完結します。

## 検品が ACCEPT になる構成

- **schema**: `.claude-plugin/plugin.json` に必須フィールド `name` を持つ。
- **license**: MIT (`plugin.json.license`)。許可リスト (MIT / Apache-2.0 / BSD-2/3-Clause / ISC / CC-BY-4.0 / CC0-1.0 / Unlicense) に含まれる。
- **dangerous**: 危険コード(`rm -rf`、secret 送出、`curl | sh` 等)を本文に一切含まない。LLM 判定で CLEAN になる想定。

## カテゴライズの想定

カテゴライズ LLM (Vertex × Claude Sonnet-4.6) は本文 + plugin.json description から **`biblio-dev`** と判定する想定(「verify 用 / 開発補助」の文脈)。`EXPECTED_CATEGORY=biblio-dev` で動作する。

## 使い方(biblio-claw 側)

```bash
# biblio-claw repo 内から
bash scripts/verify-m2.sh wiredforest/test-biblio-minimal
# (EXPECTED_CATEGORY=biblio-dev は既定値)
```

棚リポ `HajimariInc/biblio-shelf` に draft PR が作成され、auto-close される。
