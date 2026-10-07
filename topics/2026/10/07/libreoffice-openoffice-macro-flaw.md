# LibreOffice・OpenOfficeにマクロ警告なしで任意コード実行を許す脆弱性
Tags: Security

- LibreOffice and OpenOffice Flaws Let Malicious Spreadsheets Run Code Without Macro Warnings (2026-10-06)
  https://thehackernews.com/2026/10/libreoffice-and-openoffice-flaws-let.html

LibreOffice(CVE-2026-63277)とApache OpenOffice(CVE-2026-59265)のCalcに脆弱性が発見され、悪意あるスプレッドシートを開くだけでマクロ実行の警告を表示せずに任意のJavaコードが実行される恐れがあることが判明した。LibreOfficeは10月5日のアップデートで修正済みだが、OpenOfficeは本稿時点で未修正であり、Javaランタイムを無効化することが回避策として推奨されている。
