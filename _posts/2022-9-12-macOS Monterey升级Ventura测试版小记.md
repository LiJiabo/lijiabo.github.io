---
layout: article
title: macOS Monterey升级Ventura测试版小记
tags: macOS Monterey Ventura beta
sharing: true
key: F5AB19B8-2819-49EC-B2DB-EA95C5065823
lang: zh
permalink: 2022/09/12/montereytoventura.html
---

### 一开始的想法

我有1块三星T7 Shield PSSD，就想把新的macOS 13开发者测试版系统**安装到移动硬盘里**尝尝鲜，结果遇上了大麻烦(−_−＃)

### 升级过程

升级时，按照网上的说法：

1. 安装macOSDeveloperBetaAccessUtility.dmg
2. 检查系统更新，下载更新
3. 可以看到Install macOS Ventura.app（根本没有！）
4. 打开，选择安装磁盘时选外部磁盘
5. 成功！

### 问题及解决过程

安装macOSDeveloperBetaAccessUtility.dmg，检查更新后，**会提示类似“此更新与此Mac不兼容”的提示**，然后还是和普通的系统更新一样：下载→同意条款→升级，点击升级后**直接就重启更新了**，**根本没有什么Install macOS Ventura.app**

大问题出在我想将系统降级回macOS Monterey的时候。

根据网上的说法，降级有这几种方法：

- 使用时间机器
- 抹掉系统磁盘，重装

1. 使用时间机器
   一开始我直接关机，开机按住电源键进入恢复模式后选择“从时间机器恢复”，结果**提示必须使用迁移助理**。使用迁移助理后，我发现它其实是只能将除了系统之外的更改恢复，**并不能直接从13恢复回12**。（其实只能先重装12系统后再使用迁移助理恢复才可行）

2. **抹掉系统磁盘，重装**

   于是我就先在App Store里下载了macOS Monterey，这才有Install macOS Monterey.app（直接安装会提示无法在更高的系统版本运行），制作好安装盘，**准备好12系统的时间机器备份和12.5.1的安装盘**（升测试版系统必备！），就抹掉了系统磁盘准备重装

#### 重装系统的坑

然而Mac重装系统居然必须要网络连接😓

我们学校的校园网分为3类：

- 需要输入**帐号和密码**的NET/NET-5G
- 需要客户端登录的PC
- 需要网页登录的TEST/TEST-5G

我自己还有iPhone 12的热点

然而**这些网络都不行**，好像必须要使用无密码且无需网页登录/只需要输入密码的Wi-Fi才行（无需登录的有线网当然也可以）

聊天咨询Apple技术支持后，得知需要另一台Mac，使用Apple Configurator 2才能降级，前往Apple授权服务提供商后也需要第二天才能拿到电脑，其实**都不需要**，直接连接符合上述要求的网络，**使用自带的重装功能**（我的Mac自带的就是macOS Monterey系统）**或者USB安装器安装新系统即可**。
