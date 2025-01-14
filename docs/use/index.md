---
hide:
  - navigation
  - footer
---

> 如果您觉得这个项目不错对您有所帮助的话，请点击仓库右上角的 Star 并分享给更多的朋友 :octicons-heart-fill-24:{ .heart style="color: red" }

## 一键执行命令

=== ":octicons-globe-16: CDN（推荐）"

    !!! quote ""

        === ":material-home: 中国大陆（默认）"

            ``` bash
            bash <(curl -sSL https://linuxmirrors.cn/main.sh)
            ```

        === ":material-school: 中国大陆教育网"

            ``` bash
            bash <(curl -sSL https://linuxmirrors.cn/main.sh) --edu # (1)!
            ```

            1.  通过 `--edu` 命令选项来使用中国大陆教育单位软件源

        === ":octicons-globe-16: 海外地区"

            ``` bash
            bash <(curl -sSL https://linuxmirrors.cn/main.sh) --abroad # (1)!
            ```

            2.  通过 `--abroad` 命令选项来使用海外软件源

=== ":simple-github: GitHub"

    !!! quote ""

        === ":material-home: 中国大陆（默认）"

            ``` bash
            bash <(curl -sSL https://raw.githubusercontent.com/SuperManito/LinuxMirrors/main/ChangeMirrors.sh)
            ```

        === ":material-school: 中国大陆教育网"

            ``` bash
            bash <(curl -sSL https://raw.githubusercontent.com/SuperManito/LinuxMirrors/main/ChangeMirrors.sh) --edu # (1)!
            ```

            1.  通过 `--edu` 命令选项来使用中国大陆教育单位软件源

        === ":octicons-globe-16: 海外地区"

            ``` bash
            bash <(curl -sSL https://raw.githubusercontent.com/SuperManito/LinuxMirrors/main/ChangeMirrors.sh) --abroad # (1)!
            ```

            2.  通过 `--abroad` 命令选项来使用海外软件源

=== ":simple-gitee: Gitee"

    !!! quote ""

        === ":material-home: 中国大陆（默认）"

            ``` bash
            bash <(curl -sSL https://gitee.com/SuperManito/LinuxMirrors/raw/main/ChangeMirrors.sh)
            ```

        === ":material-school: 中国大陆教育网"

            ``` bash
            bash <(curl -sSL https://gitee.com/SuperManito/LinuxMirrors/raw/main/ChangeMirrors.sh) --edu # (1)!
            ```

            1.  通过 `--edu` 命令选项来使用中国大陆教育单位软件源

        === ":octicons-globe-16: 海外地区"

            ``` bash
            bash <(curl -sSL https://gitee.com/SuperManito/LinuxMirrors/raw/main/ChangeMirrors.sh) --abroad # (1)!
            ```

            1.  通过 `--abroad` 命令选项来使用海外软件源

选项卡分别代表获取脚本途径和脚本内置软件源类型，请在使用前检查目标镜像站是否支持您所使用的操作系统，可以在[软件源列表](/mirrors)中查看具体有哪些软件源。

- ### 注意事项

    <div class="grid cards" markdown>

    -   :material-numeric-1:{style="color: #3CA7E5" .lg} __需使用 `ROOT` 用户执行脚本__

        ---

        切换命令为 `sudo -i` 或 `su root`。不同系统使用的命令不同，因为有些系统没有在初始安装时为 ROOT 账户设置密码（例如 Ubuntu），故需要使用 `sudo -i` 命令来切换至 ROOT

    -   :material-numeric-2:{style="color: #3CA7E5" .lg} __建议使用 `SSH` 远程工具__

        ---

        如果你使用的系统终端界面无法正常显示中文内容那么将导致无法查看交互内容。部分系统会自动开启 SSH 服务，否则请参考 [_关于开启 SSH 远程登录的方法_](#关于开启-ssh-远程登录的方法)

    -   :material-numeric-3:{style="color: #3CA7E5" .lg} __如果是在新系统上首次执行脚本__

        ---

        当前执行方式依赖 `curl` 指令获取脚本内容并执行，但部分操作系统没有预装此软件包，届时则会报错 `Command not found`，安装方法详见下方 [_关于报错 Command not found_](#关于报错-command-not-found)。还可自行复制[源码](https://gitee.com/SuperManito/LinuxMirrors/raw/main/ChangeMirrors.sh)至本地新建任意名称的 `.sh` 脚本，粘贴源码内容后通过 `bash` 指令手动执行

    </div>

- ### 常见问题

    - #### 关于报错 Command not found

        !!! quote ""

            === "Debian 系"

                ``` sh
                apt-get install -y curl
                ```

                > `Debian` &nbsp; `Ubuntu` &nbsp; `Kali` &nbsp; `Linux Mint` &nbsp; `Deepin` &nbsp; `Zorin OS` &nbsp; `Armbian` &nbsp; `Proxmox`

                新装系统需要先执行一遍更新 `apt-get update`

            === "RedHat 系 / OpenCloudOS / openEuler / Anolis OS"

                ``` sh
                dnf install -y curl || yum install -y curl
                ```

                > `Red Hat Enterprise Linux` &nbsp; `CentOS` &nbsp; `Rocky Linux` &nbsp; `AlmaLinux` &nbsp; `Fedora` &nbsp; `OpenCloudOS` &nbsp; `openEuler` &nbsp; `Anolis OS`

            === "openSUSE"

                ``` sh
                zypper install curl
                ```

            === "Arch Linux"

                ``` sh
                pacman -S curl
                ```

            === "Alpine Linux"

                ``` sh
                apk --no-cache add -f curl bash
                ```

            === "Gentoo"

                ``` sh
                emerge --ask curl
                ```

    - #### 关于开启 SSH 远程登录的方法

        !!! quote ""

            - 验证是否已安装 `SSH` 服务

                ``` bash
                ls /etc | grep ssh
                ```
                > 如果没有这个文件夹说明系统未安装 `SSH` 服务，你需要通过包管理工具安装 `openssh` 软件包

            - 设置允许 Root 用户登录

                ``` bash
                cat /etc/ssh/sshd_config | grep -Eq "^[# ]?PermitRootLogin " ; [ $? -eq 0 ] && sed -i 's/^[# ]\?PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config || echo -e "\nPermitRootLogin yes" >> /etc/ssh/sshd_config
                ```

            - 设置密码认证

                ``` bash
                cat /etc/ssh/sshd_config | grep -Eq "^[# ]?PasswordAuthentication " ; [ $? -eq 0 ] && sed -i 's/^[# ]\?PasswordAuthentication.*/PasswordAuthentication yes/g' /etc/ssh/sshd_config || echo -e "\nPasswordAuthentication yes" >> /etc/ssh/sshd_config
                ```

            - 启动/重启 `SSH` 服务

                ``` bash
                ps -ef | grep -q ssh ; [ $? -eq 0 ] && systemctl restart sshd || systemctl enable --now sshd
                ```

            > 命令仅供参考，只适配了部分常见发行版

    - #### 还原已备份的软件源

        !!! quote ""

            === "Debian 系"

                ``` sh
                cp -rf /etc/apt/sources.list.bak /etc/apt/sources.list
                apt-get update
                ```

                > `Debian` &nbsp; `Ubuntu` &nbsp; `Kali` &nbsp; `Linux Mint` &nbsp; `Deepin` &nbsp; `Zorin OS` &nbsp; `Armbian` &nbsp; `Proxmox`

            === "RedHat 系 / OpenCloudOS / openEuler / Anolis OS"

                ``` sh
                cp -rf /etc/yum.repos.d.bak /etc/yum.repos.d
                yum makecache
                ```

                > `Red Hat Enterprise Linux` &nbsp; `CentOS` &nbsp; `Rocky Linux` &nbsp; `AlmaLinux` &nbsp; `Fedora` &nbsp; `OpenCloudOS` &nbsp; `openEuler` &nbsp; `Anolis OS`

            === "openSUSE"

                ``` sh
                cp -rf /etc/zypp/repos.d.bak /etc/zypp/repos.d
                zypper ref
                ```

            === "Arch Linux"

                ``` sh
                cp -rf /etc/pacman.d/mirrorlist.bak /etc/pacman.d/mirrorlist
                pacman -Sy
                ```

            === "Alpine Linux"

                ``` sh
                cp -rf /etc/apk/repositories.bak /etc/apk/repositories
                apk update -f
                ```

            === "Gentoo"

                ``` sh
                cp -rf /etc/portage/make.conf.bak /etc/portage/make.conf
                [ -d /etc/portage/repos.conf ] && cp -rf /etc/portage/repos.conf/gentoo.conf.bak /etc/portage/repos.conf/gentoo.conf
                emerge --sync --quiet
                ```

    - #### 其它

        !!! quote ""

            - 如果提示 `bash: /proc/self/fd/11: No such file or directory`，请切换至 `Root` 用户执行，切换命令为 `sudo -i` 或 `su root`

- ### 关于调用脚本的互联网位置

    项目利用 GitHub Action 在每次提交后自动拷贝源码到文档目录作为网站资源发布，网站托管于知名 CDN 云服务商几乎没有被劫持的风险可放心使用

    当然你也可以使用代码托管仓库的原始地址来调用，这里只是想告诉你为什么会有三个不同的地址，默认的 CDN 地址更易于访问和记忆

- ### 关于未启用的软件源

    脚本遵循系统默认设置即没有启用的软件源（仓库）不会在运行完本脚本后被启用，但是它们也随脚本更换了目标软件源地址，如果你有使用需求请阅读下面的启用方法

    === "Debian 系"

        默认禁用了`deb-src`源码仓库和`proposed`预发布软件源，若需启用请将 `/etc/apt/sources.list` 文件中相关内容的所在行取消注释

        > `Debian` &nbsp; `Ubuntu` &nbsp; `Kali` &nbsp; `Linux Mint` &nbsp; `Deepin` &nbsp; `Zorin OS` &nbsp; `Armbian` &nbsp; `Proxmox`

    === "RedHat 系 / OpenCloudOS / openEuler / Anolis OS"

        部分仓库默认没有启用，若需启用请将 `/etc/yum.repos.d` 目录下相关 repo 文件中的 `enabled` 值修改为 `1`

        > `Red Hat Enterprise Linux` &nbsp; `CentOS` &nbsp; `Rocky Linux` &nbsp; `AlmaLinux` &nbsp; `Fedora` &nbsp; `OpenCloudOS` &nbsp; `openEuler` &nbsp; `Anolis OS`

    === "openSUSE"

        部分仓库默认没有启用，若需启用请将 `/etc/zypp/repos.d` 目录下相关 repo 文件中的 `enabled` 值修改为 `1`


---

## 命令选项（高级用法）

| 名称 | 含义 | 选项值 |
| - | - | :-: |
| `--abroad` | 使用海外软件源 | 无 |
| `--edu` | 使用中国大陆教育网软件源 | 无 |
| `--source` | 指定软件源地址（域名或IP） | 地址 |
| `--source-epel` | 指定 EPEL 附加软件包仓库的软件源地址（域名或IP） | 地址 |
| `--source-security` | 指定 Debian 系统 security 仓库的软件源地址（域名或IP） | 地址 |
| `--source-vault` | 指定 CentOS/AlmaLinux 系统 vault 仓库的软件源地址（域名或IP） | 地址 |
| `--source-portage` | 指定 Gentoo 系统 portage 仓库的软件源地址（域名或IP） | 地址 |
| `--branch` | 指定软件源分支（路径） | 分支名 |
| `--branch-epel` | 指定 EPEL 附加软件包仓库的软件源分支（路径） | 分支名 |
| `--branch-security` | 指定 Debian 系统 security 仓库的软件源分支（路径） | 分支名 |
| `--branch-vault` | 指定 CentOS/AlmaLinux 系统 vault 仓库的软件源分支（路径）   分支名 | 分支名 |
| `--branch-portage` | 指定 Gentoo 系统 portage 仓库的软件源分支（路径） | 分支名 |
| `--codename` | 指定 Debian 系操作系统的版本代号 | 代号名称 |
| `--protocol` | 指定 WEB 协议 | `http` 或 `https` |
| `--use-intranet-source` | 是否优先使用内网软件源地址 | `true` 或 `false` |
| `--use-official-source` | 是否使用目标操作系统的官方软件源 | `true` 或 `false` |
| `--install-epel` | 是否安装 EPEL 附加软件包 | `true` 或 `false` |
| `--close-firewall` | 是否关闭防火墙 | `true` 或 `false` |
| `--backup` | 是否备份原有软件源 | `true` 或 `false` |
| `--upgrade-software` | 是否更新软件包 | `true` 或 `false` |
| `--clean-cache` | 是否清理下载缓存 | `true` 或 `false` |
| `--print-diff` | 是否打印源文件修改前后差异 | `true` 或 `false` |
| `--only-epel` | 仅更换 EPEL 软件源模式 | 无 |
| `--ignore-backup-tips` | 忽略覆盖备份提示（即不覆盖备份） | 无 |
| `--help` | 查看帮助菜单 | 无 |

> 软件源格式 `<指定WEB协议>://<软件源地址>/<软件源分支>`

接下来是一些高级用法的举例

- ### 指定软件源地址

    ``` { .bash .no-copy }
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
        --source mirror.example.com
    ```

- ### 指定软件源仓库分支

    主要使用场景：目标镜像站有对应的系统镜像但是不符合本项目脚本关于软件源分支设置的默认规则

    ??? note "项目默认使用的系统分支名称"

        项目脚本为了适配大的环境不会针对某一镜像站独特的镜像分支名称而单独适配

        | 系统名称 | 涉及的分支名称 |
        | --- | :---: |
        | <a href="https://www.debian.org" target="_blank"><img src="/assets/images/icon/debian.svg" width="16" height="16" style="vertical-align: -0.35em"></a> Debian | debian / debian-archive |
        | <a href="https://cn.ubuntu.com" target="_blank"><img src="/assets/images/icon/ubuntu.svg" width="16" height="16" style="vertical-align: -0.1em"></a> Ubuntu | ubuntu / ubuntu-ports |
        | <a href="https://www.kali.org" target="_blank"><img src="/assets/images/icon/kali-linux.svg" width="16" height="16"></a> Kali Linux | kali |
        | <a href="https://linuxmint.com" target="_blank"><img src="/assets/images/icon/linux-mint.ico" width="16" height="16" style="vertical-align: -0.2em"></a> Linux Mint | linuxmint / ubuntu / ubuntu-ports / debian |
        | <a href="https://www.deepin.org" target="_blank"><img src="/assets/images/icon/deepin.png" width="16" height="16" style="vertical-align: -0.25em"></a> Deepin | deepin |
        | <a href="https://zorin.com/os" target="_blank"><img src="/assets/images/icon/zorin-os.png" width="16" height="16" style="vertical-align: -0.15em"></a> Zorin OS | ubuntu / ubuntu-ports |
        | <a href="https://www.armbian.com" target="_blank"><img src="/assets/images/icon/armbian.png" width="16" height="16" style="vertical-align: -0.2em"></a> Armbian | armbian |
        | <a href="https://www.proxmox.com" target="_blank"><img src="/assets/images/icon/proxmox.svg" width="16" height="16" style="vertical-align: -0.2em"></a> Proxmox | proxmox |
        | <a href="https://access.redhat.com/products/red-hat-enterprise-linux" target="_blank"><img src="/assets/images/icon/redhat.svg" width="16" height="16" style="vertical-align: -0.1em"></a> Red Hat Enterprise Linux :material-information-outline:{ title="9版本使用 <code>CentOS Stream</code>， 7、8版本使用<code>CentOS</code>" } | centos / centos-stream / centos-altarch / centos-vault |
        | <a href="https://fedoraproject.org/zh-Hans" target="_blank"><img src="/assets/images/icon/fedora.ico" width="16" height="16" style="vertical-align: -0.2em"></a> Fedora | fedora |
        | <a href="https://www.centos.org" target="_blank"><img src="/assets/images/icon/centos.svg" width="16" height="16" style="vertical-align: -0.2em"></a> CentOS | centos / centos-stream / centos-altarch / centos-vault |
        | <a href="https://rockylinux.org" target="_blank"><img src="/assets/images/icon/rocky-linux.svg" width="16" height="16" style="vertical-align: -0.25em"></a> Rocky Linux | rocky |
        | <a href="https://almalinux.org/zh-hans" target="_blank"><img src="/assets/images/icon/almalinux.svg" width="16" height="16" style="vertical-align: -0.15em"></a> AlmaLinux | almalinux / almalinux-vault |
        | <a href="https://www.opencloudos.org" target="_blank"><img src="/assets/images/icon/opencloudos.png" width="16" height="16" style="vertical-align: -0.25em"></a> OpenCloudOS | opencloudos |
        | <a href="https://www.openeuler.org/zh" target="_blank"><img src="/assets/images/icon/openeuler.ico" width="16" height="16" style="vertical-align: -0.2em"></a> openEuler | openeuler |
        | <a href="https://openanolis.cn" target="_blank"><img src="/assets/images/icon/anolis.png" width="16" height="16" style="vertical-align: -0.1em"></a> Anolis OS | anolis |
        | <a href="https://www.opensuse.org" target="_blank"><img src="/assets/images/icon/opensuse.svg" width="16" height="16"></a> openSUSE | opensuse |
        | <a href="https://archlinux.org" target="_blank"><img src="/assets/images/icon/arch-linux.ico" width="16" height="16" style="vertical-align: -0.15em"></a> Arch Linux | archlinux / archlinuxarm |
        | <a href="https://www.alpinelinux.org" target="_blank"><img src="/assets/images/icon/alpine.png" width="16" height="16" style="vertical-align: -0.15em"></a> Alpine Linux | alpine |
        | <a href="https://www.gentoo.org" target="_blank"><img src="/assets/images/icon/gentoo.svg" width="16" height="16" style="vertical-align: -0.2em"></a> Gentoo | gentoo / gentoo-portage |


    请看下面的例子

    ``` { .bash title="使用阿里云镜像站的 Rocky Linux 软件源" }
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
      --source mirrors.aliyun.com \
      --branch rockylinux
    ```

    阿里云镜像站的 Rocky Linux 镜像分支名称为 [`rockylinux`](https://mirrors.aliyun.com/rockylinux)，不符合默认规则，但是可以通过命令选项绕过脚本默认规则来实现。

    > 部分系统会同时配置多个仓库的软件源，具体详见命令选项

- ### 单独更换 EPEL 源

    !!! info "EPEL (Extra Packages for Enterprise Linux) 是由 Fedora 组织维护的一个附加软件包仓库，它主要适用于除 Fedora 操作系统以外的红帽系 Linux 发行版，配置 EPEL 仓库已成为广大用户的普遍需求，建议默认安装它"

    有些时候你会发现想使用的镜像站没有 epel 镜像仓库，那么你可以在第一次运行脚本时不安装或更换 epel 源然后再单独执行下面的命令

    ``` bash
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) --only-epel
    ```

- ### 恢复使用官方源

    当你不小心删除了官方源的备份时可以使用此命令来恢复，使用此命令选项后将跳过选择软件源步骤

    ``` bash
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) --use-official-source true
    ```
    > 部分系统不存在官方源例如 `Arch Linux`，届时会自动更换成兼容性较高的阿里云镜像站

- ### 自定义 Debian Security 源

    如果你想尽可能提高服务器的安全性则建议使用官方源，因为镜像同步存在延迟

    ``` bash
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
      --source-security security.debian.org \
      --branch-security debian-security
    ```

- ### 指定 Debian 系 Linux 操作系统的版本代号

    大多数情况下自定义版本代号用于更换系统版本，请看下面的例子

    === "升级 Debian 至最新 12 版本 Bookworm"

        ``` bash
        bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
          --codename bookworm
        ```

    === "将 Debian 版本切换到测试分支"

        ``` bash
        bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
          --codename testing
        ```

    更换软件源后还需要执行系统更新命令 `apt-get dist-upgrade`，并且建议在更新完成并重启系统后重新执行本换源脚本，因为仅更换软件源配置中的系统版本代号可能会在后期使用时产生一些兼容性问题

    ``` { .bash title="若脚本无法实现指定版本代号，你也可以在执行脚本后手动替换" }
    sed -i "s/$(lsb_release -cs)/指定版本代号/g" /etc/apt/sources.list
    ```

- ### 更换 Ubuntu EOF版本软件源

    !!! info "EOF 为生命周期结束的缩写（End Of Life），Ubuntu 迭代速度较快一般非长期支持(LTS)版本的生命周期只有9个月。官方会定期从主仓库移除不在生命周期内的版本仓库目录，届时可能就需要使用镜像站的 `Ubuntu Old Releases` 分支"

    具体版本支持情况详见官方 [Wiki](https://wiki.ubuntu.com/Releases)，关于 `Ubuntu Old Releases` 分支的支持情况详见各镜像站

    ``` bash
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
      --source mirrors.ustc.edu.cn \
      --branch ubuntu-old-releases
    ```

- ### 无人值守（自动化）

    不通过交互完成换源操作，至少需要使用如下命令选项来实现，建议熟悉后再使用

    ``` { .bash .no-copy title="参考命令" }
    bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
      --source mirror.example.com \
      --protocol http \
      --use-intranet-source false \
      --install-epel true \
      --close-firewall true \
      --backup true \
      --upgrade-software false \
      --clean-cache false \
      --ignore-backup-tips
    ```

---

## 定制脚本

如果你是其它项目的开发者希望通过本项目来制作专属脚本，可以在克隆仓库后查看脚本头部注释，目前已经有国内教育单位镜像站的维护者这样做了，下面具体介绍一下定制方法。

首先不建议修改代码的底层逻辑，应尽量与本项目源码保持同步，不过你可以简单去除一些无关内容，例如你可以将三个软件源列表（数组）中的内容删除 `例：mirror_list_default=()`。

相关脚本功能配置是由统一的变量控制的，命令选项亦是如此，这些全局变量由全大写字母构成并遵循下划线命名法，你只需要将这些变量声明在脚本头部即可快速完成定制，具体变量详见如下表格：

| 变量名 | 含义 | 值类型 |
| :-: | :-: | :-: |
| `SOURCE` | 指定软件源地址（域名或IP） | `地址` |
| `SOURCE_EPEL` | 指定 EPEL 附加软件包仓库的软件源地址（域名或IP） | `地址` |
| `SOURCE_SECURITY` | 指定 Debian 系统 security 仓库的软件源地址（域名或IP） | `地址` |
| `SOURCE_VAULT` | 指定 CentOS/AlmaLinux 系统 vault 仓库的软件源地址（域名或IP） | `地址` |
| `SOURCE_PORTAGE` | 指定 Gentoo 系统 portage 仓库的软件源地址（域名或IP） | `地址` |
| `SOURCE_BRANCH` | 指定软件源分支（路径） | `分支名` |
| `SOURCE_EPEL_BRANCH` | 指定 EPEL 附加软件包仓库的软件源分支（路径） | `分支名` |
| `SOURCE_SECURITY_BRANCH` | 指定 Debian 系统 security 仓库的软件源分支（路径） | `分支名` |
| `SOURCE_VAULT_BRANCH` | 指定 CentOS/AlmaLinux 系统 vault 仓库的软件源分支（路径） | `分支名` |
| `SOURCE_PORTAGE_BRANCH` | 指定 Gentoo 系统 portage 仓库的软件源分支（路径） | `分支名` |
| `DEBIAN_CODENAME` | 指定 Debian 系操作系统的版本代号 | `代号名称` |
| `USE_OFFICIAL_SOURCE` | 是否使用目标操作系统的官方软件源 | `true` 或 `false` |
| `USE_INTRANET_SOURCE` | 是否优先使用内网软件源地址 | `true` 或 `false` |
| `WEB_PROTOCOL` | 指定 WEB 协议 | `http` 或 `https` |
| `INSTALL_EPEL` | 是否安装 EPEL 附加软件包 | `true` 或 `false` |
| `ONLY_EPEL` | 仅更换 EPEL 软件源模式 | `true` 或 `false` |
| `CLOSE_FIREWALL` | 是否关闭防火墙 | `true` 或 `false` |
| `BACKUP` | 是否备份原有软件源 | `true` 或 `false` |
| `IGNORE_BACKUP_TIPS` | 忽略覆盖备份提示（即不覆盖备份） | `true` 或 `false` |
| `UPGRADE_SOFTWARE` | 是否更新软件包 | `true` 或 `false` |
| `CLEAN_CACHE` | 是否清理下载缓存 | `true` 或 `false` |
| `PRINT_DIFF` | 是否打印源文件修改前后差异 | `true` 或 `false` |

> 部分变量存在默认值，另外如果对应功能配置不存在那么就可能会出现交互
