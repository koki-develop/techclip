---
date: "2026-10-07T08:12:33+09:00"
title: "Anthropic、「Claude for Government」を一般提供開始、FedRAMP High環境で政府機関にシート課金なしのAI活用を提供"
description: "AnthropicがFedRAMP High認証環境で稼働する「Claude for Government」を一般提供開始し、連邦・州政府機関にシート課金なしの利用モデルと専用の管理・セキュリティ機能を提供する。"
tags:
  - AI
references:
  - "https://claude.com/blog/claude-for-government-is-now-generally-available"
---

## 概要

Anthropicは9月30日、米連邦政府のFedRAMP High認証環境で稼働する「Claude for Government」を一般提供開始したと発表した。これにより連邦・州の政府機関は、コンプライアンス要件を損なうことなく、商用顧客と同等の能力をClaudeから得られるようになる。政府機関特有の調達・運用上の制約に対応した形でAI活用の普及を後押しする狙いがある。

## 価格モデルと管理機能

従来のシート単位の課金とは異なり、Claude for Governmentでは機関が利用量に応じて固定の増分単位で支払う方式を採用し、超過しない上限（hard not-to-exceed cap）を設定できる点が特徴だ。これにより、利用者数の変動や予期しない利用増加によるコストの不透明さを避けられる。管理者向けには、部署横断での設定デフォルトの統一、ユーザー・モデル別の支出配分と監視、グループごとの支出上限やモデル利用制限の設定、ATO(Authorization to Operate)取得を支援する監査ログへのアクセスなど、政府機関のガバナンス要件に特化した機能が用意されている。

## セキュリティとコンプライアンスへの対応

セキュリティ面では、会話データを機関が管理するデバイス上にローカル保存できる仕組み、Anthropic側でのセンシティブな操作に対する二者承認(two-person approval)、規制対応のための計測専用の利用データ出力、シングルサインオンによるIDプロバイダ連携などを備える。デプロイも標準的なMDMプラットフォームを通じて行えるため、別途クラウドプロバイダとの契約関係を結ぶ必要がない。既存顧客はアプリ内機能で過去の会話履歴を移行できるほか、新規に利用を希望する機関はclaude.com/solutions/governmentから申請できる。

## 関連サービスと今後の展望

同じFedRAMP認証環境では、Claude Code CLIとClaude for Microsoft 365も早期アクセスとして提供されており、いずれも今回と同様の管理機能を備える。シート課金に縛られない価格モデルと、ATO取得を見据えた監査・ガバナンス機能を組み合わせたことで、Anthropicは連邦政府に限らず州政府機関へのAI導入のハードルを下げる戦略を進めているとみられる。
