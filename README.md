# 在 EC2上 一鍵部屬高可性 WordPress 在 Ks8 

## 架構圖

透過 K8s + Nginx Load Balance 達成應用高可用架構

![](https://i.imgur.com/AHVikHH.png)




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



EC2 創建 DEMO

![](https://i.imgur.com/AuMXHDK.png)




## Quick Start

>透過 Docker 快速創建 Terraform & Ansible 環境及 Iac Code。


1. 啟動建立好的環境。

```bash
docker run --rm -it jeffwen0105/iac-ec2-k8s bash
```

2.  使用 vi 編輯 credentials ，將 AWS 具備創建 VPC 及 EC2 的 credentials 貼上。

```ini
[default]
aws_access_key_id=<YOUR aws_access_key_id>
aws_secret_access_key=<YOUR aws_secret_access_key>
```



3.  執行自動部屬腳本。

```bash
bash run.sh
```


## 一般操作方式

0. 環境準備 : 需要具備 Terraform 、 Ansible 、 Git 相依套件

1. 下載 IaC 原始碼

```
git clone https://github.com/JeffWen0105/lab-wordpress-k8s-ec2.git && cd lab-wordpress-k8s-ec2
```

2.  編輯 credentials ，將 AWS 具備創建 VPC 及 EC2 的 credentials 貼上。

```ini
[default]
aws_access_key_id=<YOUR aws_access_key_id>
aws_secret_access_key=<YOUR aws_secret_access_key>
```


3.  執行自動部屬腳本。

```bash
bash run.sh
```


Ansible 執行完成即可至瀏覽器訪問頁面

![](https://i.imgur.com/ShugBO8.png)

![](https://i.imgur.com/pB2Zidz.png)


K8s 節點及POD

![](https://i.imgur.com/wTZh2Om.png)

Nginx 設定

![](https://i.imgur.com/S26WpBz.png)