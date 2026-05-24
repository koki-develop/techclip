---
date: "2026-05-25T02:25:42+09:00"
title: "悪意あるVS Code拡張機能経由でGitHub社員端末が侵害、内部リポジトリ約3,800件が流出"
description: "脅威アクターグループ「TeamPCP」が不正なVS Code拡張機能を用いてGitHub社員の端末に侵入し、約3,800件の内部リポジトリを窃取した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/05/github-investigating-teampcp-claimed.html"
  - "https://www.helpnetsecurity.com/2026/05/20/github-breached-teampcp/"
---

## 概要

サイバー犯罪グループ「TeamPCP」（別名：UNC6780）が、悪意を持って改ざんされたVisual Studio Code拡張機能を媒介にGitHub社員の開発端末へ侵入し、約3,800件の内部リポジトリを窃取したことをGitHubが認めた。攻撃者はすでに盗んだソースコードを5万ドル以上で売却リストに掲載しており、買い手が見つからない場合はリークも辞さないと示唆している。GitHubは調査を進める一方で、顧客データへの影響は確認されていないと説明している。

## 攻撃手法：VS Code拡張機能の悪用

今回の侵入経路として確認されたのが、インストール数220万件を誇る人気拡張機能「Nx Console」への不正な改ざんだ。VS Code拡張機能はサンドボックス化が不十分であり、インストールされた開発者マシン上のあらゆるリソース（認証情報、クラウドAPIキー、SSHキーを含む）に対してフルアクセス権を持つ。Aikido SecurityのCharlie Eriksenは「VS Code extensions have full access to everything on the developer's machine, including credentials, cloud keys, and SSH keys（VS Code拡張機能は開発者のマシン上のすべてに完全なアクセス権を持ち、認証情報やクラウドキー、SSHキーも例外ではない）」と警鐘を鳴らす。攻撃者はこの特性を悪用し、GitHub社員の端末に保存されていたGitHub内部リポジトリへのアクセス資格情報を取得したとみられる。

## GitHubの対応と被害範囲

GitHubはインシデントの発覚後、重要なシークレットと認証情報のローテーションを直ちに実施した。現時点では、被害は内部リポジトリのみに限定されており、GitHub.comのユーザーが利用するシステムや顧客データが侵害されたという証拠は見つかっていないと説明している。ただし調査は現在も継続中であり、今後の調査で新たな事実が判明する可能性は残る。

## TeamPCPの活動背景と今後のリスク

TeamPCPはオープンソースプロジェクトやAIツールを標的にしたサプライチェーン攻撃を得意とするグループで、過去にもAquaのTrivy scanner、CheckMarxのKICS、LiteLLM、Telnyx SDK、TanStack、MistralAIなどが被害を受けている。開発者が日常的に使用するツールやパッケージを侵害することで、信頼された経路を通じた広域攻撃を狙うのが特徴だ。今回のGitHub侵害は、開発者エコシステムにおけるサプライチェーンリスクの深刻さを改めて浮き彫りにしており、企業・個人を問わずVS Code拡張機能の信頼性検証や最小権限原則の徹底が急務となっている。
