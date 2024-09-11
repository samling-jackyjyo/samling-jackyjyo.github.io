
### 1、dd前运行清理监控文件


```
#!/bin/bash 
#fuck tx process 
rm -rf /usr/local/sa 
rm -rf /usr/local/agenttools 
rm -rf /usr/local/qcloud 
process=(sap100 secu-tcs-agent sgagent64 barad_agent agent agentPlugInD pvdriver ) 
for i in ${process[@]} 
do
for A in $(ps aux |grep $i |grep -v grep |awk '{print $2}') 
do
kill -9 $A 
done 
done 
chkconfig --level 35 postfix off 
service postfix stop 
echo ''>/var/spool/cron/root 
echo '#!/bin/bash' >/etc/rc.local
```

### 2、运行脚本

```
curl -O https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.sh
```

## 功能 1:安装Linux


```
bash reinstall.sh
```

- 不输入版本号，则安装最新版
- 不含 boot 分区（Fedora 例外），不含 swap 分区，最大化利用磁盘空间
- 在虚拟机上，会自动安装合适的官方精简内核
- 安装 Red Hat 需填写 [https://access.redhat.com/downloads/content/rhel](https://access.redhat.com/downloads/content/rhel) 得到的 `qcow2` 镜像链接
- 用户名 `root` 密码 `123@@@`，可能首次开机几分钟后密码才生效
```
bash reinstall.sh centos      9
                  anolis      7|8
                  alma        8|9
                  rocky       8|9
                  redhat      8|9   --img='http://xxx.com/xxx.qcow2'
                  opencloudos 8|9
                  oracle      7|8|9
                  fedora      39|40
                  nixos       24.05
                  debian      9|10|11|12
                  openeuler   20.03|22.03|24.03
                  alpine      3.17|3.18|3.19|3.20
                  opensuse    15.5|15.6|tumbleweed
                  ubuntu      16.04|18.04|20.04|22.04|24.04 [--minimal]
                  kali
                  arch
                  gentoo
```


## 功能 2: 安装Windows ISO
- 用户名 `administrator` 密码 `123@@@`
- 如果远程登录失败，尝试使用用户名 `.\administrator`
- 静态机器会自动配置好 IP，可能首次开机几分钟后才生效

#### 方法 1: 让脚本自动查找 ISO

[](https://github.com/bin456789/reinstall#%E6%96%B9%E6%B3%95-1-%E8%AE%A9%E8%84%9A%E6%9C%AC%E8%87%AA%E5%8A%A8%E6%9F%A5%E6%89%BE-iso)

- 脚本会从 [https://massgrave.dev/genuine-installation-media.html](https://massgrave.dev/genuine-installation-media.html) 查找 iso，该网站提供的 iso 都是官方原版

```shell
bash reinstall.sh windows \
     --image-name 'Windows 10 Enterprise LTSC 2021' \
     --lang zh-cn
```

#### 方法 2: 自行指定 ISO 连接

[](https://github.com/bin456789/reinstall#%E6%96%B9%E6%B3%95-2-%E8%87%AA%E8%A1%8C%E6%8C%87%E5%AE%9A-iso-%E8%BF%9E%E6%8E%A5)

- 如果不知道 `--image-name`，可以随便填，重启后连接 SSH ，根据错误提示重新输入

```shell
bash reinstall.sh windows \
     --image-name 'Windows 10 Enterprise LTSC 2021' \
     --iso 'https://drive.massgrave.dev/en-us_windows_10_enterprise_ltsc_2021_x64_dvd_d289cf96.iso'
```

以下网站可找到 iso 链接

- [https://massgrave.dev/genuine-installation-media.html](https://massgrave.dev/genuine-installation-media.html) (推荐，iso 来自官方，每月更新，包含最新补丁)
- [https://www.microsoft.com/software-download/windows10](https://www.microsoft.com/software-download/windows10) (需用手机 User-Agent 打开)
- [https://www.microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11)
- [https://www.microsoft.com/software-download/windowsinsiderpreviewiso](https://www.microsoft.com/software-download/windowsinsiderpreviewiso) (预览版)
- [https://www.microsoft.com/evalcenter/download-windows-10-enterprise](https://www.microsoft.com/evalcenter/download-windows-10-enterprise)
- [https://www.microsoft.com/evalcenter/download-windows-11-enterprise](https://www.microsoft.com/evalcenter/download-windows-11-enterprise)
- [https://www.microsoft.com/evalcenter/download-windows-11-iot-enterprise-ltsc](https://www.microsoft.com/evalcenter/download-windows-11-iot-enterprise-ltsc)
- [https://www.microsoft.com/evalcenter/download-windows-server-2012-r2](https://www.microsoft.com/evalcenter/download-windows-server-2012-r2)
- [https://www.microsoft.com/evalcenter/download-windows-server-2016](https://www.microsoft.com/evalcenter/download-windows-server-2016)
- [https://www.microsoft.com/evalcenter/download-windows-server-2019](https://www.microsoft.com/evalcenter/download-windows-server-2019)
- [https://www.microsoft.com/evalcenter/download-windows-server-2022](https://www.microsoft.com/evalcenter/download-windows-server-2022)
- [https://www.microsoft.com/evalcenter/download-windows-server-2025](https://www.microsoft.com/evalcenter/download-windows-server-2025)

![image](https://easyimage.01011205.xyz/i/2024/09/11/f689j4.png)


#### 参数说明

[](https://github.com/bin456789/reinstall?tab=readme-ov-file#%E5%8F%82%E6%95%B0%E8%AF%B4%E6%98%8E)

`--image-name` 指定要安装的映像，不区分大小写，常用映像有：

```
Windows 7 Ultimate
Windows 10 Enterprise LTSC 2021
Windows 11 Pro
Windows Server 2022 SERVERDATACENTER
```

使用 `Dism++` 文件菜单 > 打开映像文件，选择要安装的 iso，可以得到映像名称

![image](https://easyimage.01011205.xyz/i/2024/09/11/f7yjnv.png)



#### 支持的系统

[](https://github.com/bin456789/reinstall?tab=readme-ov-file#%E6%94%AF%E6%8C%81%E7%9A%84%E7%B3%BB%E7%BB%9F)

- Windows (Vista ~ 11)
- Windows Server (2008 ~ 2025)
    - Windows Server Essentials *
    - Windows Server (Semi) 年度频道 *
    -  Hyper-V 服务器 *
    - Azure Stack HCI *

* 需填写 iso 链接

#### 脚本会按需安装以下驱动

[](https://github.com/bin456789/reinstall?tab=readme-ov-file#%E8%84%9A%E6%9C%AC%E4%BC%9A%E6%8C%89%E9%9C%80%E5%AE%89%E8%A3%85%E4%BB%A5%E4%B8%8B%E9%A9%B1%E5%8A%A8)

- KVM ([Virtio](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/)、[阿里云](https://www.alibabacloud.com/help/ecs/user-guide/update-red-hat-virtio-drivers-of-windows-instances))
- XEN (XEN、Citrix、AWS)
- AWS ([ENA 网卡](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ena-driver-releases-windows.html)、[NVME 存储控制器](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/nvme-driver-version-history.html))
- GCP ([gVNIC 网卡](https://cloud.google.com/compute/docs/networking/using-gvnic)、[GGA 显卡](https://cloud.google.com/compute/docs/instances/enable-instance-virtual-display))
-  Azure (MANA 网卡)

转载自：[https://github.com/bin456789/reinstall](https://github.com/bin456789/reinstall)
