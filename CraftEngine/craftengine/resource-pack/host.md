---
description: 本页面显示所有可用的主机类型
---

# 🛜 主机

要应用对主机文件所做的更改，需执行命令 `/ce reload all`。

不要将你的 `config.yml` 分享给其他人！ 请使用环境变量来防止密钥/令牌泄露。

## 无 <a href="#none" id="none"></a>

```yaml
type: none
```

## 自托管 <a href="#self" id="self"></a>

```yaml
type: self
ip: localhost
port: 8163
protocol: http
deny-non-minecraft-request: true
one-time-token: true
rate-limit:
  max-requests: 5
  reset-interval: 20 # 秒
```

\*\*将自己的服务器用作文件托管会消耗其部分带宽。\*\*你必须将IP设置为服务器的实际地址；否则，玩家将无法下载资源包！

与其他插件提供的 `self` 功能不同，**CraftEngine为每位玩家生成一个独特、有时间限制且仅限一次的令牌**，以阻止所有未经授权的请求，从而防止定向流量攻击。然而，这并不能保证绝对的安全——逆向工程攻击仍然是一个潜在的风险。

## 外部托管 <a href="#external" id="external"></a>

```yaml
type: external
url: ""
uuid: "" # 可选
sha1: "" # 可选
```

**将资源包托管在外部服务器上**，可以减少自己服务器上的带宽消耗。

通常把资源包上传到托管平台后，它会为你提供：

* **URL**
* **UUID（可选）**
* **SHA1（可选）**

只需将相应的值填写到对应的三个键值对即可。

请注意，为了保持版本的完整性，需要定期更新资源包。这个维护程序需要人工干预。

## LobFile <a href="#lobfile" id="lobfile"></a>

```yaml
type: lobfile
use-environment-variables: false
api-key: "xxx"
```

**通过LobFile管理你的资源包。**

在重新生成资源包时，插件会自动将副本上传到LobFile。与外部托管相比，该方式无需手动上传。

_(Note: An API-KEY is required. Visit_[ _lobfile_](https://lobfile.com/) _for details.)_\
&#xNAN;_（注意：需要API-KEY。详情请访问_[ _LobFile_](https://lobfile.com/)_。）_

环境变量

```yaml
CE_LOBFILE_API_KEY
```

## OneDrive <a href="#onedrive" id="onedrive"></a>

```yaml
type: onedrive
use-environment-variables: false
client-id: ""
client-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

环境变量

```yaml
CE_ONEDRIVE_CLIENT_ID
CE_ONEDRIVE_CLIENT_SECRET
CE_ONEDRIVE_REFRESH_TOKEN
```

## Dropbox <a href="#dropbox" id="dropbox"></a>

```yaml
type: dropbox
use-environment-variables: false
app-key: ""
app-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

环境变量

```yaml
CE_DROPBOX_APP_KEY
CE_DROPBOX_APP_SECRET
CE_DROPBOX_REFRESH_TOKEN
```

## Alist <a href="#alist" id="alist"></a>

```yaml
type: alist
use-environment-variables: false
disable-upload: false
api-url: ""
username: ""
password: ""
file-password: ""
otp-code: ""
upload-path: "server_resource_pack.zip"
```

环境变量

```yaml
CE_ALIST_USERNAME
CE_ALIST_PASSWORD
CE_ALIST_FILE_PASSWORD
```

## GitLab <a href="#gitlab" id="gitlab"></a>

```yaml
type: gitlab
use-environment-variables: false
gitlab-url: ""
access-token: ""
project-id: ""
```

根据GitLab的服务条款，你不得使用GitLab的服务器进行内容分发。你必须自行搭建GitLab服务器来分发资源包。

[https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/](https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/)

> We refer to “our services” throughout – this means all services (including related websites) owned or operated by GitLab.
>
> ...
>
> 3\. So our services, and those of others, run securely, and without disruption, you must not:
>
> * Do anything to compromise, overburden, or otherwise impair our services or those of others, including using our services to mine or demonstrate proof-of-work for a cryptocurrency or blockchain, or for the primary purpose of distributing content.

环境变量

```yaml
CE_GITLAB_ACCESS_TOKEN
```

## S3 <a href="#s3" id="s3"></a>

```yaml
type: s3
endpoint: ""
bucket: ""
access-key-id: ""
access-key-secret: ""
protocol: "https"
path-style: false
region: "auto"
upload-path: "server_resource_pack.zip"
use-legacy-signature: true
validity: 10
cdn:
  domain: ""
  protocol: "https"
```

\*\*在使用S3时，插件通过为每位玩家生成唯一且有时间限制的一次性下载链接来增强安全性。\*\*这可以防止攻击者获取固定的URL链接来发起攻击。此外，插件在更新期间会自动处理资源包的上传。

环境变量

```yaml
CE_S3_ACCESS_KEY_ID
CE_S3_ACCESS_KEY_SECRET
```
