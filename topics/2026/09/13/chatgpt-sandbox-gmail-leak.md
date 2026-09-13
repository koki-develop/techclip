# ChatGPTのサンドボックス欠陥により、他ユーザーのGmailデータが流出する脆弱性が発覚
Tags: Security, AI

- ChatGPT Flaw Let a Planted Prompt Send a Victim's Gmail Data to Another Account (2026-09-08)
  https://thehackernews.com/2026/09/chatgpt-flaw-let-planted-prompt-send.html
- The Shared Clipboard Inside the Sandbox: Cross-Account Data Leakage in ChatGPT (2026-09-08)
  https://research.checkpoint.com/2026/the-shared-clipboard-inside-the-sandbox-cross-account-data-leakage-in-chatgpt/
- ChatGPT Sandbox Flaw Let a Planted Prompt Ship Victim's Gmail Data to Another Account (2026-09-09)
  https://thecyberexpress.com/chatgpt-sandbox-flaw-leads-to-gmail-leak/

Check Point Researchの調査により、ChatGPTのコード実行サンドボックスがOpenAIの共有JFrog Artifactoryインスタンスを介して分離しきれておらず、仕込まれたプロンプトインジェクションによってあるユーザーのGmailデータが別ユーザーのアカウントへ密かに送信され得る欠陥が発覚した。OpenAIは問題のArtifactoryインスタンスを廃止して対応した。
