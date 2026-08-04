# Hugging FaceのDiffusersライブラリに任意コード実行の脆弱性「FaceHugger」、悪意あるモデル読み込みで発火
Tags: Security, AI

- Hugging Face Diffusers Flaws Could Let Model Repositories Execute Arbitrary Code (2026-08-03)
  https://thehackernews.com/2026/08/hugging-face-diffusers-flaws-could-let.html
- Bugs in Hugging Face Diffusers Bypass Custom Code Safeguard (2026-07-28)
  https://www.infosecurity-magazine.com/news/hugging-face-diffusers-trust/

Hugging FaceのDiffusersライブラリに「FaceHugger」と呼ばれる複数の深刻な脆弱性が発見された。悪意あるモデルリポジトリを読み込むだけでtrust_remote_codeの安全対策を回避して任意コードが実行される恐れがあり、0.38.0未満のバージョンが影響を受ける。
