---
layout: post
title: 横田研の計算機環境
---

## 計算機環境
横田理央研究室では、多数のスーパーコンピュータを利用することができます。
例えば：
- [理化学研究所 富岳](https://www.r-ccs.riken.jp/jp/fugaku)
- [ORNL Summit](https://www.olcf.ornl.gov/summit/)
- [産業技術総合研究所 ABCI](https://abci.ai/)
- [東京工業大学 TSUBAME 3.0](https://www.t3.gsic.titech.ac.jp/)
- [東京大学 Reedbush / Oakforest PACS / Oakbridge-CX](https://www.cc.u-tokyo.ac.jp/supercomputer)

このほかにも、研究室で運用する「ひなどりクラスタ」があります。

### ひなどりクラスタ
ひなどりクラスタはスーパーコンピュータなどでは取り入れられていない最新の環境をいち早く導入して研究を行うことを目的に構築・運用されています。
学生が主体となって仕様決定・調達・運用を行っています。

#### ハードウェア
横田理央研究室での研究対象はGPUであることが多いため、多数のGPUサーバを保有しています（合計28GPUs）。

| CPU                    | ホストメモリ   | GPU (1ノードあたりの搭載数)        | 台数 |
| ---------------------- | ------------ | ------------------------------- | ---- |
| Intel Xeon             | 96GB         | NVIDIA GeForce GTX 1080Ti (2)   | 4    |
| Silver 4215            |              | NVIDIA GeForce RTX 2080 (2)     | 2    |
|                        |              | NVIDIA GeForce RTX 2080Ti (2)   | 1    |
|                        |              | NVIDIA TITAN V (2)              | 1    |
|                        |              | NVIDIA TESLA V100 PCIe 16GB (1) | 1    |
| Intel Xeon E5-2630v3   | 64GB         | NVIDIA TITAN RTX (1)            | 1    |
| Intel Core i9-7940X    | 64GB         | NVIDIA A6000 (2)                | 1    |
| AMD EPYC 7742          | 1TB          | NVIDIA A100 SXM4 (8)            | 1    |

（2021.02.18現在）

他にも、SSHの踏み台となるログインノード、96TBのファイルサーバ、独自のVPNサービスなどを提供しています。
これらのサービスを用いることで、リモートワーク環境からでも実験を行うことができます。

複数の計算機を用いたMPIによる並列計算も10GbEによりサポートしています。
また、これに加えIntel KNL搭載ノードやPEZY SC2搭載ノードも保有しており、特殊なプロセッサについても研究がも行われています。

#### ソフトウェア
##### ジョブスケジューリング
ジョブスケジューリングには[Slurm Workload Manager](https://slurm.schedmd.com/documentation.html)をベースとし、より簡単にジョブの投入ができる独自のシステムを用いています。
Slurmには1ノードに複数のジョブを割り当てる機能がありますが、これを簡単に利用するための機能が備わっています。

##### 監視基盤
[Prometheus](https://prometheus.io/)によるメトリクスの集約、[Grafana](https://grafana.com/)によるメトリクスの可視化を行っています。
監視している主なメトリクスには、CPU使用率やGPU使用率といった性能最適化に利用できるものや、ひなどりクラスタの利用履歴やGPUの温度、消費電力など管理者による監視に必要なものがあります。
ユーザは様々な情報にブラウザ経由でアクセスできます。

![Grafana](/images/grafana.png)

##### 開発環境
CUDA関係や各種コンパイラは[Environment Modules](https://modules.readthedocs.io/en/latest/)で管理されており、好きなバージョンを指定して使うことができます。
標準的なアプリケーション以外にも、プログラムの実行中にGPUの温度や消費電力などを記録していく独自のアプリケーションの提供も行っています。

#### 運用
運用の上で「管理に時間をかけない」ことを大切にしています。
クラスタの運用は、学生や先生のボランティアによって行われておりますが、本業の研究が進まなくなってしまっては元も子もありません。
そのため、構成管理ツールの[Ansible](https://www.ansible.com/)や、リモート管理ツールのIPMI、ユーザ管理のためLDAPのSaaSを導入するなどして、できるだけ手が掛からないようにしています。
新たにノードをセットアップする処理も自動化されており、OSのインストールから30分程度でユーザが利用できます。
