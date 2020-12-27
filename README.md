# home-network-monitoring

家からパブリックネットワークへの疎通のパフォーマンスをモニタリングするためのコード

## 前提条件

- Docker for Desktop の Kubernetes
  - Elastic Search Operator 導入済み
- helm v3 インストール済み

### Elastic Search Operator インストール方法

基本的には[operatorhub.io](https://operatorhub.io/)の[Elastic Search Operator](https://operatorhub.io/operator/elastic-cloud-eck)のインストール方法に準拠する．

1. `curl -sL https://github.com/operator-framework/operator-lifecycle-manager/releases/download/v0.17.0/install.sh | bash -s v0.17.0`
2. `kubectl create -f https://operatorhub.io/install/elastic-cloud-eck.yaml`
3. `kubectl get csv -n operators`

### helm v3 のインストール方法

[helm のインストール方法](https://helm.sh/docs/intro/install/)にしたがってインストールしてください．
ここでは，v3 移行であれば問題なく実行できます．

## 使い方

### インストール

```sh
kubectl create ns home-network-monitoring
helm install home-network-monitoring ./dousu-home-network-monitoring -n home-network-monitoring
```

### 更新

```sh
helm upgrade home-network-monitoring ./dousu-home-network-monitoring -n home-network-monitoring
```

### ダッシュボード

ダッシュボードは `dashboards/` 以下に[saved_object](https://www.elastic.co/guide/en/kibana/current/managing-saved-objects.html)としておいてあるのでこれをインポートすることで見れるようになります．

## 開発

lint 実行

```sh
helm lint ./dousu-home-network-monitoring
```
