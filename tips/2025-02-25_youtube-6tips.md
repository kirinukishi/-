# Claude Code 厳選6TIPS

ソース: https://www.youtube.com/watch?v=6HrVn3viwnY

## TIP 1: 双子エージェント（セキュリティ）

- CLAUDE.md にブラックハッカー（攻撃者）とホワイトハッカー（防御者）の役割を定義
- コードを書くたびに自動でセキュリティ監査が走る
- → テンプレート作成済み: `templates/web-security/CLAUDE.md`

## TIP 2: EL Agents（VS Code拡張）

- VS Codeサイドバーにドット絵キャラが常駐
- エージェントの状態に連動してアニメーションが変わる
  - 待機中 → 寝てる
  - コード検索中 → 走り回る
  - ファイル書き込み中 → ハンマー振り下ろす
- 心理的な安心感がある（ちゃんと動いてるのが一目で分かる）

## TIP 3: Claude Code Best Practices リポジトリ

- GitHub: shanraisshan/claude-code-best-practice
- エージェント設定、コマンド、メモリ管理の設定集
- CLAUDE.md は150行以内が推奨
- .claude/agents/, .claude/rules/*.md でモジュール分割
- 推奨MCP: Context7, Playwright, DeepWiki

## TIP 4: 競合ネガティブレビュー分析

- 競合アプリの1〜2星レビューを収集
- 不満点 = そのまま機能要件になる
- 手順: スクレイピング → 要件抽出 → アプリ構築

## TIP 5: 並列セッション（Boris Cherny氏の手法）

- ターミナル5セッション + Web 5〜10セッション同時稼働
- タスクを分割して投げるだけで処理速度が倍以上
- CLAUDE.md に失敗録を追記 → 次から同じミスを回避（自己学習）
- 結果: 6ヶ月間SQLを1行も手書きしていない

## TIP 6: Ollama でローカル無料実行

- Ollama = ローカルLLMをAPIi互換で動かすツール
- Claude Codeの裏側モデルをローカルに差し替え可能
- 推奨モデル: qwen2.5-coder, GLM4
- 必要スペック: RTX 3090/4090 or Apple Silicon M系 32GB+
