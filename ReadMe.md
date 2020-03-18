## サンプルの使い方

- 以下のボタンから自身のCloud Shell上に当リポジトリを展開します

[![Open in Cloud Shell](http://gstatic.com/cloudssh/images/open-btn.svg)](https://console.cloud.google.com/cloudshell/editor?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fuse200371%2Fgke-training.git&cloudshell_tutorial=walkthroughtutorial.md)

## kubernetesとは

- コンテナのオーケストレーションシステム

- スケールアウトや複数のバージョンのアプリの管理を容易に行える

## GKEとkubernetesの違い

- GKEもGoogle Kubernetes Engineと「kubernetes」の名前が含まれておりkubernetesにおいて差は無いはず

- ただ、GKEはGCP上のリソースが利用出来る為、自前で用意する手間が無い

## kubernetes抽象概念

- Pod(ポッド)　１つ以上のコンテナを実行するkubernetes上の最小管理単位

- Node(ノード)　１つ以上のポッドを実行するワーカーマシン(物理 or 仮想)の単位

- Cluster(クラスタ)　１つ以上のノードをグループ化した単位

- Master Node(マスターノード) クラスタ内に１つ以上存在し、Worker Node(Master NodeではないNode)とPodを管理する
