# Laravel-Lang PHPパッケージがサプライチェーン攻撃で侵害、700以上のリポジトリに認証情報窃取マルウェアを仕込む

Tags: Security, OSS

- Laravel-Lang PHP Packages Compromised to Deliver Cross-Platform Credential Stealer (2026-05-22)
  https://thehackernews.com/2026/05/laravel-lang-php-packages-compromised.html
- Hackers Compromised 233 Versions of Laravel-Lang Packages by Hacking 700 GitHub Repos (2026-05-23)
  https://cybersecuritynews.com/laravel-lang-packages-compromised/
- Laravel Lang Compromised with RCE Backdoor Across 700+ Versions (2026-05-23)
  https://socket.dev/blog/laravel-lang-compromise

LaravelのローカライゼーションライブラリLaravel-Langの233バージョンがサプライチェーン攻撃で侵害され、700以上のGitHubリポジトリに及ぶ悪意あるコードが注入された。Composerオートローダーを悪用した約5,900行のPHPスティーラーがAWS/GCP/AzureのAPIキーやSSHキーなどを窃取する仕組みで、影響を受けた開発者は速やかな依存パッケージの更新と認証情報のローテーションが求められている。
