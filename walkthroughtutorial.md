# Google Kubernetes Engine 入門

## 目標

+ クラスタの作成

## プロジェクト選択

チュートリアルを展開するプロジェクトを選択して下さい。

<walkthrough-project-setup></walkthrough-project-setup>

## クラスタの作成

- 最小な構成のクラスタを作成します。

- GCEはプリエンティブルな共有コアのスペックのVMが1台起動されます。※f1-microの場合、ノード数が最低3台になる為、1つ上のスペックを指定します。

- 次のコマンドを実行します。

```sh
gcloud container clusters create sample-cluster --zone=asia-northeast1-a --machine-type=g1-small --preemptible --enable-autoscaling --num-nodes=1 --max-nodes=1 --disk-size=10
```

- GCP Consoleのメニューよりkubernetes Engineを選択し、クラスタが作成された事を確認します。

- ワークロード(Pod)は何もない状態なので作成したクラスタへWebアプリをデプロイします。

- 次のコマンドを実行します。

```sh
kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
```

- デプロイされたアプリはまだ外部に公開されていません。

- 外部に公開する為、サービスを作成します。

- 次のコマンドを実行します。

```sh
kubectl expose deployment hello-server2 --type NodePort --port 80 --target-port 8080
```

- これでノードの外部IPアドレスを使用して公開された状態になりました。

- 次に公開されたポート番号を調べる為、次のコマンドを実行します。

```sh
kubectl get svc
```

- hello-serverのPORTを参照すると80:99999/TCPの99999(表示されている数値)を覚えておきます。

- 調べたポート番号の通信を許可する為、次のコマンドを実行します。

```sh
gcloud compute firewall-rules create test-node-port --allow tcp:[ポート番号]
```

- ノードの外部IPアドレスを調べるには次のコマンドを実行します。

```sh
kubectl get nodes -o wide
```

- EXTERNAL-IPがノードの外部IPアドレスになります。

- 先程のポート番号と外部アドレスを組み合わせてブラウザよりアクセスします。

- 次のように表示されていれば正しくWebアプリが動作しています。

```
Hello, world!
Version: 1.0.0
Hostname: hello-server-XXXXXXXXX-XXXXX
```

