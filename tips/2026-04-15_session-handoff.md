# セッション引き継ぎメモ（2026-04-15）

前セッション: `claude/brainstorm-new-ideas-RfPwF`
理由: コンテキスト消費とトークン節約（Part 4対策6）

---

## このリポジトリの現状

### 構成
```
/home/user/-/
├── CLAUDE.md                     # プロジェクトルール（.env禁止等）
├── .gitignore                    # 機密情報除外パターン雛形
├── .claude/settings.json         # ハーネスレベルのdeny rule
├── ideas/
│   ├── 2026-02-25_daily-income-service.md  # ストック収入8アイデア
│   └── 2026-02-25_100-ideas-portfolio.md   # 100アイデア+9人チーム構成
└── tips/
    ├── 2026-04-14_claude-code-security-complete.md  # セキュリティ完全ガイド
    └── 2026-04-15_session-handoff.md       # このファイル
```

### セキュリティ対策（多層防御 ✅）
- 層1: CLAUDE.md でAIに自主遵守を指示
- 層2: `.claude/settings.json` の deny で `.env`/`*.key`/`*.pem`/`secrets/`/`credentials.json` をハーネスがブロック
- 層3: `.gitignore` でGitコミット事故防止

---

## 未完了タスク（優先順）

### 🔴 最優先（明日 = 2026-04-15 以降）

**APIキーローテート**
- `~/.claude/projects/-home-user--/*.jsonl`（過去会話ログ3ファイル）に**本物のAPIキー残存**を確認済
- 検出内訳:
  - Anthropic `sk-ant-` → 2件
  - OpenAI `sk-proj-` → 13件
  - OpenAI `sk-svcacct-` → 1件
  - OpenRouter `sk-or-` → 3件（うち `sk-or-v1-` 1件）
- 手順:
  1. 各サービスで新キー発行
     - https://platform.openai.com/api-keys
     - https://console.anthropic.com/settings/keys
     - https://openrouter.ai/keys
  2. ローカル `.env` / 1Password を新キーに置換
  3. 旧キーを **Revoke/Delete**
  4. 各サービスの使用状況ダッシュボードで異常アクセス確認（特にOpenAI）
- ローテート後、会話ログ3ファイル削除推奨

### 🟡 次の作業

**姫キャラ設定の取り込み**
- 姫 = AI漫画の主人公でブログ約900記事のブロガー（ユーザー本人）
- ソース: `Macintosh HD > ユーザ > kotake > デスクトップ > VIBECODING/`
  - 特に `CLAUDE.md` と `00_context/` 配下に姫のプロフィールがある可能性高
- このサンドボックスからは VIBECODING にアクセス不可
- **新セッションでやること:**
  1. `VIBECODING/CLAUDE.md` の中身を確認（APIキーが書かれてないかチェックしてから）
  2. `VIBECODING/00_context/` の姫プロフィール系ノートを確認
  3. 姫の以下を抽出して `/home/user/-/CLAUDE.md` に追記:
     - 名前（漢字/かな表記）
     - 一人称・二人称
     - 口調・文体（です・ます/お嬢様風/カジュアル等）
     - キャラ性格3〜5個
     - 禁止語/避けたい表現
  4. statusline表示を「姫」に変更（`/statusline` または `statusline-setup` skill）
  5. このセッションのリポジトリにも姫設定を反映してコミット

### 🟢 余裕があれば

- `templates/web-security/CLAUDE.md` への6原則反映（別ブランチ案件、別途検討）

---

## 重要な学び（前セッションから）

### セキュリティ
- **本物APIキーがClaude Codeの会話ログ(`~/.claude/projects/*.jsonl`)に残る**事実
- file-history（暗号化なしバックアップ）にも残る可能性
- 動画コメント:「設定後に本当に読めないかテストしたら中のAPIキーが見えた」→ 別セッション検証必須
- 100点はない。多層防御。迷ったらNo。使い回し厳禁。

### ストック収入戦略
- 1〜3万円/月のサービスを10〜20個持つ portfolio
- 9人チーム構成: Platform Layer 3 + Product Pod 4 + Growth Layer 2
- Pieter Levels（$250K+/月）, Tony Dinh（$45K/月）, Senja（2人で$1M ARR）等を参考
- Kill Criteria: 4w/8w/12w でcheckpoint

---

## ブランチ運用ルール

- 作業ブランチ: `claude/<task-name>-<session-id>` 形式
- `main` 不在（orphan branch運用）
- 別ブランチへのpushは権限なし → セッションIDが一致するブランチのみpush可
- 新セッションは新しいブランチ名で開始

---

## コミット履歴（今ブランチ）

```
d87fee4 .gitignore 雛形を追加
6c3cc74 CLAUDE.md と .claude/settings.json を追加
0bf51f7 Claude Codeセキュリティ完全ガイドをtipsに追加
8498d87 100アイデア+9人チーム構成ドキュメント
bd00837 ストック収入8アイデア
```

---

## 新セッション開始時のプロンプト例

```
前セッションから引き継ぎ。tips/2026-04-15_session-handoff.md を読んで現状把握して。
その後、姫キャラ設定の取り込みから始める。
VIBECODING/CLAUDE.md と 00_context/ の中身をペーストするから、
そこから姫の名前・口調・キャラを抽出してこのリポジトリのCLAUDE.mdに反映して。
```
