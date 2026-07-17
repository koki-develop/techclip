# AWS CloudFrontで設定配信の不具合により大規模なエラー障害が発生
Tags: Cloud

- AWS CloudFront outage serves errors instead of websites (2026-07-16)
  https://www.theregister.com/off-prem/2026/07/16/aws_cloudfront_outage_serves_errors_instead_of_websites/5272421
- AWS CloudFront's hours-long outage knocks websites offline worldwide before fix (2026-07-16)
  https://cybernews.com/news/aws-cloudfront-outage-websites-5xx-errors/
- AWS CloudFront suffers partial outage due to configuration failure (2026-07-16)
  https://www.sdxcentral.com/news/aws-cloudfront-suffers-partial-outage-due-to-configuration-failure/

AWSのCloudFrontでVPC Origins機能を使う顧客向けに設定配信の不具合が発生し、Hugging FaceやUKナショナルロッタリーなど世界中のサービスで数時間にわたり5xxエラーが発生した。原因はプライベートVPCオリジンへの接続を管理する内部フリートの制約超過だった。
