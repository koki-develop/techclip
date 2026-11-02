# AWSとGoogle Cloud、PyTorchをTrainium・TPUでネイティブ動作させるバックエンドをオープンソース公開
Tags: Cloud, Programming Languages, AI

- AWSとGoogle Cloudが「PyTorch」のAWS Trainium、Google Cloud TPU対応版をオープンソースで公開、NVIDIAからの移行に挑む (2026-10-27)
  https://www.publickey1.jp/blog/26/awsgoogle_cloudpytorchaws_trainiumgoogle_cloud_tpunvidia.html
- Google and AWS open new paths for PyTorch beyond Nvidia (2026-10-27)
  https://thenewstack.io/pytorch-tpu-trainium-migration/

AWSは独自AIチップTrainium向けのネイティブPyTorchバックエンド「TorchNeuron」を、Google CloudはTPU向けの「TorchTPU」を、それぞれオープンソースで公開した。PyTorch Conference 2026で発表されたもので、既存のPyTorchコードを大きく書き換えることなくNVIDIA製GPU以外のチップ上で実行できるようにする。ただしピーク性能を引き出すには依然ハードウェア固有の最適化が必要とされ、NVIDIA CUDAへの依存を減らす業界的な動きの一環と位置づけられている。
