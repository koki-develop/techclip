# Ruby向けウェブサーバーPuma 8.0がリリース、IO並行処理の大幅改善とJRubyパフォーマンス最適化
Tags: Programming Languages, OSS

- Puma 8.0 Release (2026-04-09)
  https://github.com/puma/puma/releases

Ruby/Rack向けウェブサーバーPumaがバージョン8.0をリリース。IO負荷の高いリクエストをスレッドプール上限を超えて処理できるmax_io_threads設定、fiber-per-requestサポート、JRuby HTTPパーサーの最適化によるレスポンス毎のアロケーション約50%削減などが含まれる。
