# 在 EC2上 一鍵部屬高可性 WordPress 在 Ks8


## 功能說明

在 AWS EC2 上自動啟三個 EC2 並 WordPress 服務在 K8s 上

1. Terraform 創建下列資源 :

```
vpc 網路，及兩個子網路(一個私有 NAT，另一個公有 IGW)
SG 安全群組開放內往叢集互通，對外開放80、22、30008等端口
創建三台 EC2
```

2. Ansible 創建下列資源:

```
安裝 Dokcer 及 K8s 叢集
k8s 啟動 Wordpress 及 mysql 服務
安裝 Nginx 並設定反向代理至 Wordpress
```


## Quick Start

