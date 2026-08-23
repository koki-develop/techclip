# Windows Defenderの正規ブート修復ドライバがカーネル操作の武器に、Black Hatで判明
Tags: Security

- Microsoft Defender's Own Driver Can Be Weaponized to Delete Security Software at Boot (2026-08-20)
  https://research.checkpoint.com/2026/btr-reforged-weaponizing-defenders-remediation-driver-as-a-kernel-operation-primitive/
- Microsoft Defender's Own Driver Can Be Weaponized to Delete Security Software at Boot (2026-08-21)
  https://thehackernews.com/2026/08/microsoft-defenders-own-driver-can-be.html
- Researchers find way to weaponize Windows Defender's own driver (2026-08-21)
  https://www.scworld.com/brief/researchers-find-way-to-weaponize-windows-defenders-own-driver

Check Point Researchは、Black Hat USA 2026およびDEF CON 34で、Windows Defenderの正規署名済みブート時修復ドライバ「BTR.sys」を悪用し、ブート段階でカーネルレベルのファイル・レジストリ操作を任意に実行できる手法を発表した。脆弱性ではなく正規機能の悪用のためCVEは付与されず、パッチ提供の予定もない。
