# npmとPyPIで決済SDKを装ったタイポスクワッティング攻撃キャンペーンが発覚
Tags: Security, OSS

- Coordinated npm and PyPI Campaign Typosquats Popular Secure Payment Apps (2026-07-07)
  https://socket.dev/blog/npm-pypi-campaign-typosquats-popular-secure-payment-apps

npmとPyPIの両パッケージレジストリで、Paysafe・Skrill・Netellerなど有名な決済SDKを装った悪意あるパッケージ計17件（npm 13件、PyPI 4件）が一斉に公開されていたことが判明した。CI/CDのシークレットや認証情報の窃取を狙う手口で、公開から約6分で検知されたものの、パッケージレジストリを狙ったサプライチェーン攻撃のリスクが改めて浮き彫りとなった。
