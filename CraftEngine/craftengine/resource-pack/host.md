---
description: This page shows all the available host types 本页面显示所有可用的主机类型
---

# 主机

To apply the changes made to the host file, execute the command `/ce reload all`.\
要应用对主机文件所做的更改，执行命令 `/ce reload all` 。

DO NOT SHARE YOUR `config.yml` TO OTHERS Please use environment variables to prevent secret/token leakage\
不要将你的 `config.yml` 分享给其他人 请使用环境变量来防止秘密/令牌泄露

### None 无 <a href="#none" id="none"></a>

Copy 复制

```
type: none
```

### Self 自己 <a href="#self" id="self"></a>

Copy 复制

```
type: self
ip: localhost
port: 8163
protocol: http
deny-non-minecraft-request: true
one-time-token: true
rate-limit:
  max-requests: 5
  reset-interval: 20 # seconds
```

**Using your server as a file host will consume some of its bandwidth.** You must set the IP to your server's actual address; otherwise, players won't be able to download resource packs!\
将你的服务器用作文件宿主将消耗其部分带宽。 你必须将 IP 设置为服务器的实际地址；否则，玩家将无法下载资源包！

Unlike the `self` feature offered by other plugins, **CraftEngine generates a unique & time-limited & one-time token for each player**, blocking all unauthorized requests to prevent targeted traffic attacks. However, this does not guarantee absolute security—reverse-engineering attacks remain a potential risk.\
与其他插件提供的 `self` 功能不同，CraftEngine 为每位玩家生成一个独特、有时间限制且仅限一次的令牌，以阻止所有未经授权的请求，从而防止定向流量攻击。然而，这并不能保证绝对安全——逆向工程攻击仍然是一个潜在的风险。

### External 外部 <a href="#external" id="external"></a>

Copy 复制

```
type: external
url: ""
uuid: "" # Optional
sha1: "" # Optional
```

**Host your resource pack on an external server.** This eliminates bandwidth consumption on your own server.\
将资源包托管在外部服务器上。 这消除了您自己服务器上的带宽消耗。

Typically, after uploading your resource pack to a hosting platform, it will provide you with:\
通常，在将您的资源包上传到托管平台后，它将为您提供：

* **URL**
* **UUID (Optional) UUID（可选）**
* **SHA1 (Optional) SHA1（可选）**

Simply fill these three fields with the corresponding values.\
只需用相应的值填充这三个字段。

Note that regular resource pack updates are required to maintain version integrity. This maintenance procedure requires manual intervention.\
请注意，为了保持版本完整性，需要定期更新资源包。这个维护程序需要人工干预。

### LobFile <a href="#lobfile" id="lobfile"></a>

Copy 复制

```
type: lobfile
use-environment-variables: false
api-key: "xxx"
```

**Manage your resource packs via Lobfile.**\
**通过 Lobfile 管理你的资源包。**

When regenerating resource packs, the plugin will automatically upload a copy to Lobfile. Compared to ExternalHost, this eliminates manual uploads.\
在重新生成资源包时，插件将自动将副本上传到 Lobfile。与 ExternalHost 相比，这消除了手动上传的需要。

_(Note: An API-KEY is required. Visit_[ _lobfile_](https://lobfile.com/) _for details.)_\
（注意：需要 API-KEY。详情请访问 lobfile。）

Enviroment Variables 环境变量

Copy 复制

```
CE_LOBFILE_API_KEY
```

### OneDrive <a href="#onedrive" id="onedrive"></a>

Copy 复制

```
type: onedrive
use-environment-variables: false
client-id: ""
client-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

Enviroment Variables 环境变量

Copy 复制

```
CE_ONEDRIVE_CLIENT_ID
CE_ONEDRIVE_CLIENT_SECRET
CE_ONEDRIVE_REFRESH_TOKEN
```

### Dropbox <a href="#dropbox" id="dropbox"></a>

Copy 复制

```
type: dropbox
use-environment-variables: false
app-key: ""
app-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

Enviroment Variables 环境变量

Copy 复制

```
CE_DROPBOX_APP_KEY
CE_DROPBOX_APP_SECRET
CE_DROPBOX_REFRESH_TOKEN
```

### Alist <a href="#alist" id="alist"></a>

Copy 复制

```
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

Enviroment Variables 环境变量

Copy 复制

```
CE_ALIST_USERNAME
CE_ALIST_PASSWORD
CE_ALIST_FILE_PASSWORD
```

### Gitlab <a href="#gitlab" id="gitlab"></a>

Copy 复制

```
type: gitlab
use-environment-variables: false
gitlab-url: ""
access-token: ""
project-id: ""
```

According to GitLab's Terms of Service, you are not permitted to use GitLab's servers for content distribution. You must set up your own GitLab server for distributing resource packs.\
根据 GitLab 的服务条款，您不得使用 GitLab 的服务器进行内容分发。您必须自行搭建 GitLab 服务器来分发资源包。

[https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/](https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/)

> We refer to “our services” throughout – this means all services (including related websites) owned or operated by GitLab.\
> 我们全文中提到的“我们的服务”是指 GitLab 拥有或运营的所有服务（包括相关网站）。
>
> ...
>
> 3\. So our services, and those of others, run securely, and without disruption, you must not:\
> 3\. 因此，为了确保我们的服务以及他人的服务能够安全、无中断地运行，您必须不得：
>
> * Do anything to compromise, overburden, or otherwise impair our services or those of others, including using our services to mine or demonstrate proof-of-work for a cryptocurrency or blockchain, or for the primary purpose of distributing content.\
>   采取任何损害、过载或以其他方式妨碍我们的服务或他人服务的行为，包括使用我们的服务进行加密货币或区块链的挖矿或工作量证明演示，或主要目的是分发内容。

Enviroment Variables 环境变量

Copy 复制

```
CE_GITLAB_ACCESS_TOKEN
```

### s3 <a href="#s3" id="s3"></a>

Copy 复制

```
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

**When using S3, the plugin enhances security by generating unique & time-limited & one-time download link for each player.** This prevents attackers from obtaining fixed URLs to launch attacks. Additionally, the plugin automatically handles resource pack uploads during updates.\
在使用 S3 时，插件通过为每位玩家生成唯一且有时间限制的一次性下载链接来增强安全性。这可以防止攻击者获取固定 URL 以发起攻击。此外，插件在更新期间会自动处理资源包的上传。

Enviroment Variables 环境变量

Copy 复制

```
CE_S3_ACCESS_KEY_ID
CE_S3_ACCESS_KEY_SECRET
```
