# フォルダ構成

```
Vault/
├── 00_Inbox/          # 未整理のメモ（とりあえず放り込む）
├── 10_Projects/       # プロジェクトごとのフォルダ
│   └── project-name/
│       ├── decisions.md      # 意思決定ログ
│       ├── architecture.md   # 構成・設計メモ
│       └── retrospective.md  # 振り返り
├── 20_Areas/          # 継続的に管理する領域
│   ├── ai-tools/     # AI ツール知見
│   ├── security/     # セキュリティ知見
│   └── team/         # チーム運用
├── 30_Resources/      # 参考資料・学習ノート
├── 40_Daily/          # 日報
├── 50_Weekly/         # 週報
├── 90_Archive/        # 完了・不要になったもの
└── _templates/        # テンプレート置き場
```

## 命名規則

- 日報: `YYMMDD_daily.md`（例: `260225_daily.md`）
- 週報: `YYMMDD_weekly.md`（月曜日の日付）
- 意思決定: `YYMMDD_decision_タイトル.md`
- 振り返り: `YYMMDD_retro_タイトル.md`
