# Bing Imagesの脆弱性、細工SVGでMicrosoft本番サーバー上のSYSTEM権限コード実行が可能に
Tags: Security

- Bing Images Flaws Let Crafted SVGs Run Commands as SYSTEM on Microsoft's Servers (2026-07-24)
  https://thehackernews.com/2026/07/bing-images-flaws-let-crafted-svgs-run.html
- Bing Images RCEs: How XBOW Found Three Critical Flaws (2026-07-23)
  https://xbow.com/blog/bing-images-rce-vulnerabilities
- Bing Images Vulnerability Let Attackers Execute Remote Code on Microsoft Servers Using SVG File (2026-07-24)
  https://cybersecuritynews.com/bing-images-vulnerability/

セキュリティ研究チームXBOWが、Bing Imagesの画像処理パイプラインに存在する3件の重大な脆弱性(CVE-2026-32194、CVE-2026-32191など、最大CVSS 9.8)を発見した。細工したSVGファイルをアップロードするだけでMicrosoftの本番サーバー上でSYSTEM権限のコマンドが実行可能だったが、責任ある開示を経てMicrosoftが修正済みである。
