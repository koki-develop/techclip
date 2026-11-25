# JDK 28、JEP 545によりZGCのメモリ準備処理を起動パスから分離し高速ウォームアップを実現
Tags: Programming Languages

- JEP 545 Moves ZGC Memory Preparation off the Startup Path in JDK 28 (2026-11-23)
  https://www.infoq.com/news/2026/11/jep-545-jdk-28/

JDK 28に統合されたJEP 545により、ZGC(Z Garbage Collector)のメモリ準備処理が起動パスからバックグラウンドの並行ワーカースレッドに移された。これにより、最小ヒープサイズでの高速起動と高速なウォームアップを同時に実現できるようになった。
