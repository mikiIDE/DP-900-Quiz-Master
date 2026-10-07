# DP-900-Quiz-Master
Copilot に作ってもらう DP-900 クイズ

## カスタムエージェント

このリポジトリには、DP-900 クイズ作成向けのカスタムエージェントを2つ追加しています。

- `.github/agents/dp900-question-author.agent.md`  
  Microsoft Learn の DP-900 学習内容に沿って、オリジナル4択問題を作成するエージェント。
- `.github/agents/dp900-question-reviewer.agent.md`  
  作成済み問題の正確性・一意正解性・品質を検証し、必要なら修正案を返すエージェント。

## Blazor ゲームアプリ

`DP900AppleQuiz/` に C#（Blazor WebAssembly）版のクイズゲームがあります。

- 不正解または時間切れでリンゴが 1 段階ずつ齧られる
- 5 回ミスでゲームオーバー
- 全問回答でクリア

ローカル実行:

```bash
dotnet run --project DP900AppleQuiz/DP900AppleQuiz.csproj
```

## Azure 無料枠向けデプロイ（Static Web Apps）

このリポジトリには `.github/workflows/azure-static-web-apps.yml` を用意済みです。

1. Azure ポータルで **Static Web Apps** を新規作成（Free プラン）
2. デプロイ元に `mikiIDE/DP-900-Quiz-Master` を指定し、ブランチは `main`
3. Build details は以下を設定
   - App location: `DP900AppleQuiz`
   - Api location: （空）
   - Output location: `wwwroot`
4. 作成後、GitHub Secrets に `AZURE_STATIC_WEB_APPS_API_TOKEN` を登録
5. `main` に push すると GitHub Actions が自動デプロイ
