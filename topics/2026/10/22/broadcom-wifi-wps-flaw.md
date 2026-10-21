# BroadcomのWi-Fi WPS実装に未修正の重大欠陥、電波到達範囲内からルーターをroot権限で乗っ取り可能
Tags: Security

- Unpatched Broadcom Wi-Fi flaw lets attackers take over routers (2026-10-19)
  https://thehackernews.com/2026/10/unpatched-broadcom-wi-fi-flaw-lets.html

研究者Quentin Kaiser氏が、Broadcom製Wi-FiチップのWPS実装に存在する脆弱性を公開した。断片化されたWPSメッセージの処理に不備があり、パスワードや事前ペアリングなしで電波到達範囲内の攻撃者がルーター上でroot権限のコードを実行できる。古いeCosベースのチップでは今後も修正されない見込みで、BroadcomはCVE番号の割り当ても拒否している。
