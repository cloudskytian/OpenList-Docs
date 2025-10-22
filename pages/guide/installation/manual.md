---
title:
  en: Manual installation
  zh-CN: 手动安装
icon: iconfont icon-interact
# This control sidebar order
top: 60
# A page can have multiple categories
categories:
  - guide
  - installation
# A page can have multiple tags
tag:
  - Install
  - Guide
# this page is sticky in article list
sticky: true
# this page will appear in starred articles
star: true
---

## Get OpenList { lang="en" }

## 获取 OpenList { lang="zh-CN" }

::: en
You can download the corresponding binary executable file for the deployment system from [Download](./download) page or [GitHub Release](https://github.com/OpenListTeam/OpenList/releases).
:::

::: zh-CN
您可以在 [下载](./download) 页面或 [GitHub Release](https://github.com/OpenListTeam/OpenList/releases) 下载待部署系统对应的二进制可执行文件。
:::

[![latest version](https://img.shields.io/github/release/OpenListTeam/OpenList)](https://github.com/OpenListTeam/OpenList/releases)

## Install using package manager { lang="en" }

## 使用包管理器安装 { lang="zh-CN" }

### Linux

::: en
Debian/Ubuntu can be installed from OpenList's APT repository and PPA repository, and the service (daemon) will be automatically configured.
:::
::: zh-CN
Debian / Ubuntu 可以从 OpenList 的 APT 仓库和 PPA 仓库安装，且会自动配置好服务（守护进程）。
:::

#### APT Repository { lang="en" }

#### APT 仓库 { lang="zh-CN" }

::: en
Recommended - Automatic GPG Setup

```bash
# One-line install with automatic GPG key setup
curl -fsSL https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/install-apt.sh | bash

# Then install OpenList
sudo apt install openlist -y
```

Manual APT Setup with GPG Verification (Modern systems - Ubuntu 22.04+/Debian 12+)

```bash
# Download and install GPG keyring
curl -fsSL https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/openlist-archive-keyring.gpg | \
  sudo tee /usr/share/keyrings/openlist-archive-keyring.gpg > /dev/null

# Add repository with GPG verification
echo "Types: deb
URIs: https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/
Suites: ./
Signed-By: /usr/share/keyrings/openlist-archive-keyring.gpg" | \
  sudo tee /etc/apt/sources.list.d/openlist.sources

# Update and install
sudo apt update && sudo apt install openlist -y
```

Manual APT Setup without GPG Verification (Not Recommended)

```bash
# Modern systems (Ubuntu 22.04+/Debian 12+)
echo "Types: deb
URIs: https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/
Suites: ./
Trusted: yes" | sudo tee /etc/apt/sources.list.d/openlist.sources

# Legacy systems (Ubuntu <22.04/Debian <12)
echo "deb [trusted=yes] https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/ ./" | \
  sudo tee /etc/apt/sources.list.d/openlist.list

# Update and install
sudo apt update && sudo apt install openlist -y
```

:::
::: zh-CN
推荐 - 自动 GPG 设置

```bash
# 一行命令安装并自动设置 GPG 密钥
curl -fsSL https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/install-apt.sh | bash

# 然后安装 OpenList
sudo apt install openlist -y
```

手动 APT 设置与 GPG 验证（现代系统 - Ubuntu 22.04+/Debian 12+）

```bash
# 下载并安装 GPG 密钥环
curl -fsSL https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/openlist-archive-keyring.gpg | \
  sudo tee /usr/share/keyrings/openlist-archive-keyring.gpg > /dev/null

# 添加带 GPG 验证的仓库
echo "Types: deb
URIs: https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/
Suites: ./
Signed-By: /usr/share/keyrings/openlist-archive-keyring.gpg" | \
  sudo tee /etc/apt/sources.list.d/openlist.sources

# 更新并安装
sudo apt update && sudo apt install openlist -y
```

手动 APT 设置（没有 GPG 验证， 不推荐）

```bash
# 现代系统（Ubuntu 22.04+/Debian 12+）
echo "Types: deb
URIs: https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/
Suites: ./
Trusted: yes" | sudo tee /etc/apt/sources.list.d/openlist.sources

# 旧版系统（Ubuntu <22.04/Debian <12）
echo "deb [trusted=yes] https://github.com/OpenListTeam/OpenList-APT/releases/latest/download/ ./" | \
  sudo tee /etc/apt/sources.list.d/openlist.list

# 更新并安装
sudo apt update && sudo apt install openlist -y
```

:::

#### PPA Repository { lang="en" }

#### PPA 仓库 { lang="zh-CN" }

::: en
Alternative - Launchpad

```bash
# Add PPA repository
sudo add-apt-repository ppa:openlist/server
sudo apt update

# Install OpenList
sudo apt install openlist -y
```

:::
::: zh-CN
备用方法 - Launchpad

```bash
# 添加 PPA 仓库
sudo add-apt-repository ppa:openlist/server
sudo apt update

# 安装 OpenList
sudo apt install openlist -y
```

:::

#### Flatpak { lang="en" }

#### Flatpak { lang="zh-CN" }

::: en
OpenList can be installed as a Flatpak package on most Linux distributions. Flatpak provides a sandboxed environment and automatic updates.

:::
::: zh-CN
OpenList 可以在大多数 Linux 发行版上作为 Flatpak 软件包安装。Flatpak 提供沙盒环境和自动更新。

:::

[![Flatpak package](https://img.shields.io/badge/dynamic/json?color=4A90E2&label=Flatpak&query=tag_name&url=https%3A%2F%2Fapi.github.com%2Frepos%2FOpenListTeam%2FOpenList-FLATPAK%2Freleases%2Flatest&logo=flatpak)](https://github.com/OpenListTeam/OpenList-FLATPAK/releases)

::: en
One-line Installation (Recommended)

```bash
curl -fsSL https://github.com/OpenListTeam/OpenList-FLATPAK/releases/latest/download/install-flatpak.sh | bash
```

Manual Installation

```bash
# Install Flatpak (if not already installed)
# On Ubuntu/Debian
sudo apt install flatpak

# On Fedora
sudo dnf install flatpak

# On Arch Linux
sudo pacman -S flatpak

# Add Flathub repository (required for dependencies)
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Download and install OpenList Flatpak package
wget https://github.com/OpenListTeam/OpenList-FLATPAK/releases/latest/download/org.oplist.openlist-linux-x86_64.flatpak
flatpak install --user --bundle org.oplist.openlist-linux-x86_64.flatpak -y

# Start OpenList
flatpak run org.oplist.openlist server
```

:::
::: zh-CN
一行命令安装（推荐）

```bash
curl -fsSL https://github.com/OpenListTeam/OpenList-FLATPAK/releases/latest/download/install-flatpak.sh | bash
```

手动安装

```bash
# 安装 Flatpak（如果尚未安装）
# 在 Ubuntu/Debian
sudo apt install flatpak

# 在 Fedora
sudo dnf install flatpak

# 在 Arch Linux
sudo pacman -S flatpak

# 添加 Flathub 仓库（依赖项所需）
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# 下载并安装 OpenList Flatpak 软件包
wget https://github.com/OpenListTeam/OpenList-FLATPAK/releases/latest/download/org.oplist.openlist-linux-x86_64.flatpak
flatpak install --user --bundle org.oplist.openlist-linux-x86_64.flatpak -y

# 启动 OpenList
flatpak run org.oplist.openlist server
```

:::

### Windows

::: en
OpenList can be installed from package managers Scoop main and WinGet on Windows.
:::
::: zh-CN
Windows 可以从 Scoop main 和 WinGet 安装。
:::

#### Scoop

[![Scoop package](https://repology.org/badge/version-for-repo/scoop/openlist.svg)](https://repology.org/project/openlist/versions)

```powershell
scoop install openlist
openlist server
```

#### WinGet

[![winget package](https://repology.org/badge/version-for-repo/winget/openlist.svg)](https://repology.org/project/openlist/versions)

```powershell
winget install OpenListTeam.OpenList
openlist server
```

### Android

::: en
::: tip
OpenList follows the AGPL 3.0 open-source license, assumes no responsibility for any downstream derivative projects, and reserves the right to pursue their compliance with the same license.
:::

::: zh-CN
::: tip
OpenList 遵循 AGPL 3.0 开源协议，对任何下游衍生项目概不负责，且保留追究其同样遵守该协议的权利。
:::

::: en
There are four ways to choose based on your needs

1. Using **https://github.com/OpenListTeam/OpenList-Mobile**
2. Using **https://github.com/LeoHaoVIP/AListLiteAndroid**
3. Using **https://github.com/jing332/AListFlutter** (no longer maintained)
4. Use `termux` to run
   - Reference: **https://anwen-anyi.github.io/index/14-android_install.html**
   - Note: Remember to authorize the APP, set the background running and battery saving policy to unlimited, otherwise it may be killed in the background, causing it to be suddenly interrupted and unusable during background use.

:::
::: zh-CN
有四种办法根据自己的需求选择

1. 使用 **https://github.com/OpenListTeam/OpenList-Mobile**
2. 使用 **https://github.com/LeoHaoVIP/AListLiteAndroid**
3. 使用 **https://github.com/jing332/AListFlutter** (已停止维护)
4. 使用 `termux` 运行
   - 参考：**https://anwen-anyi.github.io/index/14-android_install.html**
   - 注意事项：记得给APP授权，后台运行、电池省电策略设置为无限制，否则可能会被杀后台导致挂在后台使用期间突然中断无法使用

:::

#### Termux

[![Termux package](https://repology.org/badge/version-for-repo/termux/openlist.svg)](https://repology.org/project/openlist/versions)

```bash
pkg update
pkg install openlist
openlist server
```

## Running { lang="en" }

## 手动运行 { lang="zh-CN" }

::: en

```bash
Usage:
  openlist [command]

Available Commands:
  admin       Show admin user's info and some operations about admin user's password
  cancel2fa   Delete 2FA of admin user
  completion  Generate the autocompletion script for the specified shell
  crypt       Encrypt or decrypt local file or dir
  help        Help about any command
  kill        Force kill openlist server process by daemon/pid file
  lang        Generate language json file
  restart     Restart openlist server by daemon/pid file
  server      Start the server at the specified address
  start       Silent start openlist server with `--force-bin-dir`
  stop        Same as the kill command
  storage     Manage storage
  version     Show current version of OpenList

Flags:
      --data string     data folder (default "data")
      --config string   config file (default "data/config.json")
      --debug           start with debug mode
      --dev             start with dev mode
      --force-bin-dir   Force to use the directory where the binary file is located as data directory
  -h, --help            help for openlist
      --log-std         Force to log to std
      --no-prefix       disable env prefix

Use "openlist [command] --help" for more information about a command.
```

:::

::: zh-CN

```bash
使用方法：
  openlist [命令]

可用命令：
  admin      显示管理员用户的信息及管理员用户密码相关操作
  cancel2fa  删除管理员用户的 2FA
  completion 生成指定 shell 的自动补全脚本
  crypt      加密或解密本地文件或目录
  help       显示命令帮助
  kill       强制通过守护进程/进程 ID 文件终止 openlist 服务器进程
  lang       生成语言 JSON 文件
  restart    通过守护进程/进程 ID 文件重启 openlist 服务器
  server     启动指定地址的服务器
  start      静默启动 openlist 服务器，使用 `--force-bin-dir`
  stop       与 kill 命令相同
  storage    管理存储
  version    显示当前 OpenList 版本

标志参数：
  --data string   数据文件夹（默认值 "data"）
  --config string 配置文件（默认值 "data/config.json"）
  --debug         启动时使用调试模式
  --dev           启动时使用开发模式
  --force-bin-dir 强制使用二进制文件所在目录作为数据目录
  -h, --help      显示 openlist 命令帮助
  --log-std       强制日志输出到标准输出
  --no-prefix     禁用环境前缀

使用 "openlist [命令] --help" 获取更多命令信息。
```

:::

::: en
::: tip
If there is a prompt as follows：It is because [your GLIBC version is too low](../../faq/why#lib64-libc-so-6-version-glibc-2-28-not-found-required-by-openlist-or-accept-function-not-implemented), it is recommended to download the musl version.

```txt
lib64/libc.so.6: version `GLIBC_2.28' not found (required by ./openlist)
accept: function not implemented
```

When you see the output of `start server @ 0.0.0.0:5244` and no error is reported afterwards, it means that the operation is successful. The initial password will be output when running for the first time. The program listens to port 5244 by default. Now open `http://ip:5244` You can see the login page, please see [WebDav](../webdav.md) for webdav.

**For Flatpak Users**

If you installed OpenList via Flatpak, use the following commands instead:

```bash
# Start server
flatpak run org.oplist.openlist server

# Show admin info
flatpak run org.oplist.openlist admin

# Generate random admin password
flatpak run org.oplist.openlist admin random

# Set admin password
flatpak run org.oplist.openlist admin set NEW_PASSWORD

# Show version
flatpak run org.oplist.openlist version
```

:::

::: zh-CN
::: tip
手动安装如果有如下提示：是因为[你的 GLIBC 版本太低](../../faq/why.md#lib64-libc-so-6-version-glibc-2-28-not-found-required-by-openlist-或者-accept-function-not-implemented)，建议下载 musl 版本。

```txt
lib64/libc.so.6: version `GLIBC_2.28' not found (required by ./openlist)
accept: function not implemented
```

当你看到 `start server@0.0.0.0:5244` 的输出，之后没有报错，说明操作成功。 第一次运行时会输出初始密码。程序默认监听 5244 端口。 现在打开 `http://ip:5244` 可以看到登录页面，WebDAV 请参阅 [WebDav](../webdav.md)。

**Flatpak 用户**

如果您通过 Flatpak 安装了 OpenList，请使用以下命令：

```bash
# 启动服务器
flatpak run org.oplist.openlist server

# 显示管理员信息
flatpak run org.oplist.openlist admin

# 生成随机管理员密码
flatpak run org.oplist.openlist admin random

# 设置管理员密码
flatpak run org.oplist.openlist admin set NEW_PASSWORD

# 显示版本
flatpak run org.oplist.openlist version
```

<br/>
:::

::: en
::: warning
Versions above v3.25.0 change the password to an encrypted hash value, and the password cannot be calculated directly. If the password is forgotten, it can only be re-**`randomly generated`** or **`manually set`**.
:::

::: zh-CN
::: warning
v3.25.0以上版本将密码改成加密方式存储的hash值，无法直接反算出密码，如果忘记了密码只能通过重新 **`随机生成`** 或者 **`手动设置`**。
:::

::: en
The `xxxx` refers to the names corresponding to different systems/architectures, generally Linux-x86/64 is openlist-linux-amd64.
:::

::: zh-CN
`xxxx` 指的是不同系统/架构对应的名称，一般 Linux-x86/64 为 openlist-linux-amd64。
:::

### Linux

```bash
tar -zxvf openlist-xxxx.tar.gz
chmod +x openlist
./openlist server
./openlist admin
./openlist admin random
./openlist admin set NEW_PASSWORD
```

### macOS

```bash
tar -zxvf openlist-xxxx.tar.gz
chmod +x openlist
./openlist server
./openlist admin
./openlist admin random
./openlist admin set NEW_PASSWORD
```

### Windows

```powershell
Expand-Archive .\openlist-xxxx.zip
.\openlist.exe server
.\openlist.exe admin
.\openlist.exe admin random
.\openlist.exe admin set NEW_PASSWORD
```

## Daemon { lang="en" }

## 守护进程 { lang="zh-CN" }

### Linux

::: en
`vim /usr/lib/systemd/system/openlist.service` add the following content, where `path_openlist` is the path where openlist is located:
:::
::: zh-CN
使用任意方式编辑 `/usr/lib/systemd/system/openlist.service` 并添加如下内容，其中 `path_openlist` 为 OpenList 所在的路径：
:::

```ini
[Unit]
Description=openlist
After=network.target
[Service]
Type=simple
WorkingDirectory=path_openlist
ExecStart=path_openlist/openlist server
Restart=on-failure
[Install]
WantedBy=multi-user.target
```

::: en
Then `systemctl daemon-reload`, now you can use these commands to manage the program:

- Start: `systemctl start openlist`
- Shut down: `systemctl stop openlist`
- Self-start: `systemctl enable openlist`
- Cancel Self-start: `systemctl disable openlist`
- Status: `systemctl status openlist`
- Restart: `systemctl restart openlist`

Can't configure daemon? [**Video Tutorial**](https://www.bilibili.com/video/BV1rF41197Qv?t=187.0)

:::

::: zh-CN
然后，执行 `systemctl daemon-reload` 重载配置，现在你可以使用这些命令来管理程序：

- 启动: `systemctl start openlist`
- 关闭: `systemctl stop openlist`
- 配置开机自启: `systemctl enable openlist`
- 取消开机自启: `systemctl disable openlist`
- 状态: `systemctl status openlist`
- 重启: `systemctl restart openlist`

守护进程不会配置? [**视频教程**](https://www.bilibili.com/video/BV1rF41197Qv?t=187.0)

:::

### macOS

::: en
Edit `~/Library/LaunchAgents/org.openlist.plist` in any way and add the following content, modify `path_openlist` to be the path where OpenList is located, and `path/to/working/dir` to be the working path of OpenList:
:::

::: zh-CN
使用任意方式编辑 `~/Library/LaunchAgents/org.openlist.plist` 并添加如下内容，修改 `path_openlist` 为 OpenList 所在的路径，`path/to/working/dir` 为 OpenList的工作路径:
:::

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
     <dict>
         <key>Label</key>
         <string>org.openlist</string>
         <key>KeepAlive</key>
         <true/>
         <key>ProcessType</key>
         <string>Background</string>
         <key>RunAtLoad</key>
         <true/>
         <key>WorkingDirectory</key>
         <string>path/to/working/dir</string>
         <key>ProgramArguments</key>
         <array>
             <string>path_openlist/openlist</string>
             <string>server</string>
         </array>
     </dict>
</plist>
```

::: en
Then, execute `launchctl load ~/Library/LaunchAgents/org.openlist.plist` to load the configuration, now you can use these commands to manage the program:

- Start: `launchctl start ~/Library/LaunchAgents/org.openlist.plist`
- Close: `launchctl stop ~/Library/LaunchAgents/org.openlist.plist`
- Unload configuration: `launchctl unload ~/Library/LaunchAgents/org.openlist.plist`

:::

::: zh-CN
然后，执行 `launchctl load ~/Library/LaunchAgents/org.openlist.plist` 加载配置，现在你可以使用这些命令来管理程序：

- 开启: `launchctl start ~/Library/LaunchAgents/org.openlist.plist`
- 关闭: `launchctl stop ~/Library/LaunchAgents/org.openlist.plist`
- 卸载配置: `launchctl unload ~/Library/LaunchAgents/org.openlist.plist`

:::

### Windows

#### Method One { lang="en" }

#### 方法1 { lang="zh-CN" }

::: en

1.  Download the newest `nssm` from https://nssm.cc/download.
2.  Unzip the archive and go to the diretory of `nssm.exe`.
3.  Hold Shift and right click on the blank space, then release and press S or select "powershell here", you should now see a blue window named "Windows PowerShell".
4.  Type `.\nssm.exe install openlist`.
5.  Select the path of `openlist.exe` for "Path", e.g. `D:\openlist\openlist.exe`; type `server` for "Argument".
6.  You can custom "Display Name", "Description" and "Startup Type" in "Details" tab.
7.  Go to "I/O" tab and select a file for both "Output (stdout)" and "Output (stderr)", e.g. `D:\openlist\stdout.log`. The file itself (`stdout.log`) may not exist, but the folder (`D:\openlist`) must exist.
8.  Click on "Install Service".
    You can now start the service from services.msc or task manager.

:::

::: zh-CN

1.  在 https://nssm.cc/download 下载最新版本的 `nssm`；
2.  在解压后的文件夹内按住 Shift 并右击空白处，选择“在此处打开 Powershell 窗口”；
3.  在弹出的窗口中输入 `.\nssm.exe install openlist`；
4.  Path 选择 openlist.exe 的路径，如 `D:\openlist\openlist.exe`，Arguments 填 `server`；
5.  Details 选项卡中可以自定义标题和描述，可以选择服务的自启动模式（自动|延迟启动|手动|禁用）；
6.  在 I/O 选项卡为 Output (stdout) 和 Output (stderr) 各自指定一个日志文件的路径，如 `D:\openlist\stdout.log`，文件本身（`stdout.log`）可以不存在，但是指定的目录（`D:\openlist`）必须存在；
7.  点击“Install Service”即可。
    此后可以直接在服务中启动 `openlist`。

:::

#### Method Two { lang="en" }

#### 方法2 { lang="zh-CN" }

::: zh-CN
用 **`.VBS`** 脚本启动和停止，分别创建两个脚本 分别是 `启动.vbs` 和 `停止.vbs`。
直接在和 OpenList 启动程序同级文件夹里面双击启动即可，不用担心没有反应 直接去 浏览器访问即可。
:::

::: en
Use **`.VBS`** script to start and stop, create two scripts respectively `start.vbs` and `stop.vbs`.
Just double-click to start it in the folder at the same level as the OpenList startup program, don't worry about no response, just go to the browser to access it.
:::

::: en
::: info Two startup scripts
**start.vbs**

```bash title="vbscript"
Dim ws
Set ws = Wscript.CreateObject("Wscript.Shell")
ws.run "openlist.exe server",vbhide
Wscript.quit
```

**stop.vbs**

```bash title="vbscript"
Dim ws
Set ws = Wscript.CreateObject("Wscript.Shell")
ws.run "taskkill /f /im openlist.exe",0
Wscript.quit
```

1. If the script will not be created, you can download it yourself: [**Script Download**](https://www.alipan.com/s/DHPMhRtKUzY/folder/63e0961eae317bd4d4d945cda69dbb00f9837fb7)
2. If the script will not be used, you can watch the video: [**reference video**](https://www.bilibili.com/video/BV1wWYTzdE4B)
   How to realize Windows startup automatically, you can refer to the script mentioned above to use the video (second).

:::

::: zh-CN
::: info 两个启动脚本
**启动.vbs**

```bash title="vbscript"
Dim ws
Set ws = Wscript.CreateObject("Wscript.Shell")
ws.run "openlist.exe server",vbhide
Wscript.quit
```

**停止.vbs**

```bash title="vbscript"
Dim ws
Set ws = Wscript.CreateObject("Wscript.Shell")
ws.run "taskkill /f /im openlist.exe",0
Wscript.quit
```

1. 脚本不会创建的可以自行下载：[**脚本下载**](https://www.alipan.com/s/DHPMhRtKUzY/folder/63e0961eae317bd4d4d945cda69dbb00f9837fb7)
2. 脚本不会使用的可以看看视频：[**参考视频**](https://www.bilibili.com/video/BV1wWYTzdE4B)
   如何实现Windows开机自启，可以参考上面提到的脚本使用视频(第二个)

:::

::: en
::: info
For all platform, you can use follow command to silent start, stop and restart. (v3.4.0 and later)

```bash
openlist start
openlist stop
openlist restart
```

:::

::: zh-CN
::: info
对于所有平台，您可以使用以下命令来静默启动、停止和重新启动。 （v3.4.0 及更高版本）

```bash
openlist start
openlist stop
openlist restart
```

:::

## How to update { lang="en" }

## 如何更新 { lang="zh-CN" }

::: en
Download the new version of OpenList and replace the previous one.
:::

::: zh-CN
下载新版 OpenList，把之前的替换了即可。
:::
