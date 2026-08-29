# ヒューマノイドロボットUnitree G1に重大な脆弱性、Bluetooth経由でroot権限奪取が可能に
Tags: Security, Other

- Two Unitree G1 EDU Humanoid Robot Flaws Enable Root RCE, One Starts Over Bluetooth (2026-08-28)
  https://thehackernews.com/2026/08/two-unitree-g1-edu-humanoid-robot-flaws.html
- UniBLEed: Unauthenticated Root RCE on Any Unitree G1 Humanoid Robot Within Bluetooth Range (2026-08-27)
  https://boschko.ca/g1-ble-rce/
- Hack One Robot, Reach the Next: Unitree G1 Security Flaws (2026-08-29)
  https://securityaffairs.com/198085/hacking/hack-one-robot-reach-the-next-unitree-g1-security-flaws.html

ヒューマノイドロボットUnitree G1 EDUに、root権限でのリモートコード実行を可能にする複数の脆弱性(CVE-2026-76639、CVE-2026-76640など)が発見された。ネットワーク経由の脆弱性に加え、Bluetooth Low Energy経由でも認証・ペアリングなしにroot権限を奪取できる「UniBLEed」と呼ばれる手法が公開されており、Wi-Fiプロビジョニング処理中のバッファオーバーフローを悪用する。物理的な接触なしに近接する別のロボットへワーム的に感染が拡大し得る点が特に懸念されている。
