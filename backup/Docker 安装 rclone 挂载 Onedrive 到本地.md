
## 一、了解 rclone

[rclone](https://www.amjun.com/tag/r/ "查看rclone的所有文章") 是一个命令行工具，可以用来管理各种云存储服务。

它支持超过 40 种不同的云存储服务，包括 Amazon S3, Google Drive, Dropbox, Microsoft OneDrive, Google Cloud Storage, Amazon Drive, OpenStack Swift, Backblaze B2, Yandex Disk, SFTP, WebDAV, FTP, SFTP, Minio, Wasabi, Alibaba OSS,, SwiftStack, Tencent COS, Wasabi, Yandex.Disk, Yandex.Files等等。

- 基本使用
```
rclone 相关
#挂载
rclone mount <网盘名称:网盘路径> <本地路径> [参数] --daemon
#取消挂载
fusermount -qzu <本地路径>
```

## 二、挂载 Onedrive

### 1. 获取 token

下载 win版本的 [rclone](https://rclone.org/downloads/)，解压后输入以管理员的 cmd 进入文件夹，运行如下命令：
```
net stop winnat
net start winnat
rclone authorize onedrive
```

运行完后可能弹出浏览器让你登录，登录完成后就可以在命令行查看到 token。
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xt841l-0.png)

### 2. 配置 onedrive
```
docker run --rm -it \
-v /home/docker/rclone/config:/config/rclone \
rclone/rclone config
```

这里是输入 [onedrive](https://www.amjun.com/tag/o/ "查看onedrive的所有文章") 相关配置，按下图操作即可：
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xtnxjz-0.png)

接下来是选[网盘](https://www.amjun.com/tag/wp/ "查看网盘的所有文章")的类型，找到网盘 Microsoft OneDrive 的编号即可，我这里是 31，编号可能有变动。

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xtr9wi-0.png)

输入 token 时，一定要复制全，大括号里面的全部需要复制。

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xtvrcd-0.png)


接下来继续按下图操作，就可以了。

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xu6b8g-0.png)

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/12/xu8c65-0.png)


到这里配置就完成了。

### 3. 挂载 Onedrive

```
docker run -d  --name rclone \
-v /home/docker/rclone/config:/config/rclone \
-v /home/docker/rclone/onedrive:/onedrive:shared \
--device /dev/fuse --cap-add SYS_ADMIN --security-opt apparmor:unconfined \
--restart always \
rclone/rclone \
mount oneDrive:/ /onedrive --cache-dir /tmp --allow-other --vfs-cache-mode writes --allow-non-empty
```

然后进入 `/home/docker/rclone/onedrive` 文件夹，输入`ls`命令即可发现挂载成功。

转载自：[Docker 安装 rclone 挂载 Onedrive 到本地](https://www.amjun.com/1058.html)