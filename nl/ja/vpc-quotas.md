---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-06-07"
keywords: quota, resource, classic, access, gateway, address, prefix, VSI, vNIC, floating, SSH, key, security, group, rule, remote, peer, ACL, region, ingress, egress, VPN, policies, load balancer, listener, pool, per

subcollection: vpc-on-classic

---
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# 割り当て量
{: #quotas}

この資料では、{{site.data.keyword.cloud}} 仮想プライベート・クラウドおよびその中で使用できるリソースに対する割り当て量と制限について説明します。

## VPC の割り当て量
{: #vpc-quotas}

アカウントには以下の割り当て量があります。

|   リソース     | 最大数 |
| ------- | :------: |
| 仮想プライベート・クラウド | 1 地域あたり 5 つ |
| クラシック・アクセスを使用する VPC | 1 地域あたり 1 つ |
| パブリック・ゲートウェイ (PGW) | 1 VPC の 1 ゾーンあたり 1 つ |
| アドレス接頭部 | 1 VPC の 1 ゾーンあたり 5 つ |

## サブネットの割り当て量
{: #subnet-quotas}

|   リソース     | 最大数 |
| ------- | :------: |
| サブネット | 1 仮想プライベート・クラウドあたり 15 |


## VSI の割り当て量
{: #vsi-quotas}

|   リソース     | 最大数 |
| ------- | :------: |
| 仮想サーバー・インスタンス (VSI) | デフォルトでは 1 アカウントあたり 100 |
| 1 VSI あたりの vNIC 数 | 1 VSI あたり 5 つ |
| 浮動 IP アドレス | 1 VSI あたり 1 つ |
| SSH 鍵 | 1 アカウントあたり 100 |


## セキュリティー・グループの割り当て量
{: #security-groups-quotas}

セキュリティー・グループとその関連ルールには、アカウントに基づく割り当て量 (制限) がいくつかあります。

|リソース|割り当て量|
|--------|-----|
|セキュリティー・グループ|1 ネットワーク・インターフェースあたり 5 つ|
|セキュリティー・グループ|1 アカウントあたり 500|
|ルール|1 セキュリティー・グループあたり 50|
|リモート・ルール |1 セキュリティー・グループあたり 5 つ|
|ネットワーク・インターフェース|1 セキュリティー・グループあたり 100|

## ACL の割り当て量
{: #acl-quotas}

|リソース|割り当て量|
|--------|-----|
|ACL| 1 地域あたり 30  |
|着信ルール|1 ACL あたり 20 |
|発信ルール |1 ACL あたり 20 |

## VPN の割り当て量
{: #vpn-quotas}

アカウントあたりの現在の VPN リソース制限を次に示します。

|リソース|割り当て量|
|--------|-----|
| VPN ゲートウェイ| 1 アカウントあたり 20 |
| VPN ゲートウェイ | 1 ゾーンあたり 3 つ |
| VPN 接続 | 1 VPN ゲートウェイあたり 10 |
| IKE ポリシー | 1 アカウントあたり 20 |
| IPSec ポリシー | 1 アカウントあたり 20 |
| 単一 VPN ゲートウェイのピア・サブネット | すべての VPN 接続間で 50|
| ピア・サブネット  | 単一の VPN 接続で 15|
| 単一 VPN ゲートウェイのローカル・サブネット | すべての VPN 接続間で 50|
| ローカル・サブネット |  単一の VPN 接続で 15 |

## ロード・バランサーの割り当て量
{: #load-balancer-quotas}

現在のロード・バランサー・リソースの割り当て量を次に示します。

|リソース|割り当て量|
|--------|-----|
|ロード・バランサー| 1 アカウントあたり 20 |
|リスナー| 1 ロード・バランサーあたり 10 |
| プール | 1 ロード・バランサーあたり 10 |
| メンバー | 1 プールあたり 50 |

## 2 次ボリューム割り当て量
{: #secondary-volume-quotas}

| リソース |割り当て量|
|--------|----- |
| インスタンス作成時のインスタンスごとの 2 次ボリューム |  4 つの 2 次ボリュームを要求できます |
| インスタンスあたりの 2 次ボリューム (4 コア未満の既存のインスタンスの場合) | 4 つの 2 次ボリューム |
| インスタンスあたりの 2 次ボリューム (4 コア以上の既存のインスタンスの場合) | 最大 12 個の 2 次ボリューム |

