# Google、ユーザー操作不要のゼロクリックRCEを含むAndroidの重大な脆弱性を修正
Tags: Security

- Google Issues Patches for Critical Android Flaw That Could Allow RCE Without User Interaction (2026-11-04)
  https://thehackernews.com/2026/11/google-patches-critical-android-flaw.html
- Android Security Bulletin—November 2026 (2026-11-02)
  https://source.android.com/docs/security/bulletin/2026/2026-11-01
- New Android SMS of Death exploit can remotely crash unpatched phones (2026-10-31)
  https://www.bleepingcomputer.com/news/security/new-android-sms-of-death-exploit-can-remotely-crash-unpatched-phones/

Googleは2026年11月のAndroidセキュリティ公開で216件の脆弱性を修正し、うち23件をクリティカル評価とした。FrameDecoder.cppのヒープバッファオーバーフローに起因するゼロクリックRCE脆弱性(CVE-2026-58868)がAndroid 14~17に影響し、緊急通話にも支障が出かねない「SMS of Death」と呼ばれる脆弱性(CVE-2026-58882)も対象となった。研究者は不正なWAP Pushメッセージ1件で端末をクラッシュさせる概念実証エクスプロイトを既に公開しており、2026年10月の更新で対応済みのAndroid 14~17に対し、Android 12・13は未対応のままだと指摘している。
