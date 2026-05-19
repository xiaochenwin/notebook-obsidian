---
author: JoneeySir
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU3NzU3NTQxMQ==&mid=2247485717&idx=1&sn=8d3465c8032714fd5c55708598b95197&chksm=fc98ee884059737fabdeda657341642783b910d60d0a961b538c6986c5b2f4d7ce7a23d49cee&mpshare=1&scene=1&srcid=0519QOvAQIgAFcdNX34wnjNp&sharer_shareinfo=c21cdab0fb7df490356436b6dfc3766d&sharer_shareinfo_first=c21cdab0fb7df490356436b6dfc3766d#rd
saved: 2026-05-19 13:09:50
tags:
  - 笔记同步助手
id: a7a12cb0-8ed6-4aff-9e25-98191e387d5f
---

公众号名称：从不一样开始

作者名称：JoneeySir

发布时间：2026-05-12 20:09

  

![[笔记同步助手/images/49997a1e718c986f93671e439bbea631_MD5.png]]

经常需要局域网内多个设备之间，或跨越多个不同网络进行数据及时同步，又烦透了手工上传、下载，这时 Syncthing 将派上用场，它可以真正双向同步、文件删除也同步、增量同步、速度快、不走公网，如果和其他网络神器结合使用，将带来非常大的便利。

Syncthing 是一个持续文件同步程序。它能够在两台或多台计算机之间实时同步文件，并通过安全机制防止数据被他人窥探。你的数据只属于你自己，你有权决定数据存储在哪里、是否与第三方共享，以及它如何通过互联网传输。

使用这个工具实现了在统信UOS、苹果MacOS和Android上代码配置、日历数据等随时跨网双向更新，非常方便。

​

## 数据同步应用场景

-   • 局域网高速同步：多台电脑互传、不经过互联网、通常能跑满千兆网速  
    非常适合：视频素材、大文件、游戏存档
    
-   • 替代网盘：没有容量限制、不限速、更私密
    
-   • 手机照片自动备份：Android 上可自动同步相册、截图、下载目录到电脑或 NAS。
    
-   • 开发环境同步：配置文件、Markdown 笔记、SSH 配置、dotfiles、项目代码
    

可以在树莓派、OpenWRT、Linux小主机部署 Syncthing，打造家庭私有同步中心。

​

## Syncthing 的核心优势

### 去中心化（P2P）同步

不像很多网盘依赖中心服务器，Syncthing 采用点对点（P2P）同步：文件直接在设备之间传输、不需要上传到第三方云服务器、没有“中间人”保存你的数据，即使官方服务器关闭，你的同步仍然可以继续。

### 实时同步

文件变化后会自动检测：新建文件、修改文件、删除文件，几乎可以立即同步到其他设备。适合：多设备办公、笔记同步、配置文件同步、局域网高速同步

### 跨平台支持强

支持系统：Linux、macOS、Windows、Android、BSD、Docker、NAS，支持架构：ARM64、X86\_64、MIPS、RISC、PowerPC

### 不需要公网 IP

支持：NAT 穿透、中继服务器（Relay）、局域网自动发现，即使两台设备都在家用宽带后面，通常也能自动连接。

### 端到端加密（E2EE）

Syncthing 默认使用 TLS 加密：传输过程加密，中间人无法窃听，Relay 中继服务器也看不到文件内容，即使经过公网中转服务器也只能看到加密数据流。

每台设备都有唯一 Device ID：类似：QWERTY-ABCDEFG-123456...只有手动添加并信任的设备才能同步，陌生设备无法加入同步。

无账号体系：不需要注册账号、不需要邮箱、不需要手机号、不依赖厂商身份认证，隐私性非常强。

### 文件版本控制

文件历史版本、删除回收、冲突保留、避免误删文件。

​

## Syncthing 安装使用

Syncthing 官方网址最新版本是2.1.0  
[https://syncthing.net/downloads/](https://syncthing.net/downloads/)

### 安装同步神器

安装非常简单，无任何额外依赖，可以下载官方安装包直接解压，得到可执行文件，也可以使用以下命令安装。

​

```
brew install syncthing
# 在苹果系统安装

sudo apt install syncthing
# 在 Debian Linux上安装

pkg install syncthing
# 在Android手机安装
```

![[笔记同步助手/images/6431b8389793e42dabbe118adbcdfde2_MD5.png]]

### 设置同步文件夹

安装 Syncthing 工具后，可以作为后台服务启动，也可以直接 syncthing 命令运行后会自动弹出 WEB设置界面，在手机上也是如此。

​

```
brew services start syncthing
# 苹果系统启动同步服务

systemctl --user enable --now syncthing
# Linux 系统启动同步服务

http://127.0.0.1:8384
# 在同步设备上访问这个网址，进行同步设置
```

安装后进行以下设置，开始数据同步。两台多台多机器：添加对方设备 ID、设置同步文件夹ID、共享同一个文件夹、设置同步目录

> 为什么神器同步速度这么快？  
> 实际使用时会发现同步几乎是实时的，因为它对文件变化立刻检测、计算块 hash、增量同步、P2P 传输

### 使用官方APT源

对于Debian来说，官方还提供了APT源。

​

```
curl -s https://syncthing.net/release-key.txt | \
sudo gpg --dearmor -o /usr/share/keyrings/syncthing-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/syncthing-archive-keyring.gpg] \
https://apt.syncthing.net/ syncthing stable" | \
sudo tee /etc/apt/sources.list.d/syncthing.list

sudo apt update
sudo apt install syncthing
systemctl --user restart syncthing
```

### 

两个公众号文尾

分享游泳心得和软件读书笔记

感谢您支持鼓励点赞评论转发

![[笔记同步助手/images/007433421edf8293f12f554967961874_MD5.jpg]]

---

Original JoneeySir 从不一样开始

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/bf5a6276_1779167389372?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU3NzU3NTQxMQ%3D%3D%26mid%3D2247485717%26idx%3D1%26sn%3D8d3465c8032714fd5c55708598b95197%26chksm%3Dfc98ee884059737fabdeda657341642783b910d60d0a961b538c6986c5b2f4d7ce7a23d49cee%26mpshare%3D1%26scene%3D1%26srcid%3D0519QOvAQIgAFcdNX34wnjNp%26sharer_shareinfo%3Dc21cdab0fb7df490356436b6dfc3766d%26sharer_shareinfo_first%3Dc21cdab0fb7df490356436b6dfc3766d%23rd&s=obsidian)