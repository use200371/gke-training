# Google Kubernetes Engine 入門

## 目標

+ クラスタの作成

## プロジェクト選択

チュートリアルを展開するプロジェクトを選択して下さい。

<walkthrough-project-setup></walkthrough-project-setup>

## クラスタの作成

- 次のコマンドを実行します。

```sh
gcloud container clusters create sample-cluster --machine-type=g1-small --preemptible --enable-autoscaling --num-nodes=1 --zone=asia-northeast1-a --disk-size=20
```