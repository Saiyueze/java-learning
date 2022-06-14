# Docker Desktop 安装及配置

## 安装环境说明

OS：windows 11 Pro 21H2  
[Docker Desktop for Windows](https://docs.docker.com/desktop/windows/install/) 直接选择官方默认版本下载即可  

## Docker Desktop 安装说明

双击 Docker Desktop Installer 文件即可进入安装，期间会出现 Configuration 配置界面，界面上有 Install required Windows components for WSL2 和 Add shortcut to desktop 两个选项，如图：  
![Install Docker Desktop for windows Configuration](https://github.com/Saiyueze/java-tutorials/blob/main/media/toolset/docker/docker-desktop-for-windows-install-configuration.png)  

这两个选项可以直接保持默认勾选，或者根据需要进行勾选，之后选择 OK 按钮直到出现 Installation succeeded 说明安装完成，简单无碍。  
打开 Windows Terminal ，输入 docker -v 或者 docker version 查看 docker 的相关信息。如图  
![docker -v or docker version](https://github.com/Saiyueze/java-tutorials/blob/main/media/toolset/docker/docker-v-or-version.png)  
至此 Docker Desktop 已经为你准备好了，现在你可以通过在 Power Shell 中使用 docker 相关的命令操作 docker 了。  

## 优化配置与测试

Docker Desktop 默认安装在 C:\Program Files\Docker 目录，如果使用 Hyper-V 安装后会在 Hyper-V Manager 控制台新建 DockerDesktopVM 虚拟机，该虚拟机默认保存在 C:\ProgramData\DockerDesktop\vm-data 目录中。此配置可以根据需要进行修改。修改的方式如下：  
1.启动 Docker Desktop。  
2.选择 Docker Desktop 图标，选择 Settings 选项如图：  
![Docker Desktop settings](https://github.com/Saiyueze/java-tutorials/blob/main/media/toolset/docker/docker-settings.png)  
3.在配置界面中选择 Resources -> Disk image location 可配置自定义存储本地虚拟机存储路径，如下图  
![Docker Desktop配置Disk image location](https://github.com/Saiyueze/java-tutorials/blob/main/media/toolset/docker/Docker-Desktop-Settings-Resources-Disk-image-location.png)，通过 Browse 选择本机地址，然后选择 Apply & Restart 按钮等待生效。  
4.可以使用 国内的资源地址替换 Docker 默认的资源。如下图：  
![Docker Desktop配置源](https://github.com/Saiyueze/java-tutorials/blob/main/media/toolset/docker/Docker-Desktop-Settings-Docker-Engine.png)  
此处配置地址参考了[看看看傅克](https://juejin.cn/post/7014483618311602207) 文章中的源地址。  

```json
"registry-mirrors": [
    "https://hub-mirror.c.163.com",
    "https://ustc-edu-cn.mirror.aliyuncs.com",
    "https://ghcr.io",
    "https://mirror.baidubce.com"
]
```  
至此优化配置完成。  

